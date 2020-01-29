---
title: Dayanıklı Entity Framework Core SQL bağlantıları uygulama
description: Dayanıklı Entity Framework Core SQL bağlantılarını nasıl uygulayacağınızı öğrenin. Bu teknik, Bulutta Azure SQL veritabanı kullanılırken özellikle önemlidir.
ms.date: 10/16/2018
ms.openlocfilehash: 7899fc263ab3cde6ac2410ca614a7e5fa285576b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732733"
---
# <a name="implement-resilient-entity-framework-core-sql-connections"></a>Dayanıklı Entity Framework Core SQL bağlantıları uygulama

Azure SQL DB 'de Entity Framework (EF) Core zaten iç veritabanı bağlantı dayanıklılığı ve yeniden deneme mantığı sağlar. Ancak dayanıklı [EF Core bağlantılarına](/ef/core/miscellaneous/connection-resiliency)sahip olmak istiyorsanız her <xref:Microsoft.EntityFrameworkCore.DbContext> bağlantı için Entity Framework yürütme stratejisini etkinleştirmeniz gerekir.

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

EF Core bağlantılarında yeniden denemeler etkinleştirildiğinde, EF Core kullanarak gerçekleştirdiğiniz her işlem kendi yeniden kullanılabilir işlem haline gelir. Her sorgu ve her `SaveChanges` çağrısı, geçici bir hata oluşursa birim olarak yeniden denenir.

Ancak, kodunuz `BeginTransaction`kullanarak bir işlem başlatırsa, birim olarak değerlendirilmesi gereken kendi işlem grubunuzu tanımlamanız gerekir. Bir hata oluşursa işlem içindeki her şeyin geri alınması gerekmez.

Bir EF Execution strateji (yeniden deneme ilkesi) kullanırken bu işlemi yürütmeye çalışırsanız ve birden çok Dbbağlamdan `SaveChanges` çağırdığınızda, bunun gibi bir özel durum alırsınız:

> System. InvalidOperationException: yapılandırılan ' Sqlserverretryingexecutionstrateji ' yürütme stratejisi, Kullanıcı tarafından başlatılan işlemleri desteklemez. İşlemdeki tüm işlemleri yeniden kullanılabilir bir birim olarak yürütmek için ' DbContext. Database. Createexecutionstrateji () ' tarafından döndürülen yürütme stratejisini kullanın.

Çözüm, yürütülmesi gereken her şeyi temsil eden bir temsilciyle EF yürütme stratejisini el ile çağırmalıdır. Geçici bir hata oluşursa, yürütme stratejisi temsilciyi tekrar çağıracaktır. Örneğin, aşağıdaki kod, bir ürünü güncelleştirirken iki birden çok DbContext (\_catalogContext ve ıntegrationeventlogcontext) ile eShopOnContainers içinde nasıl uygulandığını gösterir ve ardından Productpricechangedıntegrationevent nesnesini kaydederek farklı bir DbContext kullanması gerekir.

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

İlk <xref:Microsoft.EntityFrameworkCore.DbContext> `_catalogContext` ve ikinci `DbContext` `_catalogIntegrationEventService` nesne içindedir. Yürütme eylemi, bir EF yürütme stratejisi kullanılarak tüm `DbContext` nesneleri genelinde gerçekleştirilir.

Bu birden çok `DbContext` işlemesini başarmak için, `SaveEventAndCatalogContextChangesAsync` aşağıdaki kodda gösterildiği gibi bir `ResilientTransaction` sınıfı kullanır:

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

`ResilientTransaction.ExecuteAsync` yöntemi, geçilen `DbContext` (`_catalogContext`) bir işlem başlatır ve ardından `EventLogService` değişiklikleri `IntegrationEventLogContext` kaydetmek için bu işlemi kullanır ve sonra tüm işlemi kaydeder.

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

- **ASP.NET MVC UYGULAMASıNDA EF Ile bağlantı dayanıklılığı ve komut yakalaşmayı** \
  [https://docs.microsoft.com/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application)

- **Cesar de La Torre. Esnek Entity Framework Core SQL bağlantılarını ve Işlemlerini kullanma** \
  <https://devblogs.microsoft.com/cesardelatorre/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/>

>[!div class="step-by-step"]
>[Önceki](implement-retries-exponential-backoff.md)
>[İleri](explore-custom-http-call-retries-exponential-backoff.md)
