---
title: Mikro hizmetlere dayalı bileşik u-u ui oluşturma
description: Microservices mimarisi sadece arka uç için değildir. Ön uçta kullanarak bir göz görünümü alın.
ms.date: 09/20/2018
ms.openlocfilehash: 1861d3bb6e5d4a0226aa8f3f72a2e0d3e83be56f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72275734"
---
# <a name="creating-composite-ui-based-on-microservices"></a><span data-ttu-id="f2005-104">Mikro hizmetlere dayalı bileşik u-u ui oluşturma</span><span class="sxs-lookup"><span data-stu-id="f2005-104">Creating composite UI based on microservices</span></span>

<span data-ttu-id="f2005-105">Microservices mimarisi genellikle sunucu tarafı işleme verileri ve mantığı ile başlar, ancak, birçok durumda, uI hala bir monolit olarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="f2005-105">Microservices architecture often starts with the server-side handling data and logic, but, in many cases, the UI is still handled as a monolith.</span></span> <span data-ttu-id="f2005-106">Ancak, daha gelişmiş bir yaklaşım, [mikro frontends](https://martinfowler.com/articles/micro-frontends.html)denilen, de mikro hizmetlere dayalı uygulama kullanıcı arabirimi tasarlamaktır.</span><span class="sxs-lookup"><span data-stu-id="f2005-106">However, a more advanced approach, called [micro frontends](https://martinfowler.com/articles/micro-frontends.html), is to design your application UI based on microservices as well.</span></span> <span data-ttu-id="f2005-107">Bu, sunucuda mikro hizmetler ve mikro hizmetleri tüketen tek bir istemci uygulaması yerine, mikro hizmetler tarafından üretilen kompozit bir ui'ye sahip olmak anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f2005-107">That means having a composite UI produced by the microservices, instead of having microservices on the server and just a monolithic client app consuming the microservices.</span></span> <span data-ttu-id="f2005-108">Bu yaklaşımla oluşturduğunuz mikro hizmetler hem mantık hem de görsel gösterim ile tamamlanabilir.</span><span class="sxs-lookup"><span data-stu-id="f2005-108">With this approach, the microservices you build can be complete with both logic and visual representation.</span></span>

<span data-ttu-id="f2005-109">Şekil 4-20, yekpare bir istemci uygulamasından sadece mikro hizmetleri tüketen daha basit bir yaklaşımı gösterir.</span><span class="sxs-lookup"><span data-stu-id="f2005-109">Figure 4-20 shows the simpler approach of just consuming microservices from a monolithic client application.</span></span> <span data-ttu-id="f2005-110">Tabii ki, HTML ve JavaScript üreten arasında bir ASP.NET MVC hizmeti olabilir.</span><span class="sxs-lookup"><span data-stu-id="f2005-110">Of course, you could have an ASP.NET MVC service in between producing the HTML and JavaScript.</span></span> <span data-ttu-id="f2005-111">Şekil, sadece mantık ve veri değil, UI şekli (HTML ve JavaScript) odaklanmak mikrohizmetleri tüketen tek bir (yekpare) istemci UI olduğunu vurgulayan bir basitleştirme olduğunu.</span><span class="sxs-lookup"><span data-stu-id="f2005-111">The figure is a simplification that highlights that you have a single (monolithic) client UI consuming the microservices, which just focus on logic and data and not on the UI shape (HTML and JavaScript).</span></span>

![Mikro hizmetlere bağlanan yekpare bir UI uygulamasının diyagramı.](./media/microservice-based-composite-ui-shape-layout/monolith-ui-consume-microservices.png)

<span data-ttu-id="f2005-113">**Şekil 4-20**.</span><span class="sxs-lookup"><span data-stu-id="f2005-113">**Figure 4-20**.</span></span> <span data-ttu-id="f2005-114">Arka uç mikro hizmetleri tüketen yekpare bir kullanıcı arası bilgi bir uygulama</span><span class="sxs-lookup"><span data-stu-id="f2005-114">A monolithic UI application consuming back-end microservices</span></span>

<span data-ttu-id="f2005-115">Buna karşılık, kompozit bir ui tam olarak oluşturulur ve mikrohizmetler kendileri tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f2005-115">In contrast, a composite UI is precisely generated and composed by the microservices themselves.</span></span> <span data-ttu-id="f2005-116">Bazı mikro hizmetler, UI'nin belirli alanlarının görsel şeklini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f2005-116">Some of the microservices drive the visual shape of specific areas of the UI.</span></span> <span data-ttu-id="f2005-117">Temel fark, şablonlara dayalı istemci ara birimi bileşenlerine (örneğin TypeScript sınıfları) sahip olması ve bu şablonlar için veri şekillendirme-UI ViewModel'in her mikro hizmetten gelmesidir.</span><span class="sxs-lookup"><span data-stu-id="f2005-117">The key difference is that you have client UI components (TypeScript classes, for example) based on templates, and the data-shaping-UI ViewModel for those templates comes from each microservice.</span></span>

<span data-ttu-id="f2005-118">İstemci uygulaması başlatma zamanında, istemci kullanıcı arabirimi bileşenlerinin her biri (örneğin TypeScript sınıfları), kendisini belirli bir senaryo için Görünüm Modelleri sağlama yeteneğine sahip bir altyapı mikro hizmetiyle kaydeder.</span><span class="sxs-lookup"><span data-stu-id="f2005-118">At client application start-up time, each of the client UI components (TypeScript classes, for example) registers itself with an infrastructure microservice capable of providing ViewModels for a given scenario.</span></span> <span data-ttu-id="f2005-119">Mikro hizmet şekli değiştirirse, UI de değişir.</span><span class="sxs-lookup"><span data-stu-id="f2005-119">If the microservice changes the shape, the UI changes also.</span></span>

<span data-ttu-id="f2005-120">Şekil 4-21 bu bileşik UI yaklaşımının bir sürümünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="f2005-120">Figure 4-21 shows a version of this composite UI approach.</span></span> <span data-ttu-id="f2005-121">Bu, farklı tekniklere dayanan parçalı parçaları biraraya getiren başka mikro hizmetleriniz olabileceğinden basitleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f2005-121">This is simplified because you might have other microservices that are aggregating granular parts that are based on different techniques.</span></span> <span data-ttu-id="f2005-122">Geleneksel bir web yaklaşımı (ASP.NET MVC) veya SPA (Tek Sayfa Uygulaması) oluşturmanıza bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="f2005-122">It depends on whether you're building a traditional web approach (ASP.NET MVC) or an SPA (Single Page Application).</span></span>

![Birçok görünüm modelinden oluşan bileşik bir ui diyagramı.](./media/microservice-based-composite-ui-shape-layout/microservice-generate-composite-ui.png)

<span data-ttu-id="f2005-124">**Şekil 4-21**.</span><span class="sxs-lookup"><span data-stu-id="f2005-124">**Figure 4-21**.</span></span> <span data-ttu-id="f2005-125">Arka uç mikro hizmetler tarafından şekillendirilen kompozit kullanıcı bir kullanıcı bir kullanıcı bir uygulama örneği</span><span class="sxs-lookup"><span data-stu-id="f2005-125">Example of a composite UI application shaped by back-end microservices</span></span>

<span data-ttu-id="f2005-126">Bu UI kompozisyon mikro hizmetlerinin her biri küçük bir API Ağ Geçidi'ne benzer.</span><span class="sxs-lookup"><span data-stu-id="f2005-126">Each of those UI composition microservices would be similar to a small API Gateway.</span></span> <span data-ttu-id="f2005-127">Ama bu durumda, her biri küçük bir uI alan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="f2005-127">But in this case, each one is responsible for a small UI area.</span></span>

<span data-ttu-id="f2005-128">Kullandığınız UI teknolojilerine bağlı olarak, mikro hizmetler tarafından yönlendirilen kompozit bir UI yaklaşımı daha zor veya daha az zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="f2005-128">A composite UI approach that's driven by microservices can be more challenging or less so, depending on what UI technologies you're using.</span></span> <span data-ttu-id="f2005-129">Örneğin, bir SPA oluşturmak veya yerel mobil uygulama için kullandığınız geleneksel bir web uygulaması oluşturmak için aynı teknikleri kullanmazsınız (bu yaklaşım için daha zor olabilecek Xamarin uygulamaları geliştirirken olduğu gibi).</span><span class="sxs-lookup"><span data-stu-id="f2005-129">For instance, you won't use the same techniques for building a traditional web application that you use for building an SPA or for native mobile app (as when developing Xamarin apps, which can be more challenging for this approach).</span></span>

<span data-ttu-id="f2005-130">[eShopOnContainers](https://aka.ms/MicroservicesArchitecture) örnek uygulama birden çok nedenden dolayı monolitik Kullanıcı Arabirimi yaklaşımını kullanır.</span><span class="sxs-lookup"><span data-stu-id="f2005-130">The [eShopOnContainers](https://aka.ms/MicroservicesArchitecture) sample application uses the monolithic UI approach for multiple reasons.</span></span> <span data-ttu-id="f2005-131">İlk olarak, mikro hizmetler ve konteynerler için bir giriş.</span><span class="sxs-lookup"><span data-stu-id="f2005-131">First, it's an introduction to microservices and containers.</span></span> <span data-ttu-id="f2005-132">Kompozit bir web sitesi daha gelişmiştir, ancak ui tasarlarken ve geliştirirken daha fazla karmaşıklık gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f2005-132">A composite UI is more advanced but also requires further complexity when designing and developing the UI.</span></span> <span data-ttu-id="f2005-133">İkincisi, eShopOnContainers da Xamarin dayalı bir yerli mobil uygulama sağlar, hangi\# istemci C tarafında daha karmaşık hale getirecek.</span><span class="sxs-lookup"><span data-stu-id="f2005-133">Second, eShopOnContainers also provides a native mobile app based on Xamarin, which would make it more complex on the client C\# side.</span></span>

<span data-ttu-id="f2005-134">Ancak, mikro hizmetlere dayalı kompozit u-kullanım hizmeti hakkında daha fazla bilgi edinmek için aşağıdaki referansları kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="f2005-134">However, we encourage you to use the following references to learn more about composite UI based on microservices.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="f2005-135">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="f2005-135">Additional resources</span></span>

- <span data-ttu-id="f2005-136">**Mikro Frontends (Martin Fowler günlüğü)**</span><span class="sxs-lookup"><span data-stu-id="f2005-136">**Micro Frontends (Martin Fowler's blog)**</span></span>  
  <https://martinfowler.com/articles/micro-frontends.html>
  
- <span data-ttu-id="f2005-137">**Mikro Frontends (Michael Geers sitesi)**</span><span class="sxs-lookup"><span data-stu-id="f2005-137">**Micro Frontends (Michael Geers site)**</span></span>  
  <https://micro-frontends.org/>
  
- <span data-ttu-id="f2005-138">**ASP.NET kullanarak Kompozit UI (Özellikle Atölye)**</span><span class="sxs-lookup"><span data-stu-id="f2005-138">**Composite UI using ASP.NET (Particular's Workshop)**</span></span>  
  <https://github.com/Particular/Workshop/tree/master/demos/asp-net-core>

- <span data-ttu-id="f2005-139">**Ruben Oostinga. Microservices Mimarisinde Monolitik Cephe**</span><span class="sxs-lookup"><span data-stu-id="f2005-139">**Ruben Oostinga. The Monolithic Frontend in the Microservices Architecture**</span></span>  
  <https://xebia.com/blog/the-monolithic-frontend-in-the-microservices-architecture/>

- <span data-ttu-id="f2005-140">**Mauro Servienti. Daha iyi ui kompozisyon sırrı**</span><span class="sxs-lookup"><span data-stu-id="f2005-140">**Mauro Servienti. The secret of better UI composition**</span></span>  
  <https://particular.net/blog/secret-of-better-ui-composition>

- <span data-ttu-id="f2005-141">**Viktor Farciç. Front-End Web Bileşenleri microservices içine dahil**</span><span class="sxs-lookup"><span data-stu-id="f2005-141">**Viktor Farcic. Including Front-End Web Components Into Microservices**</span></span>  
  <https://technologyconversations.com/2015/08/09/including-front-end-web-components-into-microservices/>

- <span data-ttu-id="f2005-142">**Microservices Mimarisinde Frontend'i Yönetme**</span><span class="sxs-lookup"><span data-stu-id="f2005-142">**Managing Frontend in the Microservices Architecture**</span></span>  
  <https://allegro.tech/2016/03/Managing-Frontend-in-the-microservices-architecture.html>

>[!div class="step-by-step"]
><span data-ttu-id="f2005-143">[Önceki](microservices-addressability-service-registry.md)
>[Sonraki](resilient-high-availability-microservices.md)</span><span class="sxs-lookup"><span data-stu-id="f2005-143">[Previous](microservices-addressability-service-registry.md)
[Next](resilient-high-availability-microservices.md)</span></span>
