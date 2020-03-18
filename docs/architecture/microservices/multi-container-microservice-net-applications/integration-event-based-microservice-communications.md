---
title: Mikro hizmetler arasında olay tabanlı iletişim uygulama (tümleştirme olayları)
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | Mikro hizmetler arasında olay tabanlı iletişimi uygulamak için tümleştirme olaylarını anlayın.
ms.date: 10/02/2018
ms.openlocfilehash: 6d4e324a05def91935a82df41c971a75cb75c3f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712409"
---
# <a name="implementing-event-based-communication-between-microservices-integration-events"></a>Mikro hizmetler arasında olay tabanlı iletişim uygulama (tümleştirme olayları)

Daha önce açıklandığı gibi, olay tabanlı iletişimi kullandığınızda, bir mikro hizmet, bir işletme kuruluşunu güncellediğinde olduğu gibi kayda değer bir şey olduğunda bir olay yayımlar. Diğer mikro hizmetler bu etkinliklere abone dir. Bir microservice bir olay aldığında, kendi iş varlıklarını güncelleştirebilir ve bu da daha fazla olayın yayınlanmasına neden olabilir. Bu nihai tutarlılık kavramının özüdür. Bu yayımlama/abone etme sistemi genellikle bir olay veri ceminin inbir uygulaması kullanılarak gerçekleştirilir. Etkinlik veri mesuliyonu, etkinliklere abone olmak ve abone olmak ve etkinlikleri yayınlamak için gereken API ile bir arayüz olarak tasarlanabilir. Ayrıca, ileti kuyruğu veya eşzamanlı iletişimi ve yayımlama/abone etme modelini destekleyen bir servis veri aracı gibi herhangi bir işlem veya ileti iletişimini temel alan bir veya daha fazla uygulama da olabilir.

Olayları, birden çok hizmeti kapsayan ve bu hizmetler arasında nihai tutarlılık sağlayan iş hareketlerini uygulamak için kullanabilirsiniz. Sonunda tutarlı bir işlem, bir dizi dağıtılmış eylemden oluşur. Her eylemde, mikro hizmet bir işletme varlığını güncelleştirir ve bir sonraki eylemi tetikleyen bir olay yayımlar. Şekil 6-18 aşağıda, bir PriceUpdated olay ve olay veri günü ile yayınlanan gösterir, böylece fiyat güncelleştirmesi Sepet ve diğer microservices yayılır.

![Bir olay veri günü ile eşzamanlı olay odaklı iletişim diyagramı.](./media/integration-event-based-microservice-communications/event-driven-communication.png)

**Şekil 6-18**. Olay veri yolundan dayalı olay odaklı iletişim

Bu bölümde, Şekil 6-18'de gösterildiği gibi genel bir olay veri aracı arabirimi kullanarak .NET ile bu tür iletişimleri nasıl uygulayabileceğiniz açıklanmaktadır. Her biri RabbitMQ, Azure Hizmet Veri Servisi veya diğer üçüncü taraf açık kaynak veya ticari hizmet veri veri tonlarında farklı bir teknoloji veya altyapı kullanan birden çok olası uygulama vardır.

## <a name="using-message-brokers-and-services-buses-for-production-systems"></a>Üretim sistemleri için mesaj brokerları ve servis otobüslerini kullanma

Mimari bölümünde belirtildiği gibi, soyut olay veri topunuzu uygulamak için birden çok ileti teknolojisi arasından seçim yapabilirsiniz. Ama bu teknolojiler farklı seviyelerde. Örneğin, bir mesajlaşma aracısı taşıma aracısı olan RabbitMQ, Azure Servis Veri Servisi, NServiceBus, MassTransit veya Brighter gibi ticari ürünlerden daha düşük bir düzeydedir. Bu ürünlerin çoğu RabbitMQ veya Azure Hizmet Veri Tos'un üzerinde çalışabilir. Ürün seçiminiz, uygulamanız için kaç özellik ve ne kadar kullanıma hazır ölçeklenebilirliğe ihtiyacınız olduğuna bağlıdır.

eShopOnContainers örneğinde olduğu gibi, geliştirme ortamınız için sadece bir etkinlik veri günü kanıtı-of-concept uygulamak için, bir konteyner olarak çalışan RabbitMQ üstüne basit bir uygulama yeterli olabilir. Ancak, yüksek ölçeklenebilirliğe ihtiyaç duyan görev açısından kritik ve üretim sistemleri için Azure Hizmet Veri Tos'u değerlendirmek ve kullanmak isteyebilirsiniz.

Dağıtılmış geliştirmeyi kolaylaştıran uzun soluklu işlemler için [Sagas](https://docs.particular.net/nservicebus/sagas/) gibi üst düzey soyutlamalara ve daha zengin özelliklere ihtiyaç duyuyorsanız, NServiceBus, MassTransit ve Brighter gibi diğer ticari ve açık kaynaklı hizmet veri neşrleri değerlendirmeye değer. Bu durumda, kullanılacak soyutlamalar ve API genellikle doğrudan kendi soyutlamalar [(basit olay veri otobüsü soyutlamalar eShopOnContainers sağlanan](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/BuildingBlocks/EventBus/EventBus/Abstractions/IEventBus.cs)gibi) yerine bu üst düzey servis otobüsleri tarafından sağlanan olanlar olacaktır. Bu konuda, nservicebus (belirli yazılım tarafından uygulanan ek türemiş örnek) [kullanarak çatallı eShopOnContainers](https://go.particular.net/eShopOnContainers) araştırma yapabilirsiniz.

Tabii ki, her zaman RabbitMQ ve Docker gibi alt düzey teknolojilerin üstüne kendi servis veri yolu özellikleri inşa edebilir, ama iş "tekerleği yeniden icat etmek" için gerekli özel bir kurumsal uygulama için çok pahalı olabilir.

Yinelemek için: örnek olay veri günü soyutlamalar ve uygulama eShopOnContainers örnek sadece kavram kanıtı olarak kullanılmak üzere tasarlanmıştır. Mevcut bölümde açıklandığı gibi, eşzamanlı ve olay odaklı iletişim yapmak istediğinize karar verdikten sonra, üretim ihtiyaçlarınıza en uygun servis veri günü ürünlerini seçmelisiniz.

## <a name="integration-events"></a>Entegrasyon olayları

Tümleştirme olayları, etki alanı durumunu birden çok mikro hizmet veya dış sistemde eşitleme olarak getirmek için kullanılır. Bu, tümleştirme olaylarını microservice dışında yayımlayarak yapılır. Bir olay birden çok alıcı mikro hizmetine (tümleştirme olayına abone olduğu kadar çok mikro hizmete) yayımlandığında, her alıcı mikro hizmetindeki uygun olay işleyicisi olayı işler.

Bir tümleştirme olayı, aşağıdaki örnekte olduğu gibi temelde bir veri tutma sınıfıdır:

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

Tümleştirme olayları her microservice uygulama düzeyinde tanımlanabilir, böylece diğer mikro hizmetlerden, viewmodels sunucu ve istemci de tanımlanır nasıl karşılaştırılabilir bir şekilde ayrılmış. Önerilmeyen şey, birden çok mikro hizmet arasında ortak bir tümleştirme olayları kitaplığını paylaşmaktır; bunu yapmak, bu mikro hizmetleri tek bir olay tanımı veri kitaplığıyla birliş haline getirecektir. Bunu, birden çok mikro hizmet arasında ortak bir etki alanı modelini paylaşmak istemediğiniz nedenlerle yapmak istemezsiniz: mikro hizmetler tamamen özerk olmalıdır.

Mikro hizmetler arasında paylaşmanız gereken yalnızca birkaç tür kitaplık vardır. Bunlardan biri, eShopOnContainers'da olduğu gibi [Event Bus istemciapi](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/BuildingBlocks/EventBus)gibi son uygulama blokları olan kütüphanelerdir. Başka bir da JSON serializers gibi NuGet bileşenleri olarak paylaşılabilir araçları oluşturan kütüphaneler olduğunu.

## <a name="the-event-bus"></a>Etkinlik otobüsü

Olay veri yolunun, Şekil 6-19'da gösterildiği gibi, bileşenlerin birbirlerinden açıkça haberdar olmasını gerektirmeden mikro hizmetler arasında yayımlama/abone tarzı iletişim erebilmektedir.

![Temel yayımlama/abone oltasını gösteren bir diyagram.](./media/integration-event-based-microservice-communications/publish-subscribe-basics.png)

**Şekil 6-19**. Etkinlik veri leşiyle temel leri yayımlama/abone etme

Yukarıdaki diyagram, a.'nın, yayıncının aboneleri tanımasına gerek kalmadan B ve C mikro hizmetlerine abone olmak için dağıtan Event Bus'a yayınyaptığını göstermektedir. Olay veri mesuliyonu Observer deseni ve yayımlama-abone oltası ile ilgilidir.

### <a name="observer-pattern"></a>Gözlemci deseni

Gözlemci [deseninde,](https://en.wikipedia.org/wiki/Observer_pattern)birincil nesneniz (Gözlemlenebilir olarak bilinir) ilgili diğer nesneleri (Gözlemciler olarak bilinir) ilgili bilgileri (olayları) ile birlikte bilgilendirir.

### <a name="publishsubscribe-pubsub-pattern"></a>Yayımla/Abone Ol (Pub/Alt) deseni

[Yayımla/Abone Ol modelinin](https://docs.microsoft.com/previous-versions/msp-n-p/ff649664(v=pandp.10)) amacı Observer deseniyle aynıdır: belirli olaylar gerçekleştiğinde diğer hizmetleri bilgilendirmek istersiniz. Ancak Observer ve Pub/Sub desenleri arasında önemli bir fark vardır. Gözlemci deseninde, yayın doğrudan gözlemlenebilirden gözlemcilere yapılır, böylece birbirlerini "bilirler". Ancak Pub/Alt deseni kullanırken, hem yayıncı hem de abone tarafından bilinen broker veya ileti aracısı veya etkinlik veri neşrisi olarak adlandırılan üçüncü bir bileşen vardır. Bu nedenle, Pub / Alt desen kullanırken yayıncı ve aboneler tam olarak belirtilen olay veri günü veya mesaj komisyoncusu sayesinde ayrılır.

### <a name="the-middleman-or-event-bus"></a>Aracı veya olay otobüsü

Yayıncı ve abone arasında anonimlik nasıl elde elabilirsiniz? Kolay bir yol, bir aracının tüm iletişimi halledin. Bir olay otobüsü böyle bir aracıdır.

Olay veri cemişu genellikle iki bölümden oluşur:

- Soyutlama veya arayüz.

- Bir veya daha fazla uygulama.

Şekil 6-19'da, uygulama açısından olay yolunun bir Pub/Alt kanaldan başka bir şey olmadığını görebilirsiniz. Bu eşzamanlı iletişimi uygulama şekliniz değişebilir. Ortam gereksinimlerine (örneğin, üretim ve geliştirme ortamları) bağlı olarak aralarında değiş tokuş yapabilmeniz için birden çok uygulama olabilir.

Şekil 6-20'de RabbitMQ, Azure Hizmet Veri Yolunu veya başka bir olay/ileti aracısı gibi altyapı mesajlaşma teknolojilerine dayalı birden çok uygulamaiçeren bir etkinlik veri yolunun soyutlamalarını görebilirsiniz.

![Olay veri yolunda soyutlama katmanının eklenmesini gösteren diyagram.](./media/integration-event-based-microservice-communications/multiple-implementations-event-bus.png)

**Şekil 6- 20.** Bir olay veritonunun birden çok uygulaması

TavşanMQ Azure Servis verikurumu veya diğerleri gibi çeşitli teknolojilerle uygulanabilmesi için etkinlik veri tonunun bir arayüz üzerinden tanımlanması iyidir. Ancak, ve daha önce de belirtildiği gibi, kendi soyutlamalar (olay veri birimi arabirimi) kullanarak sadece temel olay veri günü özellikleri soyutlamalar tarafından desteklenen gerekiyorsa iyidir. Daha zengin servis veri günü özelliklerine ihtiyacınız varsa, kendi soyutlamalarınız yerine tercih ettiğiniz ticari servis veri nesi tarafından sağlanan API ve soyutlamaları kullanmanız gerekir.

### <a name="defining-an-event-bus-interface"></a>Olay veri birimi arabirimi tanımlama

Olay veri birimi arabirimi ve arama amaçlı olası uygulamalar için bazı uygulama kodu ile başlayalım. Arabirim, aşağıdaki arabirimde olduğu gibi genel ve basit olmalıdır.

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

Yöntem `Publish` basittir. Olay veri mesuliyonu, bu etkinliğe abone olan herhangi bir mikro hizmete, hatta harici bir uygulamaya aktarılan tümleştirme olayını yayınlayacaktır. Bu yöntem, olayı yayımlayan microservice tarafından kullanılır.

Yöntemleri `Subscribe` (bağımsız değişkenlere bağlı olarak çeşitli uygulamalar olabilir) olayları almak isteyen mikro hizmetler tarafından kullanılır. Bu yöntemin iki bağımsız değişkeni vardır. İlk i ( abone olmak`IntegrationEvent`için entegrasyon olayıdır. İkinci bağımsız değişken, alıcı microservice bu tümleştirme `IIntegrationEventHandler<T>`olay iletisi aldığında yürütülecek, adlı tümleştirme olay işleyicisi (veya geri arama yöntemi) olduğunu.

## <a name="additional-resources"></a>Ek kaynaklar

Üretime hazır bazı mesajlaşma çözümleri:

- **Azure Servis Veri Servisi** \
  <https://docs.microsoft.com/azure/service-bus-messaging/>
  
- **NServiceBus** \
  <https://particular.net/nservicebus>
  
- **Toplu Taşıma** \
  <https://masstransit-project.com/>

> [!div class="step-by-step"]
> [Önceki](database-server-container.md)
> [Sonraki](rabbitmq-event-bus-development-test-environment.md)
