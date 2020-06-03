---
title: Geliştirme veya test ortamı için RabbitMQ ile bir olay veri yolu uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Geliştirme veya test ortamları için tümleştirme olayları için bir olay veri yolu mesajlaşma uygulamak üzere Kbbitmq kullanın.
ms.date: 10/02/2018
ms.openlocfilehash: 1af72d18825eb610d6900178205450e2c2e34c25
ms.sourcegitcommit: 5280b2aef60a1ed99002dba44e4b9e7f6c830604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2020
ms.locfileid: "84306896"
---
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a><span data-ttu-id="e0d27-103">Geliştirme veya test ortamı için RabbitMQ ile bir olay veri yolu uygulama</span><span class="sxs-lookup"><span data-stu-id="e0d27-103">Implementing an event bus with RabbitMQ for the development or test environment</span></span>

<span data-ttu-id="e0d27-104">Bir kapsayıcıda çalışan kbbitmq tabanlı özel olay veri yolunu oluşturursanız, eShopOnContainers uygulamasının yaptığı, yalnızca geliştirme ve test ortamlarınız için kullanılması gerektiğini söyleyerek başlayacağız.</span><span class="sxs-lookup"><span data-stu-id="e0d27-104">We should start by saying that if you create your custom event bus based on RabbitMQ running in a container, as the eShopOnContainers application does, it should be used only for your development and test environments.</span></span> <span data-ttu-id="e0d27-105">Üretim için kullanıma yönelik bir Service Bus kapsamında oluşturulmadığınız sürece bunu üretim ortamınız için kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="e0d27-105">Don't use it for your production environment, unless you are building it as a part of a production-ready service bus.</span></span> <span data-ttu-id="e0d27-106">Basit bir özel olay veri yolu, ticari bir Service Bus 'ın sahip olduğu çok sayıda üretime hazırlı kritik özelliği eksik olabilir.</span><span class="sxs-lookup"><span data-stu-id="e0d27-106">A simple custom event bus might be missing many production-ready critical features that a commercial service bus has.</span></span>

<span data-ttu-id="e0d27-107">EShopOnContainers 'daki olay veri yolu özel uygulamalarından biri, temel olarak Kbbitmq API kullanan bir kitaplıktır.</span><span class="sxs-lookup"><span data-stu-id="e0d27-107">One of the event bus custom implementations in eShopOnContainers is basically a library using the RabbitMQ API.</span></span> <span data-ttu-id="e0d27-108">(Azure Service Bus göre başka bir uygulama vardır.)</span><span class="sxs-lookup"><span data-stu-id="e0d27-108">(There's another implementation based on Azure Service Bus.)</span></span>

<span data-ttu-id="e0d27-109">Kbbitmq ile olay veri yolu uygulamasının, Şekil 6-21 ' de gösterildiği gibi mikro hizmetlerin olaylara abone olma, olayları yayımlama ve olayları almasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="e0d27-109">The event bus implementation with RabbitMQ lets microservices subscribe to events, publish events, and receive events, as shown in Figure 6-21.</span></span>

![İleti gönderici ve ileti alıcısı arasında Kbbitmq gösteren diyagram.](./media/rabbitmq-event-bus-development-test-environment/rabbitmq-implementation.png)

<span data-ttu-id="e0d27-111">**Şekil 6-21.**</span><span class="sxs-lookup"><span data-stu-id="e0d27-111">**Figure 6-21.**</span></span> <span data-ttu-id="e0d27-112">Bir olay veri yolunun Kbıbitmq uygulama</span><span class="sxs-lookup"><span data-stu-id="e0d27-112">RabbitMQ implementation of an event bus</span></span>

<span data-ttu-id="e0d27-113">Kbbitmq, dağıtımı işlemek için ileti yayımcısı ve aboneler arasında bir aracı olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="e0d27-113">RabbitMQ functions as an intermediary between message publisher and subscribers, to handle distribution.</span></span> <span data-ttu-id="e0d27-114">Kodda, Eventbuskbbitmq sınıfı, genel ıeventbus arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="e0d27-114">In the code, the EventBusRabbitMQ class implements the generic IEventBus interface.</span></span> <span data-ttu-id="e0d27-115">Bu, bu geliştirme/test sürümünden üretim sürümüne geçiş yapabilmeniz için bağımlılık ekleme tabanlıdır.</span><span class="sxs-lookup"><span data-stu-id="e0d27-115">This is based on Dependency Injection so that you can swap from this dev/test version to a production version.</span></span>

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
}
```

<span data-ttu-id="e0d27-116">Örnek bir geliştirme/test olay veri yolunun Kbbitmq uygulamasının ortak kodlamasıdır.</span><span class="sxs-lookup"><span data-stu-id="e0d27-116">The RabbitMQ implementation of a sample dev/test event bus is boilerplate code.</span></span> <span data-ttu-id="e0d27-117">Bu, kbbitmq sunucusuyla bağlantıyı işleymelidir ve sıralara bir ileti olayı yayımlamaya yönelik kod sağlar.</span><span class="sxs-lookup"><span data-stu-id="e0d27-117">It has to handle the connection to the RabbitMQ server and provide code for publishing a message event to the queues.</span></span> <span data-ttu-id="e0d27-118">Ayrıca, her olay türü için tümleştirme olay işleyicisi koleksiyonlarının bir sözlüğünü uygulamak gerekir; Bu olay türlerinde, Şekil 6-21 ' de gösterildiği gibi, her bir alıcı mikro hizmeti için farklı bir örnek oluşturma ve farklı abonelikler bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="e0d27-118">It also has to implement a dictionary of collections of integration event handlers for each event type; these event types can have a different instantiation and different subscriptions for each receiver microservice, as shown in Figure 6-21.</span></span>

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a><span data-ttu-id="e0d27-119">Kbbitmq ile basit bir yayımlama yöntemi uygulama</span><span class="sxs-lookup"><span data-stu-id="e0d27-119">Implementing a simple publish method with RabbitMQ</span></span>

<span data-ttu-id="e0d27-120">Aşağıdaki kod, tüm senaryoyu göstermek için, Kbbitmq için bir Event Bus uygulamasının ***Basitleştirilmiş*** bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="e0d27-120">The following code is a ***simplified*** version of an event bus implementation for RabbitMQ, to showcase the whole scenario.</span></span> <span data-ttu-id="e0d27-121">Bu şekilde bağlantıyı gerçekten işlemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0d27-121">You don't really handle the connection this way.</span></span> <span data-ttu-id="e0d27-122">Tam uygulamayı görmek için, [DotNet-Architecture/eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) deposundaki gerçek koda bakın.</span><span class="sxs-lookup"><span data-stu-id="e0d27-122">To see the full implementation, see the actual code in the [dotnet-architecture/eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) repository.</span></span>

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

<span data-ttu-id="e0d27-123">EShopOnContainers uygulamasındaki Publish yönteminin [gerçek kodu](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) bir [Polly](https://github.com/App-vNext/Polly) yeniden deneme ilkesi kullanılarak geliştirilmiştir ve bu da, kbbitmq kapsayıcısının hazırlanmadığından, görevi belirli sayıda kez yeniden dener.</span><span class="sxs-lookup"><span data-stu-id="e0d27-123">The [actual code](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) of the Publish method in the eShopOnContainers application is improved by using a [Polly](https://github.com/App-vNext/Polly) retry policy, which retries the task a certain number of times in case the RabbitMQ container is not ready.</span></span> <span data-ttu-id="e0d27-124">Docker-Compose kapsayıcıları başlattığında bu durum oluşabilir; Örneğin, Korbbitmq kapsayıcısı diğer kapsayıcılardan daha yavaş başlayabilir.</span><span class="sxs-lookup"><span data-stu-id="e0d27-124">This can occur when docker-compose is starting the containers; for example, the RabbitMQ container might start more slowly than the other containers.</span></span>

<span data-ttu-id="e0d27-125">Daha önce belirtildiği gibi, kbbitmq ' de birçok olası yapılandırma vardır, bu nedenle bu kod yalnızca geliştirme ve test ortamları için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e0d27-125">As mentioned earlier, there are many possible configurations in RabbitMQ, so this code should be used only for dev/test environments.</span></span>

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a><span data-ttu-id="e0d27-126">Kbbitmq API 'siyle abonelik kodunu uygulama</span><span class="sxs-lookup"><span data-stu-id="e0d27-126">Implementing the subscription code with the RabbitMQ API</span></span>

<span data-ttu-id="e0d27-127">Yayımlama kodunda olduğu gibi, aşağıdaki kod, kbbitmq için olay veri yolu uygulamasının bir kısmının basitleştirmesidir.</span><span class="sxs-lookup"><span data-stu-id="e0d27-127">As with the publish code, the following code is a simplification of part of the event bus implementation for RabbitMQ.</span></span> <span data-ttu-id="e0d27-128">Yine de, onu geliştirmediğiniz müddetçe genellikle değiştirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="e0d27-128">Again, you usually do not need to change it unless you are improving it.</span></span>

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

<span data-ttu-id="e0d27-129">Her olay türünün, kbıbitmq 'dan olayları almak için ilgili bir kanalı vardır.</span><span class="sxs-lookup"><span data-stu-id="e0d27-129">Each event type has a related channel to get events from RabbitMQ.</span></span> <span data-ttu-id="e0d27-130">Daha sonra, kanal başına çok sayıda olay işleyicisine ve gerektiğinde olay türüne sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0d27-130">You can then have as many event handlers per channel and event type as needed.</span></span>

<span data-ttu-id="e0d27-131">Subscribe yöntemi, geçerli mikro hizmette geri çağırma yöntemi ve ilgili ıntegrationevent nesnesi gibi bir ııntegrationeventhandler nesnesini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="e0d27-131">The Subscribe method accepts an IIntegrationEventHandler object, which is like a callback method in the current microservice, plus its related IntegrationEvent object.</span></span> <span data-ttu-id="e0d27-132">Kod daha sonra bu olay işleyicisini her bir tümleştirme olay türünün istemci mikro hizmeti başına sahip olduğu olay işleyicileri listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="e0d27-132">The code then adds that event handler to the list of event handlers that each integration event type can have per client microservice.</span></span> <span data-ttu-id="e0d27-133">İstemci kodu henüz olaya abone olunmamışsa, kod, olay türü için bir kanal oluşturur, böylece bu olay başka bir hizmetten yayımlandığında, bu olay bir anında iletme stilinde olayları alabilir.</span><span class="sxs-lookup"><span data-stu-id="e0d27-133">If the client code has not already been subscribed to the event, the code creates a channel for the event type so it can receive events in a push style from RabbitMQ when that event is published from any other service.</span></span>

<span data-ttu-id="e0d27-134">Yukarıda belirtildiği gibi, eShopOnContainers 'da uygulanan olay veri yolu yalnızca ve eğitim amacını içerir, bu nedenle üretim için hazırlanma.</span><span class="sxs-lookup"><span data-stu-id="e0d27-134">As mentioned above, the event bus implemented in eShopOnContainers has only and educational purpose, since it only handles the main scenarios, so it's not ready for production.</span></span>

<span data-ttu-id="e0d27-135">Üretim senaryolarında, aşağıdaki ek kaynakları, Kbbitmq için özel ve [mikro hizmetler arasında olay tabanlı Iletişim uygulama](./integration-event-based-microservice-communications.md#additional-resources) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e0d27-135">For production scenarios check the additional resources below, specific for RabbitMQ, and the [Implementing event-based communication between microservices](./integration-event-based-microservice-communications.md#additional-resources) section.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="e0d27-136">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="e0d27-136">Additional resources</span></span>

<span data-ttu-id="e0d27-137">Kbbitmq desteğiyle üretime Ready bir çözüm.</span><span class="sxs-lookup"><span data-stu-id="e0d27-137">A production-ready solution with support for RabbitMQ.</span></span>

- <span data-ttu-id="e0d27-138">**Easynetq** -Kbıbitmq \ Için açık kaynak .NET API istemcisi</span><span class="sxs-lookup"><span data-stu-id="e0d27-138">**EasyNetQ** - Open Source .NET API client for RabbitMQ \</span></span>
  <https://easynetq.com/>

- <span data-ttu-id="e0d27-139">**Masstransıya** </span><span class="sxs-lookup"><span data-stu-id="e0d27-139">**MassTransit** </span></span>\
  <https://masstransit-project.com/>
  
> [!div class="step-by-step"]
> <span data-ttu-id="e0d27-140">[Önceki](integration-event-based-microservice-communications.md) 
>  [Sonraki](subscribe-events.md)</span><span class="sxs-lookup"><span data-stu-id="e0d27-140">[Previous](integration-event-based-microservice-communications.md)
[Next](subscribe-events.md)</span></span>
