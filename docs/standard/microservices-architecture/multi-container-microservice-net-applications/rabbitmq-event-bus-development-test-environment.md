---
title: "Bir olay için veri yolu RabbitMQ ile geliştirme veya test ortamına uygulama"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Bir olay için veri yolu RabbitMQ ile geliştirme veya test ortamına uygulama"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: f58d355b6f5fd31a21791d3b072c77f70f90c387
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a>Bir olay için veri yolu RabbitMQ ile geliştirme veya test ortamına uygulama

Bir kapsayıcıda çalışan RabbitMQ eShopOnContainers uygulamalarında olduğu gibi temel, özel olay bus oluşturursanız, yalnızca geliştirme ve test ortamları için kullanılması gerektiğini söyleyen başlamanız gerekir. Üretime hazır hizmet veri yolu bir parçası olarak oluşturmakta olduğunuz sürece, üretim ortamınız için bunu kullanmamanız gerekir. Basit özel olay bus ticari hizmet veri yolu olan birçok üretime hazır önemli özellikleri eksik olabilir.

EShopOnContainers özel bir olay veri yoluna temelde RabbitMQ API kullanarak bir kitaplığı uygulamasıdır. Uygulama, Şekil 8-21'de gösterildiği gibi olaylarına abone olma, olayları yayımlama ve olayları almak mikro olanak sağlar.

![](./media/image22.png)

**Şekil 8-21.** Bir olay veri yoluna RabbitMQ uygulaması

Kodda EventBusRabbitMQ sınıfı genel IEventBus arabirimini uygular. Böylece, bir üretim sürüm olarak bu geliştirme ve test sürümünden takas edebilirsiniz bu bağımlılık ekleme temel alır.

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
```

RabbitMQ örnek geliştirme ve test olay bus Demirbaş kod uygulamasıdır. RabbitMQ sunucu bağlantısını işlemek ve sıralara ileti olayı yayımlamak için kod sağlamak vardır. Ayrıca her bir olay türü için tümleştirme olay işleyicileri koleksiyonları sözlüğü uygulamak içerir; Bu olay türlerini, Şekil 8-21'de gösterildiği gibi farklı bir örnek oluşturma ve her alıcı mikro hizmet için farklı Aboneliklerde olabilir.

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a>Basit bir uygulama yayımlama RabbitMQ ile yöntemi

Aşağıdaki kod RabbitMQ, eShopOnContainers olay veri yolu uygulamasını parçası kitabıdır genellikle geliştirmeler yapıyoruz sürece kod gerekmez. Kod bir bağlantı ve RabbitMQ kanala alır, bir ileti oluşturur ve ardından sıraya ileti yayımlar.

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

[Gerçek bir kod](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) Yayımla eShopOnContainers uygulama yönteminde kullanılarak geliştirilmiş bir [Polly](https://github.com/App-vNext/Polly) RabbitMQ kapsayıcı olması durumunda, bir belirli sayıda görev yeniden deneme ilkesi yeniden deneyin hazır değil. Bu durum ortaya çıkabilir zaman docker compose'u; kapsayıcıları başlatılıyor Örneğin, RabbitMQ kapsayıcı diğer kapsayıcıları daha yavaş başlayabilir.

Daha önce belirtildiği gibi yok RabbitMQ, birçok olası yapılandırmalarında bu kod yalnızca geliştirme ve test ortamları için kullanılması gereken şekilde.

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a>Abonelik kod RabbitMQ API ile uygulama

Yayımla koduyla aşağıdaki kodu RabbitMQ için olay veri yolu uygulaması parçası alma gibidir. Yeniden, genellikle geliştirme sürece bunu değiştirmeniz gerekmez.

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Member objects and other methods ...
    // ...
    public void Subscribe<T>(IIntegrationEventHandler<T> handler)
        where T : IntegrationEvent
    {
        var eventName = typeof(T).Name;
        if (_handlers.ContainsKey(eventName))
        {
            _handlers[eventName].Add(handler);
        }
        else
        {
            var channel = GetChannel();
            channel.QueueBind(queue: _queueName,
                exchange: _brokerName,
                routingKey: eventName);
            _handlers.Add(eventName, new List<IIntegrationEventHandler>());
            _handlers[eventName].Add(handler);
            _eventTypes.Add(typeof(T));
        }
    }
}
```

Her olay türü RabbitMQ olayları almak için ilgili bir kanal sahiptir. Ardından, gerektiği gibi kanal ve olay türüne göre sayıda olay işleyicileri olabilir.

Subscribe yöntemi geçerli mikro hizmet içindeki bir geri çağırma yöntemi gibidir, IIntegrationEventHandler nesneyi artı kendi ilgili IntegrationEvent nesne kabul eder. Kod, bu olay işleyicisi sonra istemci mikro her tümleştirme olay türü olan olay işleyicileri listesine ekler. İstemci kodu zaten olaya onaylanmamış varsa, kodu olay türü için bir kanal oluşturur, bu nedenle bu olay herhangi diğer hizmetinden yayımlandığında itme stilinde RabbitMQ gelen olayları alabilir.


>[!div class="step-by-step"]
[Önceki] (tümleştirme-olay-tabanlı-mikro hizmet-communications.md) [sonraki] (abone events.md)
