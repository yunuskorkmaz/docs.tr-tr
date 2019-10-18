---
title: Orchestration desenleri-sunucusuz uygulamalar
description: Azure dayanıklı işlevler PR
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 2bd81c29e727254af6c8ecf39ee4bfef1f39d009
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522641"
---
# <a name="orchestration-patterns"></a><span data-ttu-id="89f68-103">Düzenleme desenleri</span><span class="sxs-lookup"><span data-stu-id="89f68-103">Orchestration patterns</span></span>

<span data-ttu-id="89f68-104">Dayanıklı İşlevler, sunucusuz bir ortamda ayrık, uzun süredir çalışan etkinliklerden oluşan durum bilgisiz iş akışlarının oluşturulmasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="89f68-104">Durable Functions makes it easier to create stateful workflows that are composed of discrete, long running activities in a serverless environment.</span></span> <span data-ttu-id="89f68-105">Dayanıklı İşlevler, İş akışlarınızın ilerlemesini izleyebildiğiniz ve yürütme geçmişini düzenli olarak kontrol ettiğinden, bazı ilginç desenleri uygulamak için kendisini katlayın.</span><span class="sxs-lookup"><span data-stu-id="89f68-105">Since Durable Functions can track the progress of your workflows and periodically checkpoints the execution history, it lends itself to implementing some interesting patterns.</span></span>

## <a name="function-chaining"></a><span data-ttu-id="89f68-106">İşlev Zinciri</span><span class="sxs-lookup"><span data-stu-id="89f68-106">Function chaining</span></span>

<span data-ttu-id="89f68-107">Tipik sıralı bir işlemde, etkinliklerin belirli bir sırada diğeri tarafından yürütülmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="89f68-107">In a typical sequential process, activities need to execute one after the other in a particular order.</span></span> <span data-ttu-id="89f68-108">İsteğe bağlı olarak, yaklaşan etkinlik önceki işlevden bazı çıktılar gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="89f68-108">Optionally, the upcoming activity may require some output from the previous function.</span></span> <span data-ttu-id="89f68-109">Etkinlik sıralamasına yönelik bu bağımlılık, bir yürütme işlev zinciri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="89f68-109">This dependency on the ordering of activities creates a function chain of execution.</span></span>

<span data-ttu-id="89f68-110">Bu iş akışı deseninin uygulanması için Dayanıklı İşlevler kullanmanın avantajı, kendi denetim noktası oluşturma özelliğinden gelir.</span><span class="sxs-lookup"><span data-stu-id="89f68-110">The benefit of using Durable Functions to implement this workflow pattern comes from its ability to do checkpointing.</span></span> <span data-ttu-id="89f68-111">Sunucu kilitlenirse, ağ zaman aşımına uğrar veya başka bir sorun oluşursa, dayanıklı işlevler, son bilinen durumdan devam edebilir ve başka bir sunucuda olsa bile iş akışınızı çalıştırmaya devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="89f68-111">If the server crashes, the network times out or some other issue occurs, Durable functions can resume from the last known state and continue running your workflow even if it's on another server.</span></span>

```csharp
[FunctionName("PlaceOrder")]
public static async Task<string> PlaceOrder([OrchestrationTrigger] DurableOrchestrationContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    await context.CallActivityAsync<bool>("CheckAndReserveInventory", orderData);
    await context.CallActivityAsync<bool>("ProcessPayment", orderData);

    string trackingNumber = await context.CallActivityAsync<string>("ScheduleShipping", orderData);
    await context.CallActivityAsync<string>("EmailCustomer", trackingNumber);

    return trackingNumber;
}
```

<span data-ttu-id="89f68-112">Yukarıdaki kod örneğinde, `CallActivityAsync` işlevi, veri merkezindeki bir sanal makinede belirli bir etkinliği çalıştırmaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="89f68-112">In the preceding code sample, the `CallActivityAsync` function is responsible for running a given activity on a virtual machine in the data center.</span></span> <span data-ttu-id="89f68-113">Await döndürüldüğünde ve temel alınan görev tamamlandığında, yürütme geçmiş tablosuna kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="89f68-113">When the await returns and the underlying Task completes, the execution will be recorded to the history table.</span></span> <span data-ttu-id="89f68-114">Orchestrator işlevindeki kod, görev paralel kitaplığı ve zaman uyumsuz/await anahtar kelimeleriyle ilgili tanıdık yapıların herhangi birini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="89f68-114">The code in the orchestrator function can make use of any of the familiar constructs of the Task Parallel Library and the async/await keywords.</span></span>

<span data-ttu-id="89f68-115">Aşağıdaki kod, `ProcessPayment` yönteminin nasıl görünebileceklerini basit bir örneğidir:</span><span class="sxs-lookup"><span data-stu-id="89f68-115">The following code is a simplified example of what the `ProcessPayment` method may look like:</span></span>

```csharp
[FunctionName("ProcessPayment")]
public static bool ProcessPayment([ActivityTrigger] DurableActivityContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    ApplyCoupons(orderData);
    if(IssuePaymentRequest(orderData)) {
        return true;
    }

    return false;
}
```

## <a name="asynchronous-http-apis"></a><span data-ttu-id="89f68-116">Zaman uyumsuz HTTP API 'Leri</span><span class="sxs-lookup"><span data-stu-id="89f68-116">Asynchronous HTTP APIs</span></span>

<span data-ttu-id="89f68-117">Bazı durumlarda, iş akışları görece uzun süre süren etkinlikleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="89f68-117">In some cases, workflows may contain activities that take a relatively long period of time to complete.</span></span> <span data-ttu-id="89f68-118">Medya dosyalarının yedeklenmesini blob depolamaya vurur bir işlem düşünün.</span><span class="sxs-lookup"><span data-stu-id="89f68-118">Imagine a process that kicks off the backup of media files into blob storage.</span></span> <span data-ttu-id="89f68-119">Medya dosyalarının boyutuna ve miktarına bağlı olarak, bu yedekleme işleminin tamamlanması saatler sürebilir.</span><span class="sxs-lookup"><span data-stu-id="89f68-119">Depending on the size and quantity of the media files, this backup process may take hours to complete.</span></span>

<span data-ttu-id="89f68-120">Bu senaryoda, `DurableOrchestrationClient` çalışan bir iş akışının durumunu denetleme özelliği yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="89f68-120">In this scenario, the `DurableOrchestrationClient`'s ability to check the status of a running workflow becomes useful.</span></span> <span data-ttu-id="89f68-121">Bir iş akışını başlatmak için `HttpTrigger` kullanırken, `CreateCheckStatusResponse` yöntemi `HttpResponseMessage` örneğini döndürmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="89f68-121">When using an `HttpTrigger` to start a workflow, the `CreateCheckStatusResponse` method can be used to return an instance of `HttpResponseMessage`.</span></span> <span data-ttu-id="89f68-122">Bu yanıt, istemcide çalışan işlemin durumunu denetlemek için kullanılabilecek bir URI sağlar.</span><span class="sxs-lookup"><span data-stu-id="89f68-122">This response provides the client with a URI in the payload that can be used to check the status of the running process.</span></span>

```csharp
[FunctionName("OrderWorkflow")]
public static async Task<HttpResponseMessage> Run(
    [HttpTrigger(AuthorizationLevel.Function, "POST")]HttpRequestMessage req,
    [OrchestrationClient ] DurableOrchestrationClient orchestrationClient)
{
    OrderRequestData data = await req.Content.ReadAsAsync<OrderRequestData>();

    string instanceId = await orchestrationClient.StartNewAsync("PlaceOrder", data);

    return orchestrationClient.CreateCheckStatusResponse(req, instanceId);
}
```

<span data-ttu-id="89f68-123">Aşağıdaki örnek sonuç, yanıt yükünün yapısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="89f68-123">The sample result below shows the structure of the response payload.</span></span>

```json
{
    "id": "instanceId",
    "statusQueryGetUri": "http://host/statusUri",
    "sendEventPostUri": "http://host/eventUri",
    "terminatePostUri": "http://host/terminateUri"
}
```

<span data-ttu-id="89f68-124">Tercih edilen HTTP istemcinizi kullanarak, çalışan iş akışının durumunu incelemek için statusQueryGetUri içindeki URI 'ye alma istekleri yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="89f68-124">Using your preferred HTTP client, GET requests can be made to the URI in statusQueryGetUri to inspect the status of the running workflow.</span></span> <span data-ttu-id="89f68-125">Döndürülen durum yanıtı aşağıdaki koda benzemelidir.</span><span class="sxs-lookup"><span data-stu-id="89f68-125">The returned status response should resemble the following code.</span></span>

```json
{
    "runtimeStatus": "Running",
    "input": {
        "$type": "DurableFunctionsDemos.OrderRequestData, DurableFunctionsDemos"
    },
    "output": null,
    "createdTime": "2018-01-01T00:22:05Z",
    "lastUpdatedTime": "2018-01-01T00:22:09Z"
}
```

<span data-ttu-id="89f68-126">İşlem devam ettiğinden, durum yanıtı **başarısız** ya da **tamamlandı**olarak değişir.</span><span class="sxs-lookup"><span data-stu-id="89f68-126">As the process continues, the status response will change to either **Failed** or **Completed**.</span></span> <span data-ttu-id="89f68-127">Başarılı tamamlandığında, yükteki **output** özelliği döndürülen tüm verileri içerecektir.</span><span class="sxs-lookup"><span data-stu-id="89f68-127">On successful completion, the **output** property in the payload will contain any returned data.</span></span>

## <a name="monitoring"></a><span data-ttu-id="89f68-128">İzleme</span><span class="sxs-lookup"><span data-stu-id="89f68-128">Monitoring</span></span>

<span data-ttu-id="89f68-129">Azure Işlevleri, basit yinelenen görevler için bir CRON ifadesine göre zamanlanabilecek `TimerTrigger` sağlar.</span><span class="sxs-lookup"><span data-stu-id="89f68-129">For simple recurring tasks, Azure Functions provides the `TimerTrigger` that can be scheduled based on a CRON expression.</span></span> <span data-ttu-id="89f68-130">Zamanlayıcı basit, kısa süreli görevler için iyi işler, ancak daha esnek zamanlamanın gerektiği senaryolar olabilir.</span><span class="sxs-lookup"><span data-stu-id="89f68-130">The timer works well for simple, short-lived tasks, but there might be scenarios where more flexible scheduling is needed.</span></span> <span data-ttu-id="89f68-131">Bu senaryo, izleme deseninin ve Dayanıklı İşlevler yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="89f68-131">This scenario is when the monitoring pattern and Durable Functions can help.</span></span>

<span data-ttu-id="89f68-132">Dayanıklı İşlevler, esnek zamanlama aralıklarına, ömür yönetimine ve tek bir düzenleme işlevinden birden çok izleme işleminin oluşturulmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="89f68-132">Durable Functions allows for flexible scheduling intervals, lifetime management, and the creation of multiple monitor processes from a single orchestration function.</span></span> <span data-ttu-id="89f68-133">Bu işlevsellik için bir kullanım örneği, belirli bir eşiğin karşılandıktan sonra tamamlanan stok fiyatı değişiklikleri için izleyicileri oluşturmak olabilir.</span><span class="sxs-lookup"><span data-stu-id="89f68-133">One use case for this functionality might be to create watchers for stock price changes that complete once a certain threshold is met.</span></span>

```csharp
[FunctionName("CheckStockPrice")]
public static async Task CheckStockPrice([OrchestrationTrigger] DurableOrchestrationContext context)
{
    StockWatcherInfo stockInfo = context.GetInput<StockWatcherInfo>();
    const int checkIntervalSeconds = 120;
    StockPrice initialStockPrice = null;

    DateTime fireAt;
    DateTime exitTime = context.CurrentUtcDateTime.Add(stockInfo.TimeLimit);

    while (context.CurrentUtcDateTime < exitTime)
    {
        StockPrice currentStockPrice = await context.CallActivityAsync<StockPrice>("GetStockPrice", stockInfo);

        if (initialStockPrice == null)
        {
            initialStockPrice = currentStockPrice;
            fireAt = context.CurrentUtcDateTime.AddSeconds(checkIntervalSeconds);
            await context.CreateTimer(fireAt, CancellationToken.None);
            continue;
        }

        decimal percentageChange = (initialStockPrice.Price - currentStockPrice.Price) /
                               ((initialStockPrice.Price + currentStockPrice.Price) / 2);

        if (Math.Abs(percentageChange) >= stockInfo.PercentageChange)
        {
            // Change threshold detected
            await context.CallActivityAsync("NotifyStockPercentageChange", currentStockPrice);
            break;
        }

        // Sleep til next polling interval
        fireAt = context.CurrentUtcDateTime.AddSeconds(checkIntervalSeconds);
        await context.CreateTimer(fireAt, CancellationToken.None);
    }
}
```

<span data-ttu-id="89f68-134">`DurableOrchestrationContext` `CreateTimer` yöntemi, stok fiyatı değişikliklerini denetlemek için döngünün bir sonraki çağrılma zamanlamasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="89f68-134">`DurableOrchestrationContext`'s `CreateTimer` method sets up the schedule for the next invocation of the loop to check for stock price changes.</span></span> <span data-ttu-id="89f68-135">`DurableOrchestrationContext` Ayrıca UTC 'de geçerli tarih saat değerini almak için bir `CurrentUtcDateTime` özelliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="89f68-135">`DurableOrchestrationContext` also has a `CurrentUtcDateTime` property to get the current DateTime value in UTC.</span></span> <span data-ttu-id="89f68-136">Test için kolayca bir şekilde kullanıldığından, bu özelliğin `DateTime.UtcNow` yerine kullanılması daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="89f68-136">It's better to use this property instead of `DateTime.UtcNow` because it's easily mocked for testing.</span></span>

## <a name="recommended-resources"></a><span data-ttu-id="89f68-137">Önerilen Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="89f68-137">Recommended resources</span></span>

- [<span data-ttu-id="89f68-138">Azure Dayanıklı İşlevler</span><span class="sxs-lookup"><span data-stu-id="89f68-138">Azure Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
- [<span data-ttu-id="89f68-139">.NET Core ve .NET Standard birim testi</span><span class="sxs-lookup"><span data-stu-id="89f68-139">Unit Testing in .NET Core and .NET Standard</span></span>](../../core/testing/index.md)

>[!div class="step-by-step"]
><span data-ttu-id="89f68-140">[Önceki](durable-azure-functions.md)
>[İleri](serverless-business-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="89f68-140">[Previous](durable-azure-functions.md)
[Next](serverless-business-scenarios.md)</span></span>
