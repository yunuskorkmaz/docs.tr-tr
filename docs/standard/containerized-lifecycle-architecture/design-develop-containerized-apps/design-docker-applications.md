---
title: "Docker uygulamaları tasarlama"
description: "Microsoft Platformu ve araçları ile kapsayıcılı Docker uygulama yaşam döngüsü"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.openlocfilehash: db8376abf95aab51fad23f4b351cb772351117ac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="design-docker-applications"></a><span data-ttu-id="97a0b-104">Docker uygulamaları tasarlama</span><span class="sxs-lookup"><span data-stu-id="97a0b-104">Design Docker applications</span></span>

<span data-ttu-id="97a0b-105">Bölüm 1 kapsayıcıları ve Docker ile ilgili temel kavramlar sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="97a0b-105">Chapter 1 introduced the fundamental concepts regarding containers and Docker.</span></span> <span data-ttu-id="97a0b-106">Bu bilgileri başlamak için gereken bilgileri temel düzeyidir.</span><span class="sxs-lookup"><span data-stu-id="97a0b-106">That information is the basic level of information you need to get started.</span></span> <span data-ttu-id="97a0b-107">Ancak, kurumsal uygulamalar karmaşık ve oluşan tek bir hizmet veya kapsayıcı yerine birden çok Hizmetleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="97a0b-107">But, enterprise applications can be complex and composed of multiple services instead of a single service or container.</span></span> <span data-ttu-id="97a0b-108">Bu isteğe bağlı kullanım durumları için ek yaklaşımlar orchestration kavramları tasarım, Service-Oriented mimarisi (SOA) gibi ve daha gelişmiş mikro kavramlar ve kapsayıcı için bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="97a0b-108">For those optional use cases, you need to know additional approaches to design, such as Service-Oriented Architecture (SOA) and the more advanced microservices concepts and container orchestration concepts.</span></span> <span data-ttu-id="97a0b-109">Bu belgenin kapsamı mikro için sınırlı değildir, ancak ayrıca kapsayıcıları ve Docker normal SAO, arka plan görevleri veya işleri kullanmak, veya hatta olduğundan için Docker tüm uygulama yaşam döngüsü, bu nedenle, bu mikro mimarisi derinlemesine keşfetmek değil tek yapılı uygulama dağıtım yaklaşımlar ile.</span><span class="sxs-lookup"><span data-stu-id="97a0b-109">The scope of this document is not limited to microservices but to any Docker application life cycle, therefore, it does not explore microservices architecture in depth because you also can use containers and Docker with regular SAO, background tasks or jobs, or even with monolithic application deployment approaches.</span></span>

<span data-ttu-id="97a0b-110">Ancak, biz DevOps ve uygulama yaşam döngüsü alın önce nasıl tasarım kalacaklarını bilmek ve uygulamanızı ve tasarım seçimlerinize nelerdir oluşturmak önem taşır.</span><span class="sxs-lookup"><span data-stu-id="97a0b-110">However, before we get into the application life cycle and DevOps, it is important to know how you are going to design and construct your application and what are your design choices.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="97a0b-111">[Önceki] (index.md) [sonraki] (ortak-kapsayıcı-design-principles.md)</span><span class="sxs-lookup"><span data-stu-id="97a0b-111">[Previous] (index.md) [Next] (common-container-design-principles.md)</span></span>
