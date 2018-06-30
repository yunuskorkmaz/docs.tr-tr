---
title: Hizmet odaklı mimari
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Hizmet odaklı mimari
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 67560cc93b3d147be36a691af440bb78f2315557
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105011"
---
# <a name="service-oriented-architecture"></a><span data-ttu-id="fd6e1-103">Hizmet odaklı mimari</span><span class="sxs-lookup"><span data-stu-id="fd6e1-103">Service-oriented architecture</span></span> 

<span data-ttu-id="fd6e1-104">Hizmet odaklı mimari (SOA) aşırı kullanılmasına bir terim oldu ve farklı kişilere farklı işlemler amacı.</span><span class="sxs-lookup"><span data-stu-id="fd6e1-104">Service-oriented architecture (SOA) was an overused term and has meant different things to different people.</span></span> <span data-ttu-id="fd6e1-105">Ancak ortak payda olarak farklı alt sistemleri veya katmanları gibi olarak sınıflandırılan birden çok hizmetlerine (en yaygın olarak HTTP Hizmetleri) ayırma tarafından uygulamanızı yapısı SOA anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="fd6e1-105">But as a common denominator, SOA means that you structure your application by decomposing it into multiple services (most commonly as HTTP services) that can be classified as different types like subsystems or tiers.</span></span>

<span data-ttu-id="fd6e1-106">Kapsayıcı görüntüde tüm bağımlılıkları içerdiğinden bu hizmetleri artık Docker kapsayıcılar olarak hangi dağıtım sorunlarını çözer dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="fd6e1-106">Those services can now be deployed as Docker containers, which solves deployment issues, because all the dependencies are included in the container image.</span></span> <span data-ttu-id="fd6e1-107">Ancak, SOA uygulamaları ölçeklendirme gerektiğinde ölçeklenebilirlik olabilir ve tek Docker konaklarda dağıtıyorsanız kullanılabilirlik zorluklar tabanlı.</span><span class="sxs-lookup"><span data-stu-id="fd6e1-107">However, when you need to scale up SOA applications, you might have scalability and availability challenges if you are deploying based on single Docker hosts.</span></span> <span data-ttu-id="fd6e1-108">Burada yazılım ya da bir orchestrator kümeleme Docker çıkışı, yardımcı olacak burada biz mikro dağıtım yaklaşımlar açıklamak sonraki bölümlerde açıklandığı gibi budur.</span><span class="sxs-lookup"><span data-stu-id="fd6e1-108">This is where Docker clustering software or an orchestrator will help you out, as explained in later sections where we describe deployment approaches for microservices.</span></span>

<span data-ttu-id="fd6e1-109">Docker kapsayıcıları yararlı (ancak gerekli değildir) geleneksel hizmet odaklı mimari ve daha gelişmiş mikro mimarileri için.</span><span class="sxs-lookup"><span data-stu-id="fd6e1-109">Docker containers are useful (but not required) for both traditional service-oriented architectures and the more advanced microservices architectures.</span></span>

<span data-ttu-id="fd6e1-110">Mikro SOA türetilen ancak SOA mikro mimarisinden farklı.</span><span class="sxs-lookup"><span data-stu-id="fd6e1-110">Microservices derive from SOA, but SOA is different from microservices architecture.</span></span> <span data-ttu-id="fd6e1-111">Büyük merkezi aracıları gibi özellikleri, kuruluş düzeyinde merkezi orchestrators ve [Kurumsal hizmet veri yolu (ESB)](https://en.wikipedia.org/wiki/Enterprise_service_bus) içinde SOA tipik değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="fd6e1-111">Features like big central brokers, central orchestrators at the organization level, and the [Enterprise Service Bus (ESB)](https://en.wikipedia.org/wiki/Enterprise_service_bus) are typical in SOA.</span></span> <span data-ttu-id="fd6e1-112">Ancak, çoğu durumda bunlar mikro hizmet topluluk koruma düzenleri.</span><span class="sxs-lookup"><span data-stu-id="fd6e1-112">But in most cases, these are anti-patterns in the microservice community.</span></span> <span data-ttu-id="fd6e1-113">Aslında, bazı kişiler "mikro hizmet mimarisi doğru şekilde yapabilmeniz SOA olduğunu." karşıdır</span><span class="sxs-lookup"><span data-stu-id="fd6e1-113">In fact, some people argue that “The microservice architecture is SOA done right.”</span></span>

<span data-ttu-id="fd6e1-114">Bir SOA yaklaşım mikro hizmet mimarisinde kullanılan teknikleri ve gereksinimleri daha az Düzenleyici olduğundan bu kılavuz mikro üzerinde odaklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="fd6e1-114">This guide focuses on microservices, because a SOA approach is less prescriptive than the requirements and techniques used in a microservice architecture.</span></span> <span data-ttu-id="fd6e1-115">Mikro hizmet tabanlı bir uygulama oluşturmak nasıl biliyorsanız, ayrıca daha basit bir hizmet odaklı uygulamasının nasıl oluşturulacağını bilmeniz.</span><span class="sxs-lookup"><span data-stu-id="fd6e1-115">If you know how to build a microservice-based application, you also know how to build a simpler service-oriented application.</span></span>




>[!div class="step-by-step"]
<span data-ttu-id="fd6e1-116">[Önceki](docker-application-state-data.md)
[sonraki](microservices-architecture.md)</span><span class="sxs-lookup"><span data-stu-id="fd6e1-116">[Previous](docker-application-state-data.md)
[Next](microservices-architecture.md)</span></span>
