---
title: Hizmet odaklı mimari
description: Mikro hizmetler ve hizmet odaklı mimari (SOA) arasındaki temel farklar öğrenin.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/20/2018
ms.openlocfilehash: d19053d8296dbe75ac1e0ce037d6a713d9f5687c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62025489"
---
# <a name="service-oriented-architecture"></a><span data-ttu-id="d620e-103">Hizmet odaklı mimari</span><span class="sxs-lookup"><span data-stu-id="d620e-103">Service-oriented architecture</span></span>

<span data-ttu-id="d620e-104">Hizmet odaklı mimari (SOA) olan bir aşırı kullanılmasına terim ve farklı kişiler için farklı şeyler hazırlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="d620e-104">Service-oriented architecture (SOA) was an overused term and has meant different things to different people.</span></span> <span data-ttu-id="d620e-105">Ancak, bir ortak paydası (en yaygın olarak HTTP Hizmetleri) farklı alt sistemler veya katmanları gibi olarak sınıflandırılan birden çok hizmetlerine parçalama tarafından uygulamanızı yapı SOA anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d620e-105">But as a common denominator, SOA means that you structure your application by decomposing it into multiple services (most commonly as HTTP services) that can be classified as different types like subsystems or tiers.</span></span>

<span data-ttu-id="d620e-106">Kapsayıcı görüntüsü dahil tüm bağımlılıkları olmadığından bu hizmetleri artık Docker kapsayıcıları olarak hangi dağıtım sorunlarını çözer dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="d620e-106">Those services can now be deployed as Docker containers, which solves deployment issues, because all the dependencies are included in the container image.</span></span> <span data-ttu-id="d620e-107">Ancak, SOA uygulamaları Ölçeklendirmesi gerektiğinde, ölçeklenebilirlik olabilir ve dağıtım yapıyorsanız kullanılabilirlik sorunları tek Docker konakları üzerinde temel.</span><span class="sxs-lookup"><span data-stu-id="d620e-107">However, when you need to scale up SOA applications, you might have scalability and availability challenges if you're deploying based on single Docker hosts.</span></span> <span data-ttu-id="d620e-108">Docker kümeleme yazılım ya da bir orchestrator, burada sağlayabilirsiniz mikro hizmetlere yönelik dağıtım yaklaşımları burada açıklanan sonraki bölümlerde açıklandığı gibi budur.</span><span class="sxs-lookup"><span data-stu-id="d620e-108">This is where Docker clustering software or an orchestrator can help you, as explained in later sections where deployment approaches for microservices are described.</span></span>

<span data-ttu-id="d620e-109">Docker kapsayıcıları yararlı (ancak gerekli değil) hizmet odaklı geleneksel mimarilerde hem de daha gelişmiş bir mikro hizmet mimarileri için.</span><span class="sxs-lookup"><span data-stu-id="d620e-109">Docker containers are useful (but not required) for both traditional service-oriented architectures and the more advanced microservices architectures.</span></span>

<span data-ttu-id="d620e-110">Mikro hizmetler SOA türetilen ancak mikro hizmetler mimarisi SOA farklıdır.</span><span class="sxs-lookup"><span data-stu-id="d620e-110">Microservices derive from SOA, but SOA is different from microservices architecture.</span></span> <span data-ttu-id="d620e-111">Büyük merkezi aracıları gibi özellikler, kuruluş düzeyindeki merkez düzenleyiciler ve [Enterprise Service Bus'ı (ESB)](https://en.wikipedia.org/wiki/Enterprise_service_bus) SOA içinde normal.</span><span class="sxs-lookup"><span data-stu-id="d620e-111">Features like large central brokers, central orchestrators at the organization level, and the [Enterprise Service Bus (ESB)](https://en.wikipedia.org/wiki/Enterprise_service_bus) are typical in SOA.</span></span> <span data-ttu-id="d620e-112">Ancak, çoğu durumda, bunlar mikro hizmet topluluğundaki ters desenler.</span><span class="sxs-lookup"><span data-stu-id="d620e-112">But in most cases, these are anti-patterns in the microservice community.</span></span> <span data-ttu-id="d620e-113">Aslında, bazı kişiler "mikro hizmet mimarisi doğru yapıldığında SOA olduğunu." buna</span><span class="sxs-lookup"><span data-stu-id="d620e-113">In fact, some people argue that "The microservice architecture is SOA done right."</span></span>

<span data-ttu-id="d620e-114">Bir mikro hizmet mimarisinde kullanılır teknikler ve gereksinimleri daha az öngörücü SOA yaklaşımdır çünkü bu kılavuz, mikro hizmetler üzerinde odaklanır.</span><span class="sxs-lookup"><span data-stu-id="d620e-114">This guide focuses on microservices, because a SOA approach is less prescriptive than the requirements and techniques used in a microservice architecture.</span></span> <span data-ttu-id="d620e-115">Bir mikro hizmet tabanlı uygulama oluşturmayı biliyorsanız, ayrıca hizmet odaklı basit bir uygulamanın nasıl oluşturulacağını bilmeniz.</span><span class="sxs-lookup"><span data-stu-id="d620e-115">If you know how to build a microservice-based application, you also know how to build a simpler service-oriented application.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="d620e-116">[Önceki](docker-application-state-data.md)
>[İleri](microservices-architecture.md)</span><span class="sxs-lookup"><span data-stu-id="d620e-116">[Previous](docker-application-state-data.md)
[Next](microservices-architecture.md)</span></span>