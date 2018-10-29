---
title: Mikro hizmetler (tümleştirme olayları) arasında olay tabanlı iletişim uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Mikro hizmetler (tümleştirme olayları) arasında olay tabanlı iletişim uygulama
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: 6a365c284d66ea24a9bb4caae51c63f22c79877b
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50194052"
---
# <a name="implementing-event-based-communication-between-microservices-integration-events"></a>Mikro hizmetler (tümleştirme olayları) arasında olay tabanlı iletişim uygulama

Olay tabanlı iletişim kullandığınızda, daha önce açıklandığı gibi bir mikro hizmet önemli bir sorun olduğunda bir iş varlığı güncelleştirdiği gibi durum gerçekleştiğinde bir olay yayımlar. Diğer mikro hizmetler, bu olaylara abone olun. Bir mikro hizmet, bir olayı aldığında, yayımlanmakta daha fazla olay için yol açabilecek kendi iş varlıklarını güncelleştirebilirsiniz. Bu yayımlama/abone olma sistem, genellikle bir olay veri yolu uygulaması kullanılarak gerçekleştirilir. Olay veri yoluna abone olma ve aboneliği olayları ve olayları yayımlamak için gereken API ile arabirim olarak tasarlanabilir. Bir ileti kuyruğu veya zaman uyumsuz iletişim ve bir yayımlama/abone olma modelini destekleyen bir service bus gibi tüm işlemler arası veya Mesajlaşma iletişimi göre bir veya daha fazla uygulamaları da olabilir.

Olayları birden çok hizmet span iş işlemleri uygulamak üzere bu hizmetler arasındaki son tutarlılık sağlayan kullanabilirsiniz. Sonunda tutarlı bir işlem, dağıtılmış işlemlerin bir dizi oluşur. Her eylem bir mikro hizmet iş varlığı güncelleştirir ve sonraki eylemi tetikleyen bir olay yayımlar.

![](./media/image19.PNG)

**Şekil 8-18**. Bir olay veri yoluna bağlı olarak olay tabanlı iletişim

Bu bölümde, Şekil 8-18'de gösterildiği gibi bir genel olay veri yolu arabirimini kullanarak bu tür .NET ile iletişimin nasıl uygulayacağınıza dair açıklanmaktadır. Her bir farklı teknoloji veya RabbitMQ, Azure Service Bus, ya da başka üçüncü taraf açık kaynak veya ticari hizmet veri yolu gibi altyapı kullanarak birden çok olası uygulamaları vardır.

## <a name="using-message-brokers-and-services-buses-for-production-systems"></a>İleti aracıları ve Hizmetleri yollarına üretim sistemleri için kullanma

Mimari bölümünde belirtildiği gibi soyut olay veri yolu uygulamak için birden çok Mesajlaşma teknolojilerinin arasından seçim yapabilirsiniz. Ancak, farklı düzeylerde bu teknolojilerdir. Örneğin, RabbitMQ, Mesajlaşma Aracısı Aktarım, Azure Service Bus, NServiceBus, MassTransit veya Brighter gibi ticari ürünleri daha düşük bir düzeyde altındadır. Bu ürünlerin çoğunu, RabbitMQ veya Azure Service Bus üzerinde çalışabilir. Ürün tercih ettiğiniz kaç özellikleri ve ne kadar out-bulunmayan ölçeklenebilirlik, uygulamanız için gereken bağlıdır.

Yalnızca bir olay veri yolu kavram kanıtı hizmetine örnek olduğu gibi geliştirme ortamınız için uygulamak için basit bir uygulama bir kapsayıcı olarak çalışan RabbitMQ üzerinde yeterli olabilir. Ancak için Görev açısından kritik ve yüksek ölçeklenebilirlik gerektiren üretim sistemlerine değerlendirmek ve Azure hizmet veri Yolu'nu olmak isteyebilirsiniz.

Yüksek düzeyde soyutlama gerektiriyorsa ve gibi daha zengin özellikler [Sagas](https://docs.particular.net/nservicebus/sagas/) Dağıtılmış Geliştirme yapmak daha kolay, diğer ticari ve açık kaynak hizmeti yollarına NServiceBus, MassTransit, gibi uzun süre çalışan işlemler için ve Parlak değerlendirme değer var. Bu durumda, soyutlamaları ve kullanmak için API genellikle doğrudan bu üst düzey hizmet yolları yerine kendi soyutlama tarafından sağlanan olanları olur (gibi [sağlanan hizmetine basit olay veri yolu soyutlama](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/BuildingBlocks/EventBus/EventBus/Abstractions/IEventBus.cs)). Bu konular için ' ın, araştırma [çatallanmış NServiceBus kullanarak hizmetine](https://go.particular.net/eShopOnContainers) (belirli bir yazılım tarafından uygulanan ek türetilmiş örneği)

Elbette, her zaman kendi hizmet veri yolu özelliklerinin RabbitMQ ve Docker gibi alt düzey teknolojileri üzerine da oluşturabilirsiniz, ancak "tekerleği geliştirdi için" gereken çalışmayı özel Kurumsal uygulama için çok yüksek maliyetli olabilir.

## <a name="integration-events"></a>Tümleştirme olayları

Tümleştirme olayları, birden çok mikro hizmette veya dış sistemler arasında etki alanı durumu eşitlenmiş getirmek için kullanılır. Bu, mikro hizmet dışında tümleştirme olayları yayımlama tarafından gerçekleştirilir. Birden çok alıcı mikro hizmetler (için tümleştirme olaya abone olduğu gibi çok mikro hizmetler) için bir olay yayımlandığında her alıcı mikro hizmet uygun olay işleyicisi olayını işler.

Bir tümleştirme temel olarak aşağıdaki örnekte olduğu gibi bir veri tutan sınıf olaydır:

```csharp
public class ProductPriceChangedIntegrationEvent : IntegrationEvent
{
    public int ProductId { get; private set; }
    public decimal NewPrice { get; private set; }
    public decimal OldPrice { get; private set; }

    public ProductPriceChangedIntegrationEvent(int productId, decimal newPrice,
        decimal oldPrice)
    {
        ProductId = productId;
        NewPrice = newPrice;
        OldPrice = oldPrice;
    }
}
```

Gelen bir şekilde nasıl Viewmodel'lar sunucu ve istemci tanımlandığı için karşılaştırılabilir diğer mikro hizmetler, ayrılmış şekilde her mikro hizmet uygulama düzeyinde tümleştirme olayları tanımlanabilir. Ne önerilmez birden fazla mikro hizmetler arasında ortak bir tümleştirme olayları kitaplığı paylaşıyor; Bunu tek olay tanımı veri kitaplığı ile bu mikro hizmetler eşlenmesiyle. Aynı ortak bir etki alanı modeli birden çok mikro hizmetler arasında paylaşmak istemediğiniz açısından yapmak istiyor musunuz: mikro hizmetler tamamen otonom olmalıdır.

Yalnızca birkaç tür kitaplıkları mikro hizmetler arasında paylaşmalıdır vardır. Son uygulama bloğu gibi kitaplıkları biridir [olay veri yolu istemci API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/BuildingBlocks/EventBus), hizmetine gibi. JSON seri hale getiricileri genişletme gibi NuGet bileşenlerini de paylaşım araçları oluşturan kitaplıkları da başka bir özelliktir.

## <a name="the-event-bus"></a>Olay veri yolu

Bir olay veri yolu, Şekil 8-19'gösterildiği gibi açıkça birbirinden farkında olması gereken bileşenleri gerektirmeden mikro hizmetler arasında yayımlama/abone olun-style iletişime olanak sağlar.

![](./media/image20.png)

**Şekil 8-19**. Yayımlama/abonelik bir olay veri yolu temel kavramları

Olay veri yolu gözlemci deseni ve yayımlama ilgili-abone ol modeli.

### <a name="observer-pattern"></a>Gözlemci deseni

İçinde [gözlemci deseni](https://en.wikipedia.org/wiki/Observer_pattern), birincil nesnenizin (Observable bilinir) ilgili bilgileri (olayları) ile (gözlemciler bilinir) diğer ilgili nesneleri bildirir.

### <a name="publish-subscribe-pubsub-pattern"></a>Yayımla-abone ol (Pub/Sub) deseni 

Amacı [Pub/Sub deseni](https://msdn.microsoft.com/library/ff649664.aspx) gözlemci deseni ile aynıdır: belirli olaylar gerçekleştiğinde diğer hizmetleri bildirimde bulunmak istiyorsunuz. Ancak gözlemci ve Pub/Sub desenler arasında önemli bir fark yoktur. "Birbirine alışık oldukları için" gözlemci desende yayın gözlemciler için doğrudan observable gerçekleştirilir. Ancak bir Pub/Sub düzeni kullanılırken yayımcı ve abone tarafından bilinen aracısı veya ileti Aracısı ya da olay veri yolu, adlı üçüncü bir bileşen, yoktur. Bu nedenle, Pub/Sub düzeni kullanırken, yayımcı ve aboneleri tam olarak belirtilen olay veri yolu veya ileti Aracısı sayesinde birbirinden ayrılmıştır.

### <a name="the-middleman-or-event-bus"></a>Middleman ya da olay veri yolu 

Yayımcı ile abone arasındaki gizlilik nasıl elde edebilirim? Kolay bir yolu, tüm iletişimi dikkatli bir middleman izin ' dir. Bir olay veri yolu bir middleman ' dir.

Bir olay veri yolu, genellikle iki bölümden oluşur:

-   Soyut veya arabirim.

-   Bir veya daha fazla uygulamaları.

Şekil 8-19'nasıl bir uygulama açısından bakıldığında, olay veri yolu bir Pub/Sub kanal başka bir şey olduğunu görebilirsiniz. Bu zaman uyumsuz iletişim uygulamak yol gösterebilir. Böylece ortamı gereksinimlerini (örneğin, geliştirme ortamları ve üretim) bağlı olarak bunlar arasında değiştirme birden fazla uygulaması sahip olabilir.

Şekil 8-20 RabbitMQ, Azure Service Bus ve diğer olay/ileti aracısı gibi teknolojileri Mesajlaşma altyapısının temel birden çok uygulama ile bir olay veri yolu bir özeti görebilirsiniz. 

![](./media/image21.png)

**Şekil 8 - 20.** Bir olay veri yolu birden fazla uygulaması

Ancak ve daha önce bahsedilen olarak kendi soyutlamalar (olay veri yolu arabirimi) kullanarak yalnızca temel olay veri yolu özelliklerinin, soyutlama tarafından desteklenen gerekiyorsa uygundur. Daha zengin service bus özelliklerine ihtiyacınız varsa, büyük olasılıkla API ve kendi soyutlama yerine, tercih edilen ticari hizmet veri yolu tarafından sağlanan soyutlama kullanmanız gerekir. 

### <a name="defining-an-event-bus-interface"></a>Bir olay veri yolu arabirim tanımlama

Bazı uygulama kodu olay veri yolu arabirimin ve araştırma amacıyla olası uygulamaları ile başlayalım tıklatın. Arabirimi, genel ve basit arabirim olduğu gibi olması gerekir.

```csharp
public interface IEventBus
{
    void Publish(IntegrationEvent @event);

    void Subscribe<T, TH>()
        where T : IntegrationEvent
        where TH : IIntegrationEventHandler<T>;

    void SubscribeDynamic<TH>(string eventName)
        where TH : IDynamicIntegrationEventHandler;

    void UnsubscribeDynamic<TH>(string eventName)
        where TH : IDynamicIntegrationEventHandler;

    void Unsubscribe<T, TH>()
        where TH : IIntegrationEventHandler<T>
        where T : IntegrationEvent;
}
```

`Publish` Yöntem basittir. Olay veri yolu, herhangi bir mikro hizmet ya da o olaya abone bile bir dış uygulamaya geçirilen tümleştirme etkinliği yayınlamak. Bu yöntem olayın yayımlanması mikro hizmet tarafından kullanılır.

`Subscribe` Yöntemleri (bağımsız değişkenler bağlı olarak çeşitli uygulamalar olabilir), olaylar almak istiyorsanız mikro hizmetler tarafından kullanılır. Bu yöntem, iki bağımsız değişkeni vardır. İlk abone olmak için tümleştirme olaydır (`IntegrationEvent`). Tümleştirme olay işleyici (ya da geri arama yöntemi) adlı ikinci bağımsız değişken olan `IIntegrationEventHandler<T>`, alıcı mikro hizmet, bu tümleştirme olay iletisi aldığında çalıştırılacak.


>[!div class="step-by-step"]
[Önceki](database-server-container.md)
[İleri](rabbitmq-event-bus-development-test-environment.md)
