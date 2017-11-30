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
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a><span data-ttu-id="1fc87-104">Bir olay için veri yolu RabbitMQ ile geliştirme veya test ortamına uygulama</span><span class="sxs-lookup"><span data-stu-id="1fc87-104">Implementing an event bus with RabbitMQ for the development or test environment</span></span>

<span data-ttu-id="1fc87-105">Bir kapsayıcıda çalışan RabbitMQ eShopOnContainers uygulamalarında olduğu gibi temel, özel olay bus oluşturursanız, yalnızca geliştirme ve test ortamları için kullanılması gerektiğini söyleyen başlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1fc87-105">We should start by saying that if you create your custom event bus based on RabbitMQ running in a container, as the eShopOnContainers application does, it should be used only for your development and test environments.</span></span> <span data-ttu-id="1fc87-106">Üretime hazır hizmet veri yolu bir parçası olarak oluşturmakta olduğunuz sürece, üretim ortamınız için bunu kullanmamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1fc87-106">You should not use it for your production environment, unless you are building it as a part of a production-ready service bus.</span></span> <span data-ttu-id="1fc87-107">Basit özel olay bus ticari hizmet veri yolu olan birçok üretime hazır önemli özellikleri eksik olabilir.</span><span class="sxs-lookup"><span data-stu-id="1fc87-107">A simple custom event bus might be missing many production-ready critical features that a commercial service bus has.</span></span>

<span data-ttu-id="1fc87-108">EShopOnContainers özel bir olay veri yoluna temelde RabbitMQ API kullanarak bir kitaplığı uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="1fc87-108">The eShopOnContainers custom implementation of an event bus is basically a library using the RabbitMQ API.</span></span> <span data-ttu-id="1fc87-109">Uygulama, Şekil 8-21'de gösterildiği gibi olaylarına abone olma, olayları yayımlama ve olayları almak mikro olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="1fc87-109">The implementation lets microservices subscribe to events, publish events, and receive events, as shown in Figure 8-21.</span></span>

![](./media/image22.png)

<span data-ttu-id="1fc87-110">**Şekil 8-21.**</span><span class="sxs-lookup"><span data-stu-id="1fc87-110">**Figure 8-21.**</span></span> <span data-ttu-id="1fc87-111">Bir olay veri yoluna RabbitMQ uygulaması</span><span class="sxs-lookup"><span data-stu-id="1fc87-111">RabbitMQ implementation of an event bus</span></span>

<span data-ttu-id="1fc87-112">Kodda EventBusRabbitMQ sınıfı genel IEventBus arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="1fc87-112">In the code, the EventBusRabbitMQ class implements the generic IEventBus interface.</span></span> <span data-ttu-id="1fc87-113">Böylece, bir üretim sürüm olarak bu geliştirme ve test sürümünden takas edebilirsiniz bu bağımlılık ekleme temel alır.</span><span class="sxs-lookup"><span data-stu-id="1fc87-113">This is based on Dependency Injection so that you can swap from this dev/test version to a production version.</span></span>

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
```

<span data-ttu-id="1fc87-114">RabbitMQ örnek geliştirme ve test olay bus Demirbaş kod uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="1fc87-114">The RabbitMQ implementation of a sample dev/test event bus is boilerplate code.</span></span> <span data-ttu-id="1fc87-115">RabbitMQ sunucu bağlantısını işlemek ve sıralara ileti olayı yayımlamak için kod sağlamak vardır.</span><span class="sxs-lookup"><span data-stu-id="1fc87-115">It has to handle the connection to the RabbitMQ server and provide code for publishing a message event to the queues.</span></span> <span data-ttu-id="1fc87-116">Ayrıca her bir olay türü için tümleştirme olay işleyicileri koleksiyonları sözlüğü uygulamak içerir; Bu olay türlerini, Şekil 8-21'de gösterildiği gibi farklı bir örnek oluşturma ve her alıcı mikro hizmet için farklı Aboneliklerde olabilir.</span><span class="sxs-lookup"><span data-stu-id="1fc87-116">It also has to implement a dictionary of collections of integration event handlers for each event type; these event types can have a different instantiation and different subscriptions for each receiver microservice, as shown in Figure 8-21.</span></span>

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a><span data-ttu-id="1fc87-117">Basit bir uygulama yayımlama RabbitMQ ile yöntemi</span><span class="sxs-lookup"><span data-stu-id="1fc87-117">Implementing a simple publish method with RabbitMQ</span></span>

<span data-ttu-id="1fc87-118">Aşağıdaki kod RabbitMQ, eShopOnContainers olay veri yolu uygulamasını parçası kitabıdır genellikle geliştirmeler yapıyoruz sürece kod gerekmez.</span><span class="sxs-lookup"><span data-stu-id="1fc87-118">The following code is part of the eShopOnContainers event bus implementation for RabbitMQ, so you usually do not need to code it unless you are making improvements.</span></span> <span data-ttu-id="1fc87-119">Kod bir bağlantı ve RabbitMQ kanala alır, bir ileti oluşturur ve ardından sıraya ileti yayımlar.</span><span class="sxs-lookup"><span data-stu-id="1fc87-119">The code gets a connection and channel to RabbitMQ, creates a message, and then publishes the message into the queue.</span></span>

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

<span data-ttu-id="1fc87-120">[Gerçek bir kod](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) Yayımla eShopOnContainers uygulama yönteminde kullanılarak geliştirilmiş bir [Polly](https://github.com/App-vNext/Polly) RabbitMQ kapsayıcı olması durumunda, bir belirli sayıda görev yeniden deneme ilkesi yeniden deneyin hazır değil.</span><span class="sxs-lookup"><span data-stu-id="1fc87-120">The [actual code](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) of the Publish method in the eShopOnContainers application is improved by using a [Polly](https://github.com/App-vNext/Polly) retry policy, which retries the task a certain number of times in case the RabbitMQ container is not ready.</span></span> <span data-ttu-id="1fc87-121">Bu durum ortaya çıkabilir zaman docker compose'u; kapsayıcıları başlatılıyor Örneğin, RabbitMQ kapsayıcı diğer kapsayıcıları daha yavaş başlayabilir.</span><span class="sxs-lookup"><span data-stu-id="1fc87-121">This can occur when docker-compose is starting the containers; for example, the RabbitMQ container might start more slowly than the other containers.</span></span>

<span data-ttu-id="1fc87-122">Daha önce belirtildiği gibi yok RabbitMQ, birçok olası yapılandırmalarında bu kod yalnızca geliştirme ve test ortamları için kullanılması gereken şekilde.</span><span class="sxs-lookup"><span data-stu-id="1fc87-122">As mentioned earlier, there are many possible configurations in RabbitMQ, so this code should be used only for dev/test environments.</span></span>

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a><span data-ttu-id="1fc87-123">Abonelik kod RabbitMQ API ile uygulama</span><span class="sxs-lookup"><span data-stu-id="1fc87-123">Implementing the subscription code with the RabbitMQ API</span></span>

<span data-ttu-id="1fc87-124">Yayımla koduyla aşağıdaki kodu RabbitMQ için olay veri yolu uygulaması parçası alma gibidir.</span><span class="sxs-lookup"><span data-stu-id="1fc87-124">As with the publish code, the following code is a simplification of part of the event bus implementation for RabbitMQ.</span></span> <span data-ttu-id="1fc87-125">Yeniden, genellikle geliştirme sürece bunu değiştirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="1fc87-125">Again, you usually do not need to change it unless you are improving it.</span></span>

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

<span data-ttu-id="1fc87-126">Her olay türü RabbitMQ olayları almak için ilgili bir kanal sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1fc87-126">Each event type has a related channel to get events from RabbitMQ.</span></span> <span data-ttu-id="1fc87-127">Ardından, gerektiği gibi kanal ve olay türüne göre sayıda olay işleyicileri olabilir.</span><span class="sxs-lookup"><span data-stu-id="1fc87-127">You can then have as many event handlers per channel and event type as needed.</span></span>

<span data-ttu-id="1fc87-128">Subscribe yöntemi geçerli mikro hizmet içindeki bir geri çağırma yöntemi gibidir, IIntegrationEventHandler nesneyi artı kendi ilgili IntegrationEvent nesne kabul eder.</span><span class="sxs-lookup"><span data-stu-id="1fc87-128">The Subscribe method accepts an IIntegrationEventHandler object, which is like a callback method in the current microservice, plus its related IntegrationEvent object.</span></span> <span data-ttu-id="1fc87-129">Kod, bu olay işleyicisi sonra istemci mikro her tümleştirme olay türü olan olay işleyicileri listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="1fc87-129">The code then adds that event handler to the list of event handlers that each integration event type can have per client microservice.</span></span> <span data-ttu-id="1fc87-130">İstemci kodu zaten olaya onaylanmamış varsa, kodu olay türü için bir kanal oluşturur, bu nedenle bu olay herhangi diğer hizmetinden yayımlandığında itme stilinde RabbitMQ gelen olayları alabilir.</span><span class="sxs-lookup"><span data-stu-id="1fc87-130">If the client code has not already been subscribed to the event, the code creates a channel for the event type so it can receive events in a push style from RabbitMQ when that event is published from any other service.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="1fc87-131">[Önceki] (tümleştirme-olay-tabanlı-mikro hizmet-communications.md) [sonraki] (abone events.md)</span><span class="sxs-lookup"><span data-stu-id="1fc87-131">[Previous] (integration-event-based-microservice-communications.md) [Next] (subscribe-events.md)</span></span>
