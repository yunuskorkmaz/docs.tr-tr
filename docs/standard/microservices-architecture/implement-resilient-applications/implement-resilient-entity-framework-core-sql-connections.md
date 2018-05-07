---
title: Esnek Entity Framework Çekirdek SQL bağlantıları uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Esnek Entity Framework Çekirdek SQL bağlantıları uygulama
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 54d0df517514c359c155de35d34e1e0f56eed4eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="implementing-resilient-entity-framework-core-sql-connections"></a>Esnek Entity Framework Çekirdek SQL bağlantıları uygulama

Azure SQL DB için Entity Framework Çekirdek zaten iç veritabanı bağlantısı dayanıklılık ve yeniden deneme mantığı sağlar. Ancak sahip olmak istiyorsanız her DbContext bağlantısı için Entity Framework yürütme stratejisi etkinleştirmeniz gerekiyor [dayanıklı EF çekirdek bağlantıları](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency).

Örneği için aşağıdaki kodu EF çekirdek bağlantı düzeyinde bağlantı başarısız olursa yeniden denenir dayanıklı SQL bağlantıları sağlar.

```csharp
// Startup.cs from any ASP.NET Core Web API
public class Startup
{
    // Other code ...
    public IServiceProvider ConfigureServices(IServiceCollection services)
    {
        // ...
        services.AddDbContext<OrderingContext>(options =>
        {
            options.UseSqlServer(Configuration["ConnectionString"],
            sqlServerOptionsAction: sqlOptions =>
            {
                sqlOptions.EnableRetryOnFailure(
                maxRetryCount: 5,
                maxRetryDelay: TimeSpan.FromSeconds(30),
                errorNumbersToAdd: null);
            });
        });
    }
//...
}
```

## <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a>Yürütme stratejilerini ve BeginTransaction ve birden çok DbContexts kullanarak açık işlemleri

EF çekirdek bağlantıları yeniden deneme etkinleştirildiğinde, EF çekirdek kullanarak gerçekleştirdiğiniz her işlem yeniden denenebilir çalışması haline gelir. Geçici bir hata oluşursa, her sorgu ve her çağrı SaveChanges bir birim olarak yeniden denenecek.

Ancak, kodunuzu BeginTransaction kullanarak bir işlem başlatır, bir birim olarak kabul edilmesi için gereken işlemleri kendi grubunun tanımlıyorsanız — işlem içinde her şeyi sahip olması alındı geri bir hata oluşursa. EF yürütme stratejisi (yeniden deneme ilkesi) kullanırken bu işlemi yürütme girişimi ve işlemde birden çok DbContexts birkaç SaveChanges çağrılarından dahil aşağıdaki gibi bir özel durum görürsünüz.

> System.InvalidOperationException: 'SqlServerRetryingExecutionStrategy' yapılandırılmış yürütme stratejisi kullanıcı tarafından başlatılan işlemleri desteklemez. İşlem yeniden denenebilir bir birim olarak tüm işlemleri yürütmek için 'DbContext.Database.CreateExecutionStrategy()' tarafından döndürülen yürütme stratejisi kullanın.

Çözüm, yürütülecek gereken her şeyi temsil eden bir temsilci ile EF yürütme stratejisi el ile çağırmaktır. Geçici bir hata oluşursa, yürütme stratejisi temsilci yeniden çağırır. Örneğin, aşağıdaki kodu göster nasıl şu iki eShopOnContainers uygulanan birden çok DbContexts (\_catalogContext ve IntegrationEventLogContext) ürün ve ardından kaydetme güncelleştirirken ProductPriceChangedIntegrationEvent nesne, farklı bir DbContext kullanması gerekir.

```csharp
public async Task<IActionResult> UpdateProduct([FromBody]CatalogItem
    productToUpdate)
{
    // Other code ...
    // Update current product
    catalogItem = productToUpdate;

    // Use of an EF Core resiliency strategy when using multiple DbContexts
    // within an explicit transaction
    // See:
    // https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency
    var strategy = _catalogContext.Database.CreateExecutionStrategy();
    await strategy.ExecuteAsync(async () =>
    {
        // Achieving atomicity between original Catalog database operation and the
        // IntegrationEventLog thanks to a local transaction
        using (var transaction = _catalogContext.Database.BeginTransaction())
        {
            _catalogContext.CatalogItems.Update(catalogItem);
            await _catalogContext.SaveChangesAsync();
            // Save to EventLog only if product price changed
            if (raiseProductPriceChangedEvent)
            await _integrationEventLogService.SaveEventAsync(priceChangedEvent);
            transaction.Commit();
        }
    });
}
```

İlk DbContext olan \_catalogContext ve ikinci DbContext içinde olduğunu \_integrationEventLogService nesnesi. Yürütme eylemi EF yürütme stratejisi kullanarak birden çok DbContexts gerçekleştirilir.

## <a name="additional-resources"></a>Ek kaynaklar

-   **Bağlantı dayanıklılığı ve Entity Framework komut kişiler tarafından ele**
    [*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)

-   **Cesar de la Torre. Esnek Entity Framework Çekirdek Sql bağlantıları ve işlemleri kullanma**
    <https://blogs.msdn.microsoft.com/cesardelatorre/2017/03/26/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/>


>[!div class="step-by-step"]
[Önceki] (uygulama-yeniden deneme-üstel-backoff.md) [sonraki] (implement-custom-http-call-retries-exponential-backoff.md)
