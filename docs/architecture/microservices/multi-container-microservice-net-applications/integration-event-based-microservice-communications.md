---
title: Mikro hizmetler arasında olay tabanlı iletişim uygulama (tümleştirme olayları)
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Mikro hizmetler arasında olay tabanlı iletişim uygulamak için tümleştirme olaylarını anlayın.
ms.date: 10/02/2018
ms.openlocfilehash: 6d4e324a05def91935a82df41c971a75cb75c3f8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712409"
---
# <a name="implementing-event-based-communication-between-microservices-integration-events"></a>Mikro hizmetler arasında olay tabanlı iletişim uygulama (tümleştirme olayları)

Daha önce açıklandığı gibi, olay tabanlı iletişimi kullandığınızda bir mikro hizmet, bir iş varlığını güncelleştirdiğinde olduğu gibi bir şey gerçekleştiğinde bir olay yayınlar. Diğer mikro hizmetler bu olaylara abone olur. Bir mikro hizmet bir olay aldığında, kendi iş varlıklarını güncelleştirebilir ve bu da daha fazla olay yayımlanmaya neden olabilir. Bu, nihai tutarlılık kavramının özünü. Bu yayımlama/abone olma sistemi genellikle bir olay veri yolunun uygulanması kullanılarak gerçekleştirilir. Olay veri yolu, olaylara abone olmak ve olayları kaldırmak ve olayları yayımlamak için gereken API ile bir arabirim olarak tasarlanabilir. Ayrıca, bir mesajlaşma kuyruğu veya zaman uyumsuz iletişimi destekleyen bir hizmet veri yolu veya bir yayımlama/abonelik modeli gibi işlem içi veya mesajlaşma iletişimine dayalı bir veya daha fazla uygulama olabilir.

Olayları, bu hizmetler arasında nihai tutarlılık sağlayan birden çok hizmete yayılan iş işlemlerini uygulamak için kullanabilirsiniz. Sonuçta tutarlı bir işlem, bir dizi dağıtılmış eylemden oluşur. Her eylemde, mikro hizmet bir iş varlığını güncelleştirir ve sonraki eylemi tetikleyen bir olay yayımlar. Şekil 6-18 aşağıdaki şekilde, ve olay veri yolu aracılığıyla yayınlanan PriceUpdated olayını gösterir, bu nedenle fiyat güncelleştirmesi sepet ve diğer mikro hizmetlere yayılır.

![Olay veri yolu ile zaman uyumsuz olay odaklı iletişimin diyagramı.](./media/integration-event-based-microservice-communications/event-driven-communication.png)

**Şekil 6-18**. Olay veri yoluna dayalı olay odaklı iletişim

Bu bölümde, Şekil 6-18 ' de gösterildiği gibi, .NET ile bu tür iletişimin nasıl uygulanacağı açıklanır. Her biri, Korbbitmq, Azure Service Bus veya diğer üçüncü taraf açık kaynaklı veya ticari hizmet veri yolu gibi farklı bir teknoloji veya altyapıyı kullanan birden çok olası uygulama vardır.

## <a name="using-message-brokers-and-services-buses-for-production-systems"></a>Üretim sistemleri için ileti aracılarını ve hizmet veri yollarını kullanma

Mimari bölümünde belirtildiği gibi, soyut olay veri yolunu uygulamak için birden çok mesajlaşma teknolojisinden seçim yapabilirsiniz. Ancak bu teknolojiler farklı düzeylerde bulunur. Örneğin, bir mesajlaşma Aracısı taşıması olan Kbbitmq, Azure Service Bus, NServiceBus, Masstransıya veya daha parlak gibi ticari ürünlerden daha düşük bir düzeyindedir. Bu ürünlerin çoğu, Korbbitmq veya Azure Service Bus üzerinde çalışabilir. Ürün seçiminiz, uygulamanız için ne kadar özellik ve ne kadar hazır ölçeklenebilirlik için ihtiyaç duydığınıza bağlıdır.

EShopOnContainers örneğinde olduğu gibi, geliştirme ortamınız için yalnızca bir olay veri yolu kavramını uygulamak amacıyla, bir kapsayıcı olarak çalışan Kbbitmq üzerinde basit bir uygulama yeterince olabilir. Ancak, yüksek ölçeklenebilirlik gerektiren görev açısından kritik ve üretim sistemlerinde Azure Service Bus değerlendirmek ve kullanmak isteyebilirsiniz.

Dağıtılmış geliştirmeyi daha kolay hale getirmek için yüksek düzeyde soyut ve çok daha zengin özellikler, örneğin NServiceBus, Masstransıya ve daha [parlak gibi diğer](https://docs.particular.net/nservicebus/sagas/) ticari ve açık kaynaklı hizmet yolları, değerlendirmek için gereklidir. Bu durumda, kullanılacak soyutlamalar ve API genellikle kendi soyutlamaları yerine bu üst düzey hizmet veri yolları tarafından sağlananlar olur ( [eShopOnContainers 'da sunulan basit olay veri yolu soyutlaması](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/BuildingBlocks/EventBus/EventBus/Abstractions/IEventBus.cs)gibi). Bu şekilde, NServiceBus (belirli yazılımlar tarafından uygulanan ek türetilmiş örnek) [kullanarak, forlenmiş eShopOnContainers](https://go.particular.net/eShopOnContainers) 'ı araştırabilirsiniz.

Tabii ki, her zaman Pbbitmq ve Docker gibi alt düzey teknolojilerin üzerinde kendi hizmet veri yolu özelliklerini derleyebilir, ancak "tekerleği yeniden bağlamak" için gereken iş, özel bir kurumsal uygulama için çok maliyetli olabilir.

Yeniden yinelemek için: eShopOnContainers örneğinde gösterilen örnek olay veri yolu soyutlamaları ve uygulama, yalnızca kavram kanıtı olarak kullanılmak üzere tasarlanmıştır. Geçerli bölümde açıklandığı gibi zaman uyumsuz ve olay odaklı iletişim sağlamak istediğinize karar verdikten sonra, üretim için gereksinimlerinize en uygun hizmet veri yolu ürününü seçmeniz gerekir.

## <a name="integration-events"></a>Tümleştirme olayları

Tümleştirme olayları, etki alanı durumunun birden fazla mikro hizmet veya dış sistemler arasında eşitlenmiş şekilde getirilmesi için kullanılır. Bu, mikro hizmet dışındaki tümleştirme olayları yayınlanarak yapılır. Bir olay birden çok alıcı mikro hizmetine yayımlandığında (Tümleştirme olayına abone olan çok sayıda mikro hizmet için), her bir alıcı mikro hizmetindeki uygun olay işleyicisi olayı işler.

Bir tümleştirme olayı, aşağıdaki örnekte olduğu gibi temel olarak veri tutan bir sınıftır:

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

Tümleştirme olayları, her bir mikro hizmetin uygulama düzeyinde tanımlanabilir, bu nedenle diğer mikro hizmetlerden farklı olarak, görüntü modellerinin sunucu ve istemcide nasıl tanımlandıklarından bağımsız olarak bir şekilde ayrılır. Çok sayıda mikro hizmette ortak bir tümleştirme olayları kitaplığını paylaşma önerilmez; Bunun yapılması, bu mikro hizmetlerden tek bir olay tanımı veri kitaplığıyla eşlenmelidir. Birden çok mikro hizmette ortak bir etki alanı modeli paylaşmak istemediğiniz nedenlerle bunu yapmak istemezsiniz: mikro hizmetler tamamen otonom olmalıdır.

Mikro hizmetler arasında paylaşmanız gereken yalnızca birkaç kitaplık türü vardır. Bir tane, eShopOnContainers içinde olduğu gibi, [olay veri yolu istemci API 'si](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/BuildingBlocks/EventBus)gibi son uygulama blokları olan kitaplıklardır. Diğer bir deyişle, JSON serileştiricileri gibi NuGet bileşenleri olarak da paylaşılabilen araçlar oluşturan kitaplıklarıdır.

## <a name="the-event-bus"></a>Olay veri yolu

Bir olay veri yolu, Şekil 6-19 ' de gösterildiği gibi, bileşenlerin birbirleriyle açıkça farkında olması gerekmeden mikro hizmetler arasında yayımlama/abonelik stili iletişim sağlar.

![Temel yayımla/abone ol deseninin gösterildiği diyagram.](./media/integration-event-based-microservice-communications/publish-subscribe-basics.png)

**Şekil 6-19**. Bir olay veri yolundan temel olarak yayımlama/abone olma

Yukarıdaki diyagramda, mikro hizmet B ve C 'yi abone olarak yayımlayan ve yayımcı tarafından abonelere gerek duymadan bir olay veri yolu yayımlayıcısı gösterilmektedir. Olay veri yolu, gözlemci düzeniyle ve Yayımla-abone ol düzeniyle ilgilidir.

### <a name="observer-pattern"></a>Gözlemci kalıbı

[Gözlemci](https://en.wikipedia.org/wiki/Observer_pattern)düzeninde, birincil nesneniz (observable olarak bilinir) ilgili bilgileri (olay) ile ilgili diğer nesneleri (observers olarak bilinir) bilgilendirir.

### <a name="publishsubscribe-pubsub-pattern"></a>Yayımla/abone ol (yayımlama/alt) kalıbı

[Yayımla/abone ol deseninin](https://docs.microsoft.com/previous-versions/msp-n-p/ff649664(v=pandp.10)) amacı gözlemci düzeniyle aynıdır: belirli olaylar gerçekleşirken diğer hizmetlere bildirimde bulunmasını istiyorsunuz. Ancak gözlemci ve Pub/Sub desenleri arasında önemli bir farklılık vardır. Gözlemci modelinde, yayın doğrudan observable 'dan observers 'a yapılır, bu nedenle birbirini "bilir". Ancak, bir yayın/alt model kullanılırken, aracı veya ileti Aracısı ya da yayımcı ve abone tarafından bilinen olay veri yolu adlı üçüncü bir bileşen vardır. Bu nedenle, yayın/alt model kullanılırken yayımcı ve aboneler, belirtilen olay veri yolu veya ileti aracısına tam olarak bir şekilde ayrılır.

### <a name="the-middleman-or-event-bus"></a>Middleman veya olay veri yolu

Yayımcı ve abone arasında nasıl anonimlik elde edersiniz? Kolay bir yol, tüm iletişimin Middleman bir ele almasına olanak tanır. Bir olay veri yolu, Middleman.

Olay veri yolu genellikle iki bölümden oluşur:

- Soyutlama veya arabirim.

- Bir veya daha fazla uygulama.

Şekil 6-19 ' de, bir uygulama görünümünden, olay veri yolunun bir yayın/alt kanaldan ne kadar fazla şey olduğu hakkında bilgi alabilirsiniz. Bu zaman uyumsuz iletişimi uygulama yönteminiz farklılık gösterebilir. Ortam gereksinimlerine (örneğin, üretim ve geliştirme ortamlarına göre) bağlı olarak, aralarında geçiş yapabilmeniz için birden çok uygulama olabilir.

Şekil 6-20 ' de, kbbitmq, Azure Service Bus veya başka bir olay/ileti Aracısı gibi altyapı mesajlaşma teknolojilerine göre birden çok uygulama içeren bir olay veri yolu soyutlama görebilirsiniz.

![Bir olay veri yolu soyutlama katmanının eklenmesini gösteren diyagram.](./media/integration-event-based-microservice-communications/multiple-implementations-event-bus.png)

**Şekil 6-20.** Bir olay veri yolunun birden çok uygulaması

Veri yolu, bir arabirim aracılığıyla tanımlanabilmesi ve bu sayede, Kbıbitmq Azure Service Bus veya diğerleri gibi çeşitli teknolojilerle uygulanabilmesi yararlı olur. Ancak, daha önce bahsedildiği gibi, kendi soyutlarınızın (olay veri yolu arabirimi) kullanılması yalnızca, soyutlamalar tarafından desteklenen temel olay veri yolu özelliklerine ihtiyacınız varsa iyidir. Daha zengin Service Bus özelliklerine ihtiyacınız varsa, büyük olasılıkla kendi soyutlamaları yerine tercih ettiğiniz ticari hizmet veri yolu tarafından sunulan API 'yi ve soyutlamaları kullanmanız gerekir.

### <a name="defining-an-event-bus-interface"></a>Olay veri yolu arabirimi tanımlama

Olay veri yolu arabirimi ve Araştırma amaçları için olası uygulamalar için bazı uygulama kodları ile başlayalım. Arabirim, aşağıdaki arabirimde olduğu gibi genel ve kolay olmalıdır.

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

`Publish` yöntemi basittir. Olay veri yolu, kendisine geçirilen tümleştirme olayını herhangi bir mikro hizmete veya hatta bu olaya abone olan bir dış uygulamaya yayınlayacak. Bu yöntem, olayı yayımlayan mikro hizmet tarafından kullanılır.

`Subscribe` Yöntemleri (bağımsız değişkenlere bağlı olarak birkaç uygulama olabilir), olayları almak isteyen mikro hizmetler tarafından kullanılır. Bu yöntemin iki bağımsız değişkeni vardır. Birincisi, Abone olunacak tümleştirme olayıdır (`IntegrationEvent`). İkinci bağımsız değişken, alıcı mikro hizmeti bu tümleştirme olay iletisini aldığında yürütülecek `IIntegrationEventHandler<T>`adlı tümleştirme olay işleyicisidir (veya geri çağırma yöntemidir).

## <a name="additional-resources"></a>Ek kaynaklar

Üretime yönelik olarak hazırlanmaya yönelik bazı mesajlaşma çözümleri:

- **Azure Service Bus** \
  <https://docs.microsoft.com/azure/service-bus-messaging/>
  
- **Nservicebus** \
  <https://particular.net/nservicebus>
  
- **Masstransıt** \
  <https://masstransit-project.com/>

> [!div class="step-by-step"]
> [Önceki](database-server-container.md)
> [İleri](rabbitmq-event-bus-development-test-environment.md)
