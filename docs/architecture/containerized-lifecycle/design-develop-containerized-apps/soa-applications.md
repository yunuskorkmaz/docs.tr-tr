---
title: SOA uygulamaları
description: Ayrıca kapsayıcının SOA uygulamaları için yararlı bir dağıtım seçeneği olabileceğini göz önünde bulundurun.
ms.date: 08/06/2020
ms.openlocfilehash: 5cc616eaf3be31ae704320df6ec54deed9529989
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87915255"
---
# <a name="service-oriented-applications"></a><span data-ttu-id="1f06d-103">Hizmet odaklı uygulamalar</span><span class="sxs-lookup"><span data-stu-id="1f06d-103">Service-oriented applications</span></span>

<span data-ttu-id="1f06d-104">Hizmet odaklı mimari (SOA), farklı kişilere çok sayıda farklı şeyler sunan aşırı kullanılan bir terimdir.</span><span class="sxs-lookup"><span data-stu-id="1f06d-104">Service-Oriented Architecture (SOA) was an overused term that meant many different things to different people.</span></span> <span data-ttu-id="1f06d-105">Ancak, ortak paydalar olarak, SOA, alt sistemler gibi farklı türlerde sınıflandırılabilen çeşitli hizmetlere (genellikle HTTP Hizmetleri) veya başka durumlarda Katmanlar olarak sınıflandırılabilen uygulamanızın mimarisini yapılandırabilmeniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1f06d-105">But as a common denominator, SOA means that you structure the architecture of your application by decomposing it into several services (most commonly as HTTP services) that can be classified in different types like subsystems or, in other cases, as tiers.</span></span>

<span data-ttu-id="1f06d-106">Bugün, bu hizmetleri, dağıtım ile ilgili sorunları çözerek, tüm bağımlılıkların kapsayıcı görüntüsüne dahil olduğu için bu hizmetleri Docker Kapsayıcıları olarak dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f06d-106">Today, you can deploy those services as Docker containers, which solve deployment-related issues because all of the dependencies are included in the container image.</span></span> <span data-ttu-id="1f06d-107">Ancak, SOAs 'yi ölçeklendirmeniz gerektiğinde, tek örneklere dayalı dağıtım yapıyorsanız sorunlarla karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f06d-107">However, when you need to scale out SOAs, you might encounter challenges if you're deploying based on single instances.</span></span> <span data-ttu-id="1f06d-108">Bu zorluk, Docker kümeleme yazılımı veya Orchestrator kullanılarak işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="1f06d-108">This challenge can be handled using Docker clustering software or an orchestrator.</span></span> <span data-ttu-id="1f06d-109">Mikro hizmet yaklaşımlarını araştırdığınızda, sonraki bölümde bulunan düzenlemeleri daha ayrıntılı bir şekilde gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="1f06d-109">You'll get to look at orchestrators in greater detail in the next section, when you explore microservices approaches.</span></span>

<span data-ttu-id="1f06d-110">Docker Kapsayıcıları hem geleneksel hizmet yönelimli mimariler hem de daha gelişmiş mikro hizmet mimarileri için yararlıdır (ancak gerekli değildir).</span><span class="sxs-lookup"><span data-stu-id="1f06d-110">Docker containers are useful (but not required) for both traditional service-oriented architectures and the more advanced microservices architectures.</span></span>

<span data-ttu-id="1f06d-111">Günün sonunda, kapsayıcı kümeleme çözümleri hem geleneksel bir SOA mimarisi hem de her bir mikro hizmetin veri modeline sahip olduğu daha gelişmiş bir mikro hizmet mimarisi için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="1f06d-111">At the end of the day, the container clustering solutions are useful for both a traditional SOA architecture and for a more advanced microservices architecture in which each microservice owns its data model.</span></span> <span data-ttu-id="1f06d-112">Ayrıca, birden çok veritabanı sayesinde, SOA Hizmetleri tarafından paylaşılan tek parçalı veritabanları ile çalışmak yerine veri katmanını da genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f06d-112">And thanks to multiple databases, you can also scale out the data tier instead of working with monolithic databases shared by the SOA services.</span></span> <span data-ttu-id="1f06d-113">Bununla birlikte, verileri bölmek hakkında tartışma yalnızca mimari ve tasarım ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="1f06d-113">However, the discussion about splitting the data is purely about architecture and design.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="1f06d-114">[Önceki](state-and-data-in-docker-applications.md) 
> [Sonraki](orchestrate-high-scalability-availability.md)</span><span class="sxs-lookup"><span data-stu-id="1f06d-114">[Previous](state-and-data-in-docker-applications.md)
[Next](orchestrate-high-scalability-availability.md)</span></span>
