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
# <a name="orchestration-patterns"></a>Orkestrasyon desenleri

Dayanıklı Işlevler, sunucusuz bir ortamda ayrık, uzun süren etkinliklerden oluşan durumlu iş akışları oluşturmayı kolaylaştırır. Dayanıklı Fonksiyonlar iş akışlarınızın ilerlemesini izleyip yürütme geçmişini düzenli olarak kontrol edebildiği için, bazı ilginç desenler ilerler.

## <a name="function-chaining"></a>İşlev zinciri oluşturma

Tipik bir sıralı işlemde, etkinliklerin belirli bir sırada birbiri ardına yürütülmesi gerekir. İsteğe bağlı olarak, yaklaşan etkinlik önceki işlevden bazı çıktı gerektirebilir. Etkinliklerin sıralanmasına yapılan bu bağımlılık, bir yürütme işlevi zinciri oluşturur.

Bu iş akışı deseni uygulamak için Dayanıklı Fonksiyonlar kullanmanın yararı, denetim noktası yapma yeteneğinden gelir. Sunucu çökerse, ağ süreleri doluyorveya başka bir sorun oluşursa, Dayanıklı işlevler bilinen son durumdan devam edebilir ve başka bir sunucuda olsa bile iş akışınızı çalıştırmaya devam edebilir.

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

Önceki kod örneğinde, `CallActivityAsync` işlev veri merkezindeki sanal bir makinede belirli bir etkinliği çalıştırmakla yükümlüdür. Bekleme geri döndüğünde ve temel Görev tamamlandığında, yürütme geçmiş tablosuna kaydedilir. Orkestratör işlevindeki kod, Görev Paralel Kitaplığı'nın tanıdık yapılarından herhangi birini ve async/await anahtar kelimelerinden yararlanabilir.

Aşağıdaki kod, yöntemin nasıl görünebileceğine `ProcessPayment` basitleştirilmiş bir örnektir:

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

## <a name="asynchronous-http-apis"></a>Asynchronous HTTP API'ler

Bazı durumlarda, iş akışlarının tamamlanması nispeten uzun bir süre süren etkinlikler içerebilir. Ortam dosyalarının yedeklerini blob depolama alanına başlatan bir işlem düşünün. Ortam dosyalarının boyutuna ve miktarına bağlı olarak, bu yedekleme işleminin tamamlanması saatler sürebilir.

Bu senaryoda, `DurableOrchestrationClient`'çalışan bir iş akışının durumunu denetleme yeteneği yararlıdır. İş akışını `HttpTrigger` başlatmak için bir `CreateCheckStatusResponse` yöntem kullanılırken, `HttpResponseMessage`bir .. Bu yanıt, istemciye taşıma işleminin durumunu denetlemek için kullanılabilecek bir URI yükü sağlar.

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

Aşağıdaki örnek sonuç yanıt yükünün yapısını gösterir.

```json
{
    "id": "instanceId",
    "statusQueryGetUri": "http://host/statusUri",
    "sendEventPostUri": "http://host/eventUri",
    "terminatePostUri": "http://host/terminateUri"
}
```

Tercih ettiğiniz HTTP istemcisini kullanarak, GET istekleri uri için statusQueryGetUri çalışan iş akışının durumunu incelemek için yapılabilir. Döndürülen durum yanıtı aşağıdaki koda benzemelidir.

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

İşlem devam ettikçe, durum yanıtı **başarısız** veya **tamamlanmış**olarak değişecektir. Başarılı bir şekilde tamamlandığında, yükteki **çıktı** özelliği döndürülen verileri içerir.

## <a name="monitoring"></a>İzleme

Basit yinelenen görevler için Azure `TimerTrigger` İşlevleri, CRON ifadesine dayalı olarak zamanlanabilecek leri sağlar. Zamanlayıcı basit, kısa ömürlü görevler için iyi çalışır, ancak daha esnek zamanlama nın gerekli olduğu senaryolar olabilir. Bu senaryo, izleme deseni ve Dayanıklı İşlevler yardımcı olabilir.

Dayanıklı Fonksiyonlar, esnek zamanlama aralıkları, ömür boyu yönetim ve tek bir orkestrasyon işlevinden birden çok monitör işleminin oluşturulmasına olanak tanır. Bu işlevsellik için bir kullanım örneği, belirli bir eşik karşılandıktan sonra tamamlanan hisse senedi fiyat değişiklikleri için izleyiciler oluşturmak olabilir.

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

`DurableOrchestrationContext`'nin `CreateTimer` yöntemi, hisse senedi fiyat değişikliklerini denetlemek için döngünün bir sonraki çağırması için zamanlamayı ayarlar. `DurableOrchestrationContext`ayrıca UTC geçerli DateTime değeri almak için bir `CurrentUtcDateTime` özelliği vardır. Test etmek için kolayca alay `DateTime.UtcNow` edildiği için bu özelliği kullanmak daha iyidir.

## <a name="recommended-resources"></a>Önerilen kaynaklar

- [Azure Dayanıklı İşlevler](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
- [.NET Çekirdek ve .NET Standardında Birim Testi](../../core/testing/index.md)

>[!div class="step-by-step"]
>[Önceki](durable-azure-functions.md)
>[Sonraki](serverless-business-scenarios.md)
