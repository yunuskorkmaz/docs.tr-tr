---
title: "SOA uygulamaları"
description: "Microsoft Platformu ve araçları ile kapsayıcılı Docker uygulama yaşam döngüsü"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 92a69ccd18759be3b319395d8609d65bb6d3e1b6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="soa-applications"></a><span data-ttu-id="d4a2a-104">SOA uygulamaları</span><span class="sxs-lookup"><span data-stu-id="d4a2a-104">SOA applications</span></span>

<span data-ttu-id="d4a2a-105">SOA aşırı kullanılmasına bir terim oldu ve farklı kişilere çok sayıda farklı işlemler anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d4a2a-105">SOA was an overused term and meant so many different things to different people.</span></span> <span data-ttu-id="d4a2a-106">Ancak en az bir ortak payda, SOA, ya da hizmet yönlendirmesi, ortalama olarak, bu yapıyı uygulamanız farklı türde sınıflandırılabilir birden çok hizmetlerinde (en yaygın olarak HTTP Hizmetleri) ayırma tarafından mimarisi gibi ve alt sistemleri ya da diğer durumlarda, farklı katmanlarını.</span><span class="sxs-lookup"><span data-stu-id="d4a2a-106">But at a minimum and as a common denominator, SOA, or service orientation, mean that you structure the architecture of your application by decomposing it in multiple services (most commonly as HTTP services) that can be classified in different types like subsystems or, in other cases, as tiers.</span></span>

<span data-ttu-id="d4a2a-107">Bugün, tüm bağımlılıklarıyla içinde kapsayıcı görüntü dahil olduğundan, dağıtım ile ilgili sorunları çözer bu hizmetlerin Docker kapsayıcılar olarak dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4a2a-107">Today, you can deploy those services as Docker containers, which solves deployment-related issues because all of the dependencies are included within the container image.</span></span> <span data-ttu-id="d4a2a-108">Ancak, SOAs genişletmek gerektiğinde, bağlı tek örneklerini dağıtıyorsanız zorluklar karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4a2a-108">However, when you need to scale-out SOAs, you might encounter challenges if you are deploying based on single instances.</span></span> <span data-ttu-id="d4a2a-109">Burada yazılım veya orchestrator kümeleme Docker yardımcı olacak budur.</span><span class="sxs-lookup"><span data-stu-id="d4a2a-109">This is where a Docker clustering software or orchestrator will help you.</span></span> <span data-ttu-id="d4a2a-110">Biz mikro yaklaşımlar incelediğinizde biz şu anda sonraki bölümde daha ayrıntılı göreceğiz.</span><span class="sxs-lookup"><span data-stu-id="d4a2a-110">We'll look at this in greater detail in the next section when we examine microservices approaches.</span></span>

<span data-ttu-id="d4a2a-111">Günün sonunda, kapsayıcı kümeleme çözümleri her mikro hizmet kendi veri modelini sahibi daha gelişmiş bir mikro mimarisi veya bir hem bir geleneksel SOA mimarisi için faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="d4a2a-111">At the end of the day, the container clustering solutions are useful for both a traditional SOA architecture or for a more advanced microservices architecture in which each microservice owns its data model.</span></span> <span data-ttu-id="d4a2a-112">Ve birden çok veritabanı sayesinde, ayrıca SOA Hizmetleri tarafından paylaşılan tek yapılı veritabanlarıyla çalışma yerine veri katmanı genişletme.</span><span class="sxs-lookup"><span data-stu-id="d4a2a-112">And, thanks to multiple databases, you also can scale-out the data tier instead of working with monolithic databases shared by the SOA services.</span></span> <span data-ttu-id="d4a2a-113">Ancak, veri bölme hakkında tartışma tamamen mimarisi ve tasarım hakkında ' dir.</span><span class="sxs-lookup"><span data-stu-id="d4a2a-113">However, the discussion about splitting the data is purely about architecture and design.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="d4a2a-114">[Önceki] (state-and-data-in-docker-applications.md) [sonraki] (düzenlemek-yüksek-ölçeklenebilirlik-availability.md)</span><span class="sxs-lookup"><span data-stu-id="d4a2a-114">[Previous] (state-and-data-in-docker-applications.md) [Next] (orchestrate-high-scalability-availability.md)</span></span>
