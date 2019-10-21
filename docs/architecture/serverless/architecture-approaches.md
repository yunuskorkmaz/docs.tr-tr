---
title: Mimari Yaklaşımlar-sunucusuz uygulamalar
description: N katmanlı mimarilerin sunucusuz 'e kadar bulut tabanlı kurumsal uygulamalar oluşturmaya yönelik mimariye bir giriş.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 74de96bef48f16ced4adf82855a740aa0afcdf1d
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522904"
---
# <a name="architecture-approaches"></a><span data-ttu-id="8811c-103">Mimari yaklaşımları</span><span class="sxs-lookup"><span data-stu-id="8811c-103">Architecture approaches</span></span>

<span data-ttu-id="8811c-104">Kurumsal uygulamaları mimarmaya yönelik mevcut yaklaşımların anlaşılması sunucusuz tarafından yürütülen rolü açıklığa kavuşturmaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="8811c-104">Understanding existing approaches to architecting enterprise apps helps clarify the role played by serverless.</span></span> <span data-ttu-id="8811c-105">Yazılım geliştirme ve tüm uzmanlarının kendi uzmanlarına ve dezavantajlarına sahip birçok yaklaşım ve desen vardır.</span><span class="sxs-lookup"><span data-stu-id="8811c-105">There are many approaches and patterns that evolved over decades of software development, and all have their own pros and cons.</span></span> <span data-ttu-id="8811c-106">Çoğu durumda, en son çözüm tek bir yaklaşım üzerinde karar vermeyebilir ancak çeşitli yaklaşımları tümleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="8811c-106">In many cases, the ultimate solution may not involve deciding on a single approach but may integrate several approaches.</span></span> <span data-ttu-id="8811c-107">Geçiş senaryoları genellikle bir mimarinin bir karma yaklaşım aracılığıyla bir mimariden diğerine kaydırılmasıyla ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="8811c-107">Migration scenarios often involve shifting from one architecture approach to another through a hybrid approach.</span></span>

<span data-ttu-id="8811c-108">Bu bölümde, kurumsal uygulamalar için hem mantıksal hem de fiziksel mimari desenlerine genel bir bakış sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8811c-108">This chapter provides an overview of both logical and physical architecture patterns for enterprise applications.</span></span>

## <a name="architecture-patterns"></a><span data-ttu-id="8811c-109">Mimari desenleri</span><span class="sxs-lookup"><span data-stu-id="8811c-109">Architecture patterns</span></span>

<span data-ttu-id="8811c-110">Modern iş uygulamaları çeşitli mimari desenlerini izler.</span><span class="sxs-lookup"><span data-stu-id="8811c-110">Modern business applications follow a variety of architecture patterns.</span></span> <span data-ttu-id="8811c-111">Bu bölüm ortak desenlerin bir anketini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8811c-111">This section represents a survey of common patterns.</span></span> <span data-ttu-id="8811c-112">Burada listelenen desenler tüm en iyi uygulamalar değildir, ancak farklı yaklaşımlar gösterir.</span><span class="sxs-lookup"><span data-stu-id="8811c-112">The patterns listed here aren't necessarily all best practices, but illustrate different approaches.</span></span>

<span data-ttu-id="8811c-113">Daha fazla bilgi için bkz. [Azure Uygulama Mimarisi Kılavuzu](https://docs.microsoft.com/azure/architecture/guide/).</span><span class="sxs-lookup"><span data-stu-id="8811c-113">For more information, see [Azure application architecture guide](https://docs.microsoft.com/azure/architecture/guide/).</span></span>

## <a name="monoliths"></a><span data-ttu-id="8811c-114">Tek tek</span><span class="sxs-lookup"><span data-stu-id="8811c-114">Monoliths</span></span>

<span data-ttu-id="8811c-115">Birçok iş uygulaması tek bir düzende izler.</span><span class="sxs-lookup"><span data-stu-id="8811c-115">Many business applications follow a monolith pattern.</span></span> <span data-ttu-id="8811c-116">Eski uygulamalar genellikle tek tek olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="8811c-116">Legacy applications are often implemented as monoliths.</span></span> <span data-ttu-id="8811c-117">Tek bir düzende, tüm uygulama kaygıları tek bir dağıtımda bulunur.</span><span class="sxs-lookup"><span data-stu-id="8811c-117">In the monolith pattern, all application concerns are contained in a single deployment.</span></span> <span data-ttu-id="8811c-118">Kullanıcı arabiriminden veritabanı çağrılarına olan her şey aynı kod tabanına dahildir.</span><span class="sxs-lookup"><span data-stu-id="8811c-118">Everything from user interface to database calls is included in the same codebase.</span></span>

![Monolith mimarisi](./media/monolith-architecture.png)

<span data-ttu-id="8811c-120">Tek tek yaklaşımın çeşitli avantajları vardır.</span><span class="sxs-lookup"><span data-stu-id="8811c-120">There are several advantages to the monolith approach.</span></span> <span data-ttu-id="8811c-121">Tek bir kod temelini çekmek ve çalışmaya başlamak genellikle kolaydır.</span><span class="sxs-lookup"><span data-stu-id="8811c-121">It's often easy to pull down a single code base and start working.</span></span> <span data-ttu-id="8811c-122">Artırma süresi daha az olabilir ve test ortamları oluşturmak, yeni bir kopya sağlamak kadar basittir.</span><span class="sxs-lookup"><span data-stu-id="8811c-122">Ramp up time may be less, and creating test environments is as simple as providing a new copy.</span></span> <span data-ttu-id="8811c-123">MONOLITH birden çok bileşeni ve uygulamayı kapsayacak şekilde tasarlanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="8811c-123">The monolith may be designed to include multiple components and applications.</span></span>

<span data-ttu-id="8811c-124">Ne yazık ki, tek bir model ölçeklendirmeye göre daha fazla eğilimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="8811c-124">Unfortunately, the monolith pattern tends to break down at scale.</span></span> <span data-ttu-id="8811c-125">Tek tek yaklaşımın önemli dezavantajları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="8811c-125">Major disadvantages of the monolith approach include:</span></span>

- <span data-ttu-id="8811c-126">Aynı kod tabanında paralel çalışmayı zorlaştırıyor.</span><span class="sxs-lookup"><span data-stu-id="8811c-126">Difficult to work in parallel in the same code base.</span></span>
- <span data-ttu-id="8811c-127">Tüm değişiklikler, ne kadar önemsiz olsun, tüm uygulamanın yeni bir sürümünü dağıtmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8811c-127">Any change, no matter how trivial, requires deploying a new version of the entire application.</span></span>
- <span data-ttu-id="8811c-128">Yeniden düzenleme büyük olasılıkla uygulamanın tamamını etkiler.</span><span class="sxs-lookup"><span data-stu-id="8811c-128">Refactoring potentially impacts the entire application.</span></span>
- <span data-ttu-id="8811c-129">Genellikle ölçeklendirmeye yönelik tek çözüm, tek başına birden çok, yoğun kaynak yoğunluklu kopya oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="8811c-129">Often the only solution to scale is to create multiple, resource-intensive copies of the monolith.</span></span>
- <span data-ttu-id="8811c-130">Sistemler Genişlemeden veya diğer sistemler alındığından, tümleştirme zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="8811c-130">As systems expand or other systems are acquired, integration can be difficult.</span></span>
- <span data-ttu-id="8811c-131">Tek bir tam yapılandırma gereksiniminden dolayı test edilmesi zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="8811c-131">It may be difficult to test due to the need to configure the entire monolith.</span></span>
- <span data-ttu-id="8811c-132">Kod yeniden kullanımı zor ve genellikle diğer uygulamalar kendi kod kopyalarına sahip olur.</span><span class="sxs-lookup"><span data-stu-id="8811c-132">Code reuse is challenging and often other apps end up having their own copies of code.</span></span>

<span data-ttu-id="8811c-133">Birçok işletme, tek bir uygulamayı geçirme fırsatı olarak buluta bakar ve aynı zamanda bunları daha kullanılabilir desenlere yeniden düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="8811c-133">Many businesses look to the cloud as an opportunity to migrate monolith applications and at the same time refactor them to more usable patterns.</span></span> <span data-ttu-id="8811c-134">Ayrı ayrı uygulamaları ve bileşenleri, bunların korunmasını, dağıtılmasını ve ayrı olarak ölçeklendirilmesine olanak tanımak için yaygın olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8811c-134">It's common to break out the individual applications and components to allow them to be maintained, deployed, and scaled separately.</span></span>

## <a name="n-layer-applications"></a><span data-ttu-id="8811c-135">N katmanlı uygulamalar</span><span class="sxs-lookup"><span data-stu-id="8811c-135">N-Layer applications</span></span>

<span data-ttu-id="8811c-136">N katmanlı uygulama bölümü uygulama mantığını belirli katmanlara dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="8811c-136">N-layer application partition application logic into specific layers.</span></span> <span data-ttu-id="8811c-137">En yaygın katmanlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="8811c-137">The most common layers include:</span></span>

- <span data-ttu-id="8811c-138">Kullanıcı arabirimi</span><span class="sxs-lookup"><span data-stu-id="8811c-138">User interface</span></span>
- <span data-ttu-id="8811c-139">İş mantığı</span><span class="sxs-lookup"><span data-stu-id="8811c-139">Business logic</span></span>
- <span data-ttu-id="8811c-140">Veri erişimi</span><span class="sxs-lookup"><span data-stu-id="8811c-140">Data access</span></span>

<span data-ttu-id="8811c-141">Diğer katmanlar, ara yazılım, toplu işlem ve API içerebilir.</span><span class="sxs-lookup"><span data-stu-id="8811c-141">Other layers may include middleware, batch processing, and API.</span></span> <span data-ttu-id="8811c-142">Katmanların mantıklı olduğunu unutmamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="8811c-142">It's important to note the layers are logical.</span></span> <span data-ttu-id="8811c-143">Yalıtılmış olarak geliştirilse de, hepsi aynı hedef platforma dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="8811c-143">Although they're developed in isolation, they may all be deployed to the same target platform.</span></span>

![N katmanlı mimari](./media/n-layer-architecture.png)

<span data-ttu-id="8811c-145">N katmanlı yaklaşımda aşağıdakiler de dahil olmak üzere birkaç avantaj vardır:</span><span class="sxs-lookup"><span data-stu-id="8811c-145">There are several advantages to the N-Layer approach, including:</span></span>

- <span data-ttu-id="8811c-146">Yeniden düzenleme bir katmana yalıtılmış.</span><span class="sxs-lookup"><span data-stu-id="8811c-146">Refactoring is isolated to a layer.</span></span>
- <span data-ttu-id="8811c-147">Takımlar bağımsız olarak ayrı katmanları oluşturabilir, test edebilir, dağıtabilir ve koruyabilir.</span><span class="sxs-lookup"><span data-stu-id="8811c-147">Teams can independently build, test, deploy, and maintain separate layers.</span></span>
- <span data-ttu-id="8811c-148">Katmanlar dışarı değiştirilebilir, örneğin veri katmanı, Kullanıcı arabirimi katmanında değişiklik gerektirmeden birden çok veritabanına erişebilir.</span><span class="sxs-lookup"><span data-stu-id="8811c-148">Layers can be swapped out, for example the data layer may access multiple databases without requiring changes to the UI layer.</span></span>

<span data-ttu-id="8811c-149">Sunucusuz, bir veya daha fazla katmanı uygulamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8811c-149">Serverless may be used to implement one or more layers.</span></span>

## <a name="microservices"></a><span data-ttu-id="8811c-150">Mikro hizmetler</span><span class="sxs-lookup"><span data-stu-id="8811c-150">Microservices</span></span>

<span data-ttu-id="8811c-151">**[Mikro hizmet](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)** mimarileri, aşağıdakiler dahil olmak üzere ortak özellikler içerir:</span><span class="sxs-lookup"><span data-stu-id="8811c-151">**[Microservices](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)** architectures contain common characteristics that include:</span></span>

- <span data-ttu-id="8811c-152">Uygulamalar çeşitli küçük hizmetlerden oluşur.</span><span class="sxs-lookup"><span data-stu-id="8811c-152">Applications are composed of several small services.</span></span>
- <span data-ttu-id="8811c-153">Her hizmet kendi sürecinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="8811c-153">Each service runs in its own process.</span></span>
- <span data-ttu-id="8811c-154">Hizmetler, iş etki alanları etrafında hizalanır.</span><span class="sxs-lookup"><span data-stu-id="8811c-154">Services are aligned around business domains.</span></span>
- <span data-ttu-id="8811c-155">Hizmetler, genellikle aktarım olarak HTTP kullanarak basit API 'Ler üzerinden iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="8811c-155">Services communicate over lightweight APIs, typically using HTTP as the transport.</span></span>
- <span data-ttu-id="8811c-156">Hizmetler bağımsız olarak dağıtılabilir ve yükseltilebilir.</span><span class="sxs-lookup"><span data-stu-id="8811c-156">Services can be deployed and upgraded independently.</span></span>
- <span data-ttu-id="8811c-157">Hizmetler tek bir veri deposuna bağımlı değil.</span><span class="sxs-lookup"><span data-stu-id="8811c-157">Services aren't dependent on a single data store.</span></span>
- <span data-ttu-id="8811c-158">Sistem, sorun göz önünde bulundurularak tasarlanmıştır ve bazı hizmetler başarısız olduğunda bile uygulama çalışmaya devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="8811c-158">The system is designed with failure in mind, and the app may still run even when certain services fail.</span></span>

<span data-ttu-id="8811c-159">Mikro hizmetlerin diğer mimari yaklaşımlar için birbirini dışlamalı olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="8811c-159">Microservices don't have to be mutually exclusive to other architecture approaches.</span></span> <span data-ttu-id="8811c-160">Örneğin, N katmanlı bir mimaride, orta katman için mikro hizmetler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8811c-160">For example, an N-Tier architecture may use microservices for the middle tier.</span></span> <span data-ttu-id="8811c-161">Mikro Hizmetleri, IIS konaklarındaki sanal dizinlerden kapsayıcılara çok çeşitli yollarla uygulamak da mümkündür.</span><span class="sxs-lookup"><span data-stu-id="8811c-161">It's also possible to implement microservices in a variety of ways, from virtual directories on IIS hosts to containers.</span></span> <span data-ttu-id="8811c-162">Mikro hizmetlerin özellikleri, özellikle sunucusuz uygulamalar için idealdir.</span><span class="sxs-lookup"><span data-stu-id="8811c-162">The characteristics of microservices make them especially ideal for serverless implementations.</span></span>

![Mikro hizmetler mimarisi](./media/microservices-architecture.png)

<span data-ttu-id="8811c-164">Mikro hizmet mimarilerinin uzmanları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="8811c-164">The pros of microservices architectures include:</span></span>

- <span data-ttu-id="8811c-165">Yeniden düzenleme, genellikle tek bir hizmet olarak yalıtılır.</span><span class="sxs-lookup"><span data-stu-id="8811c-165">Refactoring is often isolated to a single service.</span></span>
- <span data-ttu-id="8811c-166">Hizmetler birbirinden bağımsız olarak yükseltilebilir.</span><span class="sxs-lookup"><span data-stu-id="8811c-166">Services can be upgraded independently of each other.</span></span>
- <span data-ttu-id="8811c-167">Dayanıklılık ve esneklik, bireysel hizmet taleplerine ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="8811c-167">Resiliency and elasticity can be tuned to the demands of individual services.</span></span>
- <span data-ttu-id="8811c-168">Geliştirme, farklı ekipler ve platformlar arasında paralel olarak gerçekleşebilir.</span><span class="sxs-lookup"><span data-stu-id="8811c-168">Development can happen in parallel across disparate teams and platforms.</span></span>
- <span data-ttu-id="8811c-169">Yalıtılmış hizmetler için kapsamlı testler yazmak daha kolay.</span><span class="sxs-lookup"><span data-stu-id="8811c-169">It's easier to write comprehensive tests for isolated services.</span></span>

<span data-ttu-id="8811c-170">Mikro hizmetler aşağıdakiler dahil olmak üzere kendi güçlüklarıyla birlikte gelir:</span><span class="sxs-lookup"><span data-stu-id="8811c-170">Microservices come with their own challenges, including:</span></span>

- <span data-ttu-id="8811c-171">Hangi hizmetlerin kullanılabilir olduğunu ve bunların nasıl çağrılacağını belirleme.</span><span class="sxs-lookup"><span data-stu-id="8811c-171">Determining what services are available and how to call them.</span></span>
- <span data-ttu-id="8811c-172">Hizmet yaşam döngüsünü yönetme.</span><span class="sxs-lookup"><span data-stu-id="8811c-172">Managing the lifecycle of services.</span></span>
- <span data-ttu-id="8811c-173">Hizmetlerin genel uygulamada nasıl bir araya uyduğunu anlama.</span><span class="sxs-lookup"><span data-stu-id="8811c-173">Understanding how services fit together in the overall application.</span></span>
- <span data-ttu-id="8811c-174">Farklı hizmetler genelinde yapılan çağrıların tam sistem testi.</span><span class="sxs-lookup"><span data-stu-id="8811c-174">Full system testing of calls made across disparate services.</span></span>

<span data-ttu-id="8811c-175">Son olarak, daha sonra ele alınan sunucusuz avantajlarına dokunma dahil olmak üzere tüm bu zorlukları ele alan çözümler vardır.</span><span class="sxs-lookup"><span data-stu-id="8811c-175">Ultimately there are solutions to address all of these challenges, including tapping into the benefits of serverless that are discussed later.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="8811c-176">[Önceki](index.md)
>[İleri](architecture-deployment-approaches.md)</span><span class="sxs-lookup"><span data-stu-id="8811c-176">[Previous](index.md)
[Next](architecture-deployment-approaches.md)</span></span>
