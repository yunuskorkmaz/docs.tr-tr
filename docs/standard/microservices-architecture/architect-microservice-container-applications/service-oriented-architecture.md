---
title: "Hizmet odaklı mimari"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Hizmet odaklı mimari"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 970ff86c77100077d4c7710c0a697d1745d35819
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="service-oriented-architecture"></a><span data-ttu-id="c4a09-104">Hizmet odaklı mimari</span><span class="sxs-lookup"><span data-stu-id="c4a09-104">Service-oriented architecture</span></span> 

<span data-ttu-id="c4a09-105">Hizmet odaklı mimari (SOA) aşırı kullanılmasına bir terim oldu ve farklı kişilere farklı işlemler amacı.</span><span class="sxs-lookup"><span data-stu-id="c4a09-105">Service-oriented architecture (SOA) was an overused term and has meant different things to different people.</span></span> <span data-ttu-id="c4a09-106">Ancak ortak payda olarak farklı alt sistemleri veya katmanları gibi olarak sınıflandırılan birden çok hizmetlerine (en yaygın olarak HTTP Hizmetleri) ayırma tarafından uygulamanızı yapısı SOA anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c4a09-106">But as a common denominator, SOA means that you structure your application by decomposing it into multiple services (most commonly as HTTP services) that can be classified as different types like subsystems or tiers.</span></span>

<span data-ttu-id="c4a09-107">Kapsayıcı görüntüde tüm bağımlılıkları içerdiğinden bu hizmetleri artık Docker kapsayıcılar olarak hangi dağıtım sorunlarını çözer dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="c4a09-107">Those services can now be deployed as Docker containers, which solves deployment issues, because all the dependencies are included in the container image.</span></span> <span data-ttu-id="c4a09-108">Ancak, SOA uygulamaları ölçeklendirme gerektiğinde ölçeklenebilirlik olabilir ve tek Docker konaklarda dağıtıyorsanız kullanılabilirlik zorluklar tabanlı.</span><span class="sxs-lookup"><span data-stu-id="c4a09-108">However, when you need to scale up SOA applications, you might have scalability and availability challenges if you are deploying based on single Docker hosts.</span></span> <span data-ttu-id="c4a09-109">Burada yazılım ya da bir orchestrator kümeleme Docker çıkışı, yardımcı olacak burada biz mikro dağıtım yaklaşımlar açıklamak sonraki bölümlerde açıklandığı gibi budur.</span><span class="sxs-lookup"><span data-stu-id="c4a09-109">This is where Docker clustering software or an orchestrator will help you out, as explained in later sections where we describe deployment approaches for microservices.</span></span>

<span data-ttu-id="c4a09-110">Docker kapsayıcıları yararlı (ancak gerekli değildir) geleneksel hizmet odaklı mimari ve daha gelişmiş mikro mimarileri için.</span><span class="sxs-lookup"><span data-stu-id="c4a09-110">Docker containers are useful (but not required) for both traditional service-oriented architectures and the more advanced microservices architectures.</span></span>

<span data-ttu-id="c4a09-111">Mikro SOA türetilen ancak SOA mikro mimarisinden farklı.</span><span class="sxs-lookup"><span data-stu-id="c4a09-111">Microservices derive from SOA, but SOA is different from microservices architecture.</span></span> <span data-ttu-id="c4a09-112">Büyük merkezi aracıları gibi özellikleri, kuruluş düzeyinde merkezi orchestrators ve [Kurumsal hizmet veri yolu (ESB)](https://en.wikipedia.org/wiki/Enterprise_service_bus) içinde SOA tipik değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="c4a09-112">Features like big central brokers, central orchestrators at the organization level, and the [Enterprise Service Bus (ESB)](https://en.wikipedia.org/wiki/Enterprise_service_bus) are typical in SOA.</span></span> <span data-ttu-id="c4a09-113">Ancak, çoğu durumda bunlar mikro hizmet topluluk koruma düzenleri.</span><span class="sxs-lookup"><span data-stu-id="c4a09-113">But in most cases, these are anti-patterns in the microservice community.</span></span> <span data-ttu-id="c4a09-114">Aslında, bazı kişiler "mikro hizmet mimarisi doğru şekilde yapabilmeniz SOA olduğunu." karşıdır</span><span class="sxs-lookup"><span data-stu-id="c4a09-114">In fact, some people argue that “The microservice architecture is SOA done right.”</span></span>

<span data-ttu-id="c4a09-115">Bir SOA yaklaşım mikro hizmet mimarisinde kullanılan teknikleri ve gereksinimleri daha az Düzenleyici olduğundan bu kılavuz mikro üzerinde odaklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c4a09-115">This guide focuses on microservices, because a SOA approach is less prescriptive than the requirements and techniques used in a microservice architecture.</span></span> <span data-ttu-id="c4a09-116">Mikro hizmet tabanlı bir uygulama oluşturmak nasıl biliyorsanız, ayrıca daha basit bir hizmet odaklı uygulamasının nasıl oluşturulacağını bilmeniz.</span><span class="sxs-lookup"><span data-stu-id="c4a09-116">If you know how to build a microservice-based application, you also know how to build a simpler service-oriented application.</span></span>




>[!div class="step-by-step"]
<span data-ttu-id="c4a09-117">[Önceki] (docker-uygulama-durumu-data.md) [sonraki] (mikro-architecture.md)</span><span class="sxs-lookup"><span data-stu-id="c4a09-117">[Previous] (docker-application-state-data.md) [Next] (microservices-architecture.md)</span></span>
