---
title: Orchestration desenleri-sunucusuz uygulamalar
description: Azure dayanıklı işlevler PR
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 18e13c5355490ef4a019ceda459114bdb6bfd539
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68676738"
---
# <a name="orchestration-patterns"></a>Düzenleme desenleri

Dayanıklı İşlevler, sunucusuz bir ortamda ayrık, uzun süredir çalışan etkinliklerden oluşan durum bilgisiz iş akışlarının oluşturulmasını kolaylaştırır. Dayanıklı İşlevler, İş akışlarınızın ilerlemesini izleyebildiğiniz ve yürütme geçmişini düzenli olarak kontrol ettiğinden, bazı ilginç desenleri uygulamak için kendisini katlayın.

## <a name="function-chaining"></a>İşlev Zinciri

Tipik sıralı bir işlemde, etkinliklerin belirli bir sırada diğeri tarafından yürütülmesi gerekir. İsteğe bağlı olarak, yaklaşan etkinlik önceki işlevden bazı çıktılar gerektirebilir. Etkinlik sıralamasına yönelik bu bağımlılık, bir yürütme işlev zinciri oluşturur.

Bu iş akışı deseninin uygulanması için Dayanıklı İşlevler kullanmanın avantajı, kendi denetim noktası oluşturma özelliğinden gelir. Sunucu kilitlenirse, ağ zaman aşımına uğrar veya başka bir sorun oluşursa, dayanıklı işlevler, son bilinen durumdan devam edebilir ve başka bir sunucuda olsa bile iş akışınızı çalıştırmaya devam edebilir.

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

Yukarıdaki kod örneğinde, `CallActivityAsync` işlev veri merkezindeki bir sanal makinede belirli bir etkinliği çalıştırmaktan sorumludur. Await döndürüldüğünde ve temel alınan görev tamamlandığında, yürütme geçmiş tablosuna kaydedilir. Orchestrator işlevindeki kod, görev paralel kitaplığı ve zaman uyumsuz/await anahtar kelimeleriyle ilgili tanıdık yapıların herhangi birini kullanabilir.

Aşağıdaki kod, `ProcessPayment` yöntemin neye benzebildiklerine yönelik basitleştirilmiş bir örnektir:

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

## <a name="asynchronous-http-apis"></a>Zaman uyumsuz HTTP API 'Leri

Bazı durumlarda, iş akışları görece uzun süre süren etkinlikleri içerebilir. Medya dosyalarının yedeklenmesini blob depolamaya vurur bir işlem düşünün. Medya dosyalarının boyutuna ve miktarına bağlı olarak, bu yedekleme işleminin tamamlanması saatler sürebilir.

Bu senaryoda, `DurableOrchestrationClient`çalışan bir iş akışının durumunu denetleme özelliği yararlı olur. Bir iş akışını `HttpTrigger` başlatmak için bir kullanırken `CreateCheckStatusResponse` , yöntemi bir örneği döndürmek `HttpResponseMessage`için kullanılabilir. Bu yanıt, istemcide çalışan işlemin durumunu denetlemek için kullanılabilecek bir URI sağlar.

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

Aşağıdaki örnek sonuç, yanıt yükünün yapısını gösterir.

```json
{
    "id": "instanceId",
    "statusQueryGetUri": "http://host/statusUri",
    "sendEventPostUri": "http://host/eventUri",
    "terminatePostUri": "http://host/terminateUri"
}
```

Tercih edilen HTTP istemcinizi kullanarak, çalışan iş akışının durumunu incelemek için statusQueryGetUri içindeki URI 'ye alma istekleri yapılabilir. Döndürülen durum yanıtı aşağıdaki koda benzemelidir.

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

İşlem devam ettiğinden, durum yanıtı **başarısız** ya da **tamamlandı**olarak değişir. Başarılı tamamlandığında, yükteki **output** özelliği döndürülen tüm verileri içerecektir.

## <a name="monitoring"></a>İzleme

Azure işlevleri, basit yinelenen görevler için bir cron ifadesine göre zamanlanabilen ' ı sağlar `TimerTrigger` . Zamanlayıcı basit, kısa süreli görevler için iyi işler, ancak daha esnek zamanlamanın gerektiği senaryolar olabilir. Bu senaryo, izleme deseninin ve Dayanıklı İşlevler yardımcı olabilir.

Dayanıklı İşlevler, esnek zamanlama aralıklarına, ömür yönetimine ve tek bir düzenleme işlevinden birden çok izleme işleminin oluşturulmasına olanak sağlar. Bu işlevsellik için bir kullanım örneği, belirli bir eşiğin karşılandıktan sonra tamamlanan stok fiyatı değişiklikleri için izleyicileri oluşturmak olabilir.

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

`DurableOrchestrationContext``CreateTimer` yöntemi, stok fiyatı değişikliklerini denetlemek için döngünün bir sonraki çağrılma zamanlamasını ayarlar. `DurableOrchestrationContext`Ayrıca UTC 'de `CurrentUtcDateTime` geçerli tarih saat değerini almak için bir özelliğe sahiptir. Test etmek için kolayca bu özelliğin `DateTime.UtcNow` kullanılması daha iyidir.

## <a name="recommended-resources"></a>Önerilen Kaynaklar

* [Azure Dayanıklı İşlevler](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
* [.NET Core ve .NET Standard birim testi](../../core/testing/index.md)

>[!div class="step-by-step"]
>[Önceki](durable-azure-functions.md)İleri
>[](serverless-business-scenarios.md)
