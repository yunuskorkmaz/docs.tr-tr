---
title: Mikro mimarisi
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Mikro mimarisi"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 5ede1f0ad19270ca6b7556ff1bb7e4cf8ccf7cbe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="microservices-architecture"></a><span data-ttu-id="4aa9e-104">Mikro mimarisi</span><span class="sxs-lookup"><span data-stu-id="4aa9e-104">Microservices architecture</span></span>

<span data-ttu-id="4aa9e-105">Adından da anlaşılacağı gibi mikro mimarisi küçük Hizmetleri kümesi olarak bir sunucu uygulaması oluşturmak için bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="4aa9e-105">As the name implies, a microservices architecture is an approach to building a server application as a set of small services.</span></span> <span data-ttu-id="4aa9e-106">Her hizmetin kendi işleminde çalışır ve HTTP/HTTPS, WebSockets, gibi protokoller kullanan diğer işlemleri ile iletişim kurar veya [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol).</span><span class="sxs-lookup"><span data-stu-id="4aa9e-106">Each service runs in its own process and communicates with other processes using protocols such as HTTP/HTTPS, WebSockets, or [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol).</span></span> <span data-ttu-id="4aa9e-107">Her mikro hizmet belirli uçtan uca etki alanı veya iş yetenek belirli bağlam sınırında uygular ve her sınırlarına geliştirilmiş olmalıdır ve bağımsız olarak dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="4aa9e-107">Each microservice implements a specific end-to-end domain or business capability within a certain context boundary, and each must be developed autonomously and be deployable independently.</span></span> <span data-ttu-id="4aa9e-108">Son olarak, her mikro hizmet, farklı veri depolama teknolojileri (SQL, NoSQL) ve farklı programlama dillerini dayalı etki alanı mantığı (Egemenlik ve merkezi olmayan veri yönetimi) ve ilişkili etki alanı veri modeli kendi.</span><span class="sxs-lookup"><span data-stu-id="4aa9e-108">Finally, each microservice should own its related domain data model and domain logic (sovereignty and decentralized data management) based on different data storage technologies (SQL, NoSQL) and different programming languages.</span></span>

<span data-ttu-id="4aa9e-109">Hangi boyutu bir mikro olmalıdır?</span><span class="sxs-lookup"><span data-stu-id="4aa9e-109">What size should a microservice be?</span></span> <span data-ttu-id="4aa9e-110">Bir mikro hizmet geliştirirken, boyutu en önemli nokta olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="4aa9e-110">When developing a microservice, size should not be the important point.</span></span> <span data-ttu-id="4aa9e-111">Bunun yerine, en önemli nokta geniş oluşturmak için geliştirme, dağıtım ve her hizmet için ölçek otonomiye sahip şekilde Hizmetleri bağlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4aa9e-111">Instead, the important point should be to create loosely coupled services so you have autonomy of development, deployment, and scale, for each service.</span></span> <span data-ttu-id="4aa9e-112">Elbette, tanımlama ve mikro tasarlama, diğer mikro ile çok fazla doğrudan bağımlılıkları olmayan sürece, bunları olabildiğince küçük yapmak çalıştığınızda.</span><span class="sxs-lookup"><span data-stu-id="4aa9e-112">Of course, when identifying and designing microservices, you should try to make them as small as possible as long as you do not have too many direct dependencies with other microservices.</span></span> <span data-ttu-id="4aa9e-113">Daha fazla mikro hizmet boyutunu gerekir iç cohesion ve kendi bağımsızlığı diğer hizmetlerden daha önemlidir.</span><span class="sxs-lookup"><span data-stu-id="4aa9e-113">More important than the size of the microservice is the internal cohesion it must have and its independence from other services.</span></span>

<span data-ttu-id="4aa9e-114">Mikro mimarisi neden?</span><span class="sxs-lookup"><span data-stu-id="4aa9e-114">Why a microservices architecture?</span></span> <span data-ttu-id="4aa9e-115">Kısacası, uzun vadeli çeviklik sağlar.</span><span class="sxs-lookup"><span data-stu-id="4aa9e-115">In short, it provides long-term agility.</span></span> <span data-ttu-id="4aa9e-116">Mikro her ayrıntılı ve otonom yaşam döngüleri sahip çok sayıda bağımsız olarak dağıtılabilir hizmetlerini temel alarak uygulamalar oluşturmanızı sağlayarak daha iyi bakım karmaşık, büyük ve yüksek düzeyde ölçeklenebilir sistemlerinde etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="4aa9e-116">Microservices enable better maintainability in complex, large, and highly-scalable systems by letting you create applications based on many independently deployable services that each have granular and autonomous lifecycles.</span></span>

<span data-ttu-id="4aa9e-117">Ek bir avantaj olarak mikro çıkışı bağımsız olarak ölçeklendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4aa9e-117">As an additional benefit, microservices can scale out independently.</span></span> <span data-ttu-id="4aa9e-118">Bir birim olarak ölçeğini gereken tek bir tek yapılı uygulama sahip olmak yerine, belirli mikro yerine ölçeklendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4aa9e-118">Instead of having a single monolithic application that you must scale out as a unit, you can instead scale out specific microservices.</span></span> <span data-ttu-id="4aa9e-119">Bu şekilde, yalnızca ölçeklendirilmesi gerekmez diğer alanlarını uygulama ölçeklendirmek yerine isteğe bağlı desteklemek için daha fazla işlem gücü veya ağ bant genişliği gerekiyor işlevsel alan ölçeklendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4aa9e-119">That way, you can scale just the functional area that needs more processing power or network bandwidth to support demand, rather than scaling out other areas of the application that do not need to be scaled.</span></span> <span data-ttu-id="4aa9e-120">Daha az donanım gerekeceğinden, maliyet tasarrufu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="4aa9e-120">That means cost savings because you need less hardware.</span></span>

![](./media/image6.png)

<span data-ttu-id="4aa9e-121">**Şekil 4-6**.</span><span class="sxs-lookup"><span data-stu-id="4aa9e-121">**Figure 4-6**.</span></span> <span data-ttu-id="4aa9e-122">Tek yapılı dağıtım mikro yaklaşım karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="4aa9e-122">Monolithic deployment versus the microservices approach</span></span>

<span data-ttu-id="4aa9e-123">Şekil 4-6 gösterildiği gibi karmaşık, büyük ve ölçeklenebilir uygulamalar belirli, küçük alanlarının değişebildiğinden mikro yaklaşım Çevik değişiklikleri ve her mikro hizmet hızlı yinelemesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="4aa9e-123">As Figure 4-6 shows, the microservices approach allows agile changes and rapid iteration of each microservice, because you can change specific, small areas of complex, large, and scalable applications.</span></span>

<span data-ttu-id="4aa9e-124">Hassas mikro tabanlı uygulamaları etkinleştirir sürekli tümleştirme ve kesintisiz teslim yöntemleri mimarisi oluşturma.</span><span class="sxs-lookup"><span data-stu-id="4aa9e-124">Architecting fine-grained microservices-based applications enables continuous integration and continuous delivery practices.</span></span> <span data-ttu-id="4aa9e-125">Ayrıca yeni işlevler teslimini uygulamasına hızlandırır.</span><span class="sxs-lookup"><span data-stu-id="4aa9e-125">It also accelerates delivery of new functions into the application.</span></span> <span data-ttu-id="4aa9e-126">Hassas uygulamalar oluşumunu ve yalıtım modunda mikro test çalıştırmak ve bunları sınırlarına aralarında Temizle sözleşmeleri korurken gelişmesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="4aa9e-126">Fine-grained composition of applications also allows you to run and test microservices in isolation, and to evolve them autonomously while maintaining clear contracts between them.</span></span> <span data-ttu-id="4aa9e-127">Arabirimleri veya sözleşmeleri değiştirmeyin sürece tüm mikro hizmet iç uyarlamasını değiştirin veya yeni işlevsellik diğer mikro bozmadan ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4aa9e-127">As long as you do not change the interfaces or contracts, you can change the internal implementation of any microservice or add new functionality without breaking other microservices.</span></span>

<span data-ttu-id="4aa9e-128">Mikro tabanlı bir sistemle üretime geçmeden başarısı etkinleştirmek için önemli yönleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="4aa9e-128">The following are important aspects to enable success in going into production with a microservices-based system:</span></span>

-   <span data-ttu-id="4aa9e-129">İzleme ve sistem durumu hizmetleri ve altyapı denetler.</span><span class="sxs-lookup"><span data-stu-id="4aa9e-129">Monitoring and health checks of the services and infrastructure.</span></span>

-   <span data-ttu-id="4aa9e-130">Ölçeklenebilir altyapı Hizmetleri (diğer bir deyişle, Bulut ve orchestrators).</span><span class="sxs-lookup"><span data-stu-id="4aa9e-130">Scalable infrastructure for the services (that is, cloud and orchestrators).</span></span>

-   <span data-ttu-id="4aa9e-131">Güvenlik tasarımı ve uygulama, birden çok düzeyde: kimlik doğrulama, yetkilendirme, gizli yönetimi, güvenli iletişim, vs.</span><span class="sxs-lookup"><span data-stu-id="4aa9e-131">Security design and implementation at multiple levels: authentication, authorization, secrets management, secure communication, etc.</span></span>

-   <span data-ttu-id="4aa9e-132">Genellikle farklı mikro odaklanan farklı ekipler ile hızlı uygulama teslim.</span><span class="sxs-lookup"><span data-stu-id="4aa9e-132">Rapid application delivery, usually with different teams focusing on different microservices.</span></span>

-   <span data-ttu-id="4aa9e-133">DevOps ve CI/CD uygulamalar ve altyapı.</span><span class="sxs-lookup"><span data-stu-id="4aa9e-133">DevOps and CI/CD practices and infrastructure.</span></span>

<span data-ttu-id="4aa9e-134">Bu, yalnızca ilk üç kapsamında veya bu kılavuzda sunulan.</span><span class="sxs-lookup"><span data-stu-id="4aa9e-134">Of these, only the first three are covered or introduced in this guide.</span></span> <span data-ttu-id="4aa9e-135">Uygulama yaşam döngüsü için ilgili en son iki nokta ilave kapsanan [Microsoft Platformu ve araçları ile kapsayıcılı Docker uygulama yaşam döngüsü](https://aka.ms/dockerlifecycleebook) e-Kitap.</span><span class="sxs-lookup"><span data-stu-id="4aa9e-135">The last two points, which are related to application lifecycle, are covered in the additional [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) e-book.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="4aa9e-136">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="4aa9e-136">Additional resources</span></span>

-   <span data-ttu-id="4aa9e-137">**İşareti Russinovich. Mikro: Bulut tarafından desteklenen bir uygulama revolution**
    [*https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/*](https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/)</span><span class="sxs-lookup"><span data-stu-id="4aa9e-137">**Mark Russinovich. Microservices: An application revolution powered by the cloud**
[*https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/*](https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/)</span></span>

-   <span data-ttu-id="4aa9e-138">**Martin Fowler. Mikro**
    [*http://www.martinfowler.com/articles/microservices.html*](http://www.martinfowler.com/articles/microservices.html)</span><span class="sxs-lookup"><span data-stu-id="4aa9e-138">**Martin Fowler. Microservices**
[*http://www.martinfowler.com/articles/microservices.html*](http://www.martinfowler.com/articles/microservices.html)</span></span>

-   <span data-ttu-id="4aa9e-139">**Martin Fowler. Mikro hizmet Önkoşullar**
    [*http://martinfowler.com/bliki/MicroservicePrerequisites.html*](http://martinfowler.com/bliki/MicroservicePrerequisites.html)</span><span class="sxs-lookup"><span data-stu-id="4aa9e-139">**Martin Fowler. Microservice Prerequisites**
[*http://martinfowler.com/bliki/MicroservicePrerequisites.html*](http://martinfowler.com/bliki/MicroservicePrerequisites.html)</span></span>

-   <span data-ttu-id="4aa9e-140">**Jimmy Nilsson. Öbek bulut bilgi işlem**
    [*https://www.infoq.com/articles/CCC-Jimmy-Nilsson*](https://www.infoq.com/articles/CCC-Jimmy-Nilsson)</span><span class="sxs-lookup"><span data-stu-id="4aa9e-140">**Jimmy Nilsson. Chunk Cloud Computing**
[*https://www.infoq.com/articles/CCC-Jimmy-Nilsson*](https://www.infoq.com/articles/CCC-Jimmy-Nilsson)</span></span>

-   <span data-ttu-id="4aa9e-141">**Cesar de la Torre. Microsoft Platformu ve araçları ile Docker uygulama yaşam döngüsü kapsayıcılı** (indirilebilir e-kitap) [ *https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)</span><span class="sxs-lookup"><span data-stu-id="4aa9e-141">**Cesar de la Torre. Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (downloadable e-book) [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)</span></span>




>[!div class="step-by-step"]
<span data-ttu-id="4aa9e-142">[Önceki] (hizmet-yönelimli-architecture.md) [sonraki] (veri-Egemenlik-başına-microservice.md)</span><span class="sxs-lookup"><span data-stu-id="4aa9e-142">[Previous] (service-oriented-architecture.md) [Next] (data-sovereignty-per-microservice.md)</span></span>
