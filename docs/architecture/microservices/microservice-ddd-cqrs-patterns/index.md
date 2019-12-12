---
title: Bir Mikro Hizmetteki İş Karmaşıklığını DDD ve CQRS Desenleriyle Giderme
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | DDD ve CQRS desenleri uygulayan karmaşık iş senaryolarına nasıl karar vermek istediğinizi anlayın
ms.date: 10/08/2018
ms.openlocfilehash: 88b105b68307c8587f877bb9ddf370e143d8539b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "73739842"
---
# <a name="tackle-business-complexity-in-a-microservice-with-ddd-and-cqrs-patterns"></a><span data-ttu-id="61f27-103">DDD ve CQRS desenleriyle mikro hizmette Iş karmaşıklığı</span><span class="sxs-lookup"><span data-stu-id="61f27-103">Tackle Business Complexity in a Microservice with DDD and CQRS Patterns</span></span>

<span data-ttu-id="61f27-104">*Her mikro hizmet için veya iş etki alanının anlaşılmasına ilişkin sınırlı bağlam için bir etki alanı modeli tasarlayın.*</span><span class="sxs-lookup"><span data-stu-id="61f27-104">*Design a domain model for each microservice or Bounded Context that reflects understanding of the business domain.*</span></span>

<span data-ttu-id="61f27-105">Bu bölüm, karmaşık alt sistemleri veya sürekli değişen iş kurallarıyla etki alanı uzmanlarından oluşan mikro hizmetleri bir arada açmak istediğinizde uyguladığınız daha gelişmiş mikro hizmetlere odaklanır.</span><span class="sxs-lookup"><span data-stu-id="61f27-105">This section focuses on more advanced microservices that you implement when you need to tackle complex subsystems, or microservices derived from the knowledge of domain experts with ever-changing business rules.</span></span> <span data-ttu-id="61f27-106">Bu bölümde kullanılan mimari desenleri, Şekil 7-1 ' de gösterildiği gibi etki alanı odaklı tasarım (DDD) ve Komut ve Sorgu Sorumluluklarının Ayrılığı (CQRS) yaklaşımlarına dayanır.</span><span class="sxs-lookup"><span data-stu-id="61f27-106">The architecture patterns used in this section are based on domain-driven design (DDD) and Command and Query Responsibility Segregation (CQRS) approaches, as illustrated in Figure 7-1.</span></span>

:::image type="complex" source="./media/index/internal-versus-external-architecture.png" alt-text="Dış ve iç mimari desenlerini karşılaştıran diyagram.":::
<span data-ttu-id="61f27-108">Dış mimari arasındaki fark: mikro hizmet desenleri, API ağ geçitleri, dayanıklı iletişimler, yayın/alt, vb. ve dahili mimari: veri odaklı/CRUD, DDD desenleri, bağımlılık ekleme, birden çok kitaplık, vb.</span><span class="sxs-lookup"><span data-stu-id="61f27-108">Difference between external architecture: microservice patterns, API gateways, resilient communications, pub/sub, etc., and internal architecture: data driven/CRUD, DDD patterns, dependency injection, multiple libraries, etc.</span></span>
:::image-end:::

<span data-ttu-id="61f27-109">**Şekil 7-1**.</span><span class="sxs-lookup"><span data-stu-id="61f27-109">**Figure 7-1**.</span></span> <span data-ttu-id="61f27-110">Her mikro hizmet için dış mikro hizmet mimarisi, iç mimari desenlerine karşı</span><span class="sxs-lookup"><span data-stu-id="61f27-110">External microservice architecture versus internal architecture patterns for each microservice</span></span>

<span data-ttu-id="61f27-111">Ancak, ASP.NET Core Web API hizmeti uygulama ya da swashbuckle veya NSwag ile Swagger meta verilerini kullanıma sunma gibi veri odaklı mikro hizmetlere yönelik tekniklerin çoğu, ile dahili olarak uygulanan daha gelişmiş mikro hizmetler için de geçerlidir. DDD desenleri.</span><span class="sxs-lookup"><span data-stu-id="61f27-111">However, most of the techniques for data driven microservices, such as how to implement an ASP.NET Core Web API service or how to expose Swagger metadata with Swashbuckle or NSwag, are also applicable to the more advanced microservices implemented internally with DDD patterns.</span></span> <span data-ttu-id="61f27-112">Bu bölüm önceki bölümlerin bir uzantısıdır, çünkü daha önce açıklanan uygulamaların çoğu, burada veya herhangi bir mikro hizmet türü için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="61f27-112">This section is an extension of the previous sections, because most of the practices explained earlier also apply here or for any kind of microservice.</span></span>

<span data-ttu-id="61f27-113">Bu bölüm öncelikle eShopOnContainers başvuru uygulamasında kullanılan Basitleştirilmiş CQRS desenleriyle ilgili ayrıntıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="61f27-113">This section first provides details on the simplified CQRS patterns used in the eShopOnContainers reference application.</span></span> <span data-ttu-id="61f27-114">Daha sonra, uygulamalarınızda yeniden kullanabileceğiniz ortak desenleri bulmanızı sağlayan DDD tekniklerine genel bir bakış alacaksınız.</span><span class="sxs-lookup"><span data-stu-id="61f27-114">Later, you will get an overview of the DDD techniques that enable you to find common patterns that you can reuse in your applications.</span></span>

<span data-ttu-id="61f27-115">DDD, öğrenme için zengin kaynak kümesi içeren büyük bir konudur.</span><span class="sxs-lookup"><span data-stu-id="61f27-115">DDD is a large topic with a rich set of resources for learning.</span></span> <span data-ttu-id="61f27-116">Eric Evans tarafından [etki alanı odaklı tasarım](https://domainlanguage.com/ddd/) ve Vaughn versuz, Jimmy Nilsson, Greg Başak, UDI Dahan, Jimmy Bogard ve bırçok başka ddd/CQRS uzmanından ek malzemeler gibi kitaplarla başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="61f27-116">You can start with books like [Domain-Driven Design](https://domainlanguage.com/ddd/) by Eric Evans and additional materials from Vaughn Vernon, Jimmy Nilsson, Greg Young, Udi Dahan, Jimmy Bogard, and many other DDD/CQRS experts.</span></span> <span data-ttu-id="61f27-117">Ancak bunların çoğu, somut iş etki alanındaki uzmanlar ile konuşmalar, beyaz taslak ve etki alanı modelleme oturumlarından DDD tekniklerini nasıl uygulayacağınızı öğrenmeyi denemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="61f27-117">But most of all you need to try to learn how to apply DDD techniques from the conversations, whiteboarding, and domain modeling sessions with the experts in your concrete business domain.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="61f27-118">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="61f27-118">Additional resources</span></span>

##### <a name="ddd-domain-driven-design"></a><span data-ttu-id="61f27-119">DDD (etki alanı odaklı tasarım)</span><span class="sxs-lookup"><span data-stu-id="61f27-119">DDD (Domain-Driven Design)</span></span>

- <span data-ttu-id="61f27-120">**Eric Evans. Etki alanı dili** </span><span class="sxs-lookup"><span data-stu-id="61f27-120">**Eric Evans. Domain Language** </span></span>\
  <https://domainlanguage.com/>

- <span data-ttu-id="61f27-121">**Marwler. Etki alanı odaklı tasarım** </span><span class="sxs-lookup"><span data-stu-id="61f27-121">**Martin Fowler. Domain-Driven Design** </span></span>\
  <https://martinfowler.com/tags/domain%20driven%20design.html>

- <span data-ttu-id="61f27-122">**Jimmy Bogard. Etki alanınızı güçlendirerek: bir öncü** </span><span class="sxs-lookup"><span data-stu-id="61f27-122">**Jimmy Bogard. Strengthening your domain: a primer** </span></span>\
  <https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/>

##### <a name="ddd-books"></a><span data-ttu-id="61f27-123">DDD kitapları</span><span class="sxs-lookup"><span data-stu-id="61f27-123">DDD books</span></span>

- <span data-ttu-id="61f27-124">**Eric Evans. Etki alanı odaklı tasarım: yazılım \ kalp halinde karmaşıklık karmaşıklığı**</span><span class="sxs-lookup"><span data-stu-id="61f27-124">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software** \</span></span>
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

- <span data-ttu-id="61f27-125">**Eric Evans. Etki alanı odaklı tasarım başvurusu: tanımlar ve desenli özetler** </span><span class="sxs-lookup"><span data-stu-id="61f27-125">**Eric Evans. Domain-Driven Design Reference: Definitions and Pattern Summaries** </span></span>\
  <https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/>

- <span data-ttu-id="61f27-126">**Vaughn versuz. Etki alanı odaklı tasarım \ uygulama**</span><span class="sxs-lookup"><span data-stu-id="61f27-126">**Vaughn Vernon. Implementing Domain-Driven Design** \</span></span>
  <https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/>

- <span data-ttu-id="61f27-127">**Vaughn versuz. Etki alanı odaklı tasarım** </span><span class="sxs-lookup"><span data-stu-id="61f27-127">**Vaughn Vernon. Domain-Driven Design Distilled** </span></span>\
  <https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/>

- <span data-ttu-id="61f27-128">**Jimmy Nilsson. Etki alanı odaklı tasarım ve desenleri uygulama** </span><span class="sxs-lookup"><span data-stu-id="61f27-128">**Jimmy Nilsson. Applying Domain-Driven Design and Patterns** </span></span>\
  <https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/>

- <span data-ttu-id="61f27-129">**Cesar de La Torre. N katmanlı etki alanı odaklı mimari Kılavuzu .NET** </span><span class="sxs-lookup"><span data-stu-id="61f27-129">**Cesar de la Torre. N-Layered Domain-Oriented Architecture Guide with .NET** </span></span>\
  <https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/>

- <span data-ttu-id="61f27-130">**Abel Avram ve Floyd Marinescu. Etki alanı odaklı tasarım hızlı** </span><span class="sxs-lookup"><span data-stu-id="61f27-130">**Abel Avram and Floyd Marinescu. Domain-Driven Design Quickly** </span></span>\
  <https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/>

- <span data-ttu-id="61f27-131">**Scott Millett, Nick ayarlama-etki alanı odaklı tasarım \ desenler, ilkeler ve uygulamalar**</span><span class="sxs-lookup"><span data-stu-id="61f27-131">**Scott Millett, Nick Tune - Patterns, Principles, and Practices of Domain-Driven Design** \</span></span>
  <http://www.wrox.com/WileyCDA/WroxTitle/Patterns-Principles-and-Practices-of-Domain-Driven-Design.productCd-1118714709.html>

##### <a name="ddd-training"></a><span data-ttu-id="61f27-132">DDD eğitimi</span><span class="sxs-lookup"><span data-stu-id="61f27-132">DDD training</span></span>

- <span data-ttu-id="61f27-133">**Julie Lerman ve Steve Smith. Etki alanı odaklı tasarım temelleri** </span><span class="sxs-lookup"><span data-stu-id="61f27-133">**Julie Lerman and Steve Smith. Domain-Driven Design Fundamentals** </span></span>\
  <https://bit.ly/PS-DDD>

>[!div class="step-by-step"]
><span data-ttu-id="61f27-134">[Önceki](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md)
>[İleri](apply-simplified-microservice-cqrs-ddd-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="61f27-134">[Previous](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md)
[Next](apply-simplified-microservice-cqrs-ddd-patterns.md)</span></span>
