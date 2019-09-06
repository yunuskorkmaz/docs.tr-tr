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
# <a name="implement-resilient-entity-framework-core-sql-connections"></a><span data-ttu-id="4e7dd-104">Dayanıklı Entity Framework Core SQL bağlantıları uygulama</span><span class="sxs-lookup"><span data-stu-id="4e7dd-104">Implement resilient Entity Framework Core SQL connections</span></span>

<span data-ttu-id="4e7dd-105">Azure SQL DB 'de Entity Framework (EF) Core zaten iç veritabanı bağlantı dayanıklılığı ve yeniden deneme mantığı sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e7dd-105">For Azure SQL DB, Entity Framework (EF) Core already provides internal database connection resiliency and retry logic.</span></span> <span data-ttu-id="4e7dd-106">Ancak dayanıklı <xref:Microsoft.EntityFrameworkCore.DbContext> [EF Core bağlantılarına](/ef/core/miscellaneous/connection-resiliency)sahip olmak istiyorsanız her bağlantı için Entity Framework yürütme stratejisini etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4e7dd-106">But you need to enable the Entity Framework execution strategy for each <xref:Microsoft.EntityFrameworkCore.DbContext> connection if you want to have [resilient EF Core connections](/ef/core/miscellaneous/connection-resiliency).</span></span>

<span data-ttu-id="4e7dd-107">Örneğin, EF Core bağlantı düzeyindeki aşağıdaki kod, bağlantı başarısız olursa yeniden denenen dayanıklı SQL bağlantılarına izin verir.</span><span class="sxs-lookup"><span data-stu-id="4e7dd-107">For instance, the following code at the EF Core connection level enables resilient SQL connections that are retried if the connection fails.</span></span>

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

## <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a><span data-ttu-id="4e7dd-108">BeginTransaction ve birden çok Dbbağlamlarını kullanarak yürütme stratejileri ve açık işlemler</span><span class="sxs-lookup"><span data-stu-id="4e7dd-108">Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts</span></span>

<span data-ttu-id="4e7dd-109">EF Core bağlantılarında yeniden denemeler etkinleştirildiğinde, EF Core kullanarak gerçekleştirdiğiniz her işlem kendi yeniden kullanılabilir işlem haline gelir.</span><span class="sxs-lookup"><span data-stu-id="4e7dd-109">When retries are enabled in EF Core connections, each operation you perform using EF Core becomes its own retriable operation.</span></span> <span data-ttu-id="4e7dd-110">Her sorgu ve her bir çağrı `SaveChanges` , geçici bir hata oluşursa birim olarak yeniden denenir.</span><span class="sxs-lookup"><span data-stu-id="4e7dd-110">Each query and each call to `SaveChanges` will be retried as a unit if a transient failure occurs.</span></span>

<span data-ttu-id="4e7dd-111">Ancak, kodunuz kullanarak `BeginTransaction`bir işlem başlatırsa, birim olarak değerlendirilmesi gereken kendi işlem grubunuzu tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4e7dd-111">However, if your code initiates a transaction using `BeginTransaction`, you're defining your own group of operations that need to be treated as a unit.</span></span> <span data-ttu-id="4e7dd-112">Bir hata oluşursa işlem içindeki her şeyin geri alınması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="4e7dd-112">Everything inside the transaction has to be rolled back if a failure occurs.</span></span>

<span data-ttu-id="4e7dd-113">Bir EF Execution strateji (yeniden deneme ilkesi) kullanırken bu işlemi yürütmeye çalışırsanız ve birden çok dbbağlamdan `SaveChanges` çağırdığınızda, bunun gibi bir özel durum alırsınız:</span><span class="sxs-lookup"><span data-stu-id="4e7dd-113">If you try to execute that transaction when using an EF execution strategy (retry policy) and you call `SaveChanges` from multiple DbContexts, you'll get an exception like this one:</span></span>

> <span data-ttu-id="4e7dd-114">System. InvalidOperationException: Yapılandırılan ' Sqlserverretryingexecutionstrateji ' yürütme stratejisi, Kullanıcı tarafından başlatılan işlemleri desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="4e7dd-114">System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions.</span></span> <span data-ttu-id="4e7dd-115">İşlemdeki tüm işlemleri yeniden kullanılabilir bir birim olarak yürütmek için ' DbContext. Database. Createexecutionstrateji () ' tarafından döndürülen yürütme stratejisini kullanın.</span><span class="sxs-lookup"><span data-stu-id="4e7dd-115">Use the execution strategy returned by 'DbContext.Database.CreateExecutionStrategy()' to execute all the operations in the transaction as a retriable unit.</span></span>

<span data-ttu-id="4e7dd-116">Çözüm, yürütülmesi gereken her şeyi temsil eden bir temsilciyle EF yürütme stratejisini el ile çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4e7dd-116">The solution is to manually invoke the EF execution strategy with a delegate representing everything that needs to be executed.</span></span> <span data-ttu-id="4e7dd-117">Geçici bir hata oluşursa, yürütme stratejisi temsilciyi tekrar çağıracaktır.</span><span class="sxs-lookup"><span data-stu-id="4e7dd-117">If a transient failure occurs, the execution strategy will invoke the delegate again.</span></span> <span data-ttu-id="4e7dd-118">Örneğin, aşağıdaki kod, bir ürünü güncelleştirirken ve daha sonra kaydettiğinizde, iki birden çok DbContext (\_catalogcontext ve ıntegrationeventlogcontext) ile eshoponcontainers içinde nasıl uygulandığını göstermektedir. Productpricechangedıntegrationevent nesnesi, farklı bir DbContext kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4e7dd-118">For example, the following code show how it's implemented in eShopOnContainers with two multiple DbContexts (\_catalogContext and the IntegrationEventLogContext) when updating a product and then saving the ProductPriceChangedIntegrationEvent object, which needs to use a different DbContext.</span></span>

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

<span data-ttu-id="4e7dd-119">Birincisi <xref:Microsoft.EntityFrameworkCore.DbContext> ve`_catalogContext` ikincisi `DbContext` nesne içindedir`_integrationEventLogService` .</span><span class="sxs-lookup"><span data-stu-id="4e7dd-119">The first <xref:Microsoft.EntityFrameworkCore.DbContext> is `_catalogContext` and the second `DbContext` is within the `_integrationEventLogService` object.</span></span> <span data-ttu-id="4e7dd-120">Yürütme eylemi, bir EF yürütme stratejisi `DbContext` kullanılarak tüm nesneler genelinde gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="4e7dd-120">The Commit action is performed across all `DbContext` objects using an EF execution strategy.</span></span>

<span data-ttu-id="4e7dd-121">Bu birden çok `DbContext` yürütmeyi `SaveEventAndCatalogContextChangesAsync` başarmak için, aşağıdaki kodda `ResilientTransaction` gösterildiği gibi bir sınıfı kullanır:</span><span class="sxs-lookup"><span data-stu-id="4e7dd-121">To achieve this multiple `DbContext` commit, the `SaveEventAndCatalogContextChangesAsync` uses a `ResilientTransaction` class, as shown in the following code:</span></span>

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

<span data-ttu-id="4e7dd-122">`IntegrationEventLogContext` `EventLogService` Yöntemi, geçirilen `DbContext` (`_catalogContext`) ' dan bir işlem başlatır ve ardından bu işlemi kullanarak değişiklikleri konumundan kaydeder ve sonra işlemin tamamını kaydeder. `ResilientTransaction.ExecuteAsync`</span><span class="sxs-lookup"><span data-stu-id="4e7dd-122">The `ResilientTransaction.ExecuteAsync` method basically begins a transaction from the passed `DbContext` (`_catalogContext`) and then makes the `EventLogService` use that transaction to save changes from the `IntegrationEventLogContext` and then commits the whole transaction.</span></span>

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

## <a name="additional-resources"></a><span data-ttu-id="4e7dd-123">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="4e7dd-123">Additional resources</span></span>

- <span data-ttu-id="4e7dd-124">**ASP.NET MVC uygulamasında EF ile bağlantı dayanıklılığı ve komut Yakaalımı** </span><span class="sxs-lookup"><span data-stu-id="4e7dd-124">**Connection Resiliency and Command Interception with EF in an ASP.NET MVC Application** </span></span>\
  [https://docs.microsoft.com/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application)

- <span data-ttu-id="4e7dd-125">**Cesar de La Torre. Esnek Entity Framework Core SQL bağlantılarını ve Işlemlerini kullanma** </span><span class="sxs-lookup"><span data-stu-id="4e7dd-125">**Cesar de la Torre. Using Resilient Entity Framework Core SQL Connections and Transactions** </span></span>\
  <https://devblogs.microsoft.com/cesardelatorre/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/>

>[!div class="step-by-step"]
><span data-ttu-id="4e7dd-126">[Önceki](implement-retries-exponential-backoff.md)İleri
>[](explore-custom-http-call-retries-exponential-backoff.md)</span><span class="sxs-lookup"><span data-stu-id="4e7dd-126">[Previous](implement-retries-exponential-backoff.md)
[Next](explore-custom-http-call-retries-exponential-backoff.md)</span></span>
