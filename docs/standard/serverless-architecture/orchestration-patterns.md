---
title: Orchestration desenleri - sunucusuz uygulamalar
description: Azure dayanıklı işlevler çekme isteği
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: c3b9dbe473ba9272a8c8c07cec86e11fcd9fc12d
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129319"
---
# <a name="orchestration-patterns"></a>Orchestration desenleri

Dayanıklı işlevler kolaylaştırır, sunucusuz bir ortamda ayrık, uzun süre çalışan etkinlikler oluşan durum bilgisi olan iş akışları oluşturmak. Dayanıklı İşlevler, yürütme geçmişini iş akışlarınız ve düzenli aralıklarla kontrol noktaları ilerlemesini izleyebilirsiniz olduğundan, kendisine bazı ilginç kalıpları uygulamak için uygundur.

## <a name="function-chaining"></a>Zincirleme işlevi

Tipik bir sıralı işlemde etkinlikleri birbiri ardına belirli bir sırayla yürütülmesi gerekir. İsteğe bağlı olarak, yaklaşan etkinlik bazı önceki işlev çıkışı gerektirebilir. Bu bağımlılık etkinlikleri sıralama üzerinde yürütme işlevi zinciri oluşturur.

Bu iş akışı deseni uygulamak için dayanıklı işlevler kullanmanın avantajı, denetim noktası yapmak için kendi yeteneği gelir. Sunucu çökerse, ağ zaman aşımına uğrar veya başka bir sorun ortaya çıkar, dayanıklı işlevler bilinen son durumundan sürdürme ve başka bir sunucu olsa bile, iş akışınızı çalıştırmak devam edebilirsiniz.

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

Yukarıdaki kod örneğinde, `CallActivityAsync` işlev, belirli bir etkinlik bir veri merkezindeki sanal makinede çalıştırmaktan sorumludur. Await döndürür ve temel alınan görev tamamlandığında, yürütme geçmiş tablosuna kaydedilir. Orchestrator işlevdeki kod yapabilir, görev paralel kitaplığı ve async/await anahtar sözcükleri tanıdık yapıları birini kullanın.

Aşağıdaki kod ne basitleştirilmiş bir örnektir `ProcessPayment` yöntemi görünebileceğini:

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

## <a name="asynchronous-http-apis"></a>Zaman uyumsuz HTTP API'leri

Bazı durumlarda, iş akışlarının tamamlanması oldukça uzun bir süre Süren etkinlikler içerebilir. Dosyaları blob depolama içine medya yedeklenmesini devre dışı başlatan bir işlem düşünün. Boyutu ve medya dosyalarını miktarını bağlı olarak, bu yedekleme işlemi tamamlamak için saat sürebilir.

Bu senaryoda, `DurableOrchestrationClient`ın çalışan bir iş akışı durumunu kontrol yeteneği yararlı olur. Kullanırken bir `HttpTrigger` bir iş akışının başlatılacağı `CreateCheckStatusResponse` yöntemi örneği döndürmek için kullanılabilir `HttpResponseMessage`. Bu yanıt yükünde çalışan işleminin durumunu denetlemek için kullanılan URI ile istemci sağlar.

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

Aşağıdaki örnek sonucu, yanıt yükünde yapısını gösterir.

```json
{
    "id": "instanceId",
    "statusQueryGetUri": "http://host/statusUri",
    "sendEventPostUri": "http://host/eventUri",
    "terminatePostUri": "http://host/terminateUri"
}
```

Tercih edilen HTTP İstemcisi'ni kullanarak GET istekleri statusQueryGetUri URI için çalışan bir iş akışı durumunu incelemek için yapılabilir. Döndürülen durum yanıt aşağıdaki koda benzemelidir.

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

İşlem devam ettikçe durum yanıt ya da değişecektir **başarısız** veya **tamamlandı**. Başarıyla tamamlandığında, **çıkış** yükünde özelliği her döndürülen veriler içerir.

## <a name="monitoring"></a>İzleme

Basit yinelenen görevler için Azure işlevlerinin sağladığı `TimerTrigger` zamanlanabilen bir CRON ifadeye göre. Zamanlayıcı da basit, kısa süreli görevler için çalışır olabilir ancak senaryoları burada daha esnek zamanlama gereklidir. Bu senaryo, izleme desen ve dayanıklı işlevler yardımcı olabilecek andır.

Dayanıklı işlevler esnek zamanlama aralıkları, ömür yönetimi ve birden çok izleme işlemlerini tek düzenleme işlevi oluşturulmasını sağlar. Bu işlev için bir kullanım örneği, belirli bir Eşiğe ulaşıldığında tamamlayan hisse senedi fiyatı değişiklikleri izleyicileri oluşturmak için olabilir.

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

`DurableOrchestrationContext`ın `CreateTimer` hisse senedi fiyatı değişiklikleri denetlemek için sonraki çağrının döngünün zamanlamasını ayarlama yöntemini ayarlar. `DurableOrchestrationContext` Ayrıca bir `CurrentUtcDateTime` özelliği geçerli bir tarih saat değeri UTC biçiminde alır. Yerine bu özelliği kullanmak iyidir `DateTime.UtcNow` kolayca test etmek için örnek için.

## <a name="recommended-resources"></a>Önerilen kaynaklar

* [Azure dayanıklı İşlevler](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
* [.NET Core ve .NET standart birim testi](https://docs.microsoft.com/dotnet/core/testing/)

>[!div class="step-by-step"]
>[Önceki](durable-azure-functions.md)
>[İleri](serverless-business-scenarios.md)