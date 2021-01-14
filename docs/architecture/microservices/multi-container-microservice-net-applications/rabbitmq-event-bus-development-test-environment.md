---
title: Geliştirme veya test ortamı için RabbitMQ ile bir olay veri yolu uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Geliştirme veya test ortamları için tümleştirme olayları için bir olay veri yolu mesajlaşma uygulamak üzere Kbbitmq kullanın.
ms.date: 01/13/2021
ms.openlocfilehash: a1e7d11e376080a03269f202fa6ae24ffeb0f4d2
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188087"
---
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a>Geliştirme veya test ortamı için RabbitMQ ile bir olay veri yolu uygulama

Bir kapsayıcıda çalışan kbbitmq tabanlı özel olay veri yolunu oluşturursanız, eShopOnContainers uygulamasının yaptığı, yalnızca geliştirme ve test ortamlarınız için kullanılması gerektiğini söyleyerek başlayacağız. Üretim için kullanıma yönelik bir Service Bus kapsamında oluşturulmadığınız sürece bunu üretim ortamınız için kullanmayın. Basit bir özel olay veri yolu, ticari bir Service Bus 'ın sahip olduğu çok sayıda üretime hazırlı kritik özelliği eksik olabilir.

EShopOnContainers 'daki olay veri yolu özel uygulamalarından biri, temel olarak Kbbitmq API kullanan bir kitaplıktır. (Azure Service Bus göre başka bir uygulama vardır.)

Kbbitmq ile olay veri yolu uygulamasının, Şekil 6-21 ' de gösterildiği gibi mikro hizmetlerin olaylara abone olma, olayları yayımlama ve olayları almasına izin verir.

![İleti gönderici ve ileti alıcısı arasında Kbbitmq gösteren diyagram.](./media/rabbitmq-event-bus-development-test-environment/rabbitmq-implementation.png)

**Şekil 6-21.** Bir olay veri yolunun Kbıbitmq uygulama

Kbbitmq, dağıtımı işlemek için ileti yayımcısı ve aboneler arasında bir aracı olarak çalışır. Kodda, Eventbuskbbitmq sınıfı, genel ıeventbus arabirimini uygular. Bu uygulama, bu geliştirme/test sürümünden üretim sürümüne geçiş yapabilmeniz için bağımlılık ekleme işlemini temel alır.

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
}
```

Örnek bir geliştirme/test olay veri yolunun Kbbitmq uygulamasının ortak kodlamasıdır. Bu, kbbitmq sunucusuyla bağlantıyı işleymelidir ve sıralara bir ileti olayı yayımlamaya yönelik kod sağlar. Ayrıca, her olay türü için tümleştirme olay işleyicisi koleksiyonlarının bir sözlüğünü uygulamak gerekir; Bu olay türlerinde, Şekil 6-21 ' de gösterildiği gibi, her bir alıcı mikro hizmeti için farklı bir örnek oluşturma ve farklı abonelikler bulunabilir.

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a>Kbbitmq ile basit bir yayımlama yöntemi uygulama

Aşağıdaki kod, tüm senaryoyu göstermek amacıyla, Kbbitmq için bir Event Bus uygulamasının **_Basitleştirilmiş_* _ sürümüdür. Bu şekilde bağlantıyı gerçekten işlemezsiniz. Tam uygulamayı görmek için, [DotNet-Architecture/eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) deposundaki gerçek koda bakın.

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

EShopOnContainers uygulamasındaki Publish yönteminin [gerçek kodu](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) bir [Polly](https://github.com/App-vNext/Polly) yeniden deneme ilkesi kullanılarak geliştirilmiştir ve bu da, kbbitmq kapsayıcısının hazırlanmasında bir süre sonra görevi yeniden dener. Bu senaryo, Docker-Compose kapsayıcıları başlattığında meydana gelebilir; Örneğin, Korbbitmq kapsayıcısı diğer kapsayıcılardan daha yavaş başlayabilir.

Daha önce belirtildiği gibi, kbbitmq ' de birçok olası yapılandırma vardır, bu nedenle bu kod yalnızca geliştirme ve test ortamları için kullanılmalıdır.

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a>Kbbitmq API 'siyle abonelik kodunu uygulama

Yayımlama kodunda olduğu gibi, aşağıdaki kod, kbbitmq için olay veri yolu uygulamasının bir kısmının basitleştirmesidir. Yine de, onu geliştirmediğiniz müddetçe genellikle değiştirmeniz gerekmez.

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

Her olay türünün, kbıbitmq 'dan olayları almak için ilgili bir kanalı vardır. Daha sonra, kanal başına çok sayıda olay işleyicisine ve gerektiğinde olay türüne sahip olabilirsiniz.

Subscribe yöntemi, geçerli mikro hizmette geri çağırma yöntemi ve ilgili ıntegrationevent nesnesi gibi bir ııntegrationeventhandler nesnesini kabul eder. Kod daha sonra bu olay işleyicisini her bir tümleştirme olay türünün istemci mikro hizmeti başına sahip olduğu olay işleyicileri listesine ekler. İstemci kodu henüz olaya abone olunmamışsa, kod, olay türü için bir kanal oluşturur, böylece bu olay başka bir hizmetten yayımlandığında, bu olay bir anında iletme stilinde olayları alabilir.

Yukarıda belirtildiği gibi, eShopOnContainers 'da uygulanan olay veri yolu yalnızca ve eğitim amacını içerir, bu nedenle üretim için hazırlanma.

Üretim senaryolarında, aşağıdaki ek kaynakları, Kbbitmq için özel ve [mikro hizmetler arasında olay tabanlı Iletişim uygulama](./integration-event-based-microservice-communications.md#additional-resources) bölümüne bakın.

## <a name="additional-resources"></a>Ek kaynaklar

Kbbitmq desteğiyle üretime Ready bir çözüm.

- _ *Easynetq**-Oybbitmq \ Için açık kaynak .NET API istemcisi
  <https://easynetq.com/>

- **Masstransıya** \
  <https://masstransit-project.com/>
  
> [!div class="step-by-step"]
> [Önceki](integration-event-based-microservice-communications.md) 
>  [Sonraki](subscribe-events.md)
