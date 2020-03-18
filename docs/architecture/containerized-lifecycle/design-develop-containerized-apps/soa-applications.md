---
title: SOA uygulamaları
description: Kapsayıcıların SOA uygulamaları için yararlı bir dağıtım seçeneği olabileceğini unutmayın.
ms.date: 02/15/2019
ms.openlocfilehash: aa56ada7b14a465fb3dafd02b03b815782ac765b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70295275"
---
# <a name="service-oriented-applications"></a><span data-ttu-id="52e10-103">Hizmet odaklı uygulamalar</span><span class="sxs-lookup"><span data-stu-id="52e10-103">Service-oriented applications</span></span>

<span data-ttu-id="52e10-104">Hizmet Odaklı Mimari (SOA) farklı insanlar için çok farklı şeyler anlamına gelen aşırı kullanılan bir terimoldu.</span><span class="sxs-lookup"><span data-stu-id="52e10-104">Service-Oriented Architecture (SOA) was an overused term that meant many different things to different people.</span></span> <span data-ttu-id="52e10-105">Ancak ortak payda olarak SOA, uygulamanızın mimarisini alt sistemler veya diğer durumlarda katman lar gibi farklı türlerde sınıflandırılabilen çeşitli hizmetlere (en yaygın olarak HTTP hizmetleri olarak) ayrıştırarak yapılandırdığınız anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="52e10-105">But as a common denominator, SOA means that you structure the architecture of your application by decomposing it into several services (most commonly as HTTP services) that can be classified in different types like subsystems or, in other cases, as tiers.</span></span>

<span data-ttu-id="52e10-106">Bugün, tüm bağımlılıklar kapsayıcı görüntüsüne dahil olduğundan dağıtımla ilgili sorunları çözen bu hizmetleri Docker kapsayıcıları olarak dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52e10-106">Today, you can deploy those services as Docker containers, which solve deployment-related issues because all of the dependencies are included in the container image.</span></span> <span data-ttu-id="52e10-107">Ancak, SOA'ları ölçeklendirmeniz gerektiğinde, tek bir örneğe göre dağıtım yapıyorsunuz zorluklarla karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52e10-107">However, when you need to scale out SOAs, you might encounter challenges if you're deploying based on single instances.</span></span> <span data-ttu-id="52e10-108">Bu sorun Docker kümeleme yazılımı veya bir orkestratör kullanılarak ele alınabilir.</span><span class="sxs-lookup"><span data-stu-id="52e10-108">This challenge can be handled using Docker clustering software or an orchestrator.</span></span> <span data-ttu-id="52e10-109">Mikro hizmetler yaklaşımlarını incelediğimiz de orkestratörlere bir sonraki bölümde daha ayrıntılı olarak bakacağız.</span><span class="sxs-lookup"><span data-stu-id="52e10-109">We'll look at orchestrators in greater detail in the next section, when we explore microservices approaches.</span></span>

<span data-ttu-id="52e10-110">Docker kapsayıcıları hem geleneksel hizmet odaklı mimariler hem de daha gelişmiş microservices mimarileri için kullanışlıdır (ancak gerekli değildir).</span><span class="sxs-lookup"><span data-stu-id="52e10-110">Docker containers are useful (but not required) for both traditional service-oriented architectures and the more advanced microservices architectures.</span></span>

<span data-ttu-id="52e10-111">Günün sonunda, konteyner kümeleme çözümleri hem geleneksel SOA mimarisi hem de her microservice'in kendi veri modeline sahip olduğu daha gelişmiş bir mikrohizmet mimarisi için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="52e10-111">At the end of the day, the container clustering solutions are useful for both a traditional SOA architecture and for a more advanced microservices architecture in which each microservice owns its data model.</span></span> <span data-ttu-id="52e10-112">Birden çok veritabanı sayesinde, SOA hizmetleri tarafından paylaşılan yekpare veritabanlarıyla çalışmak yerine veri katmanını ölçeklendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52e10-112">And thanks to multiple databases, you also can scale out the data tier instead of working with monolithic databases shared by the SOA services.</span></span> <span data-ttu-id="52e10-113">Ancak, verileri bölme ile ilgili tartışma tamamen mimari ve tasarım ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="52e10-113">However, the discussion about splitting the data is purely about architecture and design.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="52e10-114">[Önceki](state-and-data-in-docker-applications.md)
>[Sonraki](orchestrate-high-scalability-availability.md)</span><span class="sxs-lookup"><span data-stu-id="52e10-114">[Previous](state-and-data-in-docker-applications.md)
[Next](orchestrate-high-scalability-availability.md)</span></span>
