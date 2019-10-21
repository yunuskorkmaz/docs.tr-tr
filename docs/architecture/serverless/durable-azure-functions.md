---
title: Dayanıklı Azure işlevleri-sunucusuz uygulamalar
description: Sürekli Azure işlevleri, koddaki durum bilgisi olan iş akışlarını etkinleştirmek için Azure Işlevleri çalışma zamanını genişletir.
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 2c0ad086640409ac187c3aa882add4d6b39b6ff9
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522853"
---
# <a name="durable-azure-functions"></a>Dayanıklı Azure işlevleri

Azure Işlevleri ile sunucusuz uygulamalar oluştururken, işlemleriniz genellikle durum bilgisiz bir şekilde çalışacak şekilde tasarlanacaktır. Bu tasarım seçeneğinin nedeni, platformun ölçeklendirilirken, kodun hangi sunuculara çalıştığını anlamak zor hale gelir. Ayrıca, belirli bir noktada kaç örnek etkin olduğunu anlamak zor olur. Ancak, bir işlemin geçerli durumunun bilinmesini gerektiren uygulama sınıfları vardır. Çevrimiçi mağazaya sipariş gönderme sürecini göz önünde bulundurun. Kullanıma alma işlemi, işlemin durumunu bilmemiz gereken birden çok işlemden oluşan bir iş akışı olabilir. Bu tür bilgiler, müşterinin hesabında krediler varsa ve aynı zamanda kredi kartını işleme sonuçları varsa ürün envanterini içerebilir. Bu işlemler kendi iç iş akışlarına veya hatta üçüncü taraf sistemlerden gelen hizmetlere kolayca sahip olabilir.

Günümüzde, iç ve dış sistemler arasında uygulama durumunun koordinasyonuna yardımcı olacak çeşitli desenler vardır. Bu durumu yönetmek için merkezi sıraya alma sistemleri, dağıtılmış anahtar-değer depoları veya paylaşılan veritabanları kullanan çözümler arasında gelmesi yaygındır. Ancak, bunlar artık sağlanması ve yönetilmesi gereken tüm ek kaynaklardır. Sunucusuz bir ortamda, kodunuz bu kaynaklarla el ile koordine edilmeye çalışırken çok daha fazla hale gelebilir. Azure Işlevleri Dayanıklı İşlevler olarak adlandırılan durum bilgisi olan işlevleri oluşturmaya yönelik bir alternatif sunar.

Dayanıklı İşlevler, koddaki durum bilgisi olan iş akışlarının tanımını sağlayan Azure Işlevleri çalışma zamanının uzantısıdır. İş akışlarını etkinliklere bölmek için Dayanıklı İşlevler uzantısı durumu yönetebilir, ilerleme kontrol noktaları oluşturabilir ve sunucular arasında işlev çağrılarının dağıtımını işleyebilir. Arka planda, yürütme geçmişini kalıcı hale getirmek, etkinlik işlevlerini zamanlamak ve yanıtları almak için bir Azure depolama hesabı kullanır. Sunucusuz kodunuz, bu depolama hesabındaki kalıcı bilgilerle asla etkileşmemelidir ve genellikle geliştiricilerin etkileşimde bulunmak için ihtiyaç duyduğu bir şey değildir.

## <a name="triggering-a-stateful-workflow"></a>Durum bilgisi olan bir iş akışını tetikleme

Dayanıklı İşlevler durum bilgisi olan iş akışları, iki iç bileşene ayrılabilir; düzenleme ve etkinlik Tetikleyicileri. Tetikleyiciler ve bağlamalar, Azure Işlevleri tarafından, başlangıç, giriş alma ve sonuç döndürme sırasında sunucusuz işlevlerinizin bildirilmesini sağlamak için kullanılan temel bileşenlerdir.

### <a name="working-with-the-orchestration-client"></a>Orchestration istemcisiyle çalışma

Düzenlemeler, Azure Işlevlerinde tetiklenen işlemlerin diğer stilleriyle karşılaştırıldığında benzersizdir. Dayanıklı İşlevler, saat veya hatta tamamlanması gereken işlevlerin yürütülmesini sağlar. Bu tür davranışlar, çalışan bir düzenleme durumunun denetlenmesi, preemptively sonlanması veya dış olayların bildirimlerini gönderebilme gereksinimiyle birlikte gelir.

Bu tür durumlarda Dayanıklı İşlevler uzantısı, genişletilmiş işlevlerle etkileşime girebilmeniz için `DurableOrchestrationClient` sınıfını sağlar. @No__t_0 bağlamasını kullanarak Orchestration istemcisine erişebilirsiniz. Genellikle, bu özniteliği bir `HttpTrigger` veya `ServiceBusTrigger` gibi başka bir tetikleyici türüyle dahil edersiniz. Kaynak işlev tetiklendikten sonra, düzenleme istemcisi bir Orchestrator işlevi başlatmak için kullanılabilir.

```csharp
[FunctionName("KickOff")]
public static async Task<HttpResponseMessage> Run(
    [HttpTrigger(AuthorizationLevel.Function, "POST")]HttpRequestMessage req,
    [OrchestrationClient ] DurableOrchestrationClient<orchestrationClient>)
{
    OrderRequestData data = await req.Content.ReadAsAsync<OrderRequestData>();

    string instanceId = await orchestrationClient.StartNewAsync("PlaceOrder", data);

    return orchestrationClient.CreateCheckStatusResponse(req, instanceId);
}
```

### <a name="the-orchestrator-function"></a>Orchestrator işlevi

Azure Işlevleri 'nde, bir Orchestrator işlevi olarak işlev gören OrchestrationTriggerAttribute ile bir işleve açıklama ekleme. Durum bilgisi olan iş akışınızı oluşturan çeşitli etkinlikleri yönetmekten sorumludur.

Orchestrator işlevleri, OrchestrationTriggerAttribute dışındaki bağlamaları kullanamaz. Bu öznitelik, yalnızca DurableOrchestrationContext parametre türüyle kullanılabilir. İşlev imzasında girişlerin serisini kaldırma desteklenmediğinden başka giriş kullanılamaz. Orchestration istemcisi tarafından sağlanmış girdileri almak için Getınput \<T \> yöntemi kullanılmalıdır.

Ayrıca, düzenleme işlevlerinin dönüş türleri void, Task veya JSON serileştirilebilir değeri olmalıdır.

> *Hata işleme kodu breçekimi için ayrılmıştır*

```csharp
[FunctionName("PlaceOrder")]
public static async Task<string> PlaceOrder([OrchestrationTrigger] DurableOrchestrationContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    await context.CallActivityAsync<bool>("CheckAndReserveInventory", orderData);
    await context.CallActivityAsync<string>("ProcessPayment", orderData);

    string trackingNumber = await context.CallActivityAsync<string>("ScheduleShipping", orderData);
    await context.CallActivityAsync<string>("EmailCustomer", trackingNumber);

    return trackingNumber;
}
```

Bir Orchestration 'un birden fazla örneği aynı anda başlatılabilir ve çalıştırılabilir. @No__t_1 `StartNewAsync` yönteminin çağrılması, Orchestration 'un yeni bir örneğini başlatır. Yöntemi, düzenleme başladığında tamamlayan bir `Task<string>` döndürür. Düzenleme işlemi 30 saniye içinde başlatılmamışsa `TimeoutException` türünde bir özel durum oluşur.

@No__t_1 tamamlanan `Task<string>`, Orchestration örneğinin benzersiz KIMLIĞINI içermelidir. Bu örnek KIMLIĞI, belirli bir düzenleme üzerindeki işlemleri çağırmak için kullanılabilir. Düzenleme durumu veya gönderilen olay bildirimleri için sorgulanabilir.

### <a name="the-activity-functions"></a>Etkinlik işlevleri

Etkinlik işlevleri, iş akışını oluşturmak için bir Orchestration işlevi içinde birlikte oluşturulan ayrık işlemlerdir. İşte en çok gerçek iş gerçekleşir. İş mantığını, uzun süre çalışan süreçlerini ve bulmaca parçalarını daha büyük bir çözüme göre temsil ederler.

@No__t_0, `DurableActivityContext` türünde bir işlev parametresine açıklama eklemek için kullanılır. Ek açıklamanın kullanılması, işlevin etkinlik işlevi olarak kullanılması amaçlanan çalışma zamanına bildirir. Etkinlik işlevlerine giriş değerleri, `DurableActivityContext` parametresinin `GetInput<T>` yöntemi kullanılarak alınır.

Düzenleme işlevlerine benzer şekilde, etkinlik işlevlerinin dönüş türleri void, Task veya JSON serileştirilebilir bir değer olmalıdır.

Etkinlik işlevleri içinde oluşturulan işlenmemiş özel durumlar, çağıran Orchestrator işlevine gönderilir ve bir `TaskFailedException` olarak sunulur. Bu noktada, hata yakalanıp Orchestrator oturumu açabilir ve etkinlik yeniden denenebilir.

```csharp
[FunctionName("CheckAndReserveInventory")]
public static bool CheckAndReserveInventory([ActivityTrigger] DurableActivityContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    // Connect to inventory system and try to reserve items
    return true;
}
```

## <a name="recommended-resources"></a>Önerilen Kaynaklar

- [Dayanıklı İşlevler](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
- [Dayanıklı İşlevler bağlamaları](https://docs.microsoft.com/azure/azure-functions/durable-functions-bindings)
- [Dayanıklı İşlevler örnekleri yönetme](https://docs.microsoft.com/azure/azure-functions/durable-functions-instance-management)

>[!div class="step-by-step"]
>[Önceki](event-grid.md)
>[İleri](orchestration-patterns.md)
