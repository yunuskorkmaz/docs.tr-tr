---
title: Bir Mikro Hizmetteki İş Karmaşıklığını DDD ve CQRS Desenleriyle Giderme
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | DDD ve CQRS Desenleri uygulayan karmaşık iş senaryoları ile nasıl başa çılayacağımı anlama
ms.date: 10/08/2018
ms.openlocfilehash: 88b105b68307c8587f877bb9ddf370e143d8539b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73739842"
---
# <a name="tackle-business-complexity-in-a-microservice-with-ddd-and-cqrs-patterns"></a><span data-ttu-id="3f380-103">DDD ve CQRS Desenleri ile Microservice'te İş Karmaşıklığıyla Mücadele</span><span class="sxs-lookup"><span data-stu-id="3f380-103">Tackle Business Complexity in a Microservice with DDD and CQRS Patterns</span></span>

<span data-ttu-id="3f380-104">*Her microservice veya Bounded Context için iş etki alanının anlaşılmasını yansıtan bir etki alanı modeli tasarla.*</span><span class="sxs-lookup"><span data-stu-id="3f380-104">*Design a domain model for each microservice or Bounded Context that reflects understanding of the business domain.*</span></span>

<span data-ttu-id="3f380-105">Bu bölümde, karmaşık alt sistemlerle başa çıkmak için gereken de uyguladığınız daha gelişmiş mikro hizmetler veya sürekli değişen iş kurallarına sahip etki alanı uzmanlarının bilgisinden elde edilen mikro hizmetler üzerinde duruluyor.</span><span class="sxs-lookup"><span data-stu-id="3f380-105">This section focuses on more advanced microservices that you implement when you need to tackle complex subsystems, or microservices derived from the knowledge of domain experts with ever-changing business rules.</span></span> <span data-ttu-id="3f380-106">Bu bölümde kullanılan mimari desenler, Şekil 7-1'de gösterildiği gibi etki alanı odaklı tasarım (DDD) ve Komut ve Sorgu Sorumluluğu Ayrımı (CQRS) yaklaşımlarına dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3f380-106">The architecture patterns used in this section are based on domain-driven design (DDD) and Command and Query Responsibility Segregation (CQRS) approaches, as illustrated in Figure 7-1.</span></span>

:::image type="complex" source="./media/index/internal-versus-external-architecture.png" alt-text="Dış ve iç mimari desenleri karşılaştıran diyagram.":::
<span data-ttu-id="3f380-108">Dış mimari arasındaki fark: mikrohizmet kalıpları, API ağ geçitleri, esnek iletişim, pub/alt, vb. ve dahili mimari: veri odaklı/CRUD, DDD desenleri, bağımlılık enjeksiyonu, birden fazla kitaplık, vb.</span><span class="sxs-lookup"><span data-stu-id="3f380-108">Difference between external architecture: microservice patterns, API gateways, resilient communications, pub/sub, etc., and internal architecture: data driven/CRUD, DDD patterns, dependency injection, multiple libraries, etc.</span></span>
:::image-end:::

<span data-ttu-id="3f380-109">**Şekil 7-1**.</span><span class="sxs-lookup"><span data-stu-id="3f380-109">**Figure 7-1**.</span></span> <span data-ttu-id="3f380-110">Her mikro hizmet için harici microservice mimarisi ve iç mimari desenleri</span><span class="sxs-lookup"><span data-stu-id="3f380-110">External microservice architecture versus internal architecture patterns for each microservice</span></span>

<span data-ttu-id="3f380-111">Ancak, ASP.NET Core Web API hizmetinin nasıl uygulanacağı veya Swagger meta verilerinin Swashbuckle veya NSwag ile nasıl ifşa edilecek gibi veri odaklı mikro hizmetler için tekniklerin çoğu, dahili olarak uygulanan daha gelişmiş mikro hizmetler için de geçerlidir. DDD desenleri.</span><span class="sxs-lookup"><span data-stu-id="3f380-111">However, most of the techniques for data driven microservices, such as how to implement an ASP.NET Core Web API service or how to expose Swagger metadata with Swashbuckle or NSwag, are also applicable to the more advanced microservices implemented internally with DDD patterns.</span></span> <span data-ttu-id="3f380-112">Daha önce açıklanan uygulamaların çoğu burada veya her türlü mikro hizmet için de geçerli olduğundan, bu bölüm önceki bölümlerin bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="3f380-112">This section is an extension of the previous sections, because most of the practices explained earlier also apply here or for any kind of microservice.</span></span>

<span data-ttu-id="3f380-113">Bu bölümde ilk olarak eShopOnContainers başvuru uygulamasında kullanılan basitleştirilmiş CQRS desenleri hakkında ayrıntılı bilgi verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3f380-113">This section first provides details on the simplified CQRS patterns used in the eShopOnContainers reference application.</span></span> <span data-ttu-id="3f380-114">Daha sonra, uygulamalarınızda yeniden kullanabileceğiniz ortak desenleri bulmanızı sağlayan DDD tekniklerine genel bir bakış elde elabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f380-114">Later, you will get an overview of the DDD techniques that enable you to find common patterns that you can reuse in your applications.</span></span>

<span data-ttu-id="3f380-115">DDD öğrenme için kaynakların zengin bir dizi ile büyük bir konudur.</span><span class="sxs-lookup"><span data-stu-id="3f380-115">DDD is a large topic with a rich set of resources for learning.</span></span> <span data-ttu-id="3f380-116">Eric Evans'ın [Domain-Driven Design](https://domainlanguage.com/ddd/) gibi kitaplarla ve Vaughn Vernon, Jimmy Nilsson, Greg Young, Udi Dahan, Jimmy Bogard ve diğer birçok DDD/CQRS uzmanından ek materyallerle başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f380-116">You can start with books like [Domain-Driven Design](https://domainlanguage.com/ddd/) by Eric Evans and additional materials from Vaughn Vernon, Jimmy Nilsson, Greg Young, Udi Dahan, Jimmy Bogard, and many other DDD/CQRS experts.</span></span> <span data-ttu-id="3f380-117">Ama en önemlisi nasıl konuşmaları, whiteboarding ve etki alanı modelleme oturumları somut iş alanında uzmanlarla DDD teknikleri uygulamak için öğrenmek için denemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="3f380-117">But most of all you need to try to learn how to apply DDD techniques from the conversations, whiteboarding, and domain modeling sessions with the experts in your concrete business domain.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="3f380-118">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="3f380-118">Additional resources</span></span>

##### <a name="ddd-domain-driven-design"></a><span data-ttu-id="3f380-119">DDD (Etki Alanı Odaklı Tasarım)</span><span class="sxs-lookup"><span data-stu-id="3f380-119">DDD (Domain-Driven Design)</span></span>

- <span data-ttu-id="3f380-120">**Eric Evans' ı. Etki Alanı Dili** </span><span class="sxs-lookup"><span data-stu-id="3f380-120">**Eric Evans. Domain Language** </span></span>\
  <https://domainlanguage.com/>

- <span data-ttu-id="3f380-121">**Martin Fowler' ı. Etki Alanı Odaklı Tasarım** </span><span class="sxs-lookup"><span data-stu-id="3f380-121">**Martin Fowler. Domain-Driven Design** </span></span>\
  <https://martinfowler.com/tags/domain%20driven%20design.html>

- <span data-ttu-id="3f380-122">**Jimmy Bogard' ı. Etki alanınızı güçlendirme: bir astar** </span><span class="sxs-lookup"><span data-stu-id="3f380-122">**Jimmy Bogard. Strengthening your domain: a primer** </span></span>\
  <https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/>

##### <a name="ddd-books"></a><span data-ttu-id="3f380-123">DDD kitaplar</span><span class="sxs-lookup"><span data-stu-id="3f380-123">DDD books</span></span>

- <span data-ttu-id="3f380-124">**Eric Evans' ı. Etki Alanı Odaklı Tasarım: Yazılımın Kalbinde karmaşıklıkla mücadele** </span><span class="sxs-lookup"><span data-stu-id="3f380-124">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software** </span></span>\
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

- <span data-ttu-id="3f380-125">**Eric Evans' ı. Etki Alanı Odaklı Tasarım Referansı: Tanımlar ve Örüntü Özetleri** </span><span class="sxs-lookup"><span data-stu-id="3f380-125">**Eric Evans. Domain-Driven Design Reference: Definitions and Pattern Summaries** </span></span>\
  <https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/>

- <span data-ttu-id="3f380-126">**Vaughn Vernon' u. Etki Alanı Odaklı Tasarımın Uygulanması** </span><span class="sxs-lookup"><span data-stu-id="3f380-126">**Vaughn Vernon. Implementing Domain-Driven Design** </span></span>\
  <https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/>

- <span data-ttu-id="3f380-127">**Vaughn Vernon' u. Etki Alanı Odaklı Tasarım Distile** </span><span class="sxs-lookup"><span data-stu-id="3f380-127">**Vaughn Vernon. Domain-Driven Design Distilled** </span></span>\
  <https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/>

- <span data-ttu-id="3f380-128">**Jimmy Nilsson' ı. Etki Alanına Dayalı Tasarım ve Desenleruygulama** </span><span class="sxs-lookup"><span data-stu-id="3f380-128">**Jimmy Nilsson. Applying Domain-Driven Design and Patterns** </span></span>\
  <https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/>

- <span data-ttu-id="3f380-129">**Cesar de la Torre. .NET ile N Katmanlı Etki Alanı Odaklı Mimari Rehberi** </span><span class="sxs-lookup"><span data-stu-id="3f380-129">**Cesar de la Torre. N-Layered Domain-Oriented Architecture Guide with .NET** </span></span>\
  <https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/>

- <span data-ttu-id="3f380-130">**Abel Avram ve Floyd Marinescu. Etki Alanı Odaklı Tasarım Hızlı** </span><span class="sxs-lookup"><span data-stu-id="3f380-130">**Abel Avram and Floyd Marinescu. Domain-Driven Design Quickly** </span></span>\
  <https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/>

- <span data-ttu-id="3f380-131">**Scott Millett, Nick Tune - Etki Alanı Odaklı Tasarım Desenleri, İlkeleri ve Uygulamaları** </span><span class="sxs-lookup"><span data-stu-id="3f380-131">**Scott Millett, Nick Tune - Patterns, Principles, and Practices of Domain-Driven Design** </span></span>\
  <http://www.wrox.com/WileyCDA/WroxTitle/Patterns-Principles-and-Practices-of-Domain-Driven-Design.productCd-1118714709.html>

##### <a name="ddd-training"></a><span data-ttu-id="3f380-132">DDD eğitimi</span><span class="sxs-lookup"><span data-stu-id="3f380-132">DDD training</span></span>

- <span data-ttu-id="3f380-133">**Julie Lerman ve Steve Smith. Etki Alanı Odaklı Tasarım Temelleri** </span><span class="sxs-lookup"><span data-stu-id="3f380-133">**Julie Lerman and Steve Smith. Domain-Driven Design Fundamentals** </span></span>\
  <https://bit.ly/PS-DDD>

>[!div class="step-by-step"]
><span data-ttu-id="3f380-134">[Önceki](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md)
>[Sonraki](apply-simplified-microservice-cqrs-ddd-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="3f380-134">[Previous](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md)
[Next](apply-simplified-microservice-cqrs-ddd-patterns.md)</span></span>
