---
title: Mikro hizmet uygulama katmanı ve Web API’sini tasarlama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Uygulama katmanını tasarlamaya yönelik katı ilkelere ilişkin kısa bir açıklama.
ms.date: 10/08/2018
ms.openlocfilehash: 3c3b9f74e76e01deafa1f97de5d3250d57716014
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296740"
---
# <a name="design-the-microservice-application-layer-and-web-api"></a><span data-ttu-id="cb789-103">Mikro hizmet uygulama katmanını ve Web API 'sini tasarlama</span><span class="sxs-lookup"><span data-stu-id="cb789-103">Design the microservice application layer and Web API</span></span>

## <a name="use-solid-principles-and-dependency-injection"></a><span data-ttu-id="cb789-104">KATı ilkeler ve bağımlılık ekleme kullanma</span><span class="sxs-lookup"><span data-stu-id="cb789-104">Use SOLID principles and Dependency Injection</span></span>

<span data-ttu-id="cb789-105">KATı ilkeler, DDD desenleriyle mikro hizmet geliştirme gibi tüm modern ve görev açısından kritik bir uygulamada kullanılması için kritik tekniklerdir.</span><span class="sxs-lookup"><span data-stu-id="cb789-105">SOLID principles are critical techniques to be used in any modern and mission-critical application, such as developing a microservice with DDD patterns.</span></span> <span data-ttu-id="cb789-106">SOLID, beş temel ilkeden oluşan bir kısaltmakta:</span><span class="sxs-lookup"><span data-stu-id="cb789-106">SOLID is an acronym that groups five fundamental principles:</span></span>

- <span data-ttu-id="cb789-107">Tek sorumluluk ilkesi</span><span class="sxs-lookup"><span data-stu-id="cb789-107">Single Responsibility principle</span></span>

- <span data-ttu-id="cb789-108">Açık/kapalı ilke</span><span class="sxs-lookup"><span data-stu-id="cb789-108">Open/closed principle</span></span>

- <span data-ttu-id="cb789-109">Lizkov değiştirme ilkesi</span><span class="sxs-lookup"><span data-stu-id="cb789-109">Liskov substitution principle</span></span>

- <span data-ttu-id="cb789-110">Arabirim ayırma ilkesi</span><span class="sxs-lookup"><span data-stu-id="cb789-110">Interface Segregation principle</span></span>

- <span data-ttu-id="cb789-111">Bağımlılık Inversion ilkesi</span><span class="sxs-lookup"><span data-stu-id="cb789-111">Dependency Inversion principle</span></span>

<span data-ttu-id="cb789-112">SOLID, uygulamanızı veya mikro hizmet iç Katmanlarınızı tasarlama ve bunlar arasındaki bağımlılıkları çözme hakkında daha fazla bilgi.</span><span class="sxs-lookup"><span data-stu-id="cb789-112">SOLID is more about how you design your application or microservice internal layers and about decoupling dependencies between them.</span></span> <span data-ttu-id="cb789-113">Bu, etki alanı ile ilgili değil, uygulamanın teknik tasarımına yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="cb789-113">It is not related to the domain, but to the application’s technical design.</span></span> <span data-ttu-id="cb789-114">Son ilke olan bağımlılık sürümü prensibi, altyapı katmanını katmanların geri kalanından ayırarak, DDD katmanlarının daha iyi ayrılmış bir uygulamasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="cb789-114">The final principle, the Dependency Inversion principle, allows you to decouple the infrastructure layer from the rest of the layers, which allows a better decoupled implementation of the DDD layers.</span></span>

<span data-ttu-id="cb789-115">Bağımlılık ekleme (dı), bağımlılık Inversion ilkesini uygulamak için bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="cb789-115">Dependency Injection (DI) is one way to implement the Dependency Inversion principle.</span></span> <span data-ttu-id="cb789-116">Nesneler ve bunların bağımlılıkları arasında gevşek bir bağlantısı elde etmek için bir tekniktir.</span><span class="sxs-lookup"><span data-stu-id="cb789-116">It is a technique for achieving loose coupling between objects and their dependencies.</span></span> <span data-ttu-id="cb789-117">Ortak çalışanların doğrudan örneklendiği veya statik başvuruların (yani, New...) kullanılması yerine, bir sınıfın eylemlerini gerçekleştirmek için ihtiyaç duyacağı nesneler sınıfına (veya "eklenen") sunulur.</span><span class="sxs-lookup"><span data-stu-id="cb789-117">Rather than directly instantiating collaborators, or using static references (that is, using new…), the objects that a class needs in order to perform its actions are provided to (or "injected into") the class.</span></span> <span data-ttu-id="cb789-118">Çoğu zaman, sınıflar kendi bağımlılıklarıyla kendi bağımlılıklarını bildirir ve bu kullanıcıların açık bağımlılıklar ilkesini izlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="cb789-118">Most often, classes will declare their dependencies via their constructor, allowing them to follow the Explicit Dependencies principle.</span></span> <span data-ttu-id="cb789-119">Bağımlılık ekleme, genellikle Denetim (IOC) kapsayıcılarının belirli bir INVERSION tabanlıdır.</span><span class="sxs-lookup"><span data-stu-id="cb789-119">Dependency Injection is usually based on specific Inversion of Control (IoC) containers.</span></span> <span data-ttu-id="cb789-120">ASP.NET Core basit bir yerleşik IOC kapsayıcısı sağlar, ancak Autofac veya Neklemesine benzer şekilde, en sevdiğiniz IOC kapsayıcısını de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cb789-120">ASP.NET Core provides a simple built-in IoC container, but you can also use your favorite IoC container, like Autofac or Ninject.</span></span>

<span data-ttu-id="cb789-121">DÜZ ilkeleri izleyerek, sınıflarınız doğal olarak küçük, iyi bir şekilde ve kolayca test edilir.</span><span class="sxs-lookup"><span data-stu-id="cb789-121">By following the SOLID principles, your classes will tend naturally to be small, well-factored, and easily tested.</span></span> <span data-ttu-id="cb789-122">Ancak sınıflarınıza çok fazla bağımlılık eklediyseniz nasıl emin olabilirsiniz?</span><span class="sxs-lookup"><span data-stu-id="cb789-122">But how can you know if too many dependencies are being injected into your classes?</span></span> <span data-ttu-id="cb789-123">Oluşturucuyu Oluşturucu aracılığıyla kullanırsanız, yalnızca kurucularınızın parametre sayısına bakarak bunu tespit etmek kolay olur.</span><span class="sxs-lookup"><span data-stu-id="cb789-123">If you use DI through the constructor, it will be easy to detect that by just looking at the number of parameters for your constructor.</span></span> <span data-ttu-id="cb789-124">Çok fazla bağımlılık varsa, bu genellikle sınıfınızın çok fazla yapmaya çalıştığı ve muhtemelen tek sorumluluk ilkesini ihlal eden bir imzadır ( [kod kokusu](https://deviq.com/code-smells/)).</span><span class="sxs-lookup"><span data-stu-id="cb789-124">If there are too many dependencies, this is generally a sign (a [code smell](https://deviq.com/code-smells/)) that your class is trying to do too much, and is probably violating the Single Responsibility principle.</span></span>

<span data-ttu-id="cb789-125">Ayrıntılı bir şekilde ele almak için başka bir kılavuz alır.</span><span class="sxs-lookup"><span data-stu-id="cb789-125">It would take another guide to cover SOLID in detail.</span></span> <span data-ttu-id="cb789-126">Bu nedenle bu kılavuzda, bu konularda yalnızca en az bilgiye sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="cb789-126">Therefore, this guide requires you to have only a minimum knowledge of these topics.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="cb789-127">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="cb789-127">Additional resources</span></span>

- <span data-ttu-id="cb789-128">**SAĞLAM Temel OOP Ilkeleri** </span><span class="sxs-lookup"><span data-stu-id="cb789-128">**SOLID: Fundamental OOP Principles** </span></span>\
  <https://deviq.com/solid/>

- <span data-ttu-id="cb789-129">**Denetim kapsayıcıları ve bağımlılık ekleme deseninin Inversion 'ı** </span><span class="sxs-lookup"><span data-stu-id="cb789-129">**Inversion of Control Containers and the Dependency Injection pattern** </span></span>\
  <https://martinfowler.com/articles/injection.html>

- <span data-ttu-id="cb789-130">**Steve Smith. Yeni bir tutkalla** </span><span class="sxs-lookup"><span data-stu-id="cb789-130">**Steve Smith. New is Glue** </span></span>\
  <https://ardalis.com/new-is-glue>

> [!div class="step-by-step"]
> <span data-ttu-id="cb789-131">[Önceki](nosql-database-persistence-infrastructure.md)İleri
> [](microservice-application-layer-implementation-web-api.md)</span><span class="sxs-lookup"><span data-stu-id="cb789-131">[Previous](nosql-database-persistence-infrastructure.md)
[Next](microservice-application-layer-implementation-web-api.md)</span></span>
