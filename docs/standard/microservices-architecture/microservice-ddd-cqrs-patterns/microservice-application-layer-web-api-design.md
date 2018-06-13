---
title: Mikro hizmet uygulama katmanı ve Web API tasarlama
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Mikro hizmet uygulama katmanı ve Web API tasarlama
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.openlocfilehash: 77e0556e4b6d9a22cf76a79ec86d744d9009a39f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33577440"
---
# <a name="designing-the-microservice-application-layer-and-web-api"></a><span data-ttu-id="306ad-103">Mikro hizmet uygulama katmanı ve Web API tasarlama</span><span class="sxs-lookup"><span data-stu-id="306ad-103">Designing the microservice application layer and Web API</span></span>

## <a name="using-solid-principles-and-dependency-injection"></a><span data-ttu-id="306ad-104">DÜZ ilkeleri ve bağımlılık ekleme kullanılarak</span><span class="sxs-lookup"><span data-stu-id="306ad-104">Using SOLID principles and Dependency Injection</span></span>

<span data-ttu-id="306ad-105">DÜZ ilkeleri mikro hizmet DDD desenlerle geliştirme gibi modern ve kritik bir uygulamada, kullanılacak kritik tekniklerle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="306ad-105">SOLID principles are critical techniques to be used in any modern and mission-critical application, such as developing a microservice with DDD patterns.</span></span> <span data-ttu-id="306ad-106">DÜZ bir kısaltma bu grupları beş temel ilkeler verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="306ad-106">SOLID is an acronym that groups five fundamental principles:</span></span>

-   <span data-ttu-id="306ad-107">Tek sorumluluk İlkesi</span><span class="sxs-lookup"><span data-stu-id="306ad-107">Single Responsibility principle</span></span>

-   <span data-ttu-id="306ad-108">Açık ve kapalı İlkesi</span><span class="sxs-lookup"><span data-stu-id="306ad-108">Open/closed principle</span></span>

-   <span data-ttu-id="306ad-109">Liskov değiştirme İlkesi</span><span class="sxs-lookup"><span data-stu-id="306ad-109">Liskov substitution principle</span></span>

-   <span data-ttu-id="306ad-110">Arabirim arasında ayrım yapma İlkesi</span><span class="sxs-lookup"><span data-stu-id="306ad-110">Interface Segregation principle</span></span>

-   <span data-ttu-id="306ad-111">Bağımlılık tersine çevirme ilkesi</span><span class="sxs-lookup"><span data-stu-id="306ad-111">Dependency Inversion principle</span></span>

<span data-ttu-id="306ad-112">DÜZ nasıl uygulamanızı veya mikro hizmet iç Katmanlar tasarlayın ve aralarındaki bağımlılıkları ayırma hakkında daha fazla.</span><span class="sxs-lookup"><span data-stu-id="306ad-112">SOLID is more about how you design your application or microservice internal layers and about decoupling dependencies between them.</span></span> <span data-ttu-id="306ad-113">Bu etki alanı, ancak uygulamanın teknik tasarım ilişkili değil.</span><span class="sxs-lookup"><span data-stu-id="306ad-113">It is not related to the domain, but to the application’s technical design.</span></span> <span data-ttu-id="306ad-114">Son ilke, bağımlılık tersine çevirme (dı) ilkesini DDD katmanların bir daha iyi ayrılmış uygulaması sağlayan rest katmanların altyapısı katmanından ayırırsınız olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="306ad-114">The final principle, the Dependency Inversion (DI) principle, allows you to decouple the infrastructure layer from the rest of the layers, which allows a better decoupled implementation of the DDD layers.</span></span>

<span data-ttu-id="306ad-115">DI bağımlılık ters çevirmeyi ilkesini uygulamak için bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="306ad-115">DI is one way to implement the Dependency Inversion principle.</span></span> <span data-ttu-id="306ad-116">Bu nesneler ve onların bağımlılıkları arasındaki bu sıkı bağ elde etmek için bir tekniktir.</span><span class="sxs-lookup"><span data-stu-id="306ad-116">It is a technique for achieving loose coupling between objects and their dependencies.</span></span> <span data-ttu-id="306ad-117">Ortak Çalışanlar doğrudan başlatmasını veya statik başvuruları kullanma yerine eylemlerini gerçekleştirmek için bir sınıf gereken nesneler için sağlanan (veya "içine eklenen") sınıfı.</span><span class="sxs-lookup"><span data-stu-id="306ad-117">Rather than directly instantiating collaborators, or using static references, the objects that a class needs in order to perform its actions are provided to (or "injected into") the class.</span></span> <span data-ttu-id="306ad-118">Çoğu zaman sınıfları bağımlılıklarını açık bağımlılıkları ilkesini izlemek vermeden kendi Oluşturucusu aracılığıyla bildirir.</span><span class="sxs-lookup"><span data-stu-id="306ad-118">Most often, classes will declare their dependencies via their constructor, allowing them to follow the Explicit Dependencies principle.</span></span> <span data-ttu-id="306ad-119">DI genellikle belirli denetimi tersine çevirme (IOC) kapsayıcılarında temel alır.</span><span class="sxs-lookup"><span data-stu-id="306ad-119">DI is usually based on specific Inversion of Control (IoC) containers.</span></span> <span data-ttu-id="306ad-120">Basit bir yerleşik IOC kapsayıcı ASP.NET Core sağlar, ancak Autofac veya Ninject gibi sık kullanılan IOC kapsayıcı de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="306ad-120">ASP.NET Core provides a simple built-in IoC container, but you can also use your favorite IoC container, like Autofac or Ninject.</span></span>

<span data-ttu-id="306ad-121">DÜZ ilkeleri izleyerek sınıflarınızı doğal olarak küçük, iyi faktörlere göre ve kolayca sınanan olma eğilimindedir.</span><span class="sxs-lookup"><span data-stu-id="306ad-121">By following the SOLID principles, your classes will tend naturally to be small, well-factored, and easily tested.</span></span> <span data-ttu-id="306ad-122">Ancak çok fazla bağımlılıkları sınıflar olarak eklenmiş varsa nasıl biliyor?</span><span class="sxs-lookup"><span data-stu-id="306ad-122">But how can you know if too many dependencies are being injected into your classes?</span></span> <span data-ttu-id="306ad-123">Oluşturucu kullanılarak dı kullanırsanız, yalnızca sizin oluşturucusu için parametre sayısı bakarak algılayan kolay olacaktır.</span><span class="sxs-lookup"><span data-stu-id="306ad-123">If you use DI through the constructor, it will be easy to detect that by just looking at the number of parameters for your constructor.</span></span> <span data-ttu-id="306ad-124">Çok fazla bağımlılıkları varsa, bu genellikle bir işaretidir (bir [kod kokusu](http://deviq.com/code-smells/)) sınıfınız çok işlemini yapmaya çalışan ve büyük olasılıkla tek sorumluluk ilkesini ihlal etme.</span><span class="sxs-lookup"><span data-stu-id="306ad-124">If there are too many dependencies, this is generally a sign (a [code smell](http://deviq.com/code-smells/)) that your class is trying to do too much, and is probably violating the Single Responsibility principle.</span></span>

<span data-ttu-id="306ad-125">DÜZ ayrıntılı olarak ele için başka bir kılavuz kalırsınız.</span><span class="sxs-lookup"><span data-stu-id="306ad-125">It would take another guide to cover SOLID in detail.</span></span> <span data-ttu-id="306ad-126">Bu nedenle, bu kılavuzda Bu konu için en az bir bilgiye sahip gerektirir.</span><span class="sxs-lookup"><span data-stu-id="306ad-126">Therefore, this guide requires you to have only a minimum knowledge of these topics.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="306ad-127">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="306ad-127">Additional resources</span></span>

-   <span data-ttu-id="306ad-128">**DÜZ: Temel OOP ilkeleri**
    [*http://deviq.com/solid/*](http://deviq.com/solid/%20)</span><span class="sxs-lookup"><span data-stu-id="306ad-128">**SOLID: Fundamental OOP Principles**
[*http://deviq.com/solid/*](http://deviq.com/solid/%20)</span></span>

-   <span data-ttu-id="306ad-129">**Ters çevirmeyi denetimi kapsayıcıları ve bağımlılık ekleme düzeni**
    [*https://martinfowler.com/articles/injection.html*](https://martinfowler.com/articles/injection.html)</span><span class="sxs-lookup"><span data-stu-id="306ad-129">**Inversion of Control Containers and the Dependency Injection pattern**
[*https://martinfowler.com/articles/injection.html*](https://martinfowler.com/articles/injection.html)</span></span>

-   <span data-ttu-id="306ad-130">**Steve Smith. Birleştirici yenilikler**
    [*https://ardalis.com/new-is-glue*](https://ardalis.com/new-is-glue)</span><span class="sxs-lookup"><span data-stu-id="306ad-130">**Steve Smith. New is Glue**
[*https://ardalis.com/new-is-glue*](https://ardalis.com/new-is-glue)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="306ad-131">[Önceki] (nosql-veritabanı-Kalıcılık-infrastructure.md) [sonraki] (microservice-application-layer-implementation-web-api.md)</span><span class="sxs-lookup"><span data-stu-id="306ad-131">[Previous] (nosql-database-persistence-infrastructure.md) [Next] (microservice-application-layer-implementation-web-api.md)</span></span>
