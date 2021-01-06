---
title: Dayanıklı Entity Framework Core SQL bağlantıları uygulama
description: Dayanıklı Entity Framework Core SQL bağlantılarını nasıl uygulayacağınızı öğrenin. Bu teknik, Bulutta Azure SQL veritabanı kullanılırken özellikle önemlidir.
ms.date: 10/16/2018
ms.openlocfilehash: cae3550ce301750949b042957d5d10f0167e614c
ms.sourcegitcommit: 88fbb019b84c2d044d11fb4f6004aec07f2b25b1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97899567"
---
# <a name="implement-resilient-entity-framework-core-sql-connections"></a>Dayanıklı Entity Framework Core SQL bağlantıları uygulama

Azure SQL DB 'de Entity Framework (EF) Core zaten iç veritabanı bağlantı dayanıklılığı ve yeniden deneme mantığı sağlar. Ancak dayanıklı <xref:Microsoft.EntityFrameworkCore.DbContext> [EF Core bağlantılarına](/ef/core/miscellaneous/connection-resiliency)sahip olmak istiyorsanız her bağlantı için Entity Framework yürütme stratejisini etkinleştirmeniz gerekir.

Örneğin, EF Core bağlantı düzeyindeki aşağıdaki kod, bağlantı başarısız olursa yeniden denenen dayanıklı SQL bağlantılarına izin verir.

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

## <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a>BeginTransaction ve birden çok Dbbağlamlarını kullanarak yürütme stratejileri ve açık işlemler

EF Core bağlantılarında yeniden denemeler etkinleştirildiğinde, EF Core kullanarak gerçekleştirdiğiniz her işlem kendi yeniden denenebilir işlemi haline gelir. Her sorgu ve her bir çağrı, `SaveChanges` geçici bir hata oluşursa birim olarak yeniden denenir.

Ancak, kodunuz kullanarak bir işlem başlatırsa `BeginTransaction` , birim olarak değerlendirilmesi gereken kendi işlem grubunuzu tanımlamanız gerekir. Bir hata oluşursa işlem içindeki her şeyin geri alınması gerekmez.

Bir EF Execution strateji (yeniden deneme ilkesi) kullanırken bu işlemi yürütmeye çalışırsanız ve `SaveChanges` birden çok Dbbağlamdan çağırdığınızda, bunun gibi bir özel durum alırsınız:

> System. InvalidOperationException: yapılandırılan ' Sqlserverretryingexecutionstrateji ' yürütme stratejisi, Kullanıcı tarafından başlatılan işlemleri desteklemez. İşlemdeki tüm işlemleri yeniden kullanılabilir bir birim olarak yürütmek için ' DbContext. Database. Createexecutionstrateji () ' tarafından döndürülen yürütme stratejisini kullanın.

Çözüm, yürütülmesi gereken her şeyi temsil eden bir temsilciyle EF yürütme stratejisini el ile çağırmalıdır. Geçici bir hata oluşursa yürütme stratejisi temsilciyi yeniden çağırır. Örneğin, aşağıdaki kod, \_ bir ürünü güncelleştirirken ve ardından Productpricechangedıntegrationevent nesnesini kaydederek farklı bir DbContext kullanması gereken iki birden çok DbContext (catalogcontext ve ıntegrationeventlogcontext) Ile eShopOnContainers içinde nasıl uygulandığını gösterir.

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

Birincisi <xref:Microsoft.EntityFrameworkCore.DbContext> `_catalogContext` ve ikincisi `DbContext` `_catalogIntegrationEventService` nesne içindedir. Yürütme eylemi, `DbContext` BIR EF yürütme stratejisi kullanılarak tüm nesneler genelinde gerçekleştirilir.

Bu birden çok yürütmeyi başarmak için, `DbContext` `SaveEventAndCatalogContextChangesAsync` `ResilientTransaction` aşağıdaki kodda gösterildiği gibi bir sınıfı kullanır:

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

`ResilientTransaction.ExecuteAsync`Yöntemi, geçirilen () ' dan bir işlem `DbContext` başlatır `_catalogContext` ve ardından `EventLogService` Bu işlemi kullanarak değişiklikleri konumundan kaydeder `IntegrationEventLogContext` ve sonra işlemin tamamını kaydeder.

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
            await using var transaction = await _context.Database.BeginTransactionAsync();
            await action();
            await transaction.CommitAsync();
        });
    }
}
```

## <a name="additional-resources"></a>Ek kaynaklar

- **ASP.NET MVC uygulamasında EF ile bağlantı dayanıklılığı ve komut Yakaalımı** \
  [https://docs.microsoft.com/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application)

- **Cesar de La Torre. Esnek Entity Framework Core SQL bağlantılarını ve Işlemlerini kullanma** \
  <https://devblogs.microsoft.com/cesardelatorre/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/>

>[!div class="step-by-step"]
>[Önceki](implement-retries-exponential-backoff.md) 
> [Sonraki](use-httpclientfactory-to-implement-resilient-http-requests.md)
