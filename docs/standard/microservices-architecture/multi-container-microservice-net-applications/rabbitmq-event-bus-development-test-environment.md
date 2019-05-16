---
title: Geliştirme veya test ortamı için RabbitMQ ile bir olay veri yolu uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Geliştirme ve test ortamları için tümleştirme olayları için Mesajlaşma bir olay veri yolu uygulamak için RabbitMQ kullanın.
ms.date: 10/02/2018
ms.openlocfilehash: af02208bb9e680403a04377ccb740a8b15be29bc
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644432"
---
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a>Geliştirme veya test ortamı için RabbitMQ ile bir olay veri yolu uygulama

Bir kapsayıcıda çalışan RabbitMQ hizmetine uygulama gibi temel, özel olay veri yolu oluşturursanız, yalnızca geliştirme ve test ortamları için kullanılması gerektiğini diyerek başlamanız gerekir. Üretime hazır service bus bir parçası olarak oluşturmadığınız sürece, üretim ortamı için bunun kullanmamanız gerekir. Bir ticari hizmet veri yolu olan birçok üretime hazır önemli özellikleri basit bir özel olay veri yolu eksik olabilir.

Bir olay veri yolu özel uygulama hizmetine temel RabbitMQ (başka bir uygulama üzerinde Azure Service Bus tabanlı yoktur) API'sini kullanarak bir kitaplıktır.

Şekil 6-21'de gösterildiği gibi RabbitMQ ile olay veri yolu uygulaması olaylarına abone olma, olayları yayımlama ve olayları, alma mikro hizmetler sağlar.

![RabbitMQ ileti yayımcı ve aboneleri, dağıtım işlemeye arasında aracı görevi görür.](./media/image22.png)

**Şekil 6-21.** Bir olay veri yolu RabbitMQ uygulaması

Kod içinde EventBusRabbitMQ sınıfı genel IEventBus arabirim uygular. Böylece, bir üretim sürümü için bu geliştirme ve test sürümünden takas edebilirsiniz bu bağımlılık ekleme üzerinde temel alır.

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
}
```

Ortak kod örnek geliştirme/test olay Bus RabbitMQ uygulamasıdır. RabbitMQ sunucu bağlantısı işlemek ve kuyruklara ileti olay yayımlamak için kod sağlamak vardır. Her bir olay türü için tümleştirme olay işleyicileri koleksiyonlarının sözlüğü uygulamak de vardır; Bu olay türlerini, Şekil 6-21'de gösterildiği gibi farklı bir örneğini ve her alıcı mikro hizmet için farklı Aboneliklerde olabilir.

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a>Basit bir uygulama yayımlama RabbitMQ ile yöntemi

Aşağıdaki kod bir ***Basitleştirilmiş*** tam senaryoyu canlandırmak üzere, RabbitMQ için bir olay veri yolu uygulaması sürümü. Bu şekilde bağlantı gerçekten işlemez. Gerçek kod tam uygulamayı görmek için bkz [dotnet-mimari/hizmetine](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) depo. 

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

[Gerçek kod](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) yayımlama hizmetine uygulama yöntemi kullanarak gelişmiş bir [Polly](https://github.com/App-vNext/Polly) RabbitMQ kapsayıcı olması durumunda görev belirli birkaç kez yeniden deneme ilkesi, yeniden deneyin hazır değil. Bu durum ortaya çıkabilir, docker-compose; kapsayıcıları başlatılıyor Örneğin, RabbitMQ kapsayıcı diğer kapsayıcılara göre daha yavaş başlayabilir.

Daha önce bahsedildiği gibi birçok olası yapılandırmalar vardır, RabbitMQ, bu kod yalnızca geliştirme/test ortamları için kullanılması gereken şekilde.

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a>Abonelik kod RabbitMQ API'si ile uygulama

Yayımlama koduyla aşağıdaki kodu bir olay veri yolu uygulaması için RabbitMQ parçası basitleştirme gibidir. Yeniden, genellikle geliştirme sürece bunu değiştirmeniz gerekmez.

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

Her bir olay türü, RabbitMQ olayları almak için ilgili bir kanal sahiptir. Ardından, gerektiği şekilde kanal ve olay türüne göre olarak çok sayıda olay işleyicileri olabilir.

Abone ol yöntemin yanı sıra ilgili IntegrationEvent nesne gibi geçerli bir mikro hizmet içinde bir geri çağırma yöntemi olan IIntegrationEventHandler nesneyi kabul eder. Kod bu durumda istemci mikro hizmet her tümleştirme olay türü olan olay işleyicileri listesi bu olay işleyicisi ekler. İstemci kodu zaten olaya onaylanmamış, diğer herhangi bir hizmetten olay yayımlandığında, olayları bir anında iletme stil RabbitMQ, böylelikle kod olay türü için bir kanal oluşturur.

>[!div class="step-by-step"]
>[Önceki](integration-event-based-microservice-communications.md)
>[İleri](subscribe-events.md)
