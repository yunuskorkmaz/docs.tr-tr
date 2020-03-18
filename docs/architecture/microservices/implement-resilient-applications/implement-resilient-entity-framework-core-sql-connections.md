---
title: Esnek Entity Framework Core SQL bağlantılarını uygulama
description: Esnek Entity Framework Core SQL bağlantılarını nasıl uygulayacağınızı öğrenin. Bu teknik özellikle bulutta Azure SQL Veritabanı kullanırken önemlidir.
ms.date: 10/16/2018
ms.openlocfilehash: 7a047edca21d63a451e90f407b23f3358d461330
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78241071"
---
# <a name="implement-resilient-entity-framework-core-sql-connections"></a>Esnek Entity Framework Core SQL bağlantılarını uygulama

Azure SQL DB için Entity Framework (EF) Core zaten dahili veritabanı bağlantısı esnekliği ve yeniden deneme mantığı sağlar. Ancak [esnek EF Core bağlantılarına](/ef/core/miscellaneous/connection-resiliency)sahip <xref:Microsoft.EntityFrameworkCore.DbContext> olmak istiyorsanız, her bağlantı için Varlık Çerçevesi yürütme stratejisini etkinleştirmeniz gerekir.

Örneğin, EF Core bağlantı düzeyindeki aşağıdaki kod, bağlantı başarısız olursa yeniden denenen esnek SQL bağlantılarını sağlar.

```csharp
// Startup.cs from any ASP.NET Core Web API
public class Startup
{
    // Other code ...
    public IServiceProvider ConfigureServices(IServiceCollection services)
    {
        // ...
        services.AddDbContext<CatalogContext>(options =>
        {
            options.UseSqlServer(Configuration["ConnectionString"],
            sqlServerOptionsAction: sqlOptions =>
            {
                sqlOptions.EnableRetryOnFailure(
                maxRetryCount: 10,
                maxRetryDelay: TimeSpan.FromSeconds(30),
                errorNumbersToAdd: null);
            });
        });
    }
//...
}
```

## <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a>BeginTransaction ve birden çok DbContexts kullanarak yürütme stratejileri ve açık işlemler

EF Core bağlantılarında yeniden denemeler etkinleştirildiğinde, EF Core kullanarak gerçekleştirdiğiniz her işlem kendi yeniden çalışılabilir işlemi haline gelir. Geçici bir hata `SaveChanges` oluşursa, her sorgu ve her çağrı birim olarak yeniden denenecektir.

Ancak, kodunuz kullanarak `BeginTransaction`bir işlem başlatırsa, birim olarak kabul edilmesi gereken kendi işlem grubunuzu tanımlıyorsunuz. Bir hata oluşursa, işlem içindeki her şeyin geri alınması gerekir.

Bir EF yürütme stratejisi (yeniden deneme ilkesi) kullanırken bu `SaveChanges` işlemi yürütmeye çalışırsanız ve birden çok DbContext'dan arama nız varsa, bunun gibi bir özel durum alırsınız:

> System.InvalidOperationException: Yapılandırılan yürütme stratejisi 'SqlServerRetryingExecutionStrategy' kullanıcı tarafından başlatılan hareketleri desteklemez. İşlemdeki tüm işlemleri geri alabilir birim olarak yürütmek için 'DbContext.Database.CreateExecutionStrategy()' tarafından döndürülen yürütme stratejisini kullanın.

Çözüm, yürütülmesi gereken her şeyi temsil eden bir temsilciyle EF yürütme stratejisini el ile çağırmaktır. Geçici bir hata oluşursa yürütme stratejisi temsilciyi yeniden çağırır. Örneğin, aşağıdaki kod, bir ürünü güncellerken ve farklı bir DbContext\_kullanması gereken ProductPriceChangedIntegrationEvent nesnesini kaydederken iki kez birden fazla DbContexts (catalogContext ve IntegrationEventLogContext) ile eShopOnContainers'da nasıl uygulandığını gösterir.

```csharp
public async Task<IActionResult> UpdateProduct(
    [FromBody]CatalogItem productToUpdate)
{
    // Other code ...

    var oldPrice = catalogItem.Price;
    var raiseProductPriceChangedEvent = oldPrice != productToUpdate.Price;

    // Update current product
    catalogItem = productToUpdate;

    // Save product's data and publish integration event through the Event Bus
    // if price has changed
    if (raiseProductPriceChangedEvent)
    {
        //Create Integration Event to be published through the Event Bus
        var priceChangedEvent = new ProductPriceChangedIntegrationEvent(
          catalogItem.Id, productToUpdate.Price, oldPrice);

       // Achieving atomicity between original Catalog database operation and the
       // IntegrationEventLog thanks to a local transaction
       await _catalogIntegrationEventService.SaveEventAndCatalogContextChangesAsync(
           priceChangedEvent);

       // Publish through the Event Bus and mark the saved event as published
       await _catalogIntegrationEventService.PublishThroughEventBusAsync(
           priceChangedEvent);
    }
    // Just save the updated product because the Product's Price hasn't changed.
    else
    {
        await _catalogContext.SaveChangesAsync();
    }
}
```

Birincisi, <xref:Microsoft.EntityFrameworkCore.DbContext> `_catalogContext` ikincisi `DbContext` nesnenin `_catalogIntegrationEventService` içindedir. Commit eylemi, bir `DbContext` EF yürütme stratejisi kullanılarak tüm nesneler arasında gerçekleştirilir.

Bu birden `DbContext` çok işlemeyi `ResilientTransaction` gerçekleştirmek için, aşağıdaki kodda gösterildiği gibi bir sınıf `SaveEventAndCatalogContextChangesAsync` kullanır:

```csharp
public class CatalogIntegrationEventService : ICatalogIntegrationEventService
{
    //…
    public async Task SaveEventAndCatalogContextChangesAsync(
        IntegrationEvent evt)
    {
        // Use of an EF Core resiliency strategy when using multiple DbContexts
        // within an explicit BeginTransaction():
        // https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency
        await ResilientTransaction.New(_catalogContext).ExecuteAsync(async () =>
        {
            // Achieving atomicity between original catalog database
            // operation and the IntegrationEventLog thanks to a local transaction
            await _catalogContext.SaveChangesAsync();
            await _eventLogService.SaveEventAsync(evt,
                _catalogContext.Database.CurrentTransaction.GetDbTransaction());
        });
    }
}
```

Yöntem `ResilientTransaction.ExecuteAsync` `DbContext` temelde geçirilen ()`_catalogContext`bir işlem başlar `EventLogService` ve sonra değişiklikleri kaydetmek `IntegrationEventLogContext` için bu hareketi kullanır ve sonra tüm işlem işler.

```csharp
public class ResilientTransaction
{
    private DbContext _context;
    private ResilientTransaction(DbContext context) =>
        _context = context ?? throw new ArgumentNullException(nameof(context));

    public static ResilientTransaction New (DbContext context) =>
        new ResilientTransaction(context);

    public async Task ExecuteAsync(Func<Task> action)
    {
        // Use of an EF Core resiliency strategy when using multiple DbContexts
        // within an explicit BeginTransaction():
        // https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency
        var strategy = _context.Database.CreateExecutionStrategy();
        await strategy.ExecuteAsync(async () =>
        {
            using (var transaction = _context.Database.BeginTransaction())
            {
                await action();
                transaction.Commit();
            }
        });
    }
}
```

## <a name="additional-resources"></a>Ek kaynaklar

- **ASP.NET MVC Uygulamasında EF ile Bağlantı Esnekliği ve Komut Durdurma** \
  [https://docs.microsoft.com/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application)

- **Cesar de la Torre. Esnek Varlık Çerçeve Temel SQL Bağlantı ve Hareketlerini Kullanma** \
  <https://devblogs.microsoft.com/cesardelatorre/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/>

>[!div class="step-by-step"]
>[Önceki](implement-retries-exponential-backoff.md)
>[Sonraki](use-httpclientfactory-to-implement-resilient-http-requests.md)
