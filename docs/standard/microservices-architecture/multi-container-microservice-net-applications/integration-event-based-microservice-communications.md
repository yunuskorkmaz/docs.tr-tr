---
title: Mikro hizmetler arasında olay tabanlı iletişim uygulama (tümleştirme olayları)
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Mikro hizmetler arasında olay tabanlı iletişim uygulamak için tümleştirme olayları anlayın.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/02/2018
ms.openlocfilehash: b451d896186ffb650e495c10786106c37ab16131
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61773587"
---
# <a name="implementing-event-based-communication-between-microservices-integration-events"></a>Mikro hizmetler arasında olay tabanlı iletişim uygulama (tümleştirme olayları)

Olay tabanlı iletişim kullandığınızda, daha önce açıklandığı gibi bir mikro hizmet önemli bir sorun olduğunda bir iş varlığı güncelleştirdiği gibi durum gerçekleştiğinde bir olay yayımlar. Diğer mikro hizmetler, bu olaylara abone olun. Bir mikro hizmet, bir olayı aldığında, yayımlanmakta daha fazla olay için yol açabilecek kendi iş varlıklarını güncelleştirebilirsiniz. Son tutarlılık kavram ortaya budur. Bu yayımlama/abone olma sistem, genellikle bir olay veri yolu uygulaması kullanılarak gerçekleştirilir. Olay veri yoluna abone olma ve aboneliği olayları ve olayları yayımlamak için gereken API ile arabirim olarak tasarlanabilir. Bir ileti kuyruğu veya zaman uyumsuz iletişim ve bir yayımlama/abone olma modelini destekleyen bir service bus gibi tüm işlemler arası veya Mesajlaşma iletişimi göre bir veya daha fazla uygulamaları da olabilir.

Olayları birden çok hizmet span iş işlemleri uygulamak üzere bu hizmetler arasındaki son tutarlılık sağlayan kullanabilirsiniz. Sonunda tutarlı bir işlem, dağıtılmış işlemlerin bir dizi oluşur. Her eylem bir mikro hizmet iş varlığı güncelleştirir ve sonraki eylemi tetikleyen bir olay yayımlar.

![Sepet ve ek mikro hizmetler nihai tutarlılığı elde etmek için bir olay veri yolu ile olay temelli iletişimi kullanarak Kataloğu mikro hizmet.](./media/image19.png)

**Şekil 6-18**. Bir olay veri yoluna bağlı olarak olay tabanlı iletişim

Bu bölümde, Şekil 6-18'de gösterildiği gibi bir genel olay veri yolu arabirimini kullanarak bu tür .NET ile iletişimin nasıl uygulayacağınıza dair açıklanmaktadır. Her bir farklı teknoloji veya RabbitMQ, Azure Service Bus veya diğer üçüncü taraf açık kaynak veya ticari service bus gibi altyapı kullanarak birden çok olası uygulamaları vardır.

## <a name="using-message-brokers-and-services-buses-for-production-systems"></a>İleti aracıları ve Hizmetleri yollarına üretim sistemleri için kullanma

Mimari bölümünde belirtildiği gibi soyut olay veri yolu uygulamak için birden çok Mesajlaşma teknolojilerinin arasından seçim yapabilirsiniz. Ancak, farklı düzeylerde bu teknolojilerdir. Örneğin, RabbitMQ, Mesajlaşma Aracısı Aktarım, Azure Service Bus, NServiceBus, MassTransit veya Brighter gibi ticari ürünleri daha düşük bir düzeyde altındadır. Bu ürünlerin çoğunu, RabbitMQ veya Azure Service Bus üzerinde çalışabilir. Ürün tercih ettiğiniz kaç özellikleri ve ne kadar out-bulunmayan ölçeklenebilirlik, uygulamanız için gereken bağlıdır.

Yalnızca bir olay veri yolu kavram kanıtı hizmetine örnek olduğu gibi geliştirme ortamınız için uygulamak için basit bir uygulama bir kapsayıcı olarak çalışan RabbitMQ üzerinde yeterli olabilir. Ancak için Görev açısından kritik ve yüksek ölçeklenebilirlik gerektiren üretim sistemlerine değerlendirmek ve Azure hizmet veri Yolu'nu olmak isteyebilirsiniz.

Yüksek düzeyde soyutlama gerektiriyorsa ve gibi daha zengin özellikler [Sagas](https://docs.particular.net/nservicebus/sagas/) Dağıtılmış Geliştirme yapmak daha kolay, diğer ticari ve açık kaynak hizmeti yollarına NServiceBus, MassTransit, gibi uzun süre çalışan işlemler için ve Parlak değerlendirme değer var. Bu durumda, soyutlamaları ve kullanmak için API genellikle doğrudan bu üst düzey hizmet yolları yerine kendi soyutlama tarafından sağlanan olanları olur (gibi [sağlanan hizmetine basit olay veri yolu soyutlama](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/BuildingBlocks/EventBus/EventBus/Abstractions/IEventBus.cs)). Bu konular için ' ın, araştırma [çatallanmış NServiceBus kullanarak hizmetine](https://go.particular.net/eShopOnContainers) (belirli bir yazılım tarafından uygulanan ek türetilmiş örneği)

Elbette, her zaman kendi hizmet veri yolu özelliklerinin RabbitMQ ve Docker gibi alt düzey teknolojileri üzerine da oluşturabilirsiniz, ancak "tekerleği geliştirdi için" gereken çalışmayı özel Kurumsal uygulama için çok yüksek maliyetli olabilir.

Bir kez daha açıklayalım: örnek olay veri yolu soyutlamaları ve uygulama hizmetine örnekte büyütmüş yalnızca kavram kanıtı kullanılmak üzere tasarlanmıştır. Zaman uyumsuz ve olay odaklı iletişim sağlamak geçerli bölümünde açıklandığı gibi istediğiniz verdikten sonra üretim için ihtiyaçlarınıza en uygun hizmet veri yolu ürün seçmeniz gerekir.

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

Bir olay veri yolu Şekil 6-19'gösterildiği gibi açıkça birbirinden farkında olması gereken bileşenleri gerektirmeden mikro hizmetler arasında yayımlama/abone olun-style iletişime olanak sağlar.

![Temel pub/sub desenini, mikro hizmet A B ve C, mikro hizmetler yayımcının aboneleri bilmenize gerek abone olmaya dağıtır olay Bus yayımlar.](./media/image20.png)

**Şekil 6-19**. Yayımlama/abonelik bir olay veri yolu temel kavramları

Olay veri yolu gözlemci deseni ve yayımlama ilgili-abone ol modeli.

### <a name="observer-pattern"></a>Gözlemci deseni

İçinde [gözlemci deseni](https://en.wikipedia.org/wiki/Observer_pattern), birincil nesnenizin (Observable bilinir) ilgili bilgileri (olayları) ile (gözlemciler bilinir) diğer ilgili nesneleri bildirir.

### <a name="publishsubscribe-pubsub-pattern"></a>Yayımlama/abone ol (Pub/Sub) deseni

Amacı [Yayımla/abone ol deseni](https://docs.microsoft.com/previous-versions/msp-n-p/ff649664(v=pandp.10)) gözlemci deseni ile aynıdır: belirli olaylar gerçekleştiğinde diğer hizmetleri bildirimde bulunmak istiyorsunuz. Ancak gözlemci ve Pub/Sub desenler arasında önemli bir fark yoktur. "Birbirine alışık oldukları için" gözlemci desende yayın gözlemciler için doğrudan observable gerçekleştirilir. Ancak bir Pub/Sub düzeni kullanılırken yayımcı ve abone tarafından bilinen aracısı veya ileti Aracısı ya da olay veri yolu, adlı üçüncü bir bileşen, yoktur. Bu nedenle, Pub/Sub düzeni kullanırken, yayımcı ve aboneleri tam olarak belirtilen olay veri yolu veya ileti Aracısı sayesinde birbirinden ayrılmıştır.

### <a name="the-middleman-or-event-bus"></a>Middleman ya da olay veri yolu

Yayımcı ile abone arasındaki gizlilik nasıl elde edebilirim? Kolay bir yolu, tüm iletişimi dikkatli bir middleman izin ' dir. Bir olay veri yolu bir middleman ' dir.

Bir olay veri yolu, genellikle iki bölümden oluşur:

- Soyut veya arabirim.

- Bir veya daha fazla uygulamaları.

Şekil 6-19'nasıl bir uygulama açısından bakıldığında, olay veri yolu bir Pub/Sub kanal başka bir şey olduğunu görebilirsiniz. Bu zaman uyumsuz iletişim uygulamak yol gösterebilir. Böylece ortamı gereksinimlerini (örneğin, geliştirme ortamları ve üretim) bağlı olarak bunlar arasında değiştirme birden fazla uygulaması sahip olabilir.

Şekil 6-20 RabbitMQ, Azure Service Bus veya başka bir olay/ileti aracısı gibi teknolojileri Mesajlaşma altyapısının temel birden çok uygulama ile bir olay veri yolu bir özeti görebilirsiniz.

![RabbitMQ Azure Service bus veya diğerleri gibi çeşitli teknolojilerle uygulanabilir için bir arabirim ile tanımlanan olay veri yolu uygundur.](./media/image21.png)

**Şekil 6 - 20.** Bir olay veri yolu birden fazla uygulaması

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

> [!div class="step-by-step"]
> [Önceki](database-server-container.md)
> [İleri](rabbitmq-event-bus-development-test-environment.md)
