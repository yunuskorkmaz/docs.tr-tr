---
title: "Mikro hizmet DDD ve CQRS desenler ile iş karmaşıklığı tackling"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Mikro hizmet DDD ve CQRS desenler ile iş karmaşıklığı tackling"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: be2d8a2fd77d65b82574efde3b9922a1176ad2f2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="tackling-business-complexity-in-a-microservice-with-ddd-and-cqrs-patterns"></a><span data-ttu-id="f29d4-104">Mikro hizmet DDD ve CQRS desenler ile iş karmaşıklığı tackling</span><span class="sxs-lookup"><span data-stu-id="f29d4-104">Tackling Business Complexity in a Microservice with DDD and CQRS Patterns</span></span>

<span data-ttu-id="f29d4-105">*Her mikro hizmet veya iş etki alanının anlama yansıtır ilişkisindeki bağlamı için bir etki alanı modeli tasarlayın.*</span><span class="sxs-lookup"><span data-stu-id="f29d4-105">*Design a domain model for each microservice or Bounded Context that reflects understanding of the business domain.*</span></span>

<span data-ttu-id="f29d4-106">Bu bölümde daha gelişmiş karmaşık alt sistemleri üstesinden gelmek gerektiğinde uygulayan mikro veya sürekli değişen iş kuralları etki alanı uzmanlarıyla bilgi türetilmiş mikro odaklanır.</span><span class="sxs-lookup"><span data-stu-id="f29d4-106">This section focuses on more advanced microservices that you implement when you need to tackle complex subsystems, or microservices derived from the knowledge of domain experts with ever-changing business rules.</span></span> <span data-ttu-id="f29d4-107">Bu bölümde kullanılan mimarisi desenleri etki alanı Odaklı Tasarım (DDD) ve komut ve sorgu sorumluluk ayrımı (CQRS) yaklaşım, Şekil 9-1'de gösterildiği gibi temel alır.</span><span class="sxs-lookup"><span data-stu-id="f29d4-107">The architecture patterns used in this section are based on domain-driven design (DDD) and Command and Query Responsibility Segregation (CQRS) approaches, as illustrated in Figure 9-1.</span></span>

![](./media/image1.png)

<span data-ttu-id="f29d4-108">**Şekil 9-1**.</span><span class="sxs-lookup"><span data-stu-id="f29d4-108">**Figure 9-1**.</span></span> <span data-ttu-id="f29d4-109">Her mikro hizmet için iç mimari desenleri karşı dış mikro hizmet mimarisi</span><span class="sxs-lookup"><span data-stu-id="f29d4-109">External microservice architecture versus internal architecture patterns for each microservice</span></span>

<span data-ttu-id="f29d4-110">Ancak, bir ASP.NET çekirdek Web API hizmeti uygulama veya Swashbuckle, Swagger meta verilerini kullanıma sunmak nasıl gibi mikro verilerle teknikleri de dahili DDD ile uygulanan daha gelişmiş mikro uygulanabilir çoğu desenler.</span><span class="sxs-lookup"><span data-stu-id="f29d4-110">However, most of the techniques for data driven microservices, such as how to implement an ASP.NET Core Web API service or how to expose Swagger metadata with Swashbuckle, are also applicable to the more advanced microservices implemented internally with DDD patterns.</span></span> <span data-ttu-id="f29d4-111">Bu bölümde önceki bölümlerde uzantısı çünkü daha önce açıklanan uygulamalarının çoğu burada veya mikro hizmet herhangi bir tür için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f29d4-111">This section is an extension of the previous sections, because most of the practices explained earlier also apply here or for any kind of microservice.</span></span>

<span data-ttu-id="f29d4-112">Bu bölümde ilk eShopOnContainers başvuru uygulamada kullanılan Basitleştirilmiş CQRS desenleri ayrıntıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="f29d4-112">This section first provides details on the simplified CQRS patterns used in the eShopOnContainers reference application.</span></span> <span data-ttu-id="f29d4-113">Daha sonra uygulamalarınızda yeniden kullanabilirsiniz ortak desenler bulmak etkinleştirmeniz DDD teknikleri genel bir bakış alırsınız.</span><span class="sxs-lookup"><span data-stu-id="f29d4-113">Later, you will get an overview of the DDD techniques that enable you to find common patterns that you can reuse in your applications.</span></span>

<span data-ttu-id="f29d4-114">GGG, zengin bir bilgi edinme kaynakları ile büyük bir konudur.</span><span class="sxs-lookup"><span data-stu-id="f29d4-114">DDD is a large topic with a rich set of resources for learning.</span></span> <span data-ttu-id="f29d4-115">Gibi kitaplarıyla başlatabilirsiniz [Domain-Driven tasarım](https://domainlanguage.com/ddd/) Eric Evans ve ek malzemeleri Vaughn Vernon, Jimmy Nilsson, Greg Young, UDI Dahan, Jimmy Bogard ve diğer birçok DDD/CQRS uzmanlar tarafından.</span><span class="sxs-lookup"><span data-stu-id="f29d4-115">You can start with books like [Domain-Driven Design](https://domainlanguage.com/ddd/) by Eric Evans and additional materials from Vaughn Vernon, Jimmy Nilsson, Greg Young, Udi Dahan, Jimmy Bogard, and many other DDD/CQRS experts.</span></span> <span data-ttu-id="f29d4-116">Ancak, tüm çoğunu görüşmeleri, whiteboarding ve etki alanı somut iş etki alanınızdaki uzmanlarla oturumları modelleme DDD teknikleri uygulamak öğrenmek denemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f29d4-116">But most of all you need to try to learn how to apply DDD techniques from the conversations, whiteboarding, and domain modeling sessions with the experts in your concrete business domain.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="f29d4-117">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="f29d4-117">Additional resources</span></span>

##### <a name="ddd-domain-driven-design"></a><span data-ttu-id="f29d4-118">DDD (etki alanı tabanlı tasarım)</span><span class="sxs-lookup"><span data-stu-id="f29d4-118">DDD (Domain-Driven Design)</span></span>

-   <span data-ttu-id="f29d4-119">**Eric Evans. Etki alanı dil**
    [*http://domainlanguage.com/*](http://domainlanguage.com/)</span><span class="sxs-lookup"><span data-stu-id="f29d4-119">**Eric Evans. Domain Language**
[*http://domainlanguage.com/*](http://domainlanguage.com/)</span></span>

-   <span data-ttu-id="f29d4-120">**Martin Fowler. Etki alanı tabanlı tasarım**
    [*http://martinfowler.com/tags/domain%20driven%20design.html*](http://martinfowler.com/tags/domain%20driven%20design.html)</span><span class="sxs-lookup"><span data-stu-id="f29d4-120">**Martin Fowler. Domain-Driven Design**
[*http://martinfowler.com/tags/domain%20driven%20design.html*](http://martinfowler.com/tags/domain%20driven%20design.html)</span></span>

-   <span data-ttu-id="f29d4-121">**Jimmy Bogard. Etki alanınızı güçlendirme: öncü**
    [*https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/*](https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/)</span><span class="sxs-lookup"><span data-stu-id="f29d4-121">**Jimmy Bogard. Strengthening your domain: a primer**
[*https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/*](https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/)</span></span>

##### <a name="ddd-books"></a><span data-ttu-id="f29d4-122">DDD defterleri</span><span class="sxs-lookup"><span data-stu-id="f29d4-122">DDD books</span></span>

-   <span data-ttu-id="f29d4-123">**Eric Evans. Etki alanı Odaklı Tasarım: Yazılım Kalp karmaşıklığı Tackling**
    [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span><span class="sxs-lookup"><span data-stu-id="f29d4-123">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software**
[*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span></span>

-   <span data-ttu-id="f29d4-124">**Eric Evans. Etki alanı Odaklı Tasarım başvuru: Tanımları ve desen özetleri**
    [*https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/*](https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/)</span><span class="sxs-lookup"><span data-stu-id="f29d4-124">**Eric Evans. Domain-Driven Design Reference: Definitions and Pattern Summaries**
[*https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/*](https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/)</span></span>

-   <span data-ttu-id="f29d4-125">**Vaughn Vernon. Etki alanı tabanlı tasarımı uygulama**
    [*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)</span><span class="sxs-lookup"><span data-stu-id="f29d4-125">**Vaughn Vernon. Implementing Domain-Driven Design**
[*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)</span></span>

-   <span data-ttu-id="f29d4-126">**Vaughn Vernon. Etki alanı tabanlı biçimlendirileceğini tasarım**
    [*https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/*](https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/)</span><span class="sxs-lookup"><span data-stu-id="f29d4-126">**Vaughn Vernon. Domain-Driven Design Distilled**
[*https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/*](https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/)</span></span>

-   <span data-ttu-id="f29d4-127">**Jimmy Nilsson. Etki alanı Odaklı Tasarım ve desenleri uygulama**
    [*https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/*](https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/)</span><span class="sxs-lookup"><span data-stu-id="f29d4-127">**Jimmy Nilsson. Applying Domain-Driven Design and Patterns**
[*https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/*](https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/)</span></span>

-   <span data-ttu-id="f29d4-128">**Cesar de la Torre. .NET ile N katmanlı etki alanı odaklı Mimari Kılavuzu**
    [*https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/*](https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/)</span><span class="sxs-lookup"><span data-stu-id="f29d4-128">**Cesar de la Torre. N-Layered Domain-Oriented Architecture Guide with .NET**
[*https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/*](https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/)</span></span>

-   <span data-ttu-id="f29d4-129">**Abel Avram ve Floyd Marinescu. Etki alanı tasarım hızla temelli**
    [*https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/*](https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/)</span><span class="sxs-lookup"><span data-stu-id="f29d4-129">**Abel Avram and Floyd Marinescu. Domain-Driven Design Quickly**
[*https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/*](https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/)</span></span>

<span data-ttu-id="f29d4-130">DDD eğitim</span><span class="sxs-lookup"><span data-stu-id="f29d4-130">DDD training</span></span>

-   <span data-ttu-id="f29d4-131">**Julie Lerman ve Steve Smith. Etki alanı tabanlı tasarım Temelleri**
    [*http://bit.ly/PS-DDD*](http://bit.ly/PS-DDD)</span><span class="sxs-lookup"><span data-stu-id="f29d4-131">**Julie Lerman and Steve Smith. Domain-Driven Design Fundamentals**
[*http://bit.ly/PS-DDD*](http://bit.ly/PS-DDD)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="f29d4-132">[Önceki] (.. / multi-container-microservice-net-applications/test-aspnet-core-services-web-apps.md) [sonraki] (apply-simplified-microservice-cqrs-ddd-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="f29d4-132">[Previous] (../multi-container-microservice-net-applications/test-aspnet-core-services-web-apps.md) [Next] (apply-simplified-microservice-cqrs-ddd-patterns.md)</span></span>
