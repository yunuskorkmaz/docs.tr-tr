---
title: Orchestration desenleri - sunucusuz uygulamalar
description: Azure dayanıklı işlevler çekme isteği
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: b3f0587241a940941f40512504f7838ef94e3150
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37405017"
---
# <a name="orchestration-patterns"></a><span data-ttu-id="fae8e-103">Orchestration desenleri</span><span class="sxs-lookup"><span data-stu-id="fae8e-103">Orchestration patterns</span></span>

<span data-ttu-id="fae8e-104">Dayanıklı işlevler kolaylaştırır, sunucusuz bir ortamda ayrık, uzun süre çalışan etkinlikler oluşan durum bilgisi olan iş akışları oluşturmak.</span><span class="sxs-lookup"><span data-stu-id="fae8e-104">Durable Functions makes it easier to create stateful workflows that are composed of discrete, long running activities in a serverless environment.</span></span> <span data-ttu-id="fae8e-105">Dayanıklı İşlevler, yürütme geçmişini iş akışlarınız ve düzenli aralıklarla kontrol noktaları ilerlemesini izleyebilirsiniz olduğundan, kendisine bazı ilginç kalıpları uygulamak için uygundur.</span><span class="sxs-lookup"><span data-stu-id="fae8e-105">Since Durable Functions can track the progress of your workflows and periodically checkpoints the execution history, it lends itself to implementing some interesting patterns.</span></span>

## <a name="function-chaining"></a><span data-ttu-id="fae8e-106">Zincirleme işlevi</span><span class="sxs-lookup"><span data-stu-id="fae8e-106">Function chaining</span></span>

<span data-ttu-id="fae8e-107">Tipik bir sıralı işlemde etkinlikleri birbiri ardına belirli bir sırayla yürütülmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="fae8e-107">In a typical sequential process, activities need to execute one after the other in a particular order.</span></span> <span data-ttu-id="fae8e-108">İsteğe bağlı olarak, yaklaşan etkinlik bazı önceki işlev çıkışı gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="fae8e-108">Optionally, the upcoming activity may require some output from the previous function.</span></span> <span data-ttu-id="fae8e-109">Bu bağımlılık etkinlikleri sıralama üzerinde yürütme işlevi zinciri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fae8e-109">This dependency on the ordering of activities creates a function chain of execution.</span></span>

<span data-ttu-id="fae8e-110">Bu iş akışı deseni uygulamak için dayanıklı işlevler kullanmanın avantajı, denetim noktası yapmak için kendi yeteneği gelir.</span><span class="sxs-lookup"><span data-stu-id="fae8e-110">The benefit of using Durable Functions to implement this workflow pattern comes from its ability to do checkpointing.</span></span> <span data-ttu-id="fae8e-111">Sunucu çökerse, ağ zaman aşımına uğrar veya başka bir sorun ortaya çıkar, dayanıklı işlevler bilinen son durumundan sürdürme ve başka bir sunucu olsa bile, iş akışınızı çalıştırmak devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fae8e-111">If the server crashes, the network times out or some other issue occurs, Durable functions can resume from the last known state and continue running your workflow even if it's on another server.</span></span>

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

<span data-ttu-id="fae8e-112">Yukarıdaki kod örneğinde, `CallActivityAsync` işlev, belirli bir etkinlik bir veri merkezindeki sanal makinede çalıştırmaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="fae8e-112">In the preceding code sample, the `CallActivityAsync` function is responsible for running a given activity on a virtual machine in the data center.</span></span> <span data-ttu-id="fae8e-113">Await döndürür ve temel alınan görev tamamlandığında, yürütme geçmiş tablosuna kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="fae8e-113">When the await returns and the underlying Task completes, the execution will be recorded to the history table.</span></span> <span data-ttu-id="fae8e-114">Orchestrator işlevdeki kod yapabilir, görev paralel kitaplığı ve async/await anahtar sözcükleri tanıdık yapıları birini kullanın.</span><span class="sxs-lookup"><span data-stu-id="fae8e-114">The code in the orchestrator function can make use of any of the familiar constructs of the Task Parallel Library and the async/await keywords.</span></span>

<span data-ttu-id="fae8e-115">Aşağıdaki kod ne basitleştirilmiş bir örnektir `ProcessPayment` yöntemi görünebileceğini:</span><span class="sxs-lookup"><span data-stu-id="fae8e-115">The following code is a simplified example of what the `ProcessPayment` method may look like:</span></span>

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

## <a name="asynchronous-http-apis"></a><span data-ttu-id="fae8e-116">Zaman uyumsuz HTTP API'leri</span><span class="sxs-lookup"><span data-stu-id="fae8e-116">Asynchronous HTTP APIs</span></span>

<span data-ttu-id="fae8e-117">Bazı durumlarda, iş akışlarının tamamlanması oldukça uzun bir süre Süren etkinlikler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="fae8e-117">In some cases, workflows may contain activities that take a relatively long period of time to complete.</span></span> <span data-ttu-id="fae8e-118">Dosyaları blob depolama içine medya yedeklenmesini devre dışı başlatan bir işlem düşünün.</span><span class="sxs-lookup"><span data-stu-id="fae8e-118">Imagine a process that kicks off the backup of media files into blob storage.</span></span> <span data-ttu-id="fae8e-119">Boyutu ve medya dosyalarını miktarını bağlı olarak, bu yedekleme işlemi tamamlamak için saat sürebilir.</span><span class="sxs-lookup"><span data-stu-id="fae8e-119">Depending on the size and quantity of the media files, this backup process may take hours to complete.</span></span>

<span data-ttu-id="fae8e-120">Bu senaryoda, `DurableOrchestrationClient`ın çalışan bir iş akışı durumunu kontrol yeteneği yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="fae8e-120">In this scenario, the `DurableOrchestrationClient`'s ability to check the status of a running workflow becomes useful.</span></span> <span data-ttu-id="fae8e-121">Kullanırken bir `HttpTrigger` bir iş akışının başlatılacağı `CreateCheckStatusResponse` yöntemi örneği döndürmek için kullanılabilir `HttpResponseMessage`.</span><span class="sxs-lookup"><span data-stu-id="fae8e-121">When using an `HttpTrigger` to start a workflow, the `CreateCheckStatusResponse` method can be used to return an instance of `HttpResponseMessage`.</span></span> <span data-ttu-id="fae8e-122">Bu yanıt yükünde çalışan işleminin durumunu denetlemek için kullanılan URI ile istemci sağlar.</span><span class="sxs-lookup"><span data-stu-id="fae8e-122">This response provides the client with a URI in the payload that can be used to check the status of the running process.</span></span>

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

<span data-ttu-id="fae8e-123">Aşağıdaki örnek sonucu, yanıt yükünde yapısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fae8e-123">The sample result below shows the structure of the response payload.</span></span>

```json
{
    "id": "instanceId",
    "statusQueryGetUri": "http://host/statusUri",
    "sendEventPostUri": "http://host/eventUri",
    "terminatePostUri": "http://host/terminateUri"
}
```

<span data-ttu-id="fae8e-124">Tercih edilen HTTP İstemcisi'ni kullanarak GET istekleri statusQueryGetUri URI için çalışan bir iş akışı durumunu incelemek için yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="fae8e-124">Using your preferred HTTP client, GET requests can be made to the URI in statusQueryGetUri to inspect the status of the running workflow.</span></span> <span data-ttu-id="fae8e-125">Döndürülen durum yanıt aşağıdaki koda benzemelidir.</span><span class="sxs-lookup"><span data-stu-id="fae8e-125">The returned status response should resemble the following code.</span></span>

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

<span data-ttu-id="fae8e-126">İşlem devam ettikçe durum yanıt ya da değişecektir **başarısız** veya **tamamlandı**.</span><span class="sxs-lookup"><span data-stu-id="fae8e-126">As the process continues, the status response will change to either **Failed** or **Completed**.</span></span> <span data-ttu-id="fae8e-127">Başarıyla tamamlandığında, **çıkış** yükünde özelliği her döndürülen veriler içerir.</span><span class="sxs-lookup"><span data-stu-id="fae8e-127">On successful completion, the **output** property in the payload will contain any returned data.</span></span>

## <a name="monitoring"></a><span data-ttu-id="fae8e-128">İzleme</span><span class="sxs-lookup"><span data-stu-id="fae8e-128">Monitoring</span></span>

<span data-ttu-id="fae8e-129">Basit yinelenen görevler için Azure işlevlerinin sağladığı `TimerTrigger` zamanlanabilen bir CRON ifadeye göre.</span><span class="sxs-lookup"><span data-stu-id="fae8e-129">For simple recurring tasks, Azure Functions provides the `TimerTrigger` that can be scheduled based on a CRON expression.</span></span> <span data-ttu-id="fae8e-130">Zamanlayıcı da basit, kısa süreli görevler için çalışır olabilir ancak senaryoları burada daha esnek zamanlama gereklidir.</span><span class="sxs-lookup"><span data-stu-id="fae8e-130">The timer works well for simple, short-lived tasks, but there might be scenarios where more flexible scheduling is needed.</span></span> <span data-ttu-id="fae8e-131">Bu senaryo, izleme desen ve dayanıklı işlevler yardımcı olabilecek andır.</span><span class="sxs-lookup"><span data-stu-id="fae8e-131">This scenario is when the monitoring pattern and Durable Functions can help.</span></span>

<span data-ttu-id="fae8e-132">Dayanıklı işlevler esnek zamanlama aralıkları, ömür yönetimi ve birden çok izleme işlemlerini tek düzenleme işlevi oluşturulmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="fae8e-132">Durable Functions allows for flexible scheduling intervals, lifetime management, and the creation of multiple monitor processes from a single orchestration function.</span></span> <span data-ttu-id="fae8e-133">Bu işlev için bir kullanım örneği, belirli bir Eşiğe ulaşıldığında tamamlayan hisse senedi fiyatı değişiklikleri izleyicileri oluşturmak için olabilir.</span><span class="sxs-lookup"><span data-stu-id="fae8e-133">One use case for this functionality might be to create watchers for stock price changes that complete once a certain threshold is met.</span></span>

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

<span data-ttu-id="fae8e-134">`DurableOrchestrationContext`ın `CreateTimer` hisse senedi fiyatı değişiklikleri denetlemek için sonraki çağrının döngünün zamanlamasını ayarlama yöntemini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="fae8e-134">`DurableOrchestrationContext`'s `CreateTimer` method sets up the schedule for the next invocation of the loop to check for stock price changes.</span></span> <span data-ttu-id="fae8e-135">`DurableOrchestrationContext` Ayrıca bir `CurrentUtcDateTime` özelliği geçerli bir tarih saat değeri UTC biçiminde alır.</span><span class="sxs-lookup"><span data-stu-id="fae8e-135">`DurableOrchestrationContext` also has a `CurrentUtcDateTime` property to get the current DateTime value in UTC.</span></span> <span data-ttu-id="fae8e-136">Yerine bu özelliği kullanmak iyidir `DateTime.UtcNow` kolayca test etmek için örnek için.</span><span class="sxs-lookup"><span data-stu-id="fae8e-136">It's better to use this property instead of `DateTime.UtcNow` because it's easily mocked for testing.</span></span>

## <a name="recommended-resources"></a><span data-ttu-id="fae8e-137">Önerilen kaynaklar</span><span class="sxs-lookup"><span data-stu-id="fae8e-137">Recommended resources</span></span>

* [<span data-ttu-id="fae8e-138">Azure dayanıklı İşlevler</span><span class="sxs-lookup"><span data-stu-id="fae8e-138">Azure Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
* [<span data-ttu-id="fae8e-139">.NET Core ve .NET standart birim testi</span><span class="sxs-lookup"><span data-stu-id="fae8e-139">Unit Testing in .NET Core and .NET Standard</span></span>](https://docs.microsoft.com/en-us/dotnet/core/testing/)

>[!div class="step-by-step"]
<span data-ttu-id="fae8e-140">[Önceki](durable-azure-functions.md)
[İleri](serverless-business-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="fae8e-140">[Previous](durable-azure-functions.md)
[Next](serverless-business-scenarios.md)</span></span>
