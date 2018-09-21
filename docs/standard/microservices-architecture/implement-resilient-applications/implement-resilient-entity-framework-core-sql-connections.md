---
title: Dayanıklı Entity Framework Core SQL bağlantıları uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Dayanıklı Entity Framework Core SQL bağlantıları uygulayın. Bu yöntem Azure SQL veritabanı bulutta kullanırken özellikle önemlidir.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/08/2018
ms.openlocfilehash: 59db9cdb894f76f54e77732be47dc6140a594121
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46561519"
---
# <a name="implement-resilient-entity-framework-core-sql-connections"></a><span data-ttu-id="c7d8a-104">Dayanıklı Entity Framework Core SQL bağlantıları uygulama</span><span class="sxs-lookup"><span data-stu-id="c7d8a-104">Implement resilient Entity Framework Core SQL connections</span></span>

<span data-ttu-id="c7d8a-105">Azure SQL DB için Entity Framework Core zaten iç veritabanı bağlantı dayanıklılığı ve yeniden deneme mantığı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c7d8a-105">For Azure SQL DB, Entity Framework Core already provides internal database connection resiliency and retry logic.</span></span> <span data-ttu-id="c7d8a-106">Ancak olmasını istiyorsanız, her bir DbContext bağlantı için Entity Framework yürütme stratejisi etkinleştirmeniz gerekiyor [dayanıklı EF Core bağlantıları](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency).</span><span class="sxs-lookup"><span data-stu-id="c7d8a-106">But you need to enable the Entity Framework execution strategy for each DbContext connection if you want to have [resilient EF Core connections](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency).</span></span>

<span data-ttu-id="c7d8a-107">Örneğin, aşağıdaki kodu EF Core bağlantı düzeyinde bağlantı başarısız olursa şartıyla dayanıklı SQL bağlantısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c7d8a-107">For instance, the following code at the EF Core connection level enables resilient SQL connections that are retried if the connection fails.</span></span>

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

## <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a><span data-ttu-id="c7d8a-108">Yürütme stratejileri ve BeginTransaction ve birden çok DbContexts kullanarak açık işlemleri</span><span class="sxs-lookup"><span data-stu-id="c7d8a-108">Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts</span></span>

<span data-ttu-id="c7d8a-109">EF Core bağlantıları yeniden deneme etkinleştirildiğinde, EF Core kullanarak gerçekleştirdiğiniz her işlem yeniden denenebilir kendi işlem olur.</span><span class="sxs-lookup"><span data-stu-id="c7d8a-109">When retries are enabled in EF Core connections, each operation you perform using EF Core becomes its own retryable operation.</span></span> <span data-ttu-id="c7d8a-110">Geçici bir hata oluşursa, her sorgu ve SaveChanges yapılan her çağrı bir birim olarak yeniden denenecek.</span><span class="sxs-lookup"><span data-stu-id="c7d8a-110">Each query and each call to SaveChanges will be retried as a unit if a transient failure occurs.</span></span>

<span data-ttu-id="c7d8a-111">Kodunuzu BeginTransaction'ı kullanarak bir işlem başlatır, ancak bir birim olarak kabul edilmesi için gereken işlemleri kendi grubu tanımladığınız — işlem içinde her şeyi sahip olması toplu geri bir arıza oluşması durumunda.</span><span class="sxs-lookup"><span data-stu-id="c7d8a-111">However, if your code initiates a transaction using BeginTransaction, you are defining your own group of operations that need to be treated as a unit—everything inside the transaction has be rolled back if a failure occurs.</span></span> <span data-ttu-id="c7d8a-112">EF yürütme stratejisi (yeniden deneme ilkesi) kullanılırken, işlem yürütme girişimi ve bir işlemde birden çok DbContexts birkaç SaveChanges çağrılarından dahil, aşağıdaki gibi bir özel durum görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="c7d8a-112">You will see an exception like the following if you attempt to execute that transaction when using an EF execution strategy (retry policy) and you include several SaveChanges calls from multiple DbContexts in the transaction.</span></span>

> <span data-ttu-id="c7d8a-113">System.InvalidOperationException: 'SqlServerRetryingExecutionStrategy' yapılandırılmış yürütme stratejisi, kullanıcı tarafından başlatılan işlemleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="c7d8a-113">System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions.</span></span> <span data-ttu-id="c7d8a-114">İşlem yeniden denenebilir bir birim olarak tüm işlemleri yürütmek için 'DbContext.Database.CreateExecutionStrategy()' tarafından döndürülen yürütme stratejisi kullanın.</span><span class="sxs-lookup"><span data-stu-id="c7d8a-114">Use the execution strategy returned by 'DbContext.Database.CreateExecutionStrategy()' to execute all the operations in the transaction as a retriable unit.</span></span>

<span data-ttu-id="c7d8a-115">El ile yürütülmesi gereken her şeyi temsil eden bir temsilci ile EF yürütme stratejisi çağırmak için kullanılan çözümüdür.</span><span class="sxs-lookup"><span data-stu-id="c7d8a-115">The solution is to manually invoke the EF execution strategy with a delegate representing everything that needs to be executed.</span></span> <span data-ttu-id="c7d8a-116">Geçici bir hata oluşursa yürütme stratejisi temsilciyi yeniden çağırır.</span><span class="sxs-lookup"><span data-stu-id="c7d8a-116">If a transient failure occurs, the execution strategy will invoke the delegate again.</span></span> <span data-ttu-id="c7d8a-117">Örneğin, aşağıdaki kodu göster hizmetine iki ile nasıl uygulandığı birden çok DbContexts (\_catalogContext ve IntegrationEventLogContext) ürün ve sonra kaydetme güncelleştirilirken Farklı bir DbContext kullanması gereken ProductPriceChangedIntegrationEvent nesnesi.</span><span class="sxs-lookup"><span data-stu-id="c7d8a-117">For example, the following code show how it is implemented in eShopOnContainers with two multiple DbContexts (\_catalogContext and the IntegrationEventLogContext) when updating a product and then saving the ProductPriceChangedIntegrationEvent object, which needs to use a different DbContext.</span></span>

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

<span data-ttu-id="c7d8a-118">İlk DbContext olduğu \_catalogContext ve ikinci DbContext içinde olduğunu \_integrationEventLogService nesne.</span><span class="sxs-lookup"><span data-stu-id="c7d8a-118">The first DbContext is \_catalogContext and the second DbContext is within the \_integrationEventLogService object.</span></span> <span data-ttu-id="c7d8a-119">Yürütme eylemi bir EF yürütme stratejisi kullanarak birden çok DbContexts gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c7d8a-119">The Commit action is performed across multiple DbContexts using an EF execution strategy.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="c7d8a-120">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="c7d8a-120">Additional resources</span></span>

-   <span data-ttu-id="c7d8a-121">**EF bağlantı dayanıklılığı** (Entity Framework Core) [*https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency*](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)</span><span class="sxs-lookup"><span data-stu-id="c7d8a-121">**EF Connection Resiliency** (Entity Framework Core) [*https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency*](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)</span></span>

-   <span data-ttu-id="c7d8a-122">**Bağlantı dayanıklılığı ve komut durdurma Entity Framework ile**
    [*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)</span><span class="sxs-lookup"><span data-stu-id="c7d8a-122">**Connection Resiliency and Command Interception with the Entity Framework**
[*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)</span></span>

-   <span data-ttu-id="c7d8a-123">**Cesar de la Torre. Dayanıklı Entity Framework Core Sql bağlantıları ve işlemleri kullanma**
    <https://blogs.msdn.microsoft.com/cesardelatorre/2017/03/26/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/></span><span class="sxs-lookup"><span data-stu-id="c7d8a-123">**Cesar de la Torre. Using Resilient Entity Framework Core Sql Connections and Transactions**
<https://blogs.msdn.microsoft.com/cesardelatorre/2017/03/26/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/></span></span>

>[!div class="step-by-step"]
<span data-ttu-id="c7d8a-124">[Önceki](implement-retries-exponential-backoff.md)
[İleri](explore-custom-http-call-retries-exponential-backoff.md)</span><span class="sxs-lookup"><span data-stu-id="c7d8a-124">[Previous](implement-retries-exponential-backoff.md)
[Next](explore-custom-http-call-retries-exponential-backoff.md)</span></span>
