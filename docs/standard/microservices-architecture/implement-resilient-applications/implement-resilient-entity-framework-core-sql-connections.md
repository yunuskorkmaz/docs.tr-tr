---
title: Dayanıklı Entity Framework Core SQL bağlantıları uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Dayanıklı Entity Framework Core SQL bağlantıları uygulayın. Bu yöntem Azure SQL veritabanı bulutta kullanırken özellikle önemlidir.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/08/2018
ms.openlocfilehash: 59db9cdb894f76f54e77732be47dc6140a594121
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46323279"
---
# <a name="implement-resilient-entity-framework-core-sql-connections"></a>Dayanıklı Entity Framework Core SQL bağlantıları uygulama

Azure SQL DB için Entity Framework Core zaten iç veritabanı bağlantı dayanıklılığı ve yeniden deneme mantığı sağlar. Ancak olmasını istiyorsanız, her bir DbContext bağlantı için Entity Framework yürütme stratejisi etkinleştirmeniz gerekiyor [dayanıklı EF Core bağlantıları](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency).

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

EF Core bağlantıları yeniden deneme etkinleştirildiğinde, EF Core kullanarak gerçekleştirdiğiniz her işlem yeniden denenebilir kendi işlem olur. Geçici bir hata oluşursa, her sorgu ve SaveChanges yapılan her çağrı bir birim olarak yeniden denenecek.

Kodunuzu BeginTransaction'ı kullanarak bir işlem başlatır, ancak bir birim olarak kabul edilmesi için gereken işlemleri kendi grubu tanımladığınız — işlem içinde her şeyi sahip olması toplu geri bir arıza oluşması durumunda. EF yürütme stratejisi (yeniden deneme ilkesi) kullanılırken, işlem yürütme girişimi ve bir işlemde birden çok DbContexts birkaç SaveChanges çağrılarından dahil, aşağıdaki gibi bir özel durum görürsünüz.

> System.InvalidOperationException: 'SqlServerRetryingExecutionStrategy' yapılandırılmış yürütme stratejisi, kullanıcı tarafından başlatılan işlemleri desteklemez. İşlem yeniden denenebilir bir birim olarak tüm işlemleri yürütmek için 'DbContext.Database.CreateExecutionStrategy()' tarafından döndürülen yürütme stratejisi kullanın.

El ile yürütülmesi gereken her şeyi temsil eden bir temsilci ile EF yürütme stratejisi çağırmak için kullanılan çözümüdür. Geçici bir hata oluşursa yürütme stratejisi temsilciyi yeniden çağırır. Örneğin, aşağıdaki kodu göster hizmetine iki ile nasıl uygulandığı birden çok DbContexts (\_catalogContext ve IntegrationEventLogContext) ürün ve sonra kaydetme güncelleştirilirken Farklı bir DbContext kullanması gereken ProductPriceChangedIntegrationEvent nesnesi.

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

İlk DbContext olduğu \_catalogContext ve ikinci DbContext içinde olduğunu \_integrationEventLogService nesne. Yürütme eylemi bir EF yürütme stratejisi kullanarak birden çok DbContexts gerçekleştirilir.

## <a name="additional-resources"></a>Ek kaynaklar

-   **EF bağlantı dayanıklılığı** (Entity Framework Core) [*https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency*](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)

-   **Bağlantı dayanıklılığı ve komut durdurma Entity Framework ile**
    [*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)

-   **Cesar de la Torre. Dayanıklı Entity Framework Core Sql bağlantıları ve işlemleri kullanma**
    <https://blogs.msdn.microsoft.com/cesardelatorre/2017/03/26/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/>

>[!div class="step-by-step"]
[Önceki](implement-retries-exponential-backoff.md)
[İleri](explore-custom-http-call-retries-exponential-backoff.md)
