---
title: Dayanıklı Azure işlevleri - sunucusuz uygulamalar
description: Dayanıklı Azure işlevleri, Azure işlevleri çalışma zamanı, durum bilgisi olan iş akışlarının kodda etkinleştirmek için genişletin.
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: f7ee74926d6658042120113b49dc763383881423
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65643410"
---
# <a name="durable-azure-functions"></a>Dayanıklı Azure işlevleri

Azure işlevleri ile sunucusuz uygulamalar oluştururken, durum bilgisi olmayan bir şekilde çalıştırmak için işlemlerinizi genellikle tasarlanması. Bu tasarım tercihinin nedeni, platform ölçekler kodu çalıştıran hangi sunucuların anlamak zor hale olmasıdır. Ayrıca, kaç tane belirli bir anda etkin olan anlamak zor olur. Ancak, bilinmesi bir işlemin geçerli durumunu gerektiren uygulamalar sınıfı vardır. Bir çevrimiçi mağaza için bir sipariş göndermeden işleminde göz önünde bulundurun. Kullanıma alma işlemi işleminin durumunu bilmeniz gereken birden çok işlemlerini oluşan bir iş akışı olabilir. Bir müşterinin hesabını ve kredi kartı işleme sonuçlarını tüm krediler varsa ürün envanteri gibi bilgileri içerebilir. Bu işlemler kolayca kendi iç iş akışları veya üçüncü taraf sistemlerden hatta Hizmetleri olabilir.

Çeşitli desenlerini bugün bu yardımcı uygulama durumu iç ve dış sistemler arasında koordinasyon ile mevcut. Merkezi kuyruk sistemleri, dağıtılmış anahtar-değer depoları veya o durumu yönetmek için paylaşılan veritabanları kullanan çözümler arasında gelen yaygındır. Ancak, bunlar artık sağlanan ve yönetilen için gereken tüm ek kaynaklara uygulanır. Sunucusuz bir ortamda kodunuzu ile bu kaynakları el ile koordine etmek zahmetli hale gelebilir. Azure işlevleri, durum bilgisi olan işlevler dayanıklı işlevler adlı oluşturmak için bir alternatif sunar.

Dayanıklı işlevler kod durum bilgisi olan iş akışı tanımını sağlayan Azure işlevleri çalışma zamanı bir uzantısıdır. Etkinlikler iş akışlarına bölmek tarafından dayanıklı işlevler uzantısını durumu yönetebilir, ilerleme denetim noktalarını oluşturma ve işlev çağrılarının dağıtım sunucular arasında işleme. Arka planda bir Azure depolama hesabını kullan yürütme geçmişi kalıcı hale getirmek için etkinlik işlevlerini zamanlamak ve yanıtları almak kolaylaştırır. Sunucusuz kod hiçbir zaman bu depolama hesabında kalıcı bilgilerle etkileşim kuracağını ve genellikle geliştiriciler ile etkileşim kurmak için gerekli değildir.

## <a name="triggering-a-stateful-workflow"></a>Durum bilgisi olan iş akışı tetikler

Dayanıklı işlevler durum bilgisi olan iş akışlarında iç iki bileşene ayrılabilir; düzenleme ve etkinliği tetikler. Tetikleyiciler ve bağlamalar başlatmak almak için giriş ve döndürülecek sonuçları bildirilmesini sağlamak uygulamanızın sunucusuz işlevlerini etkinleştirmek için Azure işlevleri tarafından kullanılan temel bileşenleridir.

### <a name="working-with-the-orchestration-client"></a>Düzenleme istemcisi ile çalışma

Azure işlevleri'nde tetiklenen işlemlerinin başka stilleri karşılaştırıldığında düzenlemeleri benzersizdir. Dayanıklı işlevler ele saat veya gün tamamlamak için bile işlevlerin yürütülmesini sağlar. Bu türden bir davranış, çalışan bir düzenleme durumunu denetlemek izinlere gerek ile sıd'lerde sonlandırmak veya dış olaylar bildirim göndermek gelir.

Böyle durumlarda, dayanıklı işlevler uzantısını sağlar `DurableOrchestrationClient` ile etkileşimde bulunmanızı sağlar sınıfını işlevleri düzenlenir. Kullanarak düzenleme istemcisi için size erişim `OrchestrationClientAttribute` bağlama. Genellikle, bu öznitelik başka bir tetikleyici türü ile gibi dahil bir `HttpTrigger` veya `ServiceBusTrigger`. Kaynak işlevi tetiklendikten sonra düzenleme istemcisi bir düzenleyici işlevi başlatmak için kullanılabilir.

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

Azure işlevleri işaretleri OrchestrationTriggerAttribute işleviyle bu işlev bir düzenleyici işlevi ek açıklama ekleniyor. Durum bilgisi olan iş akışınızı kurabilmeniz çeşitli etkinliklerinin yönetmekten sorumludur.

Orchestrator işlevleri yapamazsınız OrchestrationTriggerAttribute dışında bağlamalarının kullanın. Bu öznitelik yalnızca DurableOrchestrationContext parametre türü ile kullanılabilir. İşlev imzası girişlerinde seri durumdan çıkarma desteklenmiyor olduğundan, diğer giriş kullanılabilir. Düzenleme istemcisi, GetInput sağlanan girişler almak için\<T\> yöntemi kullanılmalıdır.

Ayrıca, orchestration işlevlerin dönüş türleri olmalıdır void, görev veya JSON seri hale getirilebilir bir değer.

> *Hata işleme kodunu konuyu uzatmamak amacıyla bırakıldı '*

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

Birden çok örneğini düzenleme aynı anda kullanmaya başlama ve çalışıyor olabilir. Çağırma `StartNewAsync` metodunda `DurableOrchestrationClient` düzenleme yeni bir örneğini başlatır. Yöntem döndürür bir `Task<string>` düzenleme başlatıldığında tamamlar. Türünde bir özel durum `TimeoutException` düzenleme 30 saniye içinde başlamadığı olursa durum.

Tamamlanan `Task<string>` gelen `StartNewAsync` düzenleme örneğinin benzersiz Kimliğini içermelidir. Bu örnek kimliği, belirli düzenleme işlemleri çağırmak için kullanılabilir. Düzenleme durumu sorgulanan veya olay bildirimleri gönderdiniz.

### <a name="the-activity-functions"></a>Etkinlik işlevleri

Etkinlik işlevleri iş akışı oluşturmak için bir düzenleme işlevi içinde birlikte oluşan ayrık işlemlerdir. İşte burada gerçek çoğunu gerçekleşmesi. Bunlar, iş mantığı göstermek, çalışan işlemleri ve daha büyük bir çözümü için Bulmacanın parçaları uzun.

`ActivityTriggerAttribute` Türünde bir işlev parametre öğesine açıklama eklemek için kullanılan `DurableActivityContext`. Ek açıklama kullanarak, çalışma zamanı işlevi bir etkinlik işlevi kullanılması amaçlanmıştır bildirir. Etkinlik işlevlere giriş değerlerini kullanarak alınır `GetInput<T>` yöntemi `DurableActivityContext` parametresi.

Benzer şekilde düzenleme işlevleri, etkinlik işlevlerin dönüş türleri olmalıdır void, görev veya JSON seri hale getirilebilir bir değer.

Etkinlik işlevler içinde oluşturulan işlenmemiş özel durumlar çağırma orchestrator işlevine gönderileceği alıp olarak sunulan bir `TaskFailedException`. Bu noktada, hata yakalandı ve orchestrator'da günlüğe kaydedilir ve etkinlik yeniden denenebilir.

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

* [Dayanıklı İşlevler](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
* [Dayanıklı işlevler için bağlamaları](https://docs.microsoft.com/azure/azure-functions/durable-functions-bindings)
* [Dayanıklı işlevler örneklerini yönetme](https://docs.microsoft.com/azure/azure-functions/durable-functions-instance-management)

>[!div class="step-by-step"]
>[Önceki](event-grid.md)
>[İleri](orchestration-patterns.md)
