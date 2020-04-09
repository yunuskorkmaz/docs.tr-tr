---
title: Geliştirme veya test ortamı için RabbitMQ ile bir olay veri yolu uygulama
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | Geliştirme veya test ortamları için tümleştirme etkinlikleri için bir olay veri günü mesajlaşması uygulamak için RabbitMQ'yi kullanın.
ms.date: 10/02/2018
ms.openlocfilehash: 12e37fabfe915b4d2089d27f7852528a9a037d3c
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988303"
---
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a><span data-ttu-id="55850-103">Geliştirme veya test ortamı için RabbitMQ ile bir olay veri yolu uygulama</span><span class="sxs-lookup"><span data-stu-id="55850-103">Implementing an event bus with RabbitMQ for the development or test environment</span></span>

<span data-ttu-id="55850-104">EShopOnContainers uygulamasının yaptığı gibi, bir konteynerde çalışan RabbitMQ'ye dayalı özel etkinlik otobüsünüzü oluşturursanız, bunun yalnızca geliştirme ve test ortamlarınız için kullanılması gerektiğini söyleyerek başlamalıyız.</span><span class="sxs-lookup"><span data-stu-id="55850-104">We should start by saying that if you create your custom event bus based on RabbitMQ running in a container, as the eShopOnContainers application does, it should be used only for your development and test environments.</span></span> <span data-ttu-id="55850-105">Üretime hazır servis veri tonunun bir parçası olarak oluşturmadığınız sürece, üretim ortamınız için kullanmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="55850-105">You should not use it for your production environment, unless you are building it as a part of a production-ready service bus.</span></span> <span data-ttu-id="55850-106">Basit bir özel olay veri otobüsü, ticari servis verine sahip olduğu üretime hazır birçok kritik özelliği eksik olabilir.</span><span class="sxs-lookup"><span data-stu-id="55850-106">A simple custom event bus might be missing many production-ready critical features that a commercial service bus has.</span></span>

<span data-ttu-id="55850-107">EShopOnContainers olay otobüs özel uygulama biri temelde RabbitMQ API kullanarak bir kütüphane.</span><span class="sxs-lookup"><span data-stu-id="55850-107">One of the event bus custom implementation in eShopOnContainers is basically a library using the RabbitMQ API.</span></span> <span data-ttu-id="55850-108">(Azure Hizmet Veri Yolunda'na dayalı başka bir uygulama daha vardır.)</span><span class="sxs-lookup"><span data-stu-id="55850-108">(There's another implementation based on Azure Service Bus.)</span></span>

<span data-ttu-id="55850-109">RabbitMQ ile etkinlik otobüsü uygulaması, mikro hizmetlerin olaylara abone olmasını, olayları yayınlamasını ve Şekil 6-21'de gösterildiği gibi etkinlikleri almasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="55850-109">The event bus implementation with RabbitMQ lets microservices subscribe to events, publish events, and receive events, as shown in Figure 6-21.</span></span>

![İleti gönderen ve ileti alıcısı arasında RabbitMQ gösteren diyagram.](./media/rabbitmq-event-bus-development-test-environment/rabbitmq-implementation.png)

<span data-ttu-id="55850-111">**Şekil 6-21.**</span><span class="sxs-lookup"><span data-stu-id="55850-111">**Figure 6-21.**</span></span> <span data-ttu-id="55850-112">Bir olay otobüs RabbitMQ uygulaması</span><span class="sxs-lookup"><span data-stu-id="55850-112">RabbitMQ implementation of an event bus</span></span>

<span data-ttu-id="55850-113">RabbitMQ, dağıtımı işlemek için ileti yayımcısı ve aboneler arasında bir aracı işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="55850-113">RabbitMQ functions as an intermediary between message publisher and subscribers, to handle distribution.</span></span> <span data-ttu-id="55850-114">Kodda, EventBusRabbitMQ sınıfı genel IEventBus arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="55850-114">In the code, the EventBusRabbitMQ class implements the generic IEventBus interface.</span></span> <span data-ttu-id="55850-115">Bu, bu geliştirme/test sürümünden üretim sürümüne değiş tokuş yapabilmeniz için Bağımlılık Enjeksiyonu'na dayanır.</span><span class="sxs-lookup"><span data-stu-id="55850-115">This is based on Dependency Injection so that you can swap from this dev/test version to a production version.</span></span>

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
}
```

<span data-ttu-id="55850-116">Bir örnek dev/test olay veri tobunun RabbitMQ uygulaması ortak koddur.</span><span class="sxs-lookup"><span data-stu-id="55850-116">The RabbitMQ implementation of a sample dev/test event bus is boilerplate code.</span></span> <span data-ttu-id="55850-117">RabbitMQ sunucusuna olan bağlantıyı işlemeli ve kuyruklara bir ileti olayı yayımlamak için kod sağlaması gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="55850-117">It has to handle the connection to the RabbitMQ server and provide code for publishing a message event to the queues.</span></span> <span data-ttu-id="55850-118">Ayrıca, her olay türü için tümleştirme olay işleyicileri koleksiyonları bir sözlük uygulamak zorundadır; bu etkinlik türleri, Şekil 6-21'de gösterildiği gibi, her alıcı mikro hizmeti için farklı bir anlık kullanım ve farklı aboneliklere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="55850-118">It also has to implement a dictionary of collections of integration event handlers for each event type; these event types can have a different instantiation and different subscriptions for each receiver microservice, as shown in Figure 6-21.</span></span>

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a><span data-ttu-id="55850-119">RabbitMQ ile basit bir yayın yöntemi uygulama</span><span class="sxs-lookup"><span data-stu-id="55850-119">Implementing a simple publish method with RabbitMQ</span></span>

<span data-ttu-id="55850-120">Aşağıdaki kod, tüm senaryoyu sergilemek için RabbitMQ için bir olay veri otobüsü uygulamasının ***basitleştirilmiş*** bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="55850-120">The following code is a ***simplified*** version of an event bus implementation for RabbitMQ, to showcase the whole scenario.</span></span> <span data-ttu-id="55850-121">Bağlantıyı bu şekilde halletmiyorsun.</span><span class="sxs-lookup"><span data-stu-id="55850-121">You don't really handle the connection this way.</span></span> <span data-ttu-id="55850-122">Tam uygulamayı görmek [için, dotnet-architecture/eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) deposundaki gerçek kodu görün.</span><span class="sxs-lookup"><span data-stu-id="55850-122">To see the full implementation, see the actual code in the [dotnet-architecture/eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) repository.</span></span>

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

<span data-ttu-id="55850-123">eShopOnContainers uygulamasında Yayımlama yönteminin [gerçek kodu,](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) RabbitMQ kapsayıcısının hazır olmaması durumunda görevi belirli sayıda yeniden deneen [Polly](https://github.com/App-vNext/Polly) yeniden deneme ilkesi kullanılarak geliştirilir.</span><span class="sxs-lookup"><span data-stu-id="55850-123">The [actual code](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) of the Publish method in the eShopOnContainers application is improved by using a [Polly](https://github.com/App-vNext/Polly) retry policy, which retries the task a certain number of times in case the RabbitMQ container is not ready.</span></span> <span data-ttu-id="55850-124">Bu, docker-compose kapsayıcıları başlatırken oluşabilir; örneğin, RabbitMQ kapsayıcısı diğer kaplardan daha yavaş başlayabilir.</span><span class="sxs-lookup"><span data-stu-id="55850-124">This can occur when docker-compose is starting the containers; for example, the RabbitMQ container might start more slowly than the other containers.</span></span>

<span data-ttu-id="55850-125">Daha önce de belirtildiği gibi, RabbitMQ birçok olası yapılandırmaları vardır, bu nedenle bu kod sadece dev / test ortamları için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="55850-125">As mentioned earlier, there are many possible configurations in RabbitMQ, so this code should be used only for dev/test environments.</span></span>

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a><span data-ttu-id="55850-126">RabbitMQ API ile abonelik kodunun uygulanması</span><span class="sxs-lookup"><span data-stu-id="55850-126">Implementing the subscription code with the RabbitMQ API</span></span>

<span data-ttu-id="55850-127">Yayımlama kodunda olduğu gibi, aşağıdaki kod RabbitMQ için olay veri otobüsü uygulamasının bir kısmının basitleştirilmesidir.</span><span class="sxs-lookup"><span data-stu-id="55850-127">As with the publish code, the following code is a simplification of part of the event bus implementation for RabbitMQ.</span></span> <span data-ttu-id="55850-128">Yine, genellikle bunu geliştirmek sürece değiştirmek gerekmez.</span><span class="sxs-lookup"><span data-stu-id="55850-128">Again, you usually do not need to change it unless you are improving it.</span></span>

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

<span data-ttu-id="55850-129">Her olay türü RabbitMQ olayları almak için ilgili bir kanal vardır.</span><span class="sxs-lookup"><span data-stu-id="55850-129">Each event type has a related channel to get events from RabbitMQ.</span></span> <span data-ttu-id="55850-130">Daha sonra kanal ve olay türü başına gerektiği kadar olay işleyicileri olabilir.</span><span class="sxs-lookup"><span data-stu-id="55850-130">You can then have as many event handlers per channel and event type as needed.</span></span>

<span data-ttu-id="55850-131">Abone Ol yöntemi, geçerli microservice bir geri çağırma yöntemi gibi bir IIntegrationEventHandler nesnesi, artı ilgili IntegrationEvent nesnesi kabul eder.</span><span class="sxs-lookup"><span data-stu-id="55850-131">The Subscribe method accepts an IIntegrationEventHandler object, which is like a callback method in the current microservice, plus its related IntegrationEvent object.</span></span> <span data-ttu-id="55850-132">Kod daha sonra olay işleyicisi her tümleştirme olay türü istemci microservice başına olabilir olay işleyicileri listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="55850-132">The code then adds that event handler to the list of event handlers that each integration event type can have per client microservice.</span></span> <span data-ttu-id="55850-133">İstemci kodu etkinliğe zaten abone edilmemişse, kod olay türü için bir kanal oluşturur, böylece bu olay başka bir hizmetten yayımlandığında RabbitMQ'den itme stilinde olayları alabilir.</span><span class="sxs-lookup"><span data-stu-id="55850-133">If the client code has not already been subscribed to the event, the code creates a channel for the event type so it can receive events in a push style from RabbitMQ when that event is published from any other service.</span></span>

<span data-ttu-id="55850-134">Yukarıda belirtildiği gibi, eShopOnContainers uygulanan olay otobüs sadece ve eğitim amacı vardır, sadece ana senaryoları işler beri, bu yüzden üretim için hazır değil.</span><span class="sxs-lookup"><span data-stu-id="55850-134">As mentioned above, the event bus implemented in eShopOnContainers has only and educational purpose, since it only handles the main scenarios, so it's not ready for production.</span></span>

<span data-ttu-id="55850-135">Üretim senaryoları için, RabbitMQ'ye özgü aşağıdaki ek kaynakları ve mikro hizmetler bölümü [arasındaki etkinlik tabanlı iletişimi uygulayın.](./integration-event-based-microservice-communications.md#additional-resources)</span><span class="sxs-lookup"><span data-stu-id="55850-135">For production scenarios check the additional resources below, specific for RabbitMQ, and the [Implementing event-based communication between microservices](./integration-event-based-microservice-communications.md#additional-resources) section.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="55850-136">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="55850-136">Additional resources</span></span>

<span data-ttu-id="55850-137">RabbitMQ desteği ile üretime hazır çözümler.</span><span class="sxs-lookup"><span data-stu-id="55850-137">A production-ready solutions with support for RabbitMQ.</span></span>

- <span data-ttu-id="55850-138">**EasyNetQ** - RabbitMQ için Açık Kaynak .NET API istemcisi </span><span class="sxs-lookup"><span data-stu-id="55850-138">**EasyNetQ** - Open Source .NET API client for RabbitMQ </span></span>\
  <http://easynetq.com/>

- <span data-ttu-id="55850-139">**Toplu Taşıma** </span><span class="sxs-lookup"><span data-stu-id="55850-139">**MassTransit** </span></span>\
  <https://masstransit-project.com/>
  
> [!div class="step-by-step"]
> <span data-ttu-id="55850-140">[Önceki](integration-event-based-microservice-communications.md)
> [Sonraki](subscribe-events.md)</span><span class="sxs-lookup"><span data-stu-id="55850-140">[Previous](integration-event-based-microservice-communications.md)
[Next](subscribe-events.md)</span></span>
