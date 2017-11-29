---
title: "Esnek Entity Framework Çekirdek SQL bağlantıları uygulama"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Esnek Entity Framework Çekirdek SQL bağlantıları uygulama"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 8600625c2022d69ebaa2645c2a8159a848b12ff0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-resilient-entity-framework-core-sql-connections"></a><span data-ttu-id="07b4e-104">Esnek Entity Framework Çekirdek SQL bağlantıları uygulama</span><span class="sxs-lookup"><span data-stu-id="07b4e-104">Implementing resilient Entity Framework Core SQL connections</span></span>

<span data-ttu-id="07b4e-105">Azure SQL DB için Entity Framework Çekirdek zaten iç veritabanı bağlantısı dayanıklılık ve yeniden deneme mantığı sağlar.</span><span class="sxs-lookup"><span data-stu-id="07b4e-105">For Azure SQL DB, Entity Framework Core already provides internal database connection resiliency and retry logic.</span></span> <span data-ttu-id="07b4e-106">Ancak sahip olmak istiyorsanız her DbContext bağlantısı için Entity Framework yürütme stratejisi etkinleştirmeniz gerekiyor [dayanıklı EF çekirdek bağlantıları](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency).</span><span class="sxs-lookup"><span data-stu-id="07b4e-106">But you need to enable the Entity Framework execution strategy for each DbContext connection if you want to have [resilient EF Core connections](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency).</span></span>

<span data-ttu-id="07b4e-107">Örneği için aşağıdaki kodu EF çekirdek bağlantı düzeyinde bağlantı başarısız olursa yeniden denenir dayanıklı SQL bağlantıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="07b4e-107">For instance, the following code at the EF Core connection level enables resilient SQL connections that are retried if the connection fails.</span></span>

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

## <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a><span data-ttu-id="07b4e-108">Yürütme stratejilerini ve BeginTransaction ve birden çok DbContexts kullanarak açık işlemleri</span><span class="sxs-lookup"><span data-stu-id="07b4e-108">Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts</span></span>

<span data-ttu-id="07b4e-109">EF çekirdek bağlantıları yeniden deneme etkinleştirildiğinde, EF çekirdek kullanarak gerçekleştirdiğiniz her işlem yeniden denenebilir çalışması haline gelir.</span><span class="sxs-lookup"><span data-stu-id="07b4e-109">When retries are enabled in EF Core connections, each operation you perform using EF Core becomes its own retriable operation.</span></span> <span data-ttu-id="07b4e-110">Geçici bir hata oluşursa, her sorgu ve her çağrı SaveChanges bir birim olarak yeniden denenecek.</span><span class="sxs-lookup"><span data-stu-id="07b4e-110">Each query and each call to SaveChanges will be retried as a unit if a transient failure occurs.</span></span>

<span data-ttu-id="07b4e-111">Ancak, kodunuzu BeginTransaction kullanarak bir işlem başlatır, bir birim olarak kabul edilmesi için gereken işlemleri kendi grubunun tanımlıyorsanız — işlem içinde her şeyi sahip olması alındı geri bir hata oluşursa.</span><span class="sxs-lookup"><span data-stu-id="07b4e-111">However, if your code initiates a transaction using BeginTransaction, you are defining your own group of operations that need to be treated as a unit—everything inside the transaction has be rolled back if a failure occurs.</span></span> <span data-ttu-id="07b4e-112">EF yürütme stratejisi (yeniden deneme ilkesi) kullanırken bu işlemi yürütme girişimi ve işlemde birden çok DbContexts birkaç SaveChanges çağrılarından dahil aşağıdaki gibi bir özel durum görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="07b4e-112">You will see an exception like the following if you attempt to execute that transaction when using an EF execution strategy (retry policy) and you include several SaveChanges calls from multiple DbContexts in the transaction.</span></span>

> <span data-ttu-id="07b4e-113">System.InvalidOperationException: 'SqlServerRetryingExecutionStrategy' yapılandırılmış yürütme stratejisi kullanıcı tarafından başlatılan işlemleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="07b4e-113">System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions.</span></span> <span data-ttu-id="07b4e-114">İşlem yeniden denenebilir bir birim olarak tüm işlemleri yürütmek için 'DbContext.Database.CreateExecutionStrategy()' tarafından döndürülen yürütme stratejisi kullanın.</span><span class="sxs-lookup"><span data-stu-id="07b4e-114">Use the execution strategy returned by 'DbContext.Database.CreateExecutionStrategy()' to execute all the operations in the transaction as a retriable unit.</span></span>

<span data-ttu-id="07b4e-115">Çözüm, yürütülecek gereken her şeyi temsil eden bir temsilci ile EF yürütme stratejisi el ile çağırmaktır.</span><span class="sxs-lookup"><span data-stu-id="07b4e-115">The solution is to manually invoke the EF execution strategy with a delegate representing everything that needs to be executed.</span></span> <span data-ttu-id="07b4e-116">Geçici bir hata oluşursa, yürütme stratejisi temsilci yeniden çağırır.</span><span class="sxs-lookup"><span data-stu-id="07b4e-116">If a transient failure occurs, the execution strategy will invoke the delegate again.</span></span> <span data-ttu-id="07b4e-117">Örneğin, aşağıdaki kodu göster nasıl şu iki eShopOnContainers uygulanan birden çok DbContexts (\_catalogContext ve IntegrationEventLogContext) ürün ve ardından kaydetme güncelleştirirken ProductPriceChangedIntegrationEvent nesne, farklı bir DbContext kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="07b4e-117">For example, the following code show how it is implemented in eShopOnContainers with two multiple DbContexts (\_catalogContext and the IntegrationEventLogContext) when updating a product and then saving the ProductPriceChangedIntegrationEvent object, which needs to use a different DbContext.</span></span>

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

<span data-ttu-id="07b4e-118">İlk DbContext olan \_catalogContext ve ikinci DbContext içinde olduğunu \_integrationEventLogService nesnesi.</span><span class="sxs-lookup"><span data-stu-id="07b4e-118">The first DbContext is \_catalogContext and the second DbContext is within the \_integrationEventLogService object.</span></span> <span data-ttu-id="07b4e-119">Yürütme eylemi EF yürütme stratejisi kullanarak birden çok DbContexts gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="07b4e-119">The Commit action is performed across multiple DbContexts using an EF execution strategy.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="07b4e-120">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="07b4e-120">Additional resources</span></span>

-   <span data-ttu-id="07b4e-121">**Bağlantı dayanıklılığı ve Entity Framework komut kişiler tarafından ele**
    [*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)</span><span class="sxs-lookup"><span data-stu-id="07b4e-121">**Connection Resiliency and Command Interception with the Entity Framework**
[*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)</span></span>

-   <span data-ttu-id="07b4e-122">**Cesar de la Torre. Esnek Entity Framework Çekirdek Sql bağlantıları ve işlemleri kullanarak**
    <https://blogs.msdn.microsoft.com/cesardelatorre/2017/03/26/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/></span><span class="sxs-lookup"><span data-stu-id="07b4e-122">**Cesar de la Torre. Using Resilient Entity Framework Core Sql Connections and Transactions**
<https://blogs.msdn.microsoft.com/cesardelatorre/2017/03/26/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/></span></span>


>[!div class="step-by-step"]
<span data-ttu-id="07b4e-123">[Önceki] (uygulama-yeniden deneme-üstel-backoff.md) [sonraki] (implement-custom-http-call-retries-exponential-backoff.md)</span><span class="sxs-lookup"><span data-stu-id="07b4e-123">[Previous] (implement-retries-exponential-backoff.md) [Next] (implement-custom-http-call-retries-exponential-backoff.md)</span></span>
