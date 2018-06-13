---
title: Olay tabanlı mikro (tümleştirme olayları) arasındaki iletişimi uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Olay tabanlı mikro (tümleştirme olayları) arasındaki iletişimi uygulama
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: 5d7037f91cb338721f91d35567246ebbca018a3c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579183"
---
# <a name="implementing-event-based-communication-between-microservices-integration-events"></a>Olay tabanlı mikro (tümleştirme olayları) arasındaki iletişimi uygulama

Olay tabanlı iletişim kullandığınızda, daha önce açıklandığı gibi bir mikro hizmet dikkat çekici bir şey olduğunda iş varlığı güncelleştirdiği gibi olduğunda bir olay yayımlar. Diğer mikro bu olaylarına abone olma. Bir mikro hizmet bir olayı aldığında, daha fazla olay yayımlanmakta yol açabilecek kendi iş varlıklarını güncelleştirebilirsiniz. Bu yayımlama/abonelik sistem genellikle bir olay veri yolu uygulaması kullanılarak gerçekleştirilir. Olay veri yolu bir arabirim abone olma ve aboneliği olayları ve olayları yayımlamak için gereken API ile tasarlanabilir. İleti sırası veya zaman uyumsuz iletişim ve publish/subscribe modelini destekleyen bir hizmet veri yolu gibi tüm işlemler arası veya Mesajlaşma iletişim göre bir veya daha fazla uygulamaları da olabilir.

Olayları birden çok hizmet span iş işlemleri uygulamak üzere bu hizmetleri arasında nihai tutarlılık sağlayan kullanabilirsiniz. Sonuçta tutarlı bir işlem dağıtılmış işlemlerin bir dizi oluşur. Her bir eylemde mikro hizmet iş varlığı güncelleştirir ve bir sonraki eylem tetikleyen bir olay yayımlar.

![](./media/image19.PNG)

**Şekil 8-18**. Bir olay veri yoluna bağlı olay denetimli iletişim

Bu bölümde, Şekil 8-18'de gösterildiği gibi bir genel olay veri yolu arabirimi kullanarak bu tür iletişim .NET ile nasıl uygulayabileceğiniz açıklanmaktadır. Her farklı teknoloji veya RabbitMQ, Azure Service Bus veya diğer üçüncü taraf açık kaynak veya ticari hizmet veri yolu gibi altyapısını kullanarak birden fazla olası uygulamaları vardır.

## <a name="using-message-brokers-and-services-buses-for-production-systems"></a>İleti aracıları ve Hizmetleri yollarına üretim sistemleri için kullanma

Mimari bölümünde belirtildiği gibi soyut olay bus uygulamak için birden çok Mesajlaşma teknolojileri arasından seçim yapabilirsiniz. Ancak, farklı düzeylerde bu teknolojilerdir. Örneğin, Azure Service Bus, NServiceBus, MassTransit veya Brighter gibi ticari ürün daha düşük bir düzeye RabbitMQ, bir Mesajlaşma Aracısı taşıma altındadır. Bu ürünler çoğunu RabbitMQ veya Azure Service Bus üzerinde çalışabilir. Seçiminiz ürünün kaç özellikler ve ne kadar out-of--box ölçeklenebilirlik, uygulamanız için gereken bağlıdır.

Yalnızca bir olay veri yolu, kavram eShopOnContainers örnek olduğu gibi geliştirme ortamınız için uygulamak için bir kapsayıcı olarak çalışan RabbitMQ üstünde basit bir uygulama yeterli olabilir. Ancak için kritik ve yüksek ölçeklenebilirlik gereken üretim sistemlerine değerlendirin ve Azure Service Bus hizmetini kullanmak olmak isteyebilirsiniz.

Üst düzey soyutlamalar gerektirir ve daha zengin özellikleri ister [Sagas](https://docs.particular.net/nservicebus/sagas/) daha kolay, diğer ticari ve açık kaynak hizmeti yollarına NServiceBus, MassTransit, gibi Dağıtılmış Geliştirme yapmak uzun süre çalışan işlemleri ve Parlak değerlendirme değer var. Bu durumda, soyutlamalar ve kullanmak için API genellikle doğrudan bu üst düzey hizmet yollarına kendi soyutlamalar yerine tarafından sağlanan olanları olur (gibi [eShopOnContainers sırasında sağlanan Basit olay bus soyutlamalar](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/BuildingBlocks/EventBus/EventBus/Abstractions/IEventBus.cs)). Bu konular için ' ın, araştırma [çatallanmış NServiceBus kullanarak eShopOnContainers](http://go.particular.net/eShopOnContainers) (belirli yazılımı tarafından uygulanan ek türetilmiş örneği)

Doğal olarak, her zaman kendi hizmet veri yolu özellikleri üzerinde alt düzey teknolojileri RabbitMQ ve Docker gibi oluşturabilirsiniz, ancak "tekerleği reinvent için" gereken çalışmayı özel Kurumsal uygulama için çok yüksek maliyetli olabilir.

## <a name="integration-events"></a>Tümleştirme olayları

Tümleştirme olaylar, birden çok mikro veya dış sistemler arasında etki alanı durumu eşitlenmiş getirmek için kullanılır. Bu tümleştirme olaylarını mikro hizmet dışında yayımlama tarafından gerçekleştirilir. Bir olay (için tümleştirme olayına abone olarak sayıda mikro) birden çok alıcı mikro yayımlandığında, her alıcı mikro hizmet uygun olay işleyicisini olayını işler.

Bir tümleştirme temelde aşağıdaki örnekteki gibi bir veri tutan sınıfı olaydır:

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

Bir şekilde nasıl ViewModels sunucu ve istemci tanımlanan için karşılaştırılabilir diğer mikro gelen ayrılmış şekilde tümleştirme olaylarını her mikro hizmet uygulama düzeyinde tanımlanabilir. Ne önerilmez ortak bir tümleştirme olayları kitaplık arasında birden çok mikro paylaşan; Bunu tek olay tanımı veri kitaplığı ile bu mikro Kuplaj. Ortak etki alanı modeli birden çok mikro paylaşmak istediğiniz değil, aynı nedenleri için bunu yapmak istiyor musunuz: mikro tamamen otonom olmalıdır.

Yalnızca birkaç tür mikro paylaşmalıdır kitaplıkları vardır. Son uygulama blokları gibi kitaplıkları biridir [olay Bus İstemcisi API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/BuildingBlocks/EventBus), eShopOnContainers gibi. Başka bir JSON serileştiricileri gibi bir NuGet bileşenler de paylaşım araçları oluşturan kitaplıkları olur.

## <a name="the-event-bus"></a>Olay veri yolu

Bir olay veri yoluna Şekil 8-19'gösterildiği gibi açıkça birbirinden farkında olması gereken bileşenleri gerektirmeden mikro Yayımla/abone-style iletişimine izin verir.

![](./media/image20.png)

**Şekil 8-19**. Yayımlama/abonelik bir olay veri yoluna temel kavramları

Olay bus gözlemci deseni ve yayımlama ile ilgili-düzeni abone olun.

### <a name="observer-pattern"></a>Gözlemci deseni

İçinde [gözlemci deseni](https://en.wikipedia.org/wiki/Observer_pattern), birincil nesnenizin (Observable da bilinir) ilgili bilgileri (olayları) (Gözlemcilerin da bilinir) diğer ilgilendiğiniz nesneleri bildirir.

### <a name="publish-subscribe-pubsub-pattern"></a>Yayımlama-abone olma (Pub/alt) düzeni 

Amacı [Pub/alt düzeni](https://msdn.microsoft.com/library/ff649664.aspx) gözlemci deseni ile aynıdır: belirli olaylar gerçekleştiğinde diğer hizmetler bildirmek istediğiniz. Ancak gözlemci ve Pub/alt desenleri arasında önemli bir fark yoktur. Bunlar "birbirine bilmesi" gözlemci deseninde yayın gözlemcilerin için doğrudan observable gerçekleştirilir. Ancak Pub/alt düzeni kullanırken yayımcı ve abone tarafından bilinen aracısı veya ileti aracısı veya olay veri yolu, adlı üçüncü bir bileşen yok. Bu nedenle, Pub/alt düzeni kullanırken, yayımcı ve aboneleri tam olarak belirtilen olay veri yolu veya ileti Aracısı sayesinde birbirinden ayrılır.

### <a name="the-middleman-or-event-bus"></a>Middleman veya olay veri yolu 

Gizlilik yayımcısı ile abone arasında nasıl elde? Tüm iletişimi dikkatli bir middleman izin kolay yoludur. Bir olay veri yoluna bir middleman ' dir.

Bir olay veri yoluna genellikle iki bölümden oluşur:

-   Özet veya arabirim.

-   Bir veya daha fazla uygulamaları.

Şekil 8-19'nasıl, bir uygulama açısından bakıldığında, olay bus Pub/alt kanal'den fazla bir şey olduğunu görebilirsiniz. Bu zaman uyumsuz iletişim uygulamak şekilde farklılık gösterebilir. Böylece, aralarında ortamı gereksinimlerini (örneğin, geliştirme ortamları ve üretim) bağlı olarak takas edebilirsiniz birden fazla uygulaması olabilir.

Şekil 8-20 olarak RabbitMQ, Azure Service Bus veya diğer olay/ileti aracısı gibi teknolojileri Mesajlaşma altyapısı göre birden çok uygulamalarıyla birlikte bir olay veri yolu için bir Özet görebilirsiniz. 

![](./media/image21.png)

**Şekil 8 - 20.** Birden çok olay veri yolu uygulamaları

Ancak ve daha önce açıklanan olarak kendi soyutlamalar (olay veri yolu arabirimi) kullanarak yalnızca temel olay bus özelliklerini, soyutlamalar tarafından desteklenen gerekiyorsa iyi olur. Daha zengin service bus özelliklerini gerekiyorsa, API ve kendi soyutlamalar yerine, tercih edilen ticari hizmet veri yolu tarafından sağlanan soyutlamalar büyük olasılıkla kullanmanız gerekir. 

### <a name="defining-an-event-bus-interface"></a>Bir olay veri yolu arabirimi tanımlama

Olay veri yolu arabirimi için bazı uygulama kodu ve araştırması amacıyla olası uygulamaları ile başlayalım tıklatın. Arabirim genel ve aşağıdaki arabirimi olduğu gibi kolay olmalıdır.

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

`Publish` Yöntemdir kolay. Olay bus herhangi mikro hizmet ya da bu olaya abone bile bir dış uygulamaya geçirilen tümleştirme olay yayın. Bu yöntem, olay yayımlama mikro hizmet tarafından kullanılır.

`Subscribe` (Bağımsız değişkenler bağlı olarak çeşitli uygulamalarını olabilir) yöntemleri, olayları almak istediğiniz mikro tarafından kullanılır. Bu yöntem, iki bağımsız değişkenlere sahiptir. İlk abone olmak için tümleştirme olaydır (`IntegrationEvent`). Tümleştirme olay işleyicisi (veya geri çağırma yöntemi) adlı ikinci bağımsız değişkeni olan `IIntegrationEventHandler<T>`, alıcı mikro hizmet Bu tümleştirme olay iletisi aldığında gerçekleştirilecek.


>[!div class="step-by-step"]
[Önceki] (veritabanı-server-container.md) [sonraki] (rabbitmq-event-bus-development-test-environment.md)
