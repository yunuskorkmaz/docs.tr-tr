---
title: "Olay tabanlı mikro (tümleştirme olayları) arasındaki iletişimi uygulama"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Olay tabanlı mikro (tümleştirme olayları) arasındaki iletişimi uygulama"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: bfa7a3b732c67b568f0d68b1811a1ce9bb336a7e
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="implementing-event-based-communication-between-microservices-integration-events"></a><span data-ttu-id="9fb53-104">Olay tabanlı mikro (tümleştirme olayları) arasındaki iletişimi uygulama</span><span class="sxs-lookup"><span data-stu-id="9fb53-104">Implementing event-based communication between microservices (integration events)</span></span>

<span data-ttu-id="9fb53-105">Olay tabanlı iletişim kullandığınızda, daha önce açıklandığı gibi bir mikro hizmet dikkat çekici bir şey olduğunda iş varlığı güncelleştirdiği gibi olduğunda bir olay yayımlar.</span><span class="sxs-lookup"><span data-stu-id="9fb53-105">As described earlier, when you use event-based communication, a microservice publishes an event when something notable happens, such as when it updates a business entity.</span></span> <span data-ttu-id="9fb53-106">Diğer mikro bu olaylarına abone olma.</span><span class="sxs-lookup"><span data-stu-id="9fb53-106">Other microservices subscribe to those events.</span></span> <span data-ttu-id="9fb53-107">Bir mikro hizmet bir olayı aldığında, daha fazla olay yayımlanmakta yol açabilecek kendi iş varlıklarını güncelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9fb53-107">When a microservice receives an event, it can update its own business entities, which might lead to more events being published.</span></span> <span data-ttu-id="9fb53-108">Bu yayımlama/abonelik sistem genellikle bir olay veri yolu uygulaması kullanılarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="9fb53-108">This publish/subscribe system is usually performed by using an implementation of an event bus.</span></span> <span data-ttu-id="9fb53-109">Olay veri yolu bir arabirim abone olma ve aboneliği olayları ve olayları yayımlamak için gereken API ile tasarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="9fb53-109">The event bus can be designed as an interface with the API needed to subscribe and unsubscribe to events and to publish events.</span></span> <span data-ttu-id="9fb53-110">İleti sırası veya zaman uyumsuz iletişim ve publish/subscribe modelini destekleyen bir hizmet veri yolu gibi tüm işlemler arası veya Mesajlaşma iletişim göre bir veya daha fazla uygulamaları da olabilir.</span><span class="sxs-lookup"><span data-stu-id="9fb53-110">It can also have one or more implementations based on any inter-process or messaging communication, such as a messaging queue or a service bus that supports asynchronous communication and a publish/subscribe model.</span></span>

<span data-ttu-id="9fb53-111">Olayları birden çok hizmet span iş işlemleri uygulamak üzere bu hizmetleri arasında nihai tutarlılık sağlayan kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9fb53-111">You can use events to implement business transactions that span multiple services, which gives you eventual consistency between those services.</span></span> <span data-ttu-id="9fb53-112">Sonuçta tutarlı bir işlem dağıtılmış işlemlerin bir dizi oluşur.</span><span class="sxs-lookup"><span data-stu-id="9fb53-112">An eventually consistent transaction consists of a series of distributed actions.</span></span> <span data-ttu-id="9fb53-113">Her bir eylemde mikro hizmet iş varlığı güncelleştirir ve bir sonraki eylem tetikleyen bir olay yayımlar.</span><span class="sxs-lookup"><span data-stu-id="9fb53-113">At each action, the microservice updates a business entity and publishes an event that triggers the next action.</span></span>

![](./media/image19.PNG)

<span data-ttu-id="9fb53-114">**Şekil 8-18**.</span><span class="sxs-lookup"><span data-stu-id="9fb53-114">**Figure 8-18**.</span></span> <span data-ttu-id="9fb53-115">Bir olay veri yoluna bağlı olay denetimli iletişim</span><span class="sxs-lookup"><span data-stu-id="9fb53-115">Event-driven communication based on an event bus</span></span>

<span data-ttu-id="9fb53-116">Bu bölümde, Şekil 8-18'de gösterildiği gibi bir genel olay veri yolu arabirimi kullanarak bu tür iletişim .NET ile nasıl uygulayabileceğiniz açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9fb53-116">This section describes how you can implement this type of communication with .NET by using a generic event bus interface, as shown in Figure 8-18.</span></span> <span data-ttu-id="9fb53-117">Her farklı teknoloji veya RabbitMQ, Azure Service Bus veya diğer üçüncü taraf açık kaynak veya ticari hizmet veri yolu gibi altyapısını kullanarak birden fazla olası uygulamaları vardır.</span><span class="sxs-lookup"><span data-stu-id="9fb53-117">There are multiple potential implementations, each using a different technology or infrastructure such as RabbitMQ, Azure Service Bus, or any other third-party open source or commercial service bus.</span></span>

## <a name="using-message-brokers-and-services-buses-for-production-systems"></a><span data-ttu-id="9fb53-118">İleti aracıları ve Hizmetleri yollarına üretim sistemleri için kullanma</span><span class="sxs-lookup"><span data-stu-id="9fb53-118">Using message brokers and services buses for production systems</span></span>

<span data-ttu-id="9fb53-119">Mimari bölümünde belirtildiği gibi soyut olay bus uygulamak için birden çok Mesajlaşma teknolojileri arasından seçim yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9fb53-119">As noted in the architecture section, you can choose from multiple messaging technologies for implementing your abstract event bus.</span></span> <span data-ttu-id="9fb53-120">Ancak, farklı düzeylerde bu teknolojilerdir.</span><span class="sxs-lookup"><span data-stu-id="9fb53-120">But these technologies are at different levels.</span></span> <span data-ttu-id="9fb53-121">Örneğin, Azure Service Bus, NServiceBus, MassTransit veya Brighter gibi ticari ürün daha düşük bir düzeye RabbitMQ, bir Mesajlaşma Aracısı taşıma altındadır.</span><span class="sxs-lookup"><span data-stu-id="9fb53-121">For instance, RabbitMQ, a messaging broker transport, is at a lower level than commercial products like Azure Service Bus, NServiceBus, MassTransit, or Brighter.</span></span> <span data-ttu-id="9fb53-122">Bu ürünler çoğunu RabbitMQ veya Azure Service Bus üzerinde çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="9fb53-122">Most of these products can work on top of either RabbitMQ or Azure Service Bus.</span></span> <span data-ttu-id="9fb53-123">Seçiminiz ürünün kaç özellikler ve ne kadar out-of--box ölçeklenebilirlik, uygulamanız için gereken bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="9fb53-123">Your choice of product depends on how many features and how much out-of-the-box scalability you need for your application.</span></span>

<span data-ttu-id="9fb53-124">Yalnızca bir olay veri yolu, kavram eShopOnContainers örnek olduğu gibi geliştirme ortamınız için uygulamak için bir kapsayıcı olarak çalışan RabbitMQ üstünde basit bir uygulama yeterli olabilir.</span><span class="sxs-lookup"><span data-stu-id="9fb53-124">For implementing just an event bus proof-of-concept for your development environment, as in the eShopOnContainers sample, a simple implementation on top of RabbitMQ running as a container might be enough.</span></span> <span data-ttu-id="9fb53-125">Ancak için kritik ve yüksek ölçeklenebilirlik gereken üretim sistemlerine değerlendirin ve Azure Service Bus hizmetini kullanmak olmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9fb53-125">But for mission-critical and production systems that need high scalability, you might want to evaluate and use Azure Service Bus.</span></span>

<span data-ttu-id="9fb53-126">Üst düzey soyutlamalar gerektirir ve daha zengin özellikleri ister [Sagas](https://docs.particular.net/nservicebus/sagas/) daha kolay, diğer ticari ve açık kaynak hizmeti yollarına NServiceBus, MassTransit, gibi Dağıtılmış Geliştirme yapmak uzun süre çalışan işlemleri ve Parlak değerlendirme değer var.</span><span class="sxs-lookup"><span data-stu-id="9fb53-126">If you require high-level abstractions and richer features like [Sagas](https://docs.particular.net/nservicebus/sagas/) for long-running processes that make distributed development easier, other commercial and open-source service buses like NServiceBus, MassTransit, and Brighter are worth evaluating.</span></span> <span data-ttu-id="9fb53-127">Bu durumda, soyutlamalar ve kullanmak için API genellikle doğrudan bu üst düzey hizmet yollarına kendi soyutlamalar yerine tarafından sağlanan olanları olur (gibi [eShopOnContainers sırasında sağlanan Basit olay bus soyutlamalar](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/BuildingBlocks/EventBus/EventBus/Abstractions/IEventBus.cs)).</span><span class="sxs-lookup"><span data-stu-id="9fb53-127">In this case, the abstractions and API to use would usually be directly the ones provided by those high-level service buses instead of your own abstractions (like the [simple event bus abstractions provided at eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/BuildingBlocks/EventBus/EventBus/Abstractions/IEventBus.cs)).</span></span> <span data-ttu-id="9fb53-128">Bu konular için ' ın, araştırma [çatallanmış NServiceBus kullanarak eShopOnContainers](http://go.particular.net/eShopOnContainers) (belirli yazılımı tarafından uygulanan ek türetilmiş örneği)</span><span class="sxs-lookup"><span data-stu-id="9fb53-128">For that matter, you can research the [forked eShopOnContainers using NServiceBus](http://go.particular.net/eShopOnContainers) (additional derived sample implemented by Particular Software)</span></span>

<span data-ttu-id="9fb53-129">Doğal olarak, her zaman kendi hizmet veri yolu özellikleri üzerinde alt düzey teknolojileri RabbitMQ ve Docker gibi oluşturabilirsiniz, ancak "tekerleği reinvent için" gereken çalışmayı özel Kurumsal uygulama için çok yüksek maliyetli olabilir.</span><span class="sxs-lookup"><span data-stu-id="9fb53-129">Of course, you could always build your own service bus features on top of lower-level technologies like RabbitMQ and Docker, but the work needed to “reinvent the wheel” might be too costly for a custom enterprise application.</span></span>

## <a name="integration-events"></a><span data-ttu-id="9fb53-130">Tümleştirme olayları</span><span class="sxs-lookup"><span data-stu-id="9fb53-130">Integration events</span></span>

<span data-ttu-id="9fb53-131">Tümleştirme olaylar, birden çok mikro veya dış sistemler arasında etki alanı durumu eşitlenmiş getirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9fb53-131">Integration events are used for bringing domain state in sync across multiple microservices or external systems.</span></span> <span data-ttu-id="9fb53-132">Bu tümleştirme olaylarını mikro hizmet dışında yayımlama tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="9fb53-132">This is done by publishing integration events outside the microservice.</span></span> <span data-ttu-id="9fb53-133">Bir olay (için tümleştirme olayına abone olarak sayıda mikro) birden çok alıcı mikro yayımlandığında, her alıcı mikro hizmet uygun olay işleyicisini olayını işler.</span><span class="sxs-lookup"><span data-stu-id="9fb53-133">When an event is published to multiple receiver microservices (to as many microservices as are subscribed to the integration event), the appropriate event handler in each receiver microservice handles the event.</span></span>

<span data-ttu-id="9fb53-134">Bir tümleştirme temelde aşağıdaki örnekteki gibi bir veri tutan sınıfı olaydır:</span><span class="sxs-lookup"><span data-stu-id="9fb53-134">An integration event is basically a data-holding class, as in the following example:</span></span>

```csharp
public class ProductPriceChangedIntegrationEvent : IntegrationEvent
{
    public int ProductId { get; private set; }
    public decimal NewPrice { get; private set; }
    public decimal OldPrice { get; private set; }

    public ProductPriceChangedIntegrationEvent(int productId, decimal newPrice,
        decimal oldPrice)
    {
        ProductId = productId;
        NewPrice = newPrice;
        OldPrice = oldPrice;
    }
}
```

<span data-ttu-id="9fb53-135">Bir şekilde nasıl ViewModels sunucu ve istemci tanımlanan için karşılaştırılabilir diğer mikro gelen ayrılmış şekilde tümleştirme olaylarını her mikro hizmet uygulama düzeyinde tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="9fb53-135">The integration events can be defined at the application level of each microservice, so they are decoupled from other microservices, in a way comparable to how ViewModels are defined in the server and client.</span></span> <span data-ttu-id="9fb53-136">Ne önerilmez ortak bir tümleştirme olayları kitaplık arasında birden çok mikro paylaşan; Bunu tek olay tanımı veri kitaplığı ile bu mikro Kuplaj.</span><span class="sxs-lookup"><span data-stu-id="9fb53-136">What is not recommended is sharing a common integration events library across multiple microservices; doing that would be coupling those microservices with a single event definition data library.</span></span> <span data-ttu-id="9fb53-137">Ortak etki alanı modeli birden çok mikro paylaşmak istediğiniz değil, aynı nedenleri için bunu yapmak istiyor musunuz: mikro tamamen otonom olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9fb53-137">You do not want to do that for the same reasons that you do not want to share a common domain model across multiple microservices: microservices must be completely autonomous.</span></span>

<span data-ttu-id="9fb53-138">Yalnızca birkaç tür mikro paylaşmalıdır kitaplıkları vardır.</span><span class="sxs-lookup"><span data-stu-id="9fb53-138">There are only a few kinds of libraries you should share across microservices.</span></span> <span data-ttu-id="9fb53-139">Son uygulama blokları gibi kitaplıkları biridir [olay Bus İstemcisi API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/BuildingBlocks/EventBus), eShopOnContainers gibi.</span><span class="sxs-lookup"><span data-stu-id="9fb53-139">One is libraries that are final application blocks, like the [Event Bus client API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/BuildingBlocks/EventBus), as in eShopOnContainers.</span></span> <span data-ttu-id="9fb53-140">Başka bir JSON serileştiricileri gibi bir NuGet bileşenler de paylaşım araçları oluşturan kitaplıkları olur.</span><span class="sxs-lookup"><span data-stu-id="9fb53-140">Another is libraries that constitute tools that could also be shared as NuGet components, like JSON serializers.</span></span>

## <a name="the-event-bus"></a><span data-ttu-id="9fb53-141">Olay veri yolu</span><span class="sxs-lookup"><span data-stu-id="9fb53-141">The event bus</span></span>

<span data-ttu-id="9fb53-142">Bir olay veri yoluna Şekil 8-19'gösterildiği gibi açıkça birbirinden farkında olması gereken bileşenleri gerektirmeden mikro Yayımla/abone-style iletişimine izin verir.</span><span class="sxs-lookup"><span data-stu-id="9fb53-142">An event bus allows publish/subscribe-style communication between microservices without requiring the components to explicitly be aware of each other, as shown in Figure 8-19.</span></span>

![](./media/image20.png)

<span data-ttu-id="9fb53-143">**Şekil 8-19**.</span><span class="sxs-lookup"><span data-stu-id="9fb53-143">**Figure 8-19**.</span></span> <span data-ttu-id="9fb53-144">Yayımlama/abonelik bir olay veri yoluna temel kavramları</span><span class="sxs-lookup"><span data-stu-id="9fb53-144">Publish/subscribe basics with an event bus</span></span>

<span data-ttu-id="9fb53-145">Olay bus gözlemci deseni ve yayımlama ile ilgili-düzeni abone olun.</span><span class="sxs-lookup"><span data-stu-id="9fb53-145">The event bus is related to the Observer pattern and the publish-subscribe pattern.</span></span>

### <a name="observer-pattern"></a><span data-ttu-id="9fb53-146">Gözlemci deseni</span><span class="sxs-lookup"><span data-stu-id="9fb53-146">Observer pattern</span></span>

<span data-ttu-id="9fb53-147">İçinde [gözlemci deseni](https://en.wikipedia.org/wiki/Observer_pattern), birincil nesnenizin (Observable da bilinir) ilgili bilgileri (olayları) (Gözlemcilerin da bilinir) diğer ilgilendiğiniz nesneleri bildirir.</span><span class="sxs-lookup"><span data-stu-id="9fb53-147">In the [Observer pattern](https://en.wikipedia.org/wiki/Observer_pattern), your primary object (known as the Observable) notifies other interested objects (known as Observers) with relevant information (events).</span></span>

### <a name="publish-subscribe-pubsub-pattern"></a><span data-ttu-id="9fb53-148">Yayımlama-abone olma (Pub/alt) düzeni</span><span class="sxs-lookup"><span data-stu-id="9fb53-148">Publish-subscribe (Pub/Sub) pattern</span></span> 

<span data-ttu-id="9fb53-149">Amacı [Pub/alt düzeni](https://msdn.microsoft.com/en-us/library/ff649664.aspx) gözlemci deseni ile aynıdır: belirli olaylar gerçekleştiğinde diğer hizmetler bildirmek istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="9fb53-149">The purpose of the [Pub/Sub pattern](https://msdn.microsoft.com/en-us/library/ff649664.aspx) is the same as the Observer pattern: you want to notify other services when certain events take place.</span></span> <span data-ttu-id="9fb53-150">Ancak gözlemci ve Pub/alt desenleri arasında önemli bir fark yoktur.</span><span class="sxs-lookup"><span data-stu-id="9fb53-150">But there is an important difference between the Observer and Pub/Sub patterns.</span></span> <span data-ttu-id="9fb53-151">Bunlar "birbirine bilmesi" gözlemci deseninde yayın gözlemcilerin için doğrudan observable gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="9fb53-151">In the observer pattern, the broadcast is performed directly from the observable to the observers, so they “know” each other.</span></span> <span data-ttu-id="9fb53-152">Ancak Pub/alt düzeni kullanırken yayımcı ve abone tarafından bilinen aracısı veya ileti aracısı veya olay veri yolu, adlı üçüncü bir bileşen yok.</span><span class="sxs-lookup"><span data-stu-id="9fb53-152">But when using a Pub/Sub pattern, there is a third component, called broker or message broker or event bus, which is known by both the publisher and subscriber.</span></span> <span data-ttu-id="9fb53-153">Bu nedenle, Pub/alt düzeni kullanırken, yayımcı ve aboneleri tam olarak belirtilen olay veri yolu veya ileti Aracısı sayesinde birbirinden ayrılır.</span><span class="sxs-lookup"><span data-stu-id="9fb53-153">Therefore, when using the Pub/Sub pattern the publisher and the subscribers are precisely decoupled thanks to the mentioned event bus or message broker.</span></span>

### <a name="the-middleman-or-event-bus"></a><span data-ttu-id="9fb53-154">Middleman veya olay veri yolu</span><span class="sxs-lookup"><span data-stu-id="9fb53-154">The middleman or event bus</span></span> 

<span data-ttu-id="9fb53-155">Gizlilik yayımcısı ile abone arasında nasıl elde?</span><span class="sxs-lookup"><span data-stu-id="9fb53-155">How do you achieve anonymity between publisher and subscriber?</span></span> <span data-ttu-id="9fb53-156">Tüm iletişimi dikkatli bir middleman izin kolay yoludur.</span><span class="sxs-lookup"><span data-stu-id="9fb53-156">An easy way is let a middleman take care of all the communication.</span></span> <span data-ttu-id="9fb53-157">Bir olay veri yoluna bir middleman ' dir.</span><span class="sxs-lookup"><span data-stu-id="9fb53-157">An event bus is one such middleman.</span></span>

<span data-ttu-id="9fb53-158">Bir olay veri yoluna genellikle iki bölümden oluşur:</span><span class="sxs-lookup"><span data-stu-id="9fb53-158">An event bus is typically composed of two parts:</span></span>

-   <span data-ttu-id="9fb53-159">Özet veya arabirim.</span><span class="sxs-lookup"><span data-stu-id="9fb53-159">The abstraction or interface.</span></span>

-   <span data-ttu-id="9fb53-160">Bir veya daha fazla uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="9fb53-160">One or more implementations.</span></span>

<span data-ttu-id="9fb53-161">Şekil 8-19'nasıl, bir uygulama açısından bakıldığında, olay bus Pub/alt kanal'den fazla bir şey olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9fb53-161">In Figure 8-19 you can see how, from an application point of view, the event bus is nothing more than a Pub/Sub channel.</span></span> <span data-ttu-id="9fb53-162">Bu zaman uyumsuz iletişim uygulamak şekilde farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="9fb53-162">The way you implement this asynchronous communication can vary.</span></span> <span data-ttu-id="9fb53-163">Böylece, aralarında ortamı gereksinimlerini (örneğin, geliştirme ortamları ve üretim) bağlı olarak takas edebilirsiniz birden fazla uygulaması olabilir.</span><span class="sxs-lookup"><span data-stu-id="9fb53-163">It can have multiple implementations so that you can swap between them, depending on the environment requirements (for example, production versus development environments).</span></span>

<span data-ttu-id="9fb53-164">Şekil 8-20 olarak RabbitMQ, Azure Service Bus veya diğer olay/ileti aracısı gibi teknolojileri Mesajlaşma altyapısı göre birden çok uygulamalarıyla birlikte bir olay veri yolu için bir Özet görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9fb53-164">In Figure 8-20 you can see an abstraction of an event bus with multiple implementations based on infrastructure messaging technologies like RabbitMQ, Azure Service Bus, or other event/message broker.</span></span> 

![](./media/image21.png)

<span data-ttu-id="9fb53-165">**Şekil 8 - 20.**</span><span class="sxs-lookup"><span data-stu-id="9fb53-165">**Figure 8- 20.**</span></span> <span data-ttu-id="9fb53-166">Birden çok olay veri yolu uygulamaları</span><span class="sxs-lookup"><span data-stu-id="9fb53-166">Multiple implementations of an event bus</span></span>

<span data-ttu-id="9fb53-167">Ancak ve daha önce açıklanan olarak kendi soyutlamalar (olay veri yolu arabirimi) kullanarak yalnızca temel olay bus özelliklerini, soyutlamalar tarafından desteklenen gerekiyorsa iyi olur.</span><span class="sxs-lookup"><span data-stu-id="9fb53-167">However, and as mentioned previously, using your own abstractions (the event bus interface) is good only if you need basic event bus features supported by your abstractions.</span></span> <span data-ttu-id="9fb53-168">Daha zengin service bus özelliklerini gerekiyorsa, API ve kendi soyutlamalar yerine, tercih edilen ticari hizmet veri yolu tarafından sağlanan soyutlamalar büyük olasılıkla kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9fb53-168">If you need richer service bus features, you should probably use the API and abstractions provided by your preferred commercial service bus instead of your own abstractions.</span></span> 

### <a name="defining-an-event-bus-interface"></a><span data-ttu-id="9fb53-169">Bir olay veri yolu arabirimi tanımlama</span><span class="sxs-lookup"><span data-stu-id="9fb53-169">Defining an event bus interface</span></span>

<span data-ttu-id="9fb53-170">Olay veri yolu arabirimi için bazı uygulama kodu ve araştırması amacıyla olası uygulamaları ile başlayalım tıklatın.</span><span class="sxs-lookup"><span data-stu-id="9fb53-170">Let’s start with some implementation code for the event bus interface and possible implementations for exploration purposes.</span></span> <span data-ttu-id="9fb53-171">Arabirim genel ve aşağıdaki arabirimi olduğu gibi kolay olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9fb53-171">The interface should be generic and straightforward, as in the following interface.</span></span>

```csharp
public interface IEventBus
{
    void Publish(IntegrationEvent @event);

    void Subscribe<T, TH>()
        where T : IntegrationEvent
        where TH : IIntegrationEventHandler<T>;

    void SubscribeDynamic<TH>(string eventName)
        where TH : IDynamicIntegrationEventHandler;

    void UnsubscribeDynamic<TH>(string eventName)
        where TH : IDynamicIntegrationEventHandler;

    void Unsubscribe<T, TH>()
        where TH : IIntegrationEventHandler<T>
        where T : IntegrationEvent;
}
```

<span data-ttu-id="9fb53-172">`Publish` Yöntemdir kolay.</span><span class="sxs-lookup"><span data-stu-id="9fb53-172">The `Publish` method is straightforward.</span></span> <span data-ttu-id="9fb53-173">Olay bus herhangi mikro hizmet ya da bu olaya abone bile bir dış uygulamaya geçirilen tümleştirme olay yayın.</span><span class="sxs-lookup"><span data-stu-id="9fb53-173">The event bus will broadcast the integration event passed to it to any microservice, or even an external application, subscribed to that event.</span></span> <span data-ttu-id="9fb53-174">Bu yöntem, olay yayımlama mikro hizmet tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9fb53-174">This method is used by the microservice that is publishing the event.</span></span>

<span data-ttu-id="9fb53-175">`Subscribe` (Bağımsız değişkenler bağlı olarak çeşitli uygulamalarını olabilir) yöntemleri, olayları almak istediğiniz mikro tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9fb53-175">The `Subscribe` methods (you can have several implementations depending on the arguments) are used by the microservices that want to receive events.</span></span> <span data-ttu-id="9fb53-176">Bu yöntem, iki bağımsız değişkenlere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="9fb53-176">This method has two arguments.</span></span> <span data-ttu-id="9fb53-177">İlk abone olmak için tümleştirme olaydır (`IntegrationEvent`).</span><span class="sxs-lookup"><span data-stu-id="9fb53-177">The first is the integration event to subscribe to (`IntegrationEvent`).</span></span> <span data-ttu-id="9fb53-178">Tümleştirme olay işleyicisi (veya geri çağırma yöntemi) adlı ikinci bağımsız değişkeni olan `IIntegrationEventHandler<T>`, alıcı mikro hizmet Bu tümleştirme olay iletisi aldığında gerçekleştirilecek.</span><span class="sxs-lookup"><span data-stu-id="9fb53-178">The second argument is the integration event handler (or callback method), named `IIntegrationEventHandler<T>`, to be executed when the receiver microservice gets that integration event message.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="9fb53-179">[Önceki] (veritabanı-server-container.md) [sonraki] (rabbitmq-event-bus-development-test-environment.md)</span><span class="sxs-lookup"><span data-stu-id="9fb53-179">[Previous] (database-server-container.md) [Next] (rabbitmq-event-bus-development-test-environment.md)</span></span>
