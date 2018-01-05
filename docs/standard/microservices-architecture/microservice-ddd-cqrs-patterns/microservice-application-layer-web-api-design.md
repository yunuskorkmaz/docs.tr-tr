---
title: "Mikro hizmet uygulama katmanı ve Web API tasarlama"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Mikro hizmet uygulama katmanı ve Web API tasarlama"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c166e0286d0769e24a6361037eb6c4694fb821ae
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="designing-the-microservice-application-layer-and-web-api"></a><span data-ttu-id="e2e1e-104">Mikro hizmet uygulama katmanı ve Web API tasarlama</span><span class="sxs-lookup"><span data-stu-id="e2e1e-104">Designing the microservice application layer and Web API</span></span>

## <a name="using-solid-principles-and-dependency-injection"></a><span data-ttu-id="e2e1e-105">DÜZ ilkeleri ve bağımlılık ekleme kullanılarak</span><span class="sxs-lookup"><span data-stu-id="e2e1e-105">Using SOLID principles and Dependency Injection</span></span>

<span data-ttu-id="e2e1e-106">DÜZ ilkeleri mikro hizmet DDD desenlerle geliştirme gibi modern ve kritik bir uygulamada, kullanılacak kritik tekniklerle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="e2e1e-106">SOLID principles are critical techniques to be used in any modern and mission-critical application, such as developing a microservice with DDD patterns.</span></span> <span data-ttu-id="e2e1e-107">DÜZ bir kısaltma bu grupları beş temel ilkeler verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="e2e1e-107">SOLID is an acronym that groups five fundamental principles:</span></span>

-   <span data-ttu-id="e2e1e-108">Tek sorumluluk İlkesi</span><span class="sxs-lookup"><span data-stu-id="e2e1e-108">Single Responsibility principle</span></span>

-   <span data-ttu-id="e2e1e-109">Açık ve kapalı İlkesi</span><span class="sxs-lookup"><span data-stu-id="e2e1e-109">Open/closed principle</span></span>

-   <span data-ttu-id="e2e1e-110">Liskov değiştirme İlkesi</span><span class="sxs-lookup"><span data-stu-id="e2e1e-110">Liskov substitution principle</span></span>

-   <span data-ttu-id="e2e1e-111">Ters çevirmeyi arasında ayrım yapma İlkesi</span><span class="sxs-lookup"><span data-stu-id="e2e1e-111">Inversion Segregation principle</span></span>

-   <span data-ttu-id="e2e1e-112">Bağımlılık tersine çevirme ilkesi</span><span class="sxs-lookup"><span data-stu-id="e2e1e-112">Dependency Inversion principle</span></span>

<span data-ttu-id="e2e1e-113">DÜZ nasıl uygulamanızı veya mikro hizmet iç Katmanlar tasarlayın ve aralarındaki bağımlılıkları ayırma hakkında daha fazla.</span><span class="sxs-lookup"><span data-stu-id="e2e1e-113">SOLID is more about how you design your application or microservice internal layers and about decoupling dependencies between them.</span></span> <span data-ttu-id="e2e1e-114">Bu etki alanı, ancak uygulamanın teknik tasarım ilişkili değil.</span><span class="sxs-lookup"><span data-stu-id="e2e1e-114">It is not related to the domain, but to the application’s technical design.</span></span> <span data-ttu-id="e2e1e-115">Son ilke, bağımlılık tersine çevirme (dı) ilkesini DDD katmanların bir daha iyi ayrılmış uygulaması sağlayan rest katmanların altyapısı katmanından ayırırsınız olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="e2e1e-115">The final principle, the Dependency Inversion (DI) principle, allows you to decouple the infrastructure layer from the rest of the layers, which allows a better decoupled implementation of the DDD layers.</span></span>

<span data-ttu-id="e2e1e-116">DI bağımlılık ters çevirmeyi ilkesini uygulamak için bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="e2e1e-116">DI is one way to implement the Dependency Inversion principle.</span></span> <span data-ttu-id="e2e1e-117">Bu nesneler ve onların bağımlılıkları arasındaki bu sıkı bağ elde etmek için bir tekniktir.</span><span class="sxs-lookup"><span data-stu-id="e2e1e-117">It is a technique for achieving loose coupling between objects and their dependencies.</span></span> <span data-ttu-id="e2e1e-118">Ortak Çalışanlar doğrudan başlatmasını veya statik başvuruları kullanma yerine eylemlerini gerçekleştirmek için bir sınıf gereken nesneler için sağlanan (veya "içine eklenen") sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e2e1e-118">Rather than directly instantiating collaborators, or using static references, the objects that a class needs in order to perform its actions are provided to (or "injected into") the class.</span></span> <span data-ttu-id="e2e1e-119">Çoğu zaman sınıfları bağımlılıklarını açık bağımlılıkları ilkesini izlemek vermeden kendi Oluşturucusu aracılığıyla bildirir.</span><span class="sxs-lookup"><span data-stu-id="e2e1e-119">Most often, classes will declare their dependencies via their constructor, allowing them to follow the Explicit Dependencies principle.</span></span> <span data-ttu-id="e2e1e-120">DI genellikle belirli denetimi tersine çevirme (IOC) kapsayıcılarında temel alır.</span><span class="sxs-lookup"><span data-stu-id="e2e1e-120">DI is usually based on specific Inversion of Control (IoC) containers.</span></span> <span data-ttu-id="e2e1e-121">Basit bir yerleşik IOC kapsayıcı ASP.NET Core sağlar, ancak Autofac veya Ninject gibi sık kullanılan IOC kapsayıcı de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2e1e-121">ASP.NET Core provides a simple built-in IoC container, but you can also use your favorite IoC container, like Autofac or Ninject.</span></span>

<span data-ttu-id="e2e1e-122">DÜZ ilkeleri izleyerek sınıflarınızı doğal olarak küçük, iyi faktörlere göre ve kolayca sınanan olma eğilimindedir.</span><span class="sxs-lookup"><span data-stu-id="e2e1e-122">By following the SOLID principles, your classes will tend naturally to be small, well-factored, and easily tested.</span></span> <span data-ttu-id="e2e1e-123">Ancak çok fazla bağımlılıkları sınıflar olarak eklenmiş varsa nasıl biliyor?</span><span class="sxs-lookup"><span data-stu-id="e2e1e-123">But how can you know if too many dependencies are being injected into your classes?</span></span> <span data-ttu-id="e2e1e-124">Oluşturucu kullanılarak dı kullanırsanız, yalnızca sizin oluşturucusu için parametre sayısı bakarak algılayan kolay olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e2e1e-124">If you use DI through the constructor, it will be easy to detect that by just looking at the number of parameters for your constructor.</span></span> <span data-ttu-id="e2e1e-125">Çok fazla bağımlılıkları varsa, bu genellikle bir işaretidir (bir [kod kokusu](http://deviq.com/code-smells/)) sınıfınız çok işlemini yapmaya çalışan ve büyük olasılıkla tek sorumluluk ilkesini ihlal etme.</span><span class="sxs-lookup"><span data-stu-id="e2e1e-125">If there are too many dependencies, this is generally a sign (a [code smell](http://deviq.com/code-smells/)) that your class is trying to do too much, and is probably violating the Single Responsibility principle.</span></span>

<span data-ttu-id="e2e1e-126">DÜZ ayrıntılı olarak ele için başka bir kılavuz kalırsınız.</span><span class="sxs-lookup"><span data-stu-id="e2e1e-126">It would take another guide to cover SOLID in detail.</span></span> <span data-ttu-id="e2e1e-127">Bu nedenle, bu kılavuzda Bu konu için en az bir bilgiye sahip gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e2e1e-127">Therefore, this guide requires you to have only a minimum knowledge of these topics.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="e2e1e-128">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="e2e1e-128">Additional resources</span></span>

-   <span data-ttu-id="e2e1e-129">**DÜZ: Temel OOP ilkeleri**
    [*http://deviq.com/solid/*](http://deviq.com/solid/%20)</span><span class="sxs-lookup"><span data-stu-id="e2e1e-129">**SOLID: Fundamental OOP Principles**
[*http://deviq.com/solid/*](http://deviq.com/solid/%20)</span></span>

-   <span data-ttu-id="e2e1e-130">**Denetimi kapsayıcıları ve bağımlılık ekleme düzeni ters çevirmeyi**
    [*https://martinfowler.com/articles/injection.html*](https://martinfowler.com/articles/injection.html)</span><span class="sxs-lookup"><span data-stu-id="e2e1e-130">**Inversion of Control Containers and the Dependency Injection pattern**
[*https://martinfowler.com/articles/injection.html*](https://martinfowler.com/articles/injection.html)</span></span>

-   <span data-ttu-id="e2e1e-131">**Steve Smith. Birleştirici yeni**
    [*http://ardalis.com/new-is-glue*](http://ardalis.com/new-is-glue)</span><span class="sxs-lookup"><span data-stu-id="e2e1e-131">**Steve Smith. New is Glue**
[*http://ardalis.com/new-is-glue*](http://ardalis.com/new-is-glue)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="e2e1e-132">[Önceki] (nosql-veritabanı-Kalıcılık-infrastructure.md) [sonraki] (microservice-application-layer-implementation-web-api.md)</span><span class="sxs-lookup"><span data-stu-id="e2e1e-132">[Previous] (nosql-database-persistence-infrastructure.md) [Next] (microservice-application-layer-implementation-web-api.md)</span></span>
