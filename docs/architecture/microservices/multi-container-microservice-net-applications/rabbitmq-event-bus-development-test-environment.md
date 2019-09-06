---
title: Geliştirme veya test ortamı için RabbitMQ ile bir olay veri yolu uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Geliştirme veya test ortamları için tümleştirme olayları için bir olay veri yolu mesajlaşma uygulamak üzere Kbbitmq kullanın.
ms.date: 10/02/2018
ms.openlocfilehash: af02208bb9e680403a04377ccb740a8b15be29bc
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296564"
---
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a><span data-ttu-id="b2a8b-103">Geliştirme veya test ortamı için RabbitMQ ile bir olay veri yolu uygulama</span><span class="sxs-lookup"><span data-stu-id="b2a8b-103">Implementing an event bus with RabbitMQ for the development or test environment</span></span>

<span data-ttu-id="b2a8b-104">Bir kapsayıcıda çalışan kbbitmq tabanlı özel olay veri yolunu oluşturursanız, eShopOnContainers uygulamasının yaptığı, yalnızca geliştirme ve test ortamlarınız için kullanılması gerektiğini söyleyerek başlayacağız.</span><span class="sxs-lookup"><span data-stu-id="b2a8b-104">We should start by saying that if you create your custom event bus based on RabbitMQ running in a container, as the eShopOnContainers application does, it should be used only for your development and test environments.</span></span> <span data-ttu-id="b2a8b-105">Üretim için kullanıma yönelik bir Service Bus kapsamında oluşturulmadığınız sürece bunu üretim ortamınız için kullanmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="b2a8b-105">You should not use it for your production environment, unless you are building it as a part of a production-ready service bus.</span></span> <span data-ttu-id="b2a8b-106">Basit bir özel olay veri yolu, ticari bir Service Bus 'ın sahip olduğu çok sayıda üretime hazırlı kritik özelliği eksik olabilir.</span><span class="sxs-lookup"><span data-stu-id="b2a8b-106">A simple custom event bus might be missing many production-ready critical features that a commercial service bus has.</span></span>

<span data-ttu-id="b2a8b-107">EShopOnContainers 'daki olay veri yolu özel uygulamasından biri, kbbitmq API 'sini kullanan bir kitaplıktır (Azure Service Bus göre başka bir uygulama vardır).</span><span class="sxs-lookup"><span data-stu-id="b2a8b-107">One of the event bus custom implementation in eShopOnContainers is basically a library using the RabbitMQ API (There’s another implementation based on Azure Service Bus).</span></span>

<span data-ttu-id="b2a8b-108">Kbbitmq ile olay veri yolu uygulamasının, Şekil 6-21 ' de gösterildiği gibi mikro hizmetlerin olaylara abone olma, olayları yayımlama ve olayları almasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="b2a8b-108">The event bus implementation with RabbitMQ lets microservices subscribe to events, publish events, and receive events, as shown in Figure 6-21.</span></span>

![Kbbitmq, dağıtımı işlemek için ileti yayımcısı ve aboneler arasında bir aracı olarak çalışır.](./media/image22.png)

<span data-ttu-id="b2a8b-110">**Şekil 6-21.**</span><span class="sxs-lookup"><span data-stu-id="b2a8b-110">**Figure 6-21.**</span></span> <span data-ttu-id="b2a8b-111">Bir olay veri yolunun Kbıbitmq uygulama</span><span class="sxs-lookup"><span data-stu-id="b2a8b-111">RabbitMQ implementation of an event bus</span></span>

<span data-ttu-id="b2a8b-112">Kodda, Eventbuskbbitmq sınıfı, genel ıeventbus arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="b2a8b-112">In the code, the EventBusRabbitMQ class implements the generic IEventBus interface.</span></span> <span data-ttu-id="b2a8b-113">Bu, bu geliştirme/test sürümünden üretim sürümüne geçiş yapabilmeniz için bağımlılık ekleme tabanlıdır.</span><span class="sxs-lookup"><span data-stu-id="b2a8b-113">This is based on Dependency Injection so that you can swap from this dev/test version to a production version.</span></span>

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
}
```

<span data-ttu-id="b2a8b-114">Örnek bir geliştirme/test olay veri yolunun Kbbitmq uygulamasının ortak kodlamasıdır.</span><span class="sxs-lookup"><span data-stu-id="b2a8b-114">The RabbitMQ implementation of a sample dev/test event bus is boilerplate code.</span></span> <span data-ttu-id="b2a8b-115">Bu, kbbitmq sunucusuyla bağlantıyı işleymelidir ve sıralara bir ileti olayı yayımlamaya yönelik kod sağlar.</span><span class="sxs-lookup"><span data-stu-id="b2a8b-115">It has to handle the connection to the RabbitMQ server and provide code for publishing a message event to the queues.</span></span> <span data-ttu-id="b2a8b-116">Ayrıca, her olay türü için tümleştirme olay işleyicisi koleksiyonlarının bir sözlüğünü uygulamak gerekir; Bu olay türlerinde, Şekil 6-21 ' de gösterildiği gibi, her bir alıcı mikro hizmeti için farklı bir örnek oluşturma ve farklı abonelikler bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="b2a8b-116">It also has to implement a dictionary of collections of integration event handlers for each event type; these event types can have a different instantiation and different subscriptions for each receiver microservice, as shown in Figure 6-21.</span></span>

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a><span data-ttu-id="b2a8b-117">Kbbitmq ile basit bir yayımlama yöntemi uygulama</span><span class="sxs-lookup"><span data-stu-id="b2a8b-117">Implementing a simple publish method with RabbitMQ</span></span>

<span data-ttu-id="b2a8b-118">Aşağıdaki kod, tüm senaryoyu göstermek için, Kbbitmq için bir Event Bus uygulamasının ***Basitleştirilmiş*** bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="b2a8b-118">The following code is a ***simplified*** version of an event bus implementation for RabbitMQ, to showcase the whole scenario.</span></span> <span data-ttu-id="b2a8b-119">Bu şekilde bağlantıyı gerçekten işlemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2a8b-119">You don't really handle the connection this way.</span></span> <span data-ttu-id="b2a8b-120">Tam uygulamayı görmek için, [DotNet-Architecture/eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) deposundaki gerçek koda bakın.</span><span class="sxs-lookup"><span data-stu-id="b2a8b-120">To see the full implementation, see the actual code in the [dotnet-architecture/eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) repository.</span></span> 

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

<span data-ttu-id="b2a8b-121">EShopOnContainers uygulamasındaki Publish yönteminin [gerçek kodu](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) bir [Polly](https://github.com/App-vNext/Polly) yeniden deneme ilkesi kullanılarak geliştirilmiştir ve bu da, kbbitmq kapsayıcısının hazırlanmadığından, görevi belirli sayıda kez yeniden dener.</span><span class="sxs-lookup"><span data-stu-id="b2a8b-121">The [actual code](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) of the Publish method in the eShopOnContainers application is improved by using a [Polly](https://github.com/App-vNext/Polly) retry policy, which retries the task a certain number of times in case the RabbitMQ container is not ready.</span></span> <span data-ttu-id="b2a8b-122">Docker-Compose kapsayıcıları başlattığında bu durum oluşabilir; Örneğin, Korbbitmq kapsayıcısı diğer kapsayıcılardan daha yavaş başlayabilir.</span><span class="sxs-lookup"><span data-stu-id="b2a8b-122">This can occur when docker-compose is starting the containers; for example, the RabbitMQ container might start more slowly than the other containers.</span></span>

<span data-ttu-id="b2a8b-123">Daha önce belirtildiği gibi, kbbitmq ' de birçok olası yapılandırma vardır, bu nedenle bu kod yalnızca geliştirme ve test ortamları için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b2a8b-123">As mentioned earlier, there are many possible configurations in RabbitMQ, so this code should be used only for dev/test environments.</span></span>

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a><span data-ttu-id="b2a8b-124">Kbbitmq API 'siyle abonelik kodunu uygulama</span><span class="sxs-lookup"><span data-stu-id="b2a8b-124">Implementing the subscription code with the RabbitMQ API</span></span>

<span data-ttu-id="b2a8b-125">Yayımlama kodunda olduğu gibi, aşağıdaki kod, kbbitmq için olay veri yolu uygulamasının bir kısmının basitleştirmesidir.</span><span class="sxs-lookup"><span data-stu-id="b2a8b-125">As with the publish code, the following code is a simplification of part of the event bus implementation for RabbitMQ.</span></span> <span data-ttu-id="b2a8b-126">Yine de, onu geliştirmediğiniz müddetçe genellikle değiştirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="b2a8b-126">Again, you usually do not need to change it unless you are improving it.</span></span>

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

<span data-ttu-id="b2a8b-127">Her olay türünün, kbıbitmq 'dan olayları almak için ilgili bir kanalı vardır.</span><span class="sxs-lookup"><span data-stu-id="b2a8b-127">Each event type has a related channel to get events from RabbitMQ.</span></span> <span data-ttu-id="b2a8b-128">Daha sonra, kanal başına çok sayıda olay işleyicisine ve gerektiğinde olay türüne sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2a8b-128">You can then have as many event handlers per channel and event type as needed.</span></span>

<span data-ttu-id="b2a8b-129">Subscribe yöntemi, geçerli mikro hizmette geri çağırma yöntemi ve ilgili ıntegrationevent nesnesi gibi bir ııntegrationeventhandler nesnesini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="b2a8b-129">The Subscribe method accepts an IIntegrationEventHandler object, which is like a callback method in the current microservice, plus its related IntegrationEvent object.</span></span> <span data-ttu-id="b2a8b-130">Kod daha sonra bu olay işleyicisini her bir tümleştirme olay türünün istemci mikro hizmeti başına sahip olduğu olay işleyicileri listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="b2a8b-130">The code then adds that event handler to the list of event handlers that each integration event type can have per client microservice.</span></span> <span data-ttu-id="b2a8b-131">İstemci kodu henüz olaya abone olunmamışsa, kod, olay türü için bir kanal oluşturur, böylece bu olay başka bir hizmetten yayımlandığında, bu olay bir anında iletme stilinde olayları alabilir.</span><span class="sxs-lookup"><span data-stu-id="b2a8b-131">If the client code has not already been subscribed to the event, the code creates a channel for the event type so it can receive events in a push style from RabbitMQ when that event is published from any other service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b2a8b-132">[Önceki](integration-event-based-microservice-communications.md)İleri
>[](subscribe-events.md)</span><span class="sxs-lookup"><span data-stu-id="b2a8b-132">[Previous](integration-event-based-microservice-communications.md)
[Next](subscribe-events.md)</span></span>
