---
title: SOA uygulamaları
description: Kapsayıcıları SOA uygulamalar için kullanışlı bir dağıtım seçeneği de olabilir aklınızda size aittir.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: 4fd39e075c5730cf7fddb0138cdb5267a914c91f
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56221270"
---
# <a name="soa-applications"></a><span data-ttu-id="7342d-103">SOA uygulamaları</span><span class="sxs-lookup"><span data-stu-id="7342d-103">SOA applications</span></span>

<span data-ttu-id="7342d-104">SOA aşırı kullanılmasına bir terim olan ve çok sayıda farklı şeyler farklı kişilere geliyordu.</span><span class="sxs-lookup"><span data-stu-id="7342d-104">SOA was an overused term and meant so many different things to different people.</span></span> <span data-ttu-id="7342d-105">Ancak bu, yapı mimarisi (en yaygın olarak HTTP Hizmetleri) farklı türde sınıflandırılabilir birden çok Hizmetleri'nde parçalama tarafından uygulamanızın en az ve kullanımın ortak paydası olmasını, SOA, veya hizmet yönlendirmesi, ortalama olarak alt sistemler ister ya da diğer durumlarda, farklı katmanları.</span><span class="sxs-lookup"><span data-stu-id="7342d-105">But at a minimum and as a common denominator, SOA, or service orientation, mean that you structure the architecture of your application by decomposing it in multiple services (most commonly as HTTP services) that can be classified in different types like subsystems or, in other cases, as tiers.</span></span>

<span data-ttu-id="7342d-106">Bugün, kapsayıcı görüntüsü içinde bulunan tüm bağımlılıkları olduğundan, dağıtımıyla ilgili sorunları çözer. Bu hizmetleri Docker kapsayıcıları olarak dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7342d-106">Today, you can deploy those services as Docker containers, which solves deployment-related issues because all of the dependencies are included within the container image.</span></span> <span data-ttu-id="7342d-107">Ancak, SOAs genişletmek gerektiğinde bağlı olarak tek örnek dağıtıyorsanız zorlukları karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7342d-107">However, when you need to scale-out SOAs, you might encounter challenges if you are deploying based on single instances.</span></span> <span data-ttu-id="7342d-108">Burada bir Docker yazılım veya orchestrator kümeleme yardımcı olacak budur.</span><span class="sxs-lookup"><span data-stu-id="7342d-108">This is where a Docker clustering software or orchestrator will help you.</span></span> <span data-ttu-id="7342d-109">Mikro hizmetler yaklaşımları inceleyeceğiz, şu anda sonraki bölümde daha ayrıntılı olarak inceleyeceğiz.</span><span class="sxs-lookup"><span data-stu-id="7342d-109">We'll look at this in greater detail in the next section when we examine microservices approaches.</span></span>

<span data-ttu-id="7342d-110">Günün sonunda, kapsayıcı kümeleme çözümleri daha gelişmiş bir mikro hizmetler mimarisi her mikro hizmet kendi veri modelini sahip olduğu veya bir hem bir geleneksel SOA mimarisi için kullanışlı olur.</span><span class="sxs-lookup"><span data-stu-id="7342d-110">At the end of the day, the container clustering solutions are useful for both a traditional SOA architecture or for a more advanced microservices architecture in which each microservice owns its data model.</span></span> <span data-ttu-id="7342d-111">Ayrıca, birden çok veritabanı sayesinde, ayrıca SOA Hizmetleri tarafından paylaşılan tek parça veritabanlarıyla çalışmak yerine veri katmanı ölçeklendirme.</span><span class="sxs-lookup"><span data-stu-id="7342d-111">And, thanks to multiple databases, you also can scale-out the data tier instead of working with monolithic databases shared by the SOA services.</span></span> <span data-ttu-id="7342d-112">Ancak, verileri bölme hakkında bir tartışma tamamen mimari ve tasarım hakkında olur.</span><span class="sxs-lookup"><span data-stu-id="7342d-112">However, the discussion about splitting the data is purely about architecture and design.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="7342d-113">[Önceki](state-and-data-in-docker-applications.md)
>[İleri](orchestrate-high-scalability-availability.md)</span><span class="sxs-lookup"><span data-stu-id="7342d-113">[Previous](state-and-data-in-docker-applications.md)
[Next](orchestrate-high-scalability-availability.md)</span></span>