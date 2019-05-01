---
title: Dayanıklı Entity Framework Core SQL bağlantıları uygulama
description: Dayanıklı Entity Framework Core SQL bağlantıları uygulama hakkında bilgi edinin. Bu yöntem Azure SQL veritabanı bulutta kullanırken özellikle önemlidir.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/16/2018
ms.openlocfilehash: b056df033a584bc51fed5ccd52a58a6331298aa6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61818670"
---
# <a name="implement-resilient-entity-framework-core-sql-connections"></a>Dayanıklı Entity Framework Core SQL bağlantıları uygulama

Azure SQL DB için Entity Framework (EF) çekirdek zaten iç veritabanı bağlantı dayanıklılığı ve yeniden deneme mantığı sağlar. Ancak her biri için Entity Framework yürütme stratejisini etkinleştirmek gereken <xref:Microsoft.EntityFrameworkCore.DbContext> olmasını istiyorsanız bağlantı [dayanıklı EF Core bağlantıları](/ef/core/miscellaneous/connection-resiliency).

Örneğin, aşağıdaki kodu EF Core bağlantı düzeyinde bağlantı başarısız olursa şartıyla dayanıklı SQL bağlantısı sağlar.

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

## <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a>Yürütme stratejileri ve BeginTransaction ve birden çok DbContexts kullanarak açık işlemleri

EF Core bağlantıları yeniden deneme etkinleştirildiğinde, EF Core kullanarak gerçekleştirdiğiniz her işlem yeniden denenebilir kendi işlem olur. Her sorgu ve her çağrı `SaveChanges` geçici bir hata oluşursa bir birim olarak yeniden denenecek.

Ancak, kodunuzu kullanarak bir işlem başlatırsa `BeginTransaction`, bir birim olarak kabul edilmesi için gereken işlemleri kendi grubu tanımlayacağınız. İşlem içinde her şeyi bir hata oluşursa geri alınması gerekir.

EF yürütme stratejisi (yeniden deneme ilkesi) kullanılırken, işlem yürütme denerseniz ve çağırmanızı `SaveChanges` birden çok DbContexts bunun gibi bir özel durum elde edersiniz:

> System.InvalidOperationException: 'SqlServerRetryingExecutionStrategy' yapılandırılmış yürütme stratejisi, kullanıcı tarafından başlatılan işlemleri desteklemiyor. İşlem yeniden denenebilir bir birim olarak tüm işlemleri yürütmek için 'DbContext.Database.CreateExecutionStrategy()' tarafından döndürülen yürütme stratejisi kullanın.

El ile yürütülmesi gereken her şeyi temsil eden bir temsilci ile EF yürütme stratejisi çağırmak için kullanılan çözümüdür. Geçici bir hata oluşursa yürütme stratejisi temsilciyi yeniden çağırır. Örneğin, aşağıdaki kodu göster nasıl, iki hizmetine birden çok DbContexts gerçekleştirdiğini (\_catalogContext ve IntegrationEventLogContext) ürün ve sonra kaydetme güncelleştirilirken Farklı bir DbContext kullanması gereken ProductPriceChangedIntegrationEvent nesnesi.

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

İlk <xref:Microsoft.EntityFrameworkCore.DbContext> olduğu `_catalogContext` ve ikinci `DbContext` içindeki `_integrationEventLogService` nesne. Tüm işleme eylemi gerçekleştiren `DbContext` bir EF yürütme stratejisi kullanarak nesneleri.

Bu çok elde etmek için `DbContext` işlemenin `SaveEventAndCatalogContextChangesAsync` kullanan bir `ResilientTransaction` aşağıdaki kodda gösterildiği gibi sınıfı:

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

`ResilientTransaction.ExecuteAsync` Yöntemi temel bir işlemden geçirilen başlar `DbContext` (`_catalogContext`) ve ardından `EventLogService` değişiklikleri kaydetmek için bu işlem kullanmak `IntegrationEventLogContext` ve ardından tüm hareketi tamamlar.

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

- **Bağlantı dayanıklılığı ve komut durdurma bir ASP.NET MVC uygulamasındaki EF ile** \
  [https://docs.microsoft.com/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application)

- **Cesar de la Torre. Dayanıklı Entity Framework Core SQL bağlantıları ve işlemleri kullanma** \
  <https://devblogs.microsoft.com/cesardelatorre/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/>

>[!div class="step-by-step"]
>[Önceki](implement-retries-exponential-backoff.md)
>[İleri](explore-custom-http-call-retries-exponential-backoff.md)
