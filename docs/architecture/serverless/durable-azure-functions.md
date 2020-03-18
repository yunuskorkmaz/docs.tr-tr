---
title: Dayanıklı Azure fonksiyonları - Sunucusuz uygulamalar
description: Dayanıklı Azure işlevleri, koddaki devlet eserini etkinleştirmek için Azure İşlevlerini çalışma süresini genişletir.
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 2c0ad086640409ac187c3aa882add4d6b39b6ff9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522853"
---
# <a name="durable-azure-functions"></a>Dayanıklı Azure işlevleri

Azure İşlevleri ile sunucusuz uygulamalar oluştururken, işlemleriniz genellikle stateless bir şekilde çalışacak şekilde tasarlanacaktır. Bu tasarım seçiminin nedeni, platform ölçeklendikçe kodun hangi sunucularda çalıştığını bilmenin zorlaşmasıdır. Ayrıca, herhangi bir noktada kaç örneğin etkin olduğunu bilmek de zorlaşır. Ancak, bir işlemin geçerli durumunun bilinmesini gerektiren uygulama sınıfları vardır. Çevrimiçi bir mağazaya sipariş gönderme işlemini göz önünde bulundurun. Ödeme işlemi, işlemin durumunu bilmesi gereken birden çok işlemden oluşan bir iş akışı olabilir. Bu tür bilgiler, müşterinin hesabında herhangi bir kredi varsa ürün envanterini ve kredi kartının işlenmesinin sonuçlarını içerebilir. Bu işlemler kolayca kendi iç iş akışları ve hatta üçüncü taraf sistemlerden hizmetleri olabilir.

Günümüzde iç ve dış sistemler arasında uygulama durumunun koordinasyonuna yardımcı olan çeşitli desenler mevcuttur. Merkezi sıraya sistemleri, dağıtılan anahtar değer depoları veya bu durumu yönetmek için paylaşılan veritabanlarına dayanan çözümlerle karşılaşmak yaygındır. Ancak, bunların tümü artık sağlanması ve yönetilmesi gereken ek kaynaklardır. Sunucusuz bir ortamda, kodunuz bu kaynaklarla el ile koordine etmeye çalışırken hantal hale gelebilir. Azure İşlevler, Dayanıklı Işlevler adı verilen durum lu işlevler oluşturmak için bir alternatif sunar.

Dayanıklı Işlevler, koddaki devlet li iş akışlarının tanımını sağlayan Azure İşlevleri çalışma zamanının bir uzantısıdır. İş akışlarını etkinliklere ayırarak, Dayanıklı Işlevler uzantısı durumu yönetebilir, ilerleme denetim leri oluşturabilir ve işlev çağrılarının sunucular arasında dağıtımını işleyebilir. Arka planda, yürütme geçmişini sürdürmek, etkinlik işlevlerini zamanlamak ve yanıtları almak için bir Azure Depolama hesabı kullanır. Sunucusuz kodunuz hiçbir zaman bu depolama hesabındaki kalıcı bilgilerle etkileşime girmemelidir ve genellikle geliştiricilerin etkileşimde olması gereken bir şey değildir.

## <a name="triggering-a-stateful-workflow"></a>Durum lu bir iş akışını tetikleme

Dayanıklı Işlevler'deki durumsal iş akışları iki içsel bileşene ayrılabilir; orkestrasyon ve aktivite tetikler. Tetikleyiciler ve bağlamalar, sunucusuz işlevlerinizin başlatıldığında, girdi alacağında ve sonuçları döndüreceğinizde bildirilmesini sağlamak için Azure İşlevleri tarafından kullanılan temel bileşenlerdir.

### <a name="working-with-the-orchestration-client"></a>Orkestrasyon istemcisi ile çalışma

Azure İşlevlerinde tetiklenen diğer işlem stilleriyle karşılaştırıldığında, orkestrasyonlar benzersizdir. Dayanıklı Fonksiyonlar, tamamlanması saatler, hatta günler süren işlevlerin yürütülmesini sağlar. Bu tür davranışlar, çalışan bir orkestrasyonun durumunu denetleme, önceden sonlandırma veya dış olaylarla ilgili bildirimler gönderebilme gereksinimiyle birlikte gelir.

Bu gibi durumlarda, Dayanıklı İşlevler uzantısı, düzenlenmiş işlevlerle etkileşimkurmanızı sağlayan `DurableOrchestrationClient` sınıfı sağlar. Bağlamayı kullanarak orkestrasyon istemcisine `OrchestrationClientAttribute` erişebilirsiniz. Genellikle, bu özniteliği başka bir tetikleyici türüyle `HttpTrigger` eklersiniz, örneğin. `ServiceBusTrigger` Kaynak işlevi tetiklendikten sonra, orkestrasyon istemcisi bir orchestrator işlevini başlatmak için kullanılabilir.

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

### <a name="the-orchestrator-function"></a>Orkestratör işlevi

Azure İşlevlerinde OrchestrationTriggerAttribute ile bir işlevin açıklama ekedilmesi, bir orkestratör işlevi olarak işlev görür. Özel iş akışınızı oluşturan çeşitli etkinlikleri yönetmekten sorumludur.

Orchestrator işlevleri OrchestrationTriggerAttribute dışındaki bağlamaları kullanamaz. Bu öznitelik yalnızca Dayanıklı Düzenleme Bağlamı'nın parametre türüyle kullanılabilir. İşlev imzasındaki girdilerin deserialization desteklenmediğinden başka giriş ler kullanılamaz. Düzenleme istemcisi tarafından sağlanan girişleri almak için\<\> GetInput T yöntemi kullanılmalıdır.

Ayrıca, düzenleme işlevlerinin dönüş türleri geçersiz, Görev veya JSON serileştirilebilir değer olmalıdır.

> *Hata işleme kodu kısalık için dışarıda bırakıldı*

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

Bir orkestrasyonun birden çok örneği aynı anda başlatılabilir ve çalıştırılabilir. Başlatma `StartNewAsync` yöntemini `DurableOrchestrationClient` çağırmak, orkestrasyonun yeni bir örneğini başlatıyor. Yöntem, orkestrasyon başlatıldığında tamamlayan bir `Task<string>` döndürür. Orkestrasyon `TimeoutException` 30 saniye içinde başlamadıysa, tür bir istisna atılır.

Tamamlanan `Task<string>` `StartNewAsync` orkestrasyon örneğinin benzersiz kimliğini içermelidir. Bu örnek kimliği, belirli bir düzenleme deki işlemleri çağırmak için kullanılabilir. Orkestrasyon durum için sorgulanabilir veya olay bildirimleri gönderilebilir.

### <a name="the-activity-functions"></a>Etkinlik fonksiyonları

Etkinlik işlevleri, iş akışını oluşturmak için bir orkestrasyon işlevi içinde bir araya gelen ayrık işlemlerdir. Burada gerçek işin çoğu yer alacak. Onlar iş mantığı, uzun çalışan süreçler ve daha büyük bir çözüm için bulmaca parçaları temsil.

Bu `ActivityTriggerAttribute` tür `DurableActivityContext`bir işlev parametresi açıklama yapmak için kullanılır. Ek açıklamanın kullanılması, çalışma saatini işlevin bir etkinlik işlevi olarak kullanılmasının amaçlandığını bildirir. Etkinlik işlevlerine giriş değerleri `GetInput<T>` `DurableActivityContext` parametre yöntemi kullanılarak alınır.

Düzenleme işlevlerine benzer şekilde, etkinlik işlevlerinin dönüş türleri geçersiz, Görev veya JSON serileştirilebilir değer olmalıdır.

Etkinlik işlevleri içinde atılan işlenmemiş özel durumlar, çağrı orkestratör işlevine gönderilir `TaskFailedException`ve bir . Bu noktada, hata yakalanabilir ve orkestratörde günlüğe kaydedilebilir ve etkinlik yeniden denenebilir.

```csharp
[FunctionName("CheckAndReserveInventory")]
public static bool CheckAndReserveInventory([ActivityTrigger] DurableActivityContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    // Connect to inventory system and try to reserve items
    return true;
}
```

## <a name="recommended-resources"></a>Önerilen kaynaklar

- [Dayanıklı İşlevler](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
- [Dayanıklı Fonksiyonlar için Bağlamalar](https://docs.microsoft.com/azure/azure-functions/durable-functions-bindings)
- [Dayanıklı İşlevler'deki örnekleri yönetme](https://docs.microsoft.com/azure/azure-functions/durable-functions-instance-management)

>[!div class="step-by-step"]
>[Önceki](event-grid.md)
>[Sonraki](orchestration-patterns.md)
