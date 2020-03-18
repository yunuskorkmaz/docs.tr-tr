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
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a><span data-ttu-id="78faf-103">Geliştirme veya test ortamı için RabbitMQ ile bir olay veri yolu uygulama</span><span class="sxs-lookup"><span data-stu-id="78faf-103">Implementing an event bus with RabbitMQ for the development or test environment</span></span>

<span data-ttu-id="78faf-104">EShopOnContainers uygulamasının yaptığı gibi, bir konteynerde çalışan RabbitMQ'ye dayalı özel etkinlik otobüsünüzü oluşturursanız, bunun yalnızca geliştirme ve test ortamlarınız için kullanılması gerektiğini söyleyerek başlamalıyız.</span><span class="sxs-lookup"><span data-stu-id="78faf-104">We should start by saying that if you create your custom event bus based on RabbitMQ running in a container, as the eShopOnContainers application does, it should be used only for your development and test environments.</span></span> <span data-ttu-id="78faf-105">Üretime hazır servis veri tonunun bir parçası olarak oluşturmadığınız sürece, üretim ortamınız için kullanmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="78faf-105">You should not use it for your production environment, unless you are building it as a part of a production-ready service bus.</span></span> <span data-ttu-id="78faf-106">Basit bir özel olay veri otobüsü, ticari servis verine sahip olduğu üretime hazır birçok kritik özelliği eksik olabilir.</span><span class="sxs-lookup"><span data-stu-id="78faf-106">A simple custom event bus might be missing many production-ready critical features that a commercial service bus has.</span></span>

<span data-ttu-id="78faf-107">eShopOnContainers'daki etkinlik veri neşrisi özel uygulamalarından biri temelde RabbitMQ API'sini kullanan bir kitaplıktır (Azure Hizmet Veri Tos'una dayalı başka bir uygulama vardır).</span><span class="sxs-lookup"><span data-stu-id="78faf-107">One of the event bus custom implementation in eShopOnContainers is basically a library using the RabbitMQ API (There’s another implementation based on Azure Service Bus).</span></span>

<span data-ttu-id="78faf-108">RabbitMQ ile etkinlik otobüsü uygulaması, mikro hizmetlerin olaylara abone olmasını, olayları yayınlamasını ve Şekil 6-21'de gösterildiği gibi etkinlikleri almasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="78faf-108">The event bus implementation with RabbitMQ lets microservices subscribe to events, publish events, and receive events, as shown in Figure 6-21.</span></span>

![İleti gönderen ve ileti alıcısı arasında RabbitMQ gösteren diyagram.](./media/rabbitmq-event-bus-development-test-environment/rabbitmq-implementation.png)

<span data-ttu-id="78faf-110">**Şekil 6-21.**</span><span class="sxs-lookup"><span data-stu-id="78faf-110">**Figure 6-21.**</span></span> <span data-ttu-id="78faf-111">Bir olay otobüs RabbitMQ uygulaması</span><span class="sxs-lookup"><span data-stu-id="78faf-111">RabbitMQ implementation of an event bus</span></span>

<span data-ttu-id="78faf-112">RabbitMQ, dağıtımı işlemek için ileti yayımcısı ve aboneler arasında bir aracı işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="78faf-112">RabbitMQ functions as an intermediary between message publisher and subscribers, to handle distribution.</span></span> <span data-ttu-id="78faf-113">Kodda, EventBusRabbitMQ sınıfı genel IEventBus arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="78faf-113">In the code, the EventBusRabbitMQ class implements the generic IEventBus interface.</span></span> <span data-ttu-id="78faf-114">Bu, bu geliştirme/test sürümünden üretim sürümüne değiş tokuş yapabilmeniz için Bağımlılık Enjeksiyonu'na dayanır.</span><span class="sxs-lookup"><span data-stu-id="78faf-114">This is based on Dependency Injection so that you can swap from this dev/test version to a production version.</span></span>

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
}
```

<span data-ttu-id="78faf-115">Bir örnek dev/test olay veri tobunun RabbitMQ uygulaması ortak koddur.</span><span class="sxs-lookup"><span data-stu-id="78faf-115">The RabbitMQ implementation of a sample dev/test event bus is boilerplate code.</span></span> <span data-ttu-id="78faf-116">RabbitMQ sunucusuna olan bağlantıyı işlemeli ve kuyruklara bir ileti olayı yayımlamak için kod sağlaması gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="78faf-116">It has to handle the connection to the RabbitMQ server and provide code for publishing a message event to the queues.</span></span> <span data-ttu-id="78faf-117">Ayrıca, her olay türü için tümleştirme olay işleyicileri koleksiyonları bir sözlük uygulamak zorundadır; bu etkinlik türleri, Şekil 6-21'de gösterildiği gibi, her alıcı mikro hizmeti için farklı bir anlık kullanım ve farklı aboneliklere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="78faf-117">It also has to implement a dictionary of collections of integration event handlers for each event type; these event types can have a different instantiation and different subscriptions for each receiver microservice, as shown in Figure 6-21.</span></span>

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a><span data-ttu-id="78faf-118">RabbitMQ ile basit bir yayın yöntemi uygulama</span><span class="sxs-lookup"><span data-stu-id="78faf-118">Implementing a simple publish method with RabbitMQ</span></span>

<span data-ttu-id="78faf-119">Aşağıdaki kod, tüm senaryoyu sergilemek için RabbitMQ için bir olay veri otobüsü uygulamasının ***basitleştirilmiş*** bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="78faf-119">The following code is a ***simplified*** version of an event bus implementation for RabbitMQ, to showcase the whole scenario.</span></span> <span data-ttu-id="78faf-120">Bağlantıyı bu şekilde halletmiyorsun.</span><span class="sxs-lookup"><span data-stu-id="78faf-120">You don't really handle the connection this way.</span></span> <span data-ttu-id="78faf-121">Tam uygulamayı görmek [için, dotnet-architecture/eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) deposundaki gerçek kodu görün.</span><span class="sxs-lookup"><span data-stu-id="78faf-121">To see the full implementation, see the actual code in the [dotnet-architecture/eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) repository.</span></span>

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

<span data-ttu-id="78faf-122">eShopOnContainers uygulamasında Yayımlama yönteminin [gerçek kodu,](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) RabbitMQ kapsayıcısının hazır olmaması durumunda görevi belirli sayıda yeniden deneen [Polly](https://github.com/App-vNext/Polly) yeniden deneme ilkesi kullanılarak geliştirilir.</span><span class="sxs-lookup"><span data-stu-id="78faf-122">The [actual code](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) of the Publish method in the eShopOnContainers application is improved by using a [Polly](https://github.com/App-vNext/Polly) retry policy, which retries the task a certain number of times in case the RabbitMQ container is not ready.</span></span> <span data-ttu-id="78faf-123">Bu, docker-compose kapsayıcıları başlatırken oluşabilir; örneğin, RabbitMQ kapsayıcısı diğer kaplardan daha yavaş başlayabilir.</span><span class="sxs-lookup"><span data-stu-id="78faf-123">This can occur when docker-compose is starting the containers; for example, the RabbitMQ container might start more slowly than the other containers.</span></span>

<span data-ttu-id="78faf-124">Daha önce de belirtildiği gibi, RabbitMQ birçok olası yapılandırmaları vardır, bu nedenle bu kod sadece dev / test ortamları için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="78faf-124">As mentioned earlier, there are many possible configurations in RabbitMQ, so this code should be used only for dev/test environments.</span></span>

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a><span data-ttu-id="78faf-125">RabbitMQ API ile abonelik kodunun uygulanması</span><span class="sxs-lookup"><span data-stu-id="78faf-125">Implementing the subscription code with the RabbitMQ API</span></span>

<span data-ttu-id="78faf-126">Yayımlama kodunda olduğu gibi, aşağıdaki kod RabbitMQ için olay veri otobüsü uygulamasının bir kısmının basitleştirilmesidir.</span><span class="sxs-lookup"><span data-stu-id="78faf-126">As with the publish code, the following code is a simplification of part of the event bus implementation for RabbitMQ.</span></span> <span data-ttu-id="78faf-127">Yine, genellikle bunu geliştirmek sürece değiştirmek gerekmez.</span><span class="sxs-lookup"><span data-stu-id="78faf-127">Again, you usually do not need to change it unless you are improving it.</span></span>

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

<span data-ttu-id="78faf-128">Her olay türü RabbitMQ olayları almak için ilgili bir kanal vardır.</span><span class="sxs-lookup"><span data-stu-id="78faf-128">Each event type has a related channel to get events from RabbitMQ.</span></span> <span data-ttu-id="78faf-129">Daha sonra kanal ve olay türü başına gerektiği kadar olay işleyicileri olabilir.</span><span class="sxs-lookup"><span data-stu-id="78faf-129">You can then have as many event handlers per channel and event type as needed.</span></span>

<span data-ttu-id="78faf-130">Abone Ol yöntemi, geçerli microservice bir geri çağırma yöntemi gibi bir IIntegrationEventHandler nesnesi, artı ilgili IntegrationEvent nesnesi kabul eder.</span><span class="sxs-lookup"><span data-stu-id="78faf-130">The Subscribe method accepts an IIntegrationEventHandler object, which is like a callback method in the current microservice, plus its related IntegrationEvent object.</span></span> <span data-ttu-id="78faf-131">Kod daha sonra olay işleyicisi her tümleştirme olay türü istemci microservice başına olabilir olay işleyicileri listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="78faf-131">The code then adds that event handler to the list of event handlers that each integration event type can have per client microservice.</span></span> <span data-ttu-id="78faf-132">İstemci kodu etkinliğe zaten abone edilmemişse, kod olay türü için bir kanal oluşturur, böylece bu olay başka bir hizmetten yayımlandığında RabbitMQ'den itme stilinde olayları alabilir.</span><span class="sxs-lookup"><span data-stu-id="78faf-132">If the client code has not already been subscribed to the event, the code creates a channel for the event type so it can receive events in a push style from RabbitMQ when that event is published from any other service.</span></span>

<span data-ttu-id="78faf-133">Yukarıda belirtildiği gibi, eShopOnContainers uygulanan olay otobüs sadece ve eğitim amacı vardır, sadece ana senaryoları işler beri, bu yüzden üretim için hazır değil.</span><span class="sxs-lookup"><span data-stu-id="78faf-133">As mentioned above, the event bus implemented in eShopOnContainers has only and educational purpose, since it only handles the main scenarios, so it's not ready for production.</span></span>

<span data-ttu-id="78faf-134">Üretim senaryoları için, RabbitMQ'ye özgü aşağıdaki ek kaynakları ve mikro hizmetler bölümü [arasındaki etkinlik tabanlı iletişimi uygulayın.](./integration-event-based-microservice-communications.md#additional-resources)</span><span class="sxs-lookup"><span data-stu-id="78faf-134">For production scenarios check the additional resources below, specific for RabbitMQ, and the [Implementing event-based communication between microservices](./integration-event-based-microservice-communications.md#additional-resources) section.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="78faf-135">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="78faf-135">Additional resources</span></span>

<span data-ttu-id="78faf-136">RabbitMQ desteği ile üretime hazır çözümler.</span><span class="sxs-lookup"><span data-stu-id="78faf-136">A production-ready solutions with support for RabbitMQ.</span></span>

- <span data-ttu-id="78faf-137">**EasyNetQ** - RabbitMQ için Açık Kaynak .NET API istemcisi </span><span class="sxs-lookup"><span data-stu-id="78faf-137">**EasyNetQ** - Open Source .NET API client for RabbitMQ </span></span>\
  <http://easynetq.com/>

- <span data-ttu-id="78faf-138">**Toplu Taşıma** </span><span class="sxs-lookup"><span data-stu-id="78faf-138">**MassTransit** </span></span>\
  <https://masstransit-project.com/>
  
>[!div class="step-by-step"]
><span data-ttu-id="78faf-139">[Önceki](integration-event-based-microservice-communications.md)
>[Sonraki](subscribe-events.md)</span><span class="sxs-lookup"><span data-stu-id="78faf-139">[Previous](integration-event-based-microservice-communications.md)
[Next](subscribe-events.md)</span></span>
