---
title: SOA uygulamaları
description: Microsoft Platformu ve araçları ile kapsayıcılı Docker uygulama yaşam döngüsü
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 37313c4eb437b6b7a362456a7d1ee3b3aecb6020
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569431"
---
# <a name="soa-applications"></a><span data-ttu-id="e3806-103">SOA uygulamaları</span><span class="sxs-lookup"><span data-stu-id="e3806-103">SOA applications</span></span>

<span data-ttu-id="e3806-104">SOA aşırı kullanılmasına bir terim oldu ve farklı kişilere çok sayıda farklı işlemler anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e3806-104">SOA was an overused term and meant so many different things to different people.</span></span> <span data-ttu-id="e3806-105">Ancak en az bir ortak payda, SOA, ya da hizmet yönlendirmesi, ortalama olarak, bu yapıyı uygulamanız farklı türde sınıflandırılabilir birden çok hizmetlerinde (en yaygın olarak HTTP Hizmetleri) ayırma tarafından mimarisi gibi ve alt sistemleri ya da diğer durumlarda, farklı katmanlarını.</span><span class="sxs-lookup"><span data-stu-id="e3806-105">But at a minimum and as a common denominator, SOA, or service orientation, mean that you structure the architecture of your application by decomposing it in multiple services (most commonly as HTTP services) that can be classified in different types like subsystems or, in other cases, as tiers.</span></span>

<span data-ttu-id="e3806-106">Bugün, tüm bağımlılıklarıyla içinde kapsayıcı görüntü dahil olduğundan, dağıtım ile ilgili sorunları çözer bu hizmetlerin Docker kapsayıcılar olarak dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e3806-106">Today, you can deploy those services as Docker containers, which solves deployment-related issues because all of the dependencies are included within the container image.</span></span> <span data-ttu-id="e3806-107">Ancak, SOAs genişletmek gerektiğinde, bağlı tek örneklerini dağıtıyorsanız zorluklar karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e3806-107">However, when you need to scale-out SOAs, you might encounter challenges if you are deploying based on single instances.</span></span> <span data-ttu-id="e3806-108">Burada yazılım veya orchestrator kümeleme Docker yardımcı olacak budur.</span><span class="sxs-lookup"><span data-stu-id="e3806-108">This is where a Docker clustering software or orchestrator will help you.</span></span> <span data-ttu-id="e3806-109">Biz mikro yaklaşımlar incelediğinizde biz şu anda sonraki bölümde daha ayrıntılı göreceğiz.</span><span class="sxs-lookup"><span data-stu-id="e3806-109">We'll look at this in greater detail in the next section when we examine microservices approaches.</span></span>

<span data-ttu-id="e3806-110">Günün sonunda, kapsayıcı kümeleme çözümleri her mikro hizmet kendi veri modelini sahibi daha gelişmiş bir mikro mimarisi veya bir hem bir geleneksel SOA mimarisi için faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="e3806-110">At the end of the day, the container clustering solutions are useful for both a traditional SOA architecture or for a more advanced microservices architecture in which each microservice owns its data model.</span></span> <span data-ttu-id="e3806-111">Ve birden çok veritabanı sayesinde, ayrıca SOA Hizmetleri tarafından paylaşılan tek yapılı veritabanlarıyla çalışma yerine veri katmanı genişletme.</span><span class="sxs-lookup"><span data-stu-id="e3806-111">And, thanks to multiple databases, you also can scale-out the data tier instead of working with monolithic databases shared by the SOA services.</span></span> <span data-ttu-id="e3806-112">Ancak, veri bölme hakkında tartışma tamamen mimarisi ve tasarım hakkında ' dir.</span><span class="sxs-lookup"><span data-stu-id="e3806-112">However, the discussion about splitting the data is purely about architecture and design.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="e3806-113">[Önceki] (state-and-data-in-docker-applications.md) [sonraki] (düzenlemek-yüksek-ölçeklenebilirlik-availability.md)</span><span class="sxs-lookup"><span data-stu-id="e3806-113">[Previous] (state-and-data-in-docker-applications.md) [Next] (orchestrate-high-scalability-availability.md)</span></span>
