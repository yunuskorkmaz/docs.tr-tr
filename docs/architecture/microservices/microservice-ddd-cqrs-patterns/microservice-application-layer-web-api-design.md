---
title: Mikro hizmet uygulama katmanı ve Web API’sini tasarlama
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | Uygulama katmanının tasarımına ilişkin SOLID ilkelerinden kısa bir söz.
ms.date: 10/08/2018
ms.openlocfilehash: 491aa7bd90910c7f6c1d0ab56edfe0ae057ca006
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988459"
---
# <a name="design-the-microservice-application-layer-and-web-api"></a><span data-ttu-id="5e644-103">Mikro hizmet uygulama katmanını ve Web API'sini tasarlayın</span><span class="sxs-lookup"><span data-stu-id="5e644-103">Design the microservice application layer and Web API</span></span>

## <a name="use-solid-principles-and-dependency-injection"></a><span data-ttu-id="5e644-104">SOLID prensipleri ve Bağımlılık Enjeksiyonu kullanın</span><span class="sxs-lookup"><span data-stu-id="5e644-104">Use SOLID principles and Dependency Injection</span></span>

<span data-ttu-id="5e644-105">SOLID ilkeleri, DDD desenli bir mikro hizmet geliştirmek gibi her türlü modern ve görev açısından kritik uygulamada kullanılacak kritik tekniklerdir.</span><span class="sxs-lookup"><span data-stu-id="5e644-105">SOLID principles are critical techniques to be used in any modern and mission-critical application, such as developing a microservice with DDD patterns.</span></span> <span data-ttu-id="5e644-106">SOLID, beş temel ilkeyi bir arada gösteren bir kısaltmadır:</span><span class="sxs-lookup"><span data-stu-id="5e644-106">SOLID is an acronym that groups five fundamental principles:</span></span>

- <span data-ttu-id="5e644-107">Tek Sorumluluk ilkesi</span><span class="sxs-lookup"><span data-stu-id="5e644-107">Single Responsibility principle</span></span>

- <span data-ttu-id="5e644-108">Açık/kapalı ilke</span><span class="sxs-lookup"><span data-stu-id="5e644-108">Open/closed principle</span></span>

- <span data-ttu-id="5e644-109">Liskov ikame ilkesi</span><span class="sxs-lookup"><span data-stu-id="5e644-109">Liskov substitution principle</span></span>

- <span data-ttu-id="5e644-110">Arayüz Ayrımı ilkesi</span><span class="sxs-lookup"><span data-stu-id="5e644-110">Interface Segregation principle</span></span>

- <span data-ttu-id="5e644-111">Bağımlılık Ters Çevirme ilkesi</span><span class="sxs-lookup"><span data-stu-id="5e644-111">Dependency Inversion principle</span></span>

<span data-ttu-id="5e644-112">SOLID, uygulamanızı veya microservice iç katmanlarınızı nasıl tasarladığınız ve aralarındaki bağımlılıkları nasıl ayırdığınızla ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="5e644-112">SOLID is more about how you design your application or microservice internal layers and about decoupling dependencies between them.</span></span> <span data-ttu-id="5e644-113">Etki alanıyla değil, uygulamanın teknik tasarımıyla ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="5e644-113">It is not related to the domain, but to the application's technical design.</span></span> <span data-ttu-id="5e644-114">Son ilke, Bağımlılık Inversion ilkesi, DDD katmanlarıdaha iyi bir ayrılmış uygulama sağlar katmanları, geri kalanından altyapı katmanı ayırmak için izin verir.</span><span class="sxs-lookup"><span data-stu-id="5e644-114">The final principle, the Dependency Inversion principle, allows you to decouple the infrastructure layer from the rest of the layers, which allows a better decoupled implementation of the DDD layers.</span></span>

<span data-ttu-id="5e644-115">Bağımlılık Enjeksiyon (DI) Bağımlılık Inversion ilkesini uygulamak için bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="5e644-115">Dependency Injection (DI) is one way to implement the Dependency Inversion principle.</span></span> <span data-ttu-id="5e644-116">Bu nesneler ve onların bağımlılıkları arasında gevşek bağlantı elde etmek için bir tekniktir.</span><span class="sxs-lookup"><span data-stu-id="5e644-116">It is a technique for achieving loose coupling between objects and their dependencies.</span></span> <span data-ttu-id="5e644-117">İşbirlikçileri doğrudan anında kullanmak veya statik başvuruları kullanmak (diğer bir deyişle yeni...) kullanmak yerine, bir sınıfın eylemlerini gerçekleştirmek için ihtiyaç duyduğu nesneler sınıfa sağlanır (veya "enjekte edilir").</span><span class="sxs-lookup"><span data-stu-id="5e644-117">Rather than directly instantiating collaborators, or using static references (that is, using new…), the objects that a class needs in order to perform its actions are provided to (or "injected into") the class.</span></span> <span data-ttu-id="5e644-118">Çoğu zaman, sınıflar bağımlılıklarını yapıcıları aracılığıyla beyan ederek Açık Bağımlılıklar ilkesine uymalarını sağlarlar.</span><span class="sxs-lookup"><span data-stu-id="5e644-118">Most often, classes will declare their dependencies via their constructor, allowing them to follow the Explicit Dependencies principle.</span></span> <span data-ttu-id="5e644-119">Bağımlılık Enjeksiyonu genellikle kontrol (IoC) kaplarının belirli ters çevrilmelerine dayanır.</span><span class="sxs-lookup"><span data-stu-id="5e644-119">Dependency Injection is usually based on specific Inversion of Control (IoC) containers.</span></span> <span data-ttu-id="5e644-120">ASP.NET Core basit bir dahili IoC konteyner sağlar, ancak autofac veya Ninject gibi en sevdiğiniz IoC konteyner kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e644-120">ASP.NET Core provides a simple built-in IoC container, but you can also use your favorite IoC container, like Autofac or Ninject.</span></span>

<span data-ttu-id="5e644-121">SOLID ilkelerini izleyerek, sınıflarınız doğal olarak küçük, iyi faktörlü ve kolayca test edilebilir olma eğiliminde olacaktır.</span><span class="sxs-lookup"><span data-stu-id="5e644-121">By following the SOLID principles, your classes will tend naturally to be small, well-factored, and easily tested.</span></span> <span data-ttu-id="5e644-122">Ama sınıflarınıza çok fazla bağımlılık enjekte edilip edilip edilmeyişemelerini nasıl bilebilirsiniz?</span><span class="sxs-lookup"><span data-stu-id="5e644-122">But how can you know if too many dependencies are being injected into your classes?</span></span> <span data-ttu-id="5e644-123">Di'yi oluşturucu aracılığıyla kullanırsanız, bunu sadece oluşturucunuz için parametrelerin sayısına bakarak algılamak kolay olacaktır.</span><span class="sxs-lookup"><span data-stu-id="5e644-123">If you use DI through the constructor, it will be easy to detect that by just looking at the number of parameters for your constructor.</span></span> <span data-ttu-id="5e644-124">Çok fazla bağımlılık varsa, bu genellikle bir işaret [(kod kokusu)](https://deviq.com/code-smells/)sınıf çok fazla yapmaya çalışıyor ve büyük olasılıkla Tek Sorumluluk ilkesini ihlal ediyor.</span><span class="sxs-lookup"><span data-stu-id="5e644-124">If there are too many dependencies, this is generally a sign (a [code smell](https://deviq.com/code-smells/)) that your class is trying to do too much, and is probably violating the Single Responsibility principle.</span></span>

<span data-ttu-id="5e644-125">Bu ayrıntılı olarak SOLID kapsayacak şekilde başka bir rehber alacaktı.</span><span class="sxs-lookup"><span data-stu-id="5e644-125">It would take another guide to cover SOLID in detail.</span></span> <span data-ttu-id="5e644-126">Bu nedenle, bu kılavuz, bu konular hakkında yalnızca en az bilgiye sahip olmayı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5e644-126">Therefore, this guide requires you to have only a minimum knowledge of these topics.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="5e644-127">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="5e644-127">Additional resources</span></span>

- <span data-ttu-id="5e644-128">**SOLID: Temel OOP İlkeleri** </span><span class="sxs-lookup"><span data-stu-id="5e644-128">**SOLID: Fundamental OOP Principles** </span></span>\
  <https://deviq.com/solid/>

- <span data-ttu-id="5e644-129">**Kontrol Kaplarının Ters Çevrilmesi ve Bağımlılık Enjeksiyonu deseni** </span><span class="sxs-lookup"><span data-stu-id="5e644-129">**Inversion of Control Containers and the Dependency Injection pattern** </span></span>\
  <https://martinfowler.com/articles/injection.html>

- <span data-ttu-id="5e644-130">**Steve Smith' i. Yeni Tutkal olduğunu** </span><span class="sxs-lookup"><span data-stu-id="5e644-130">**Steve Smith. New is Glue** </span></span>\
  <https://ardalis.com/new-is-glue>

> [!div class="step-by-step"]
> <span data-ttu-id="5e644-131">[Önceki](nosql-database-persistence-infrastructure.md)
> [Sonraki](microservice-application-layer-implementation-web-api.md)</span><span class="sxs-lookup"><span data-stu-id="5e644-131">[Previous](nosql-database-persistence-infrastructure.md)
[Next](microservice-application-layer-implementation-web-api.md)</span></span>
