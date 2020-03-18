---
title: Mimari yaklaşımlar - Sunucusuz uygulamalar
description: N katmanlı mimarilerden sunucusuzlara bulut tabanlı kurumsal uygulamalar oluşturmak için mimari yaklaşımlarına giriş.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 74de96bef48f16ced4adf82855a740aa0afcdf1d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522904"
---
# <a name="architecture-approaches"></a><span data-ttu-id="ddfd7-103">Mimari yaklaşımları</span><span class="sxs-lookup"><span data-stu-id="ddfd7-103">Architecture approaches</span></span>

<span data-ttu-id="ddfd7-104">Kurumsal uygulamaların mimarlanmasına yönelik varolan yaklaşımların anlaşılması, sunucusuzların oynadığı rolün açıklığa kavuşturulmasına yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-104">Understanding existing approaches to architecting enterprise apps helps clarify the role played by serverless.</span></span> <span data-ttu-id="ddfd7-105">Yazılım geliştirme onlarca yıl içinde gelişti birçok yaklaşım ve desenler vardır, ve tüm kendi artıları ve eksileri var.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-105">There are many approaches and patterns that evolved over decades of software development, and all have their own pros and cons.</span></span> <span data-ttu-id="ddfd7-106">Çoğu durumda, nihai çözüm tek bir yaklaşım üzerinde karar içermeyebilir, ancak çeşitli yaklaşımlar entegre edebilir.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-106">In many cases, the ultimate solution may not involve deciding on a single approach but may integrate several approaches.</span></span> <span data-ttu-id="ddfd7-107">Geçiş senaryoları genellikle bir mimari yaklaşımdan diğerine hibrit bir yaklaşımla geçiş yapmayı içerir.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-107">Migration scenarios often involve shifting from one architecture approach to another through a hybrid approach.</span></span>

<span data-ttu-id="ddfd7-108">Bu bölümde, kurumsal uygulamalar için hem mantıksal hem de fiziksel mimari desenlere genel bir bakış sağlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-108">This chapter provides an overview of both logical and physical architecture patterns for enterprise applications.</span></span>

## <a name="architecture-patterns"></a><span data-ttu-id="ddfd7-109">Mimari desenleri</span><span class="sxs-lookup"><span data-stu-id="ddfd7-109">Architecture patterns</span></span>

<span data-ttu-id="ddfd7-110">Modern iş uygulamaları çeşitli mimari desenleri izler.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-110">Modern business applications follow a variety of architecture patterns.</span></span> <span data-ttu-id="ddfd7-111">Bu bölüm, ortak desenlerin bir anketini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-111">This section represents a survey of common patterns.</span></span> <span data-ttu-id="ddfd7-112">Burada listelenen desenler mutlaka tüm en iyi uygulamalar değildir, ancak farklı yaklaşımlar göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-112">The patterns listed here aren't necessarily all best practices, but illustrate different approaches.</span></span>

<span data-ttu-id="ddfd7-113">Daha fazla bilgi için [Azure uygulama mimarisi kılavuzuna](https://docs.microsoft.com/azure/architecture/guide/)bakın.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-113">For more information, see [Azure application architecture guide](https://docs.microsoft.com/azure/architecture/guide/).</span></span>

## <a name="monoliths"></a><span data-ttu-id="ddfd7-114">Yekpare</span><span class="sxs-lookup"><span data-stu-id="ddfd7-114">Monoliths</span></span>

<span data-ttu-id="ddfd7-115">Birçok iş uygulamaları monolit desen izleyin.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-115">Many business applications follow a monolith pattern.</span></span> <span data-ttu-id="ddfd7-116">Eski uygulamalar genellikle monolit olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-116">Legacy applications are often implemented as monoliths.</span></span> <span data-ttu-id="ddfd7-117">Monolit desende, tüm uygulama sorunları tek bir dağıtımda bulunur.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-117">In the monolith pattern, all application concerns are contained in a single deployment.</span></span> <span data-ttu-id="ddfd7-118">Kullanıcı arabiriminden veritabanı aramalarına kadar her şey aynı kod tabanına dahildir.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-118">Everything from user interface to database calls is included in the same codebase.</span></span>

![Monolit mimarisi](./media/monolith-architecture.png)

<span data-ttu-id="ddfd7-120">Monolit yaklaşımın çeşitli avantajları vardır.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-120">There are several advantages to the monolith approach.</span></span> <span data-ttu-id="ddfd7-121">Genellikle tek bir kod tabanını aşağı çekmek ve çalışmaya başlamak kolaydır.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-121">It's often easy to pull down a single code base and start working.</span></span> <span data-ttu-id="ddfd7-122">Rampa süresi daha az olabilir ve test ortamları oluşturmak yeni bir kopya sağlamak kadar basittir.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-122">Ramp up time may be less, and creating test environments is as simple as providing a new copy.</span></span> <span data-ttu-id="ddfd7-123">Monolit, birden çok bileşen ve uygulama içerecek şekilde tasarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-123">The monolith may be designed to include multiple components and applications.</span></span>

<span data-ttu-id="ddfd7-124">Ne yazık ki, monolit desen ölçekte yıkmak eğilimindedir.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-124">Unfortunately, the monolith pattern tends to break down at scale.</span></span> <span data-ttu-id="ddfd7-125">Monolit yaklaşımın başlıca dezavantajları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="ddfd7-125">Major disadvantages of the monolith approach include:</span></span>

- <span data-ttu-id="ddfd7-126">Aynı kod tabanında paralel olarak çalışmak zordur.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-126">Difficult to work in parallel in the same code base.</span></span>
- <span data-ttu-id="ddfd7-127">Herhangi bir değişiklik, ne kadar önemsiz olursa olsun, tüm uygulamanın yeni bir sürümünü dağıtmayı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-127">Any change, no matter how trivial, requires deploying a new version of the entire application.</span></span>
- <span data-ttu-id="ddfd7-128">Yeniden düzenleme, tüm uygulamayı etkileyebilecek şekilde etkiler.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-128">Refactoring potentially impacts the entire application.</span></span>
- <span data-ttu-id="ddfd7-129">Genellikle ölçeklendirmek için tek çözüm monolitin birden çok, kaynak yoğun kopyasını oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-129">Often the only solution to scale is to create multiple, resource-intensive copies of the monolith.</span></span>
- <span data-ttu-id="ddfd7-130">Sistemler genişledikçe veya diğer sistemler elde edilsinkçe, tümleştirme zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-130">As systems expand or other systems are acquired, integration can be difficult.</span></span>
- <span data-ttu-id="ddfd7-131">Tüm monoliti yapılandırma gereksinimi nedeniyle test etmek zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-131">It may be difficult to test due to the need to configure the entire monolith.</span></span>
- <span data-ttu-id="ddfd7-132">Kod yeniden kullanımı zordur ve genellikle diğer uygulamalar kendi kod kopyalarına sahip olmak zorunda kalırlar.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-132">Code reuse is challenging and often other apps end up having their own copies of code.</span></span>

<span data-ttu-id="ddfd7-133">Birçok işletme bulutu monolit uygulamaları geçirmek ve aynı zamanda bunları daha kullanılabilir desenlere yeniden düzenleme fırsatı olarak görmek.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-133">Many businesses look to the cloud as an opportunity to migrate monolith applications and at the same time refactor them to more usable patterns.</span></span> <span data-ttu-id="ddfd7-134">Ayrı ayrı bakımı, dağıtılması ve ölçeklendirilmesine izin vermek için tek tek uygulamaları ve bileşenleri ayırmak yaygındır.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-134">It's common to break out the individual applications and components to allow them to be maintained, deployed, and scaled separately.</span></span>

## <a name="n-layer-applications"></a><span data-ttu-id="ddfd7-135">N-Katman uygulamaları</span><span class="sxs-lookup"><span data-stu-id="ddfd7-135">N-Layer applications</span></span>

<span data-ttu-id="ddfd7-136">N-katmanlı uygulama bölüm uygulama mantığı belirli katmanlara.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-136">N-layer application partition application logic into specific layers.</span></span> <span data-ttu-id="ddfd7-137">En yaygın katmanlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="ddfd7-137">The most common layers include:</span></span>

- <span data-ttu-id="ddfd7-138">Kullanıcı arabirimi</span><span class="sxs-lookup"><span data-stu-id="ddfd7-138">User interface</span></span>
- <span data-ttu-id="ddfd7-139">İş mantığı</span><span class="sxs-lookup"><span data-stu-id="ddfd7-139">Business logic</span></span>
- <span data-ttu-id="ddfd7-140">Veri erişimi</span><span class="sxs-lookup"><span data-stu-id="ddfd7-140">Data access</span></span>

<span data-ttu-id="ddfd7-141">Diğer katmanlar ara yazılım, toplu işişleme ve API içerebilir.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-141">Other layers may include middleware, batch processing, and API.</span></span> <span data-ttu-id="ddfd7-142">Katmanların mantıklı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-142">It's important to note the layers are logical.</span></span> <span data-ttu-id="ddfd7-143">Her ne kadar izole edilmiş olsalar da, hepsi aynı hedef platforma konuşlandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-143">Although they're developed in isolation, they may all be deployed to the same target platform.</span></span>

![N-Layer mimarisi](./media/n-layer-architecture.png)

<span data-ttu-id="ddfd7-145">N-Layer yaklaşımının çeşitli avantajları vardır:</span><span class="sxs-lookup"><span data-stu-id="ddfd7-145">There are several advantages to the N-Layer approach, including:</span></span>

- <span data-ttu-id="ddfd7-146">Yeniden düzenleme bir katmana izole edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-146">Refactoring is isolated to a layer.</span></span>
- <span data-ttu-id="ddfd7-147">Takımlar ayrı katmanlar oluşturabilir, sınayabilir, dağıtabilir ve koruyabilir.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-147">Teams can independently build, test, deploy, and maintain separate layers.</span></span>
- <span data-ttu-id="ddfd7-148">Katmanlar değiştirilebilir, örneğin veri katmanı UI katmanında değişiklik gerektirmeden birden çok veritabanına erişebilir.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-148">Layers can be swapped out, for example the data layer may access multiple databases without requiring changes to the UI layer.</span></span>

<span data-ttu-id="ddfd7-149">Sunucusuz bir veya daha fazla katmanları uygulamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-149">Serverless may be used to implement one or more layers.</span></span>

## <a name="microservices"></a><span data-ttu-id="ddfd7-150">Mikro hizmetler</span><span class="sxs-lookup"><span data-stu-id="ddfd7-150">Microservices</span></span>

<span data-ttu-id="ddfd7-151">**[Microservices](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)** mimarileri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="ddfd7-151">**[Microservices](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)** architectures contain common characteristics that include:</span></span>

- <span data-ttu-id="ddfd7-152">Uygulamalar birkaç küçük hizmetlerden oluşur.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-152">Applications are composed of several small services.</span></span>
- <span data-ttu-id="ddfd7-153">Her hizmet kendi sürecinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-153">Each service runs in its own process.</span></span>
- <span data-ttu-id="ddfd7-154">Hizmetler iş alanları etrafında hizalanır.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-154">Services are aligned around business domains.</span></span>
- <span data-ttu-id="ddfd7-155">Hizmetler genellikle taşıma olarak HTTP kullanarak hafif API'ler üzerinden iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-155">Services communicate over lightweight APIs, typically using HTTP as the transport.</span></span>
- <span data-ttu-id="ddfd7-156">Hizmetler dağıtılabilir ve bağımsız olarak yükseltilebilir.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-156">Services can be deployed and upgraded independently.</span></span>
- <span data-ttu-id="ddfd7-157">Hizmetler tek bir veri deposuna bağlı değildir.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-157">Services aren't dependent on a single data store.</span></span>
- <span data-ttu-id="ddfd7-158">Sistem hata göz önünde bulundurularak tasarlanmıştır ve uygulama bazı hizmetler başarısız olsa bile yine de çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-158">The system is designed with failure in mind, and the app may still run even when certain services fail.</span></span>

<span data-ttu-id="ddfd7-159">Mikro hizmetler diğer mimari yaklaşımlara özel olmak zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-159">Microservices don't have to be mutually exclusive to other architecture approaches.</span></span> <span data-ttu-id="ddfd7-160">Örneğin, Bir N-Tier mimarisi orta katman için mikro hizmetleri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-160">For example, an N-Tier architecture may use microservices for the middle tier.</span></span> <span data-ttu-id="ddfd7-161">IIS ana bilgisayarlarındaki sanal dizinlerden konteynerlere kadar çeşitli şekillerde mikro hizmetler uygulamak da mümkündür.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-161">It's also possible to implement microservices in a variety of ways, from virtual directories on IIS hosts to containers.</span></span> <span data-ttu-id="ddfd7-162">Mikro hizmetlerin özellikleri, bunları özellikle sunucusuz uygulamalar için ideal kalmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-162">The characteristics of microservices make them especially ideal for serverless implementations.</span></span>

![Mikro hizmetler mimarisi](./media/microservices-architecture.png)

<span data-ttu-id="ddfd7-164">Mikrohizmet mimarilerinin artıları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="ddfd7-164">The pros of microservices architectures include:</span></span>

- <span data-ttu-id="ddfd7-165">Yeniden düzenleme genellikle tek bir hizmete yalıtılır.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-165">Refactoring is often isolated to a single service.</span></span>
- <span data-ttu-id="ddfd7-166">Hizmetler birbirinden bağımsız olarak yükseltilebilir.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-166">Services can be upgraded independently of each other.</span></span>
- <span data-ttu-id="ddfd7-167">Esneklik ve esneklik bireysel hizmetlerin taleplerine göre ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-167">Resiliency and elasticity can be tuned to the demands of individual services.</span></span>
- <span data-ttu-id="ddfd7-168">Geliştirme birbirinden farklı takımlar ve platformlar arasında paralel olarak gerçekleşebilir.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-168">Development can happen in parallel across disparate teams and platforms.</span></span>
- <span data-ttu-id="ddfd7-169">Yalıtılmış hizmetler için kapsamlı testler yazmak daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-169">It's easier to write comprehensive tests for isolated services.</span></span>

<span data-ttu-id="ddfd7-170">Mikro hizmetler, şunları dahil olmak üzere kendi zorluklarıyla birlikte gelir:</span><span class="sxs-lookup"><span data-stu-id="ddfd7-170">Microservices come with their own challenges, including:</span></span>

- <span data-ttu-id="ddfd7-171">Hangi hizmetlerin kullanılabilip çağırılabildiğini belirleme.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-171">Determining what services are available and how to call them.</span></span>
- <span data-ttu-id="ddfd7-172">Hizmetlerin yaşam döngüsünü yönetme.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-172">Managing the lifecycle of services.</span></span>
- <span data-ttu-id="ddfd7-173">Hizmetlerin genel uygulamada nasıl bir araya geldiğini anlama.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-173">Understanding how services fit together in the overall application.</span></span>
- <span data-ttu-id="ddfd7-174">Birbirinden farklı hizmetler arasında yapılan aramaların tam sistem testi.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-174">Full system testing of calls made across disparate services.</span></span>

<span data-ttu-id="ddfd7-175">Sonuç olarak, daha sonra tartışılan sunucusuzların avantajlarından yararlanmak da dahil olmak üzere tüm bu zorlukları ele alacak çözümler vardır.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-175">Ultimately there are solutions to address all of these challenges, including tapping into the benefits of serverless that are discussed later.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ddfd7-176">[Önceki](index.md)
>[Sonraki](architecture-deployment-approaches.md)</span><span class="sxs-lookup"><span data-stu-id="ddfd7-176">[Previous](index.md)
[Next](architecture-deployment-approaches.md)</span></span>
