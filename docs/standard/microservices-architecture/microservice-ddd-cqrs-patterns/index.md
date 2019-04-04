---
title: DDD ve CQRS desenleriyle bir mikro hizmetteki iş karmaşıklığını bağlayabileceğiniz
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Nasıl başa çıkabileceğiniz DDD ve CQRS desenleriyle uygulama karmaşık iş senaryolarını anlama
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: 8f2297121429acad4222f72ac4fea54e8469b215
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2019
ms.locfileid: "58464677"
---
# <a name="tackle-business-complexity-in-a-microservice-with-ddd-and-cqrs-patterns"></a><span data-ttu-id="6d7f8-103">Başa çıkmaya iş karmaşıklığını DDD ve CQRS desenleriyle bir mikro hizmetteki</span><span class="sxs-lookup"><span data-stu-id="6d7f8-103">Tackle Business Complexity in a Microservice with DDD and CQRS Patterns</span></span>

<span data-ttu-id="6d7f8-104">*Her mikro hizmet ya da iş etki alanının anlama yansıtır sınırlanmış bağlam için bir etki alanı modeli tasarlayın.*</span><span class="sxs-lookup"><span data-stu-id="6d7f8-104">*Design a domain model for each microservice or Bounded Context that reflects understanding of the business domain.*</span></span>

<span data-ttu-id="6d7f8-105">Bu bölümde daha gelişmiş karmaşık alt sistemlerin üstesinden gerektiğinde uygulayan mikro hizmette veya etki alanı uzmanlarıyla durmaksızın değişen iş kuralları bilgisi türetilen mikro hizmetler ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6d7f8-105">This section focuses on more advanced microservices that you implement when you need to tackle complex subsystems, or microservices derived from the knowledge of domain experts with ever-changing business rules.</span></span> <span data-ttu-id="6d7f8-106">Bu bölümde kullanılan mimarisi desenleri, Şekil 7-1'de gösterildiği gibi etki alanı Odaklı Tasarım (DDD) ve yaklaşım, komut ve sorgu sorumluluğu ayrımı (CQRS) bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="6d7f8-106">The architecture patterns used in this section are based on domain-driven design (DDD) and Command and Query Responsibility Segregation (CQRS) approaches, as illustrated in Figure 7-1.</span></span>

![Dış mimarisi arasındaki fark: mikro hizmet desenleri, API ağ geçitleri, dayanıklı iletişimleri, yayımlama/abonelik, vb. ve iç mimarisi: veri temelli/CRUD DDD deseni, bağımlılık ekleme, birden çok kitaplıkları, vs.](./media/image1.png)

<span data-ttu-id="6d7f8-108">**Şekil 7-1**.</span><span class="sxs-lookup"><span data-stu-id="6d7f8-108">**Figure 7-1**.</span></span> <span data-ttu-id="6d7f8-109">Her mikro hizmet için iç mimari desenleri ve dış mikro hizmet mimarisi</span><span class="sxs-lookup"><span data-stu-id="6d7f8-109">External microservice architecture versus internal architecture patterns for each microservice</span></span>

<span data-ttu-id="6d7f8-110">Ancak, veri odaklı mikro hizmetler, bir ASP.NET Core Web API'si hizmeti uygulama veya Swashbuckle veya NSwag, Swagger meta verileri nasıl sunacağınızı öğrenin gibi teknikler de ile dahili olarak uygulanan daha gelişmiş mikro hizmetler için uygulanabilir çoğu DDD deseni.</span><span class="sxs-lookup"><span data-stu-id="6d7f8-110">However, most of the techniques for data driven microservices, such as how to implement an ASP.NET Core Web API service or how to expose Swagger metadata with Swashbuckle or NSwag, are also applicable to the more advanced microservices implemented internally with DDD patterns.</span></span> <span data-ttu-id="6d7f8-111">Bu bölümde, önceki bölümlerde uzantısı çünkü daha önce açıklanan yöntemler çoğunu burada veya her türden bir mikro hizmet için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6d7f8-111">This section is an extension of the previous sections, because most of the practices explained earlier also apply here or for any kind of microservice.</span></span>

<span data-ttu-id="6d7f8-112">Bu bölümde, ilk hizmetine başvuru uygulamada kullanılan Basitleştirilmiş CQRS desenleriyle ilgili ayrıntılar verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6d7f8-112">This section first provides details on the simplified CQRS patterns used in the eShopOnContainers reference application.</span></span> <span data-ttu-id="6d7f8-113">Daha sonra uygulamalarınızda yeniden kullanabilirsiniz ortak desenler bulmanıza olanak sağlamak DDD teknikleri genel bir bakış alırsınız.</span><span class="sxs-lookup"><span data-stu-id="6d7f8-113">Later, you will get an overview of the DDD techniques that enable you to find common patterns that you can reuse in your applications.</span></span>

<span data-ttu-id="6d7f8-114">DDD zengin için kaynaklar ile büyük bir konudur.</span><span class="sxs-lookup"><span data-stu-id="6d7f8-114">DDD is a large topic with a rich set of resources for learning.</span></span> <span data-ttu-id="6d7f8-115">Kitapları gibi ile başlayabilirsiniz [etki alanı Odaklı Tasarım](https://domainlanguage.com/ddd/) Eric Evans ve ek Materyaller Vaughn Vernon, Jimmy Nilsson, Greg Young, UDI Dahan, Jimmy Bogard ve diğer birçok DDD/CQRS uzmanlar tarafından.</span><span class="sxs-lookup"><span data-stu-id="6d7f8-115">You can start with books like [Domain-Driven Design](https://domainlanguage.com/ddd/) by Eric Evans and additional materials from Vaughn Vernon, Jimmy Nilsson, Greg Young, Udi Dahan, Jimmy Bogard, and many other DDD/CQRS experts.</span></span> <span data-ttu-id="6d7f8-116">Ancak çoğu, tüm konuşmaları, Beyaz Tahta kullanımı ve etki alanı uzmanlarıyla somut iş etki alanınızda oturumları modelleme DDD teknikleri uygulama hakkında bilgi edinmek denemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6d7f8-116">But most of all you need to try to learn how to apply DDD techniques from the conversations, whiteboarding, and domain modeling sessions with the experts in your concrete business domain.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="6d7f8-117">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="6d7f8-117">Additional resources</span></span>

##### <a name="ddd-domain-driven-design"></a><span data-ttu-id="6d7f8-118">DDD (etki alanı Odaklı Tasarım)</span><span class="sxs-lookup"><span data-stu-id="6d7f8-118">DDD (Domain-Driven Design)</span></span>

- <span data-ttu-id="6d7f8-119">**Eric Evans. Etki alanı dil** \\</span><span class="sxs-lookup"><span data-stu-id="6d7f8-119">**Eric Evans. Domain Language** \\</span></span>
  [https://domainlanguage.com/](https://domainlanguage.com/)

- <span data-ttu-id="6d7f8-120">**Martin Fowler. Etki alanı Odaklı Tasarım** \\</span><span class="sxs-lookup"><span data-stu-id="6d7f8-120">**Martin Fowler. Domain-Driven Design** \\</span></span>
  [https://martinfowler.com/tags/domain%20driven%20design.html](https://martinfowler.com/tags/domain%20driven%20design.html)

- <span data-ttu-id="6d7f8-121">**Jimmy Bogard. Etki alanınızı güçlendirme: bir öncü** \\</span><span class="sxs-lookup"><span data-stu-id="6d7f8-121">**Jimmy Bogard. Strengthening your domain: a primer** \\</span></span>
  [https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/](https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/)

##### <a name="ddd-books"></a><span data-ttu-id="6d7f8-122">DDD kitaplar</span><span class="sxs-lookup"><span data-stu-id="6d7f8-122">DDD books</span></span>

- <span data-ttu-id="6d7f8-123">**Eric Evans. Etki alanı Odaklı Tasarım: Yazılım kalbi kuruluşlarda karmaşıklığı** \\</span><span class="sxs-lookup"><span data-stu-id="6d7f8-123">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software** \\</span></span>
  [https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)

- <span data-ttu-id="6d7f8-124">**Eric Evans. Etki alanı Odaklı Tasarım başvurusu: Tanımları ve desen özetleri** \\</span><span class="sxs-lookup"><span data-stu-id="6d7f8-124">**Eric Evans. Domain-Driven Design Reference: Definitions and Pattern Summaries** \\</span></span>
  [https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/](https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/)

- <span data-ttu-id="6d7f8-125">**Vaughn Vernon. Uygulama etki alanı Odaklı Tasarım** \\</span><span class="sxs-lookup"><span data-stu-id="6d7f8-125">**Vaughn Vernon. Implementing Domain-Driven Design** \\</span></span>
  [https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)

- <span data-ttu-id="6d7f8-126">**Vaughn Vernon. Etki alanı Odaklı Tasarım biçimlendirileceğini** \\</span><span class="sxs-lookup"><span data-stu-id="6d7f8-126">**Vaughn Vernon. Domain-Driven Design Distilled** \\</span></span>
  [https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/](https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/)

- <span data-ttu-id="6d7f8-127">**Jimmy Nilsson. Etki alanı Odaklı Tasarım ve desenleri uygulama** \\</span><span class="sxs-lookup"><span data-stu-id="6d7f8-127">**Jimmy Nilsson. Applying Domain-Driven Design and Patterns** \\</span></span>
  [https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/](https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/)

- <span data-ttu-id="6d7f8-128">**Cesar de la Torre. .NET ile N katmanlı etki alanı odaklı Mimari Kılavuzu** \\</span><span class="sxs-lookup"><span data-stu-id="6d7f8-128">**Cesar de la Torre. N-Layered Domain-Oriented Architecture Guide with .NET** \\</span></span>
  [https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/](https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/)

- <span data-ttu-id="6d7f8-129">**Abel Avram ve Floyd Marinescu. Etki alanı tasarım hızla odaklı** \\</span><span class="sxs-lookup"><span data-stu-id="6d7f8-129">**Abel Avram and Floyd Marinescu. Domain-Driven Design Quickly** \\</span></span>
  [https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/](https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/)

- <span data-ttu-id="6d7f8-130">**Scott Millett, Nick ayarlama - desenleri, prensipleri ve etki alanı Odaklı Tasarım yöntemleri** \\</span><span class="sxs-lookup"><span data-stu-id="6d7f8-130">**Scott Millett, Nick Tune - Patterns, Principles, and Practices of Domain-Driven Design** \\</span></span>
  [http://www.wrox.com/WileyCDA/WroxTitle/Patterns-Principles-and-Practices-of-Domain-Driven-Design.productCd-1118714709.html](http://www.wrox.com/WileyCDA/WroxTitle/Patterns-Principles-and-Practices-of-Domain-Driven-Design.productCd-1118714709.html)

##### <a name="ddd-training"></a><span data-ttu-id="6d7f8-131">DDD eğitim</span><span class="sxs-lookup"><span data-stu-id="6d7f8-131">DDD training</span></span>

- <span data-ttu-id="6d7f8-132">**Julie Lerman ve Steve Smith. Etki alanı Odaklı Tasarım ile ilgili temel bilgiler** \\</span><span class="sxs-lookup"><span data-stu-id="6d7f8-132">**Julie Lerman and Steve Smith. Domain-Driven Design Fundamentals** \\</span></span>
  [https://bit.ly/PS-DDD](https://bit.ly/PS-DDD)

>[!div class="step-by-step"]
><span data-ttu-id="6d7f8-133">[Önceki](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md)
>[İleri](apply-simplified-microservice-cqrs-ddd-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="6d7f8-133">[Previous](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md)
[Next](apply-simplified-microservice-cqrs-ddd-patterns.md)</span></span>