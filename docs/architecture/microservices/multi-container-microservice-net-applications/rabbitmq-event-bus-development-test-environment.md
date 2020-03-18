---
title: Geliştirme veya test ortamı için RabbitMQ ile bir olay veri yolu uygulama
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | Geliştirme veya test ortamları için tümleştirme etkinlikleri için bir olay veri günü mesajlaşması uygulamak için RabbitMQ'yi kullanın.
ms.date: 10/02/2018
ms.openlocfilehash: ba1cea9384893955ae0743ac8d6a34c350224cd5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74711192"
---
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a>Geliştirme veya test ortamı için RabbitMQ ile bir olay veri yolu uygulama

EShopOnContainers uygulamasının yaptığı gibi, bir konteynerde çalışan RabbitMQ'ye dayalı özel etkinlik otobüsünüzü oluşturursanız, bunun yalnızca geliştirme ve test ortamlarınız için kullanılması gerektiğini söyleyerek başlamalıyız. Üretime hazır servis veri tonunun bir parçası olarak oluşturmadığınız sürece, üretim ortamınız için kullanmamalısınız. Basit bir özel olay veri otobüsü, ticari servis verine sahip olduğu üretime hazır birçok kritik özelliği eksik olabilir.

eShopOnContainers'daki etkinlik veri neşrisi özel uygulamalarından biri temelde RabbitMQ API'sini kullanan bir kitaplıktır (Azure Hizmet Veri Tos'una dayalı başka bir uygulama vardır).

RabbitMQ ile etkinlik otobüsü uygulaması, mikro hizmetlerin olaylara abone olmasını, olayları yayınlamasını ve Şekil 6-21'de gösterildiği gibi etkinlikleri almasını sağlar.

![İleti gönderen ve ileti alıcısı arasında RabbitMQ gösteren diyagram.](./media/rabbitmq-event-bus-development-test-environment/rabbitmq-implementation.png)

**Şekil 6-21.** Bir olay otobüs RabbitMQ uygulaması

RabbitMQ, dağıtımı işlemek için ileti yayımcısı ve aboneler arasında bir aracı işlevi görür. Kodda, EventBusRabbitMQ sınıfı genel IEventBus arabirimini uygular. Bu, bu geliştirme/test sürümünden üretim sürümüne değiş tokuş yapabilmeniz için Bağımlılık Enjeksiyonu'na dayanır.

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
}
```

Bir örnek dev/test olay veri tobunun RabbitMQ uygulaması ortak koddur. RabbitMQ sunucusuna olan bağlantıyı işlemeli ve kuyruklara bir ileti olayı yayımlamak için kod sağlaması gerekiyor. Ayrıca, her olay türü için tümleştirme olay işleyicileri koleksiyonları bir sözlük uygulamak zorundadır; bu etkinlik türleri, Şekil 6-21'de gösterildiği gibi, her alıcı mikro hizmeti için farklı bir anlık kullanım ve farklı aboneliklere sahip olabilir.

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a>RabbitMQ ile basit bir yayın yöntemi uygulama

Aşağıdaki kod, tüm senaryoyu sergilemek için RabbitMQ için bir olay veri otobüsü uygulamasının ***basitleştirilmiş*** bir sürümüdür. Bağlantıyı bu şekilde halletmiyorsun. Tam uygulamayı görmek [için, dotnet-architecture/eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) deposundaki gerçek kodu görün.

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Member objects and other methods ...
    // ...

    public void Publish(IntegrationEvent @event)
    {
        var eventName = @event.GetType().Name;
        var factory = new ConnectionFactory() { HostName = _connectionString };
        using (var connection = factory.CreateConnection())
        using (var channel = connection.CreateModel())
        {
            channel.ExchangeDeclare(exchange: _brokerName,
                type: "direct");
            string message = JsonConvert.SerializeObject(@event);
            var body = Encoding.UTF8.GetBytes(message);
            channel.BasicPublish(exchange: _brokerName,
                routingKey: eventName,
                basicProperties: null,
                body: body);
       }
    }
}
```

eShopOnContainers uygulamasında Yayımlama yönteminin [gerçek kodu,](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) RabbitMQ kapsayıcısının hazır olmaması durumunda görevi belirli sayıda yeniden deneen [Polly](https://github.com/App-vNext/Polly) yeniden deneme ilkesi kullanılarak geliştirilir. Bu, docker-compose kapsayıcıları başlatırken oluşabilir; örneğin, RabbitMQ kapsayıcısı diğer kaplardan daha yavaş başlayabilir.

Daha önce de belirtildiği gibi, RabbitMQ birçok olası yapılandırmaları vardır, bu nedenle bu kod sadece dev / test ortamları için kullanılmalıdır.

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a>RabbitMQ API ile abonelik kodunun uygulanması

Yayımlama kodunda olduğu gibi, aşağıdaki kod RabbitMQ için olay veri otobüsü uygulamasının bir kısmının basitleştirilmesidir. Yine, genellikle bunu geliştirmek sürece değiştirmek gerekmez.

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Member objects and other methods ...
    // ...

    public void Subscribe<T, TH>()
        where T : IntegrationEvent
        where TH : IIntegrationEventHandler<T>
    {
        var eventName = _subsManager.GetEventKey<T>();

        var containsKey = _subsManager.HasSubscriptionsForEvent(eventName);
        if (!containsKey)
        {
            if (!_persistentConnection.IsConnected)
            {
                _persistentConnection.TryConnect();
            }

            using (var channel = _persistentConnection.CreateModel())
            {
                channel.QueueBind(queue: _queueName,
                                    exchange: BROKER_NAME,
                                    routingKey: eventName);
            }
        }

        _subsManager.AddSubscription<T, TH>();
    }
}
```

Her olay türü RabbitMQ olayları almak için ilgili bir kanal vardır. Daha sonra kanal ve olay türü başına gerektiği kadar olay işleyicileri olabilir.

Abone Ol yöntemi, geçerli microservice bir geri çağırma yöntemi gibi bir IIntegrationEventHandler nesnesi, artı ilgili IntegrationEvent nesnesi kabul eder. Kod daha sonra olay işleyicisi her tümleştirme olay türü istemci microservice başına olabilir olay işleyicileri listesine ekler. İstemci kodu etkinliğe zaten abone edilmemişse, kod olay türü için bir kanal oluşturur, böylece bu olay başka bir hizmetten yayımlandığında RabbitMQ'den itme stilinde olayları alabilir.

Yukarıda belirtildiği gibi, eShopOnContainers uygulanan olay otobüs sadece ve eğitim amacı vardır, sadece ana senaryoları işler beri, bu yüzden üretim için hazır değil.

Üretim senaryoları için, RabbitMQ'ye özgü aşağıdaki ek kaynakları ve mikro hizmetler bölümü [arasındaki etkinlik tabanlı iletişimi uygulayın.](./integration-event-based-microservice-communications.md#additional-resources)

## <a name="additional-resources"></a>Ek kaynaklar

RabbitMQ desteği ile üretime hazır çözümler.

- **EasyNetQ** - RabbitMQ için Açık Kaynak .NET API istemcisi \
  <http://easynetq.com/>

- **Toplu Taşıma** \
  <https://masstransit-project.com/>
  
>[!div class="step-by-step"]
>[Önceki](integration-event-based-microservice-communications.md)
>[Sonraki](subscribe-events.md)
