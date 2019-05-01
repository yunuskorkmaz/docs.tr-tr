---
title: Geliştirme veya test ortamı için RabbitMQ ile bir olay veri yolu uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Geliştirme ve test ortamları için tümleştirme olayları için Mesajlaşma bir olay veri yolu uygulamak için RabbitMQ kullanın.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/02/2018
ms.openlocfilehash: 2bcd3491c58884653cd6c119753696019151bfed
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61864279"
---
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a><span data-ttu-id="5d14c-103">Geliştirme veya test ortamı için RabbitMQ ile bir olay veri yolu uygulama</span><span class="sxs-lookup"><span data-stu-id="5d14c-103">Implementing an event bus with RabbitMQ for the development or test environment</span></span>

<span data-ttu-id="5d14c-104">Bir kapsayıcıda çalışan RabbitMQ hizmetine uygulama gibi temel, özel olay veri yolu oluşturursanız, yalnızca geliştirme ve test ortamları için kullanılması gerektiğini diyerek başlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5d14c-104">We should start by saying that if you create your custom event bus based on RabbitMQ running in a container, as the eShopOnContainers application does, it should be used only for your development and test environments.</span></span> <span data-ttu-id="5d14c-105">Üretime hazır service bus bir parçası olarak oluşturmadığınız sürece, üretim ortamı için bunun kullanmamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5d14c-105">You should not use it for your production environment, unless you are building it as a part of a production-ready service bus.</span></span> <span data-ttu-id="5d14c-106">Bir ticari hizmet veri yolu olan birçok üretime hazır önemli özellikleri basit bir özel olay veri yolu eksik olabilir.</span><span class="sxs-lookup"><span data-stu-id="5d14c-106">A simple custom event bus might be missing many production-ready critical features that a commercial service bus has.</span></span>

<span data-ttu-id="5d14c-107">Bir olay veri yolu özel uygulama hizmetine temel RabbitMQ (başka bir uygulama üzerinde Azure Service Bus tabanlı yoktur) API'sini kullanarak bir kitaplıktır.</span><span class="sxs-lookup"><span data-stu-id="5d14c-107">One of the event bus custom implementation in eShopOnContainers is basically a library using the RabbitMQ API (There’s another implementation based on Azure Service Bus).</span></span>

<span data-ttu-id="5d14c-108">Şekil 6-21'de gösterildiği gibi RabbitMQ ile olay veri yolu uygulaması olaylarına abone olma, olayları yayımlama ve olayları, alma mikro hizmetler sağlar.</span><span class="sxs-lookup"><span data-stu-id="5d14c-108">The event bus implementation with RabbitMQ lets microservices subscribe to events, publish events, and receive events, as shown in Figure 6-21.</span></span>

![RabbitMQ ileti yayımcı ve aboneleri, dağıtım işlemeye arasında aracı görevi görür.](./media/image22.png)

<span data-ttu-id="5d14c-110">**Şekil 6-21.**</span><span class="sxs-lookup"><span data-stu-id="5d14c-110">**Figure 6-21.**</span></span> <span data-ttu-id="5d14c-111">Bir olay veri yolu RabbitMQ uygulaması</span><span class="sxs-lookup"><span data-stu-id="5d14c-111">RabbitMQ implementation of an event bus</span></span>

<span data-ttu-id="5d14c-112">Kod içinde EventBusRabbitMQ sınıfı genel IEventBus arabirim uygular.</span><span class="sxs-lookup"><span data-stu-id="5d14c-112">In the code, the EventBusRabbitMQ class implements the generic IEventBus interface.</span></span> <span data-ttu-id="5d14c-113">Böylece, bir üretim sürümü için bu geliştirme ve test sürümünden takas edebilirsiniz bu bağımlılık ekleme üzerinde temel alır.</span><span class="sxs-lookup"><span data-stu-id="5d14c-113">This is based on Dependency Injection so that you can swap from this dev/test version to a production version.</span></span>

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
}
```

<span data-ttu-id="5d14c-114">Ortak kod örnek geliştirme/test olay Bus RabbitMQ uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="5d14c-114">The RabbitMQ implementation of a sample dev/test event bus is boilerplate code.</span></span> <span data-ttu-id="5d14c-115">RabbitMQ sunucu bağlantısı işlemek ve kuyruklara ileti olay yayımlamak için kod sağlamak vardır.</span><span class="sxs-lookup"><span data-stu-id="5d14c-115">It has to handle the connection to the RabbitMQ server and provide code for publishing a message event to the queues.</span></span> <span data-ttu-id="5d14c-116">Her bir olay türü için tümleştirme olay işleyicileri koleksiyonlarının sözlüğü uygulamak de vardır; Bu olay türlerini, Şekil 6-21'de gösterildiği gibi farklı bir örneğini ve her alıcı mikro hizmet için farklı Aboneliklerde olabilir.</span><span class="sxs-lookup"><span data-stu-id="5d14c-116">It also has to implement a dictionary of collections of integration event handlers for each event type; these event types can have a different instantiation and different subscriptions for each receiver microservice, as shown in Figure 6-21.</span></span>

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a><span data-ttu-id="5d14c-117">Basit bir uygulama yayımlama RabbitMQ ile yöntemi</span><span class="sxs-lookup"><span data-stu-id="5d14c-117">Implementing a simple publish method with RabbitMQ</span></span>

<span data-ttu-id="5d14c-118">Aşağıdaki kod bir ***Basitleştirilmiş*** tam senaryoyu canlandırmak üzere, RabbitMQ için bir olay veri yolu uygulaması sürümü.</span><span class="sxs-lookup"><span data-stu-id="5d14c-118">The following code is a ***simplified*** version of an event bus implementation for RabbitMQ, to showcase the whole scenario.</span></span> <span data-ttu-id="5d14c-119">Bu şekilde bağlantı gerçekten işlemez.</span><span class="sxs-lookup"><span data-stu-id="5d14c-119">You don't really handle the connection this way.</span></span> <span data-ttu-id="5d14c-120">Gerçek kod tam uygulamayı görmek için bkz [dotnet-mimari/hizmetine](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) depo.</span><span class="sxs-lookup"><span data-stu-id="5d14c-120">To see the full implementation, see the actual code in the [dotnet-architecture/eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) repository.</span></span> 

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

<span data-ttu-id="5d14c-121">[Gerçek kod](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) yayımlama hizmetine uygulama yöntemi kullanarak gelişmiş bir [Polly](https://github.com/App-vNext/Polly) RabbitMQ kapsayıcı olması durumunda görev belirli birkaç kez yeniden deneme ilkesi, yeniden deneyin hazır değil.</span><span class="sxs-lookup"><span data-stu-id="5d14c-121">The [actual code](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) of the Publish method in the eShopOnContainers application is improved by using a [Polly](https://github.com/App-vNext/Polly) retry policy, which retries the task a certain number of times in case the RabbitMQ container is not ready.</span></span> <span data-ttu-id="5d14c-122">Bu durum ortaya çıkabilir, docker-compose; kapsayıcıları başlatılıyor Örneğin, RabbitMQ kapsayıcı diğer kapsayıcılara göre daha yavaş başlayabilir.</span><span class="sxs-lookup"><span data-stu-id="5d14c-122">This can occur when docker-compose is starting the containers; for example, the RabbitMQ container might start more slowly than the other containers.</span></span>

<span data-ttu-id="5d14c-123">Daha önce bahsedildiği gibi birçok olası yapılandırmalar vardır, RabbitMQ, bu kod yalnızca geliştirme/test ortamları için kullanılması gereken şekilde.</span><span class="sxs-lookup"><span data-stu-id="5d14c-123">As mentioned earlier, there are many possible configurations in RabbitMQ, so this code should be used only for dev/test environments.</span></span>

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a><span data-ttu-id="5d14c-124">Abonelik kod RabbitMQ API'si ile uygulama</span><span class="sxs-lookup"><span data-stu-id="5d14c-124">Implementing the subscription code with the RabbitMQ API</span></span>

<span data-ttu-id="5d14c-125">Yayımlama koduyla aşağıdaki kodu bir olay veri yolu uygulaması için RabbitMQ parçası basitleştirme gibidir.</span><span class="sxs-lookup"><span data-stu-id="5d14c-125">As with the publish code, the following code is a simplification of part of the event bus implementation for RabbitMQ.</span></span> <span data-ttu-id="5d14c-126">Yeniden, genellikle geliştirme sürece bunu değiştirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="5d14c-126">Again, you usually do not need to change it unless you are improving it.</span></span>

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

<span data-ttu-id="5d14c-127">Her bir olay türü, RabbitMQ olayları almak için ilgili bir kanal sahiptir.</span><span class="sxs-lookup"><span data-stu-id="5d14c-127">Each event type has a related channel to get events from RabbitMQ.</span></span> <span data-ttu-id="5d14c-128">Ardından, gerektiği şekilde kanal ve olay türüne göre olarak çok sayıda olay işleyicileri olabilir.</span><span class="sxs-lookup"><span data-stu-id="5d14c-128">You can then have as many event handlers per channel and event type as needed.</span></span>

<span data-ttu-id="5d14c-129">Abone ol yöntemin yanı sıra ilgili IntegrationEvent nesne gibi geçerli bir mikro hizmet içinde bir geri çağırma yöntemi olan IIntegrationEventHandler nesneyi kabul eder.</span><span class="sxs-lookup"><span data-stu-id="5d14c-129">The Subscribe method accepts an IIntegrationEventHandler object, which is like a callback method in the current microservice, plus its related IntegrationEvent object.</span></span> <span data-ttu-id="5d14c-130">Kod bu durumda istemci mikro hizmet her tümleştirme olay türü olan olay işleyicileri listesi bu olay işleyicisi ekler.</span><span class="sxs-lookup"><span data-stu-id="5d14c-130">The code then adds that event handler to the list of event handlers that each integration event type can have per client microservice.</span></span> <span data-ttu-id="5d14c-131">İstemci kodu zaten olaya onaylanmamış, diğer herhangi bir hizmetten olay yayımlandığında, olayları bir anında iletme stil RabbitMQ, böylelikle kod olay türü için bir kanal oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5d14c-131">If the client code has not already been subscribed to the event, the code creates a channel for the event type so it can receive events in a push style from RabbitMQ when that event is published from any other service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="5d14c-132">[Önceki](integration-event-based-microservice-communications.md)
>[İleri](subscribe-events.md)</span><span class="sxs-lookup"><span data-stu-id="5d14c-132">[Previous](integration-event-based-microservice-communications.md)
[Next](subscribe-events.md)</span></span>
