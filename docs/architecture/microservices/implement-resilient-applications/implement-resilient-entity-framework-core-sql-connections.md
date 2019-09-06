---
title: Dayanıklı Entity Framework Core SQL bağlantıları uygulama
description: Dayanıklı Entity Framework Core SQL bağlantılarını nasıl uygulayacağınızı öğrenin. Bu teknik, Bulutta Azure SQL veritabanı kullanılırken özellikle önemlidir.
ms.date: 10/16/2018
ms.openlocfilehash: 3bf5c1827cee1da69aeccdc9f15573c301fc9363
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296071"
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

EF Core bağlantılarında yeniden denemeler etkinleştirildiğinde, EF Core kullanarak gerçekleştirdiğiniz her işlem kendi yeniden kullanılabilir işlem haline gelir. Her sorgu ve her bir çağrı `SaveChanges` , geçici bir hata oluşursa birim olarak yeniden denenir.

Ancak, kodunuz kullanarak `BeginTransaction`bir işlem başlatırsa, birim olarak değerlendirilmesi gereken kendi işlem grubunuzu tanımlamanız gerekir. Bir hata oluşursa işlem içindeki her şeyin geri alınması gerekmez.

Bir EF Execution strateji (yeniden deneme ilkesi) kullanırken bu işlemi yürütmeye çalışırsanız ve birden çok dbbağlamdan `SaveChanges` çağırdığınızda, bunun gibi bir özel durum alırsınız:

> System. InvalidOperationException: Yapılandırılan ' Sqlserverretryingexecutionstrateji ' yürütme stratejisi, Kullanıcı tarafından başlatılan işlemleri desteklemiyor. İşlemdeki tüm işlemleri yeniden kullanılabilir bir birim olarak yürütmek için ' DbContext. Database. Createexecutionstrateji () ' tarafından döndürülen yürütme stratejisini kullanın.

Çözüm, yürütülmesi gereken her şeyi temsil eden bir temsilciyle EF yürütme stratejisini el ile çağırmalıdır. Geçici bir hata oluşursa, yürütme stratejisi temsilciyi tekrar çağıracaktır. Örneğin, aşağıdaki kod, bir ürünü güncelleştirirken ve daha sonra kaydettiğinizde, iki birden çok DbContext (\_catalogcontext ve ıntegrationeventlogcontext) ile eshoponcontainers içinde nasıl uygulandığını göstermektedir. Productpricechangedıntegrationevent nesnesi, farklı bir DbContext kullanması gerekir.

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

Birincisi <xref:Microsoft.EntityFrameworkCore.DbContext> ve`_catalogContext` ikincisi `DbContext` nesne içindedir`_integrationEventLogService` . Yürütme eylemi, bir EF yürütme stratejisi `DbContext` kullanılarak tüm nesneler genelinde gerçekleştirilir.

Bu birden çok `DbContext` yürütmeyi `SaveEventAndCatalogContextChangesAsync` başarmak için, aşağıdaki kodda `ResilientTransaction` gösterildiği gibi bir sınıfı kullanır:

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

`IntegrationEventLogContext` `EventLogService` Yöntemi, geçirilen `DbContext` (`_catalogContext`) ' dan bir işlem başlatır ve ardından bu işlemi kullanarak değişiklikleri konumundan kaydeder ve sonra işlemin tamamını kaydeder. `ResilientTransaction.ExecuteAsync`

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

- **ASP.NET MVC uygulamasında EF ile bağlantı dayanıklılığı ve komut Yakaalımı** \
  [https://docs.microsoft.com/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application)

- **Cesar de La Torre. Esnek Entity Framework Core SQL bağlantılarını ve Işlemlerini kullanma** \
  <https://devblogs.microsoft.com/cesardelatorre/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/>

>[!div class="step-by-step"]
>[Önceki](implement-retries-exponential-backoff.md)İleri
>[](explore-custom-http-call-retries-exponential-backoff.md)
