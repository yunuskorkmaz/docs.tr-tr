---
title: Orkestrasyon desenleri - Sunucusuz uygulamalar
description: Azure Dayanıklı fonksiyonlar pr
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 2bd81c29e727254af6c8ecf39ee4bfef1f39d009
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522641"
---
# <a name="orchestration-patterns"></a><span data-ttu-id="968c6-103">Orkestrasyon desenleri</span><span class="sxs-lookup"><span data-stu-id="968c6-103">Orchestration patterns</span></span>

<span data-ttu-id="968c6-104">Dayanıklı Işlevler, sunucusuz bir ortamda ayrık, uzun süren etkinliklerden oluşan durumlu iş akışları oluşturmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="968c6-104">Durable Functions makes it easier to create stateful workflows that are composed of discrete, long running activities in a serverless environment.</span></span> <span data-ttu-id="968c6-105">Dayanıklı Fonksiyonlar iş akışlarınızın ilerlemesini izleyip yürütme geçmişini düzenli olarak kontrol edebildiği için, bazı ilginç desenler ilerler.</span><span class="sxs-lookup"><span data-stu-id="968c6-105">Since Durable Functions can track the progress of your workflows and periodically checkpoints the execution history, it lends itself to implementing some interesting patterns.</span></span>

## <a name="function-chaining"></a><span data-ttu-id="968c6-106">İşlev zinciri oluşturma</span><span class="sxs-lookup"><span data-stu-id="968c6-106">Function chaining</span></span>

<span data-ttu-id="968c6-107">Tipik bir sıralı işlemde, etkinliklerin belirli bir sırada birbiri ardına yürütülmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="968c6-107">In a typical sequential process, activities need to execute one after the other in a particular order.</span></span> <span data-ttu-id="968c6-108">İsteğe bağlı olarak, yaklaşan etkinlik önceki işlevden bazı çıktı gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="968c6-108">Optionally, the upcoming activity may require some output from the previous function.</span></span> <span data-ttu-id="968c6-109">Etkinliklerin sıralanmasına yapılan bu bağımlılık, bir yürütme işlevi zinciri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="968c6-109">This dependency on the ordering of activities creates a function chain of execution.</span></span>

<span data-ttu-id="968c6-110">Bu iş akışı deseni uygulamak için Dayanıklı Fonksiyonlar kullanmanın yararı, denetim noktası yapma yeteneğinden gelir.</span><span class="sxs-lookup"><span data-stu-id="968c6-110">The benefit of using Durable Functions to implement this workflow pattern comes from its ability to do checkpointing.</span></span> <span data-ttu-id="968c6-111">Sunucu çökerse, ağ süreleri doluyorveya başka bir sorun oluşursa, Dayanıklı işlevler bilinen son durumdan devam edebilir ve başka bir sunucuda olsa bile iş akışınızı çalıştırmaya devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="968c6-111">If the server crashes, the network times out or some other issue occurs, Durable functions can resume from the last known state and continue running your workflow even if it's on another server.</span></span>

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

<span data-ttu-id="968c6-112">Önceki kod örneğinde, `CallActivityAsync` işlev veri merkezindeki sanal bir makinede belirli bir etkinliği çalıştırmakla yükümlüdür.</span><span class="sxs-lookup"><span data-stu-id="968c6-112">In the preceding code sample, the `CallActivityAsync` function is responsible for running a given activity on a virtual machine in the data center.</span></span> <span data-ttu-id="968c6-113">Bekleme geri döndüğünde ve temel Görev tamamlandığında, yürütme geçmiş tablosuna kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="968c6-113">When the await returns and the underlying Task completes, the execution will be recorded to the history table.</span></span> <span data-ttu-id="968c6-114">Orkestratör işlevindeki kod, Görev Paralel Kitaplığı'nın tanıdık yapılarından herhangi birini ve async/await anahtar kelimelerinden yararlanabilir.</span><span class="sxs-lookup"><span data-stu-id="968c6-114">The code in the orchestrator function can make use of any of the familiar constructs of the Task Parallel Library and the async/await keywords.</span></span>

<span data-ttu-id="968c6-115">Aşağıdaki kod, yöntemin nasıl görünebileceğine `ProcessPayment` basitleştirilmiş bir örnektir:</span><span class="sxs-lookup"><span data-stu-id="968c6-115">The following code is a simplified example of what the `ProcessPayment` method may look like:</span></span>

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

## <a name="asynchronous-http-apis"></a><span data-ttu-id="968c6-116">Asynchronous HTTP API'ler</span><span class="sxs-lookup"><span data-stu-id="968c6-116">Asynchronous HTTP APIs</span></span>

<span data-ttu-id="968c6-117">Bazı durumlarda, iş akışlarının tamamlanması nispeten uzun bir süre süren etkinlikler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="968c6-117">In some cases, workflows may contain activities that take a relatively long period of time to complete.</span></span> <span data-ttu-id="968c6-118">Ortam dosyalarının yedeklerini blob depolama alanına başlatan bir işlem düşünün.</span><span class="sxs-lookup"><span data-stu-id="968c6-118">Imagine a process that kicks off the backup of media files into blob storage.</span></span> <span data-ttu-id="968c6-119">Ortam dosyalarının boyutuna ve miktarına bağlı olarak, bu yedekleme işleminin tamamlanması saatler sürebilir.</span><span class="sxs-lookup"><span data-stu-id="968c6-119">Depending on the size and quantity of the media files, this backup process may take hours to complete.</span></span>

<span data-ttu-id="968c6-120">Bu senaryoda, `DurableOrchestrationClient`'çalışan bir iş akışının durumunu denetleme yeteneği yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="968c6-120">In this scenario, the `DurableOrchestrationClient`'s ability to check the status of a running workflow becomes useful.</span></span> <span data-ttu-id="968c6-121">İş akışını `HttpTrigger` başlatmak için bir `CreateCheckStatusResponse` yöntem kullanılırken, `HttpResponseMessage`bir ..</span><span class="sxs-lookup"><span data-stu-id="968c6-121">When using an `HttpTrigger` to start a workflow, the `CreateCheckStatusResponse` method can be used to return an instance of `HttpResponseMessage`.</span></span> <span data-ttu-id="968c6-122">Bu yanıt, istemciye taşıma işleminin durumunu denetlemek için kullanılabilecek bir URI yükü sağlar.</span><span class="sxs-lookup"><span data-stu-id="968c6-122">This response provides the client with a URI in the payload that can be used to check the status of the running process.</span></span>

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

<span data-ttu-id="968c6-123">Aşağıdaki örnek sonuç yanıt yükünün yapısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="968c6-123">The sample result below shows the structure of the response payload.</span></span>

```json
{
    "id": "instanceId",
    "statusQueryGetUri": "http://host/statusUri",
    "sendEventPostUri": "http://host/eventUri",
    "terminatePostUri": "http://host/terminateUri"
}
```

<span data-ttu-id="968c6-124">Tercih ettiğiniz HTTP istemcisini kullanarak, GET istekleri uri için statusQueryGetUri çalışan iş akışının durumunu incelemek için yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="968c6-124">Using your preferred HTTP client, GET requests can be made to the URI in statusQueryGetUri to inspect the status of the running workflow.</span></span> <span data-ttu-id="968c6-125">Döndürülen durum yanıtı aşağıdaki koda benzemelidir.</span><span class="sxs-lookup"><span data-stu-id="968c6-125">The returned status response should resemble the following code.</span></span>

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

<span data-ttu-id="968c6-126">İşlem devam ettikçe, durum yanıtı **başarısız** veya **tamamlanmış**olarak değişecektir.</span><span class="sxs-lookup"><span data-stu-id="968c6-126">As the process continues, the status response will change to either **Failed** or **Completed**.</span></span> <span data-ttu-id="968c6-127">Başarılı bir şekilde tamamlandığında, yükteki **çıktı** özelliği döndürülen verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="968c6-127">On successful completion, the **output** property in the payload will contain any returned data.</span></span>

## <a name="monitoring"></a><span data-ttu-id="968c6-128">İzleme</span><span class="sxs-lookup"><span data-stu-id="968c6-128">Monitoring</span></span>

<span data-ttu-id="968c6-129">Basit yinelenen görevler için Azure `TimerTrigger` İşlevleri, CRON ifadesine dayalı olarak zamanlanabilecek leri sağlar.</span><span class="sxs-lookup"><span data-stu-id="968c6-129">For simple recurring tasks, Azure Functions provides the `TimerTrigger` that can be scheduled based on a CRON expression.</span></span> <span data-ttu-id="968c6-130">Zamanlayıcı basit, kısa ömürlü görevler için iyi çalışır, ancak daha esnek zamanlama nın gerekli olduğu senaryolar olabilir.</span><span class="sxs-lookup"><span data-stu-id="968c6-130">The timer works well for simple, short-lived tasks, but there might be scenarios where more flexible scheduling is needed.</span></span> <span data-ttu-id="968c6-131">Bu senaryo, izleme deseni ve Dayanıklı İşlevler yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="968c6-131">This scenario is when the monitoring pattern and Durable Functions can help.</span></span>

<span data-ttu-id="968c6-132">Dayanıklı Fonksiyonlar, esnek zamanlama aralıkları, ömür boyu yönetim ve tek bir orkestrasyon işlevinden birden çok monitör işleminin oluşturulmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="968c6-132">Durable Functions allows for flexible scheduling intervals, lifetime management, and the creation of multiple monitor processes from a single orchestration function.</span></span> <span data-ttu-id="968c6-133">Bu işlevsellik için bir kullanım örneği, belirli bir eşik karşılandıktan sonra tamamlanan hisse senedi fiyat değişiklikleri için izleyiciler oluşturmak olabilir.</span><span class="sxs-lookup"><span data-stu-id="968c6-133">One use case for this functionality might be to create watchers for stock price changes that complete once a certain threshold is met.</span></span>

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

<span data-ttu-id="968c6-134">`DurableOrchestrationContext`'nin `CreateTimer` yöntemi, hisse senedi fiyat değişikliklerini denetlemek için döngünün bir sonraki çağırması için zamanlamayı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="968c6-134">`DurableOrchestrationContext`'s `CreateTimer` method sets up the schedule for the next invocation of the loop to check for stock price changes.</span></span> <span data-ttu-id="968c6-135">`DurableOrchestrationContext`ayrıca UTC geçerli DateTime değeri almak için bir `CurrentUtcDateTime` özelliği vardır.</span><span class="sxs-lookup"><span data-stu-id="968c6-135">`DurableOrchestrationContext` also has a `CurrentUtcDateTime` property to get the current DateTime value in UTC.</span></span> <span data-ttu-id="968c6-136">Test etmek için kolayca alay `DateTime.UtcNow` edildiği için bu özelliği kullanmak daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="968c6-136">It's better to use this property instead of `DateTime.UtcNow` because it's easily mocked for testing.</span></span>

## <a name="recommended-resources"></a><span data-ttu-id="968c6-137">Önerilen kaynaklar</span><span class="sxs-lookup"><span data-stu-id="968c6-137">Recommended resources</span></span>

- [<span data-ttu-id="968c6-138">Azure Dayanıklı İşlevler</span><span class="sxs-lookup"><span data-stu-id="968c6-138">Azure Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
- [<span data-ttu-id="968c6-139">.NET Çekirdek ve .NET Standardında Birim Testi</span><span class="sxs-lookup"><span data-stu-id="968c6-139">Unit Testing in .NET Core and .NET Standard</span></span>](../../core/testing/index.md)

>[!div class="step-by-step"]
><span data-ttu-id="968c6-140">[Önceki](durable-azure-functions.md)
>[Sonraki](serverless-business-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="968c6-140">[Previous](durable-azure-functions.md)
[Next](serverless-business-scenarios.md)</span></span>
