---
title: DDD ve CQRS desenleriyle bir mikro hizmetteki iş karmaşıklığını bağlayabileceğiniz
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | DDD ve CQRS desenleriyle bir mikro hizmetteki iş karmaşıklığını bağlayabileceğiniz
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/06/2018
ms.openlocfilehash: 1af53f8f37e516219767fdde49eb7da9927d9e29
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50182469"
---
# <a name="tackling-business-complexity-in-a-microservice-with-ddd-and-cqrs-patterns"></a><span data-ttu-id="7eb50-103">DDD ve CQRS desenleriyle bir mikro hizmetteki iş karmaşıklığını bağlayabileceğiniz</span><span class="sxs-lookup"><span data-stu-id="7eb50-103">Tackling Business Complexity in a Microservice with DDD and CQRS Patterns</span></span>

<span data-ttu-id="7eb50-104">*Her mikro hizmet ya da iş etki alanının anlama yansıtır sınırlanmış bağlam için bir etki alanı modeli tasarlayın.*</span><span class="sxs-lookup"><span data-stu-id="7eb50-104">*Design a domain model for each microservice or Bounded Context that reflects understanding of the business domain.*</span></span>

<span data-ttu-id="7eb50-105">Bu bölümde daha gelişmiş karmaşık alt sistemlerin üstesinden gerektiğinde uygulayan mikro hizmette veya etki alanı uzmanlarıyla durmaksızın değişen iş kuralları bilgisi türetilen mikro hizmetler ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7eb50-105">This section focuses on more advanced microservices that you implement when you need to tackle complex subsystems, or microservices derived from the knowledge of domain experts with ever-changing business rules.</span></span> <span data-ttu-id="7eb50-106">Bu bölümde kullanılan mimarisi desenleri, Şekil 9-1'de gösterildiği gibi etki alanı Odaklı Tasarım (DDD) ve yaklaşım, komut ve sorgu sorumluluğu ayrımı (CQRS) bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="7eb50-106">The architecture patterns used in this section are based on domain-driven design (DDD) and Command and Query Responsibility Segregation (CQRS) approaches, as illustrated in Figure 9-1.</span></span>

![](./media/image1.png)

<span data-ttu-id="7eb50-107">**Şekil 9-1**.</span><span class="sxs-lookup"><span data-stu-id="7eb50-107">**Figure 9-1**.</span></span> <span data-ttu-id="7eb50-108">Her mikro hizmet için iç mimari desenleri ve dış mikro hizmet mimarisi</span><span class="sxs-lookup"><span data-stu-id="7eb50-108">External microservice architecture versus internal architecture patterns for each microservice</span></span>

<span data-ttu-id="7eb50-109">Ancak, veri odaklı mikro hizmetler, bir ASP.NET Core Web API'si hizmeti uygulama veya Swashbuckle, Swagger meta verilerini nasıl sunacağınızı öğrenin gibi teknikler de DDD ile dahili olarak uygulanan daha gelişmiş mikro hizmetler için geçerli çoğu desenler.</span><span class="sxs-lookup"><span data-stu-id="7eb50-109">However, most of the techniques for data driven microservices, such as how to implement an ASP.NET Core Web API service or how to expose Swagger metadata with Swashbuckle, are also applicable to the more advanced microservices implemented internally with DDD patterns.</span></span> <span data-ttu-id="7eb50-110">Bu bölümde, önceki bölümlerde uzantısı çünkü daha önce açıklanan yöntemler çoğunu burada veya her türden bir mikro hizmet için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="7eb50-110">This section is an extension of the previous sections, because most of the practices explained earlier also apply here or for any kind of microservice.</span></span>

<span data-ttu-id="7eb50-111">Bu bölümde, ilk hizmetine başvuru uygulamada kullanılan Basitleştirilmiş CQRS desenleriyle ilgili ayrıntılar verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7eb50-111">This section first provides details on the simplified CQRS patterns used in the eShopOnContainers reference application.</span></span> <span data-ttu-id="7eb50-112">Daha sonra uygulamalarınızda yeniden kullanabilirsiniz ortak desenler bulmanıza olanak sağlamak DDD teknikleri genel bir bakış alırsınız.</span><span class="sxs-lookup"><span data-stu-id="7eb50-112">Later, you will get an overview of the DDD techniques that enable you to find common patterns that you can reuse in your applications.</span></span>

<span data-ttu-id="7eb50-113">DDD zengin için kaynaklar ile büyük bir konudur.</span><span class="sxs-lookup"><span data-stu-id="7eb50-113">DDD is a large topic with a rich set of resources for learning.</span></span> <span data-ttu-id="7eb50-114">Kitapları gibi ile başlayabilirsiniz [etki alanı Odaklı Tasarım](https://domainlanguage.com/ddd/) Eric Evans ve ek Materyaller Vaughn Vernon, Jimmy Nilsson, Greg Young, UDI Dahan, Jimmy Bogard ve diğer birçok DDD/CQRS uzmanlar tarafından.</span><span class="sxs-lookup"><span data-stu-id="7eb50-114">You can start with books like [Domain-Driven Design](https://domainlanguage.com/ddd/) by Eric Evans and additional materials from Vaughn Vernon, Jimmy Nilsson, Greg Young, Udi Dahan, Jimmy Bogard, and many other DDD/CQRS experts.</span></span> <span data-ttu-id="7eb50-115">Ancak çoğu, tüm konuşmaları, Beyaz Tahta kullanımı ve etki alanı uzmanlarıyla somut iş etki alanınızda oturumları modelleme DDD teknikleri uygulama hakkında bilgi edinmek denemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7eb50-115">But most of all you need to try to learn how to apply DDD techniques from the conversations, whiteboarding, and domain modeling sessions with the experts in your concrete business domain.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="7eb50-116">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="7eb50-116">Additional resources</span></span>

##### <a name="ddd-domain-driven-design"></a><span data-ttu-id="7eb50-117">DDD (etki alanı Odaklı Tasarım)</span><span class="sxs-lookup"><span data-stu-id="7eb50-117">DDD (Domain-Driven Design)</span></span>

-   <span data-ttu-id="7eb50-118">**Eric Evans. Etki alanı dil**
    [*https://domainlanguage.com/*](https://domainlanguage.com/)</span><span class="sxs-lookup"><span data-stu-id="7eb50-118">**Eric Evans. Domain Language**
[*https://domainlanguage.com/*](https://domainlanguage.com/)</span></span>

-   <span data-ttu-id="7eb50-119">**Martin Fowler. Etki alanı Odaklı Tasarım**
    [*https://martinfowler.com/tags/domain%20driven%20design.html*](https://martinfowler.com/tags/domain%20driven%20design.html)</span><span class="sxs-lookup"><span data-stu-id="7eb50-119">**Martin Fowler. Domain-Driven Design**
[*https://martinfowler.com/tags/domain%20driven%20design.html*](https://martinfowler.com/tags/domain%20driven%20design.html)</span></span>

-   <span data-ttu-id="7eb50-120">**Jimmy Bogard. Etki alanınızı güçlendirme: bir öncü**
    [*https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/*](https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/)</span><span class="sxs-lookup"><span data-stu-id="7eb50-120">**Jimmy Bogard. Strengthening your domain: a primer**
[*https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/*](https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/)</span></span>

##### <a name="ddd-books"></a><span data-ttu-id="7eb50-121">DDD kitaplar</span><span class="sxs-lookup"><span data-stu-id="7eb50-121">DDD books</span></span>

-   <span data-ttu-id="7eb50-122">**Eric Evans. Etki alanı Odaklı Tasarım: Yazılım kalbi karmaşıklığı bağlayabileceğiniz**
    [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span><span class="sxs-lookup"><span data-stu-id="7eb50-122">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software**
[*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span></span>

-   <span data-ttu-id="7eb50-123">**Eric Evans. Etki alanı Odaklı Tasarım başvurusu: Tanımları ve desen özetleri**
    [*https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/*](https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/)</span><span class="sxs-lookup"><span data-stu-id="7eb50-123">**Eric Evans. Domain-Driven Design Reference: Definitions and Pattern Summaries**
[*https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/*](https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/)</span></span>

-   <span data-ttu-id="7eb50-124">**Vaughn Vernon. Uygulama etki alanı Odaklı Tasarım**
    [*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)</span><span class="sxs-lookup"><span data-stu-id="7eb50-124">**Vaughn Vernon. Implementing Domain-Driven Design**
[*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)</span></span>

-   <span data-ttu-id="7eb50-125">**Vaughn Vernon. Etki alanı Odaklı Tasarım biçimlendirileceğini**
    [*https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/*](https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/)</span><span class="sxs-lookup"><span data-stu-id="7eb50-125">**Vaughn Vernon. Domain-Driven Design Distilled**
[*https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/*](https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/)</span></span>

-   <span data-ttu-id="7eb50-126">**Jimmy Nilsson. Etki alanı Odaklı Tasarım ve desenleri uygulama**
    [*https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/*](https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/)</span><span class="sxs-lookup"><span data-stu-id="7eb50-126">**Jimmy Nilsson. Applying Domain-Driven Design and Patterns**
[*https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/*](https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/)</span></span>

-   <span data-ttu-id="7eb50-127">**Cesar de la Torre. .NET ile N katmanlı etki alanı odaklı Mimari Kılavuzu**
    [*https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/*](https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/)</span><span class="sxs-lookup"><span data-stu-id="7eb50-127">**Cesar de la Torre. N-Layered Domain-Oriented Architecture Guide with .NET**
[*https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/*](https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/)</span></span>

-   <span data-ttu-id="7eb50-128">**Abel Avram ve Floyd Marinescu. Etki alanı tasarım hızla odaklı**
    [*https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/*](https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/)</span><span class="sxs-lookup"><span data-stu-id="7eb50-128">**Abel Avram and Floyd Marinescu. Domain-Driven Design Quickly**
[*https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/*](https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/)</span></span>

<span data-ttu-id="7eb50-129">DDD eğitim</span><span class="sxs-lookup"><span data-stu-id="7eb50-129">DDD training</span></span>

-   <span data-ttu-id="7eb50-130">**Julie Lerman ve Steve Smith. Etki alanı Odaklı Tasarım ile ilgili temel bilgiler**
    [*https://bit.ly/PS-DDD*](https://bit.ly/PS-DDD)</span><span class="sxs-lookup"><span data-stu-id="7eb50-130">**Julie Lerman and Steve Smith. Domain-Driven Design Fundamentals**
[*https://bit.ly/PS-DDD*](https://bit.ly/PS-DDD)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="7eb50-131">[Önceki](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md)
[İleri](apply-simplified-microservice-cqrs-ddd-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="7eb50-131">[Previous](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md)
[Next](apply-simplified-microservice-cqrs-ddd-patterns.md)</span></span>