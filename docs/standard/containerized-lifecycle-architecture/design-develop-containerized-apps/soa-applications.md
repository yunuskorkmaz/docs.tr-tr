---
title: SOA uygulamaları
description: Kapsayıcıları SOA uygulamalar için kullanışlı bir dağıtım seçeneği de olabilir aklınızda size aittir.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: ee71873ac15246f979fd2b08d92280ba797ff6ee
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61795414"
---
# <a name="service-oriented-applications"></a><span data-ttu-id="cff80-103">Hizmet odaklı uygulamalar</span><span class="sxs-lookup"><span data-stu-id="cff80-103">Service-oriented applications</span></span>

<span data-ttu-id="cff80-104">Hizmet odaklı mimari (SOA) birçok farklı şey farklı kişilere geliyordu aşırı kullanılmasına bir terim oluştu.</span><span class="sxs-lookup"><span data-stu-id="cff80-104">Service-Oriented Architecture (SOA) was an overused term that meant many different things to different people.</span></span> <span data-ttu-id="cff80-105">Ancak, alt sistemleri gibi farklı türlerde veya diğer durumlarda, katmanları olarak sınıflandırılan çeşitli Hizmetleri (en yaygın olarak HTTP Hizmetleri) parçalama tarafından uygulamanızın mimarisini yapısı bir ortak paydası SOA anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="cff80-105">But as a common denominator, SOA means that you structure the architecture of your application by decomposing it into several services (most commonly as HTTP services) that can be classified in different types like subsystems or, in other cases, as tiers.</span></span>

<span data-ttu-id="cff80-106">Bugün, bu hizmetler, tüm bağımlılıkları kapsayıcı görüntüsüne dahil olduğu dağıtımıyla ilgili sorunları çözmeye Docker kapsayıcıları olarak dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cff80-106">Today, you can deploy those services as Docker containers, which solve deployment-related issues because all of the dependencies are included in the container image.</span></span> <span data-ttu-id="cff80-107">Ancak, out SOAs Ölçeklendirmesi gerektiğinde, bağlı olarak tek örnek dağıtıyorsanız zorlukları karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cff80-107">However, when you need to scale out SOAs, you might encounter challenges if you're deploying based on single instances.</span></span> <span data-ttu-id="cff80-108">Bu sınama, yazılım veya bir orchestrator kümeleme Docker kullanarak işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="cff80-108">This challenge can be handled using Docker clustering software or an orchestrator.</span></span> <span data-ttu-id="cff80-109">Mikro hizmetler yaklaşımları inceleyeceğiz, sonraki bölümde daha ayrıntılı düzenleyicileri şu konuları inceleyeceğiz.</span><span class="sxs-lookup"><span data-stu-id="cff80-109">We'll look at orchestrators in greater detail in the next section, when we explore microservices approaches.</span></span>

<span data-ttu-id="cff80-110">Docker kapsayıcıları yararlı (ancak gerekli değil) hizmet odaklı geleneksel mimarilerde hem de daha gelişmiş bir mikro hizmet mimarileri için.</span><span class="sxs-lookup"><span data-stu-id="cff80-110">Docker containers are useful (but not required) for both traditional service-oriented architectures and the more advanced microservices architectures.</span></span>

<span data-ttu-id="cff80-111">Günün sonunda, kapsayıcı kümeleme çözümleri ve her bir mikro hizmet kendi veri modelini sahibi olan daha gelişmiş bir mikro hizmet mimarisi bir hem bir geleneksel SOA mimarisi için yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="cff80-111">At the end of the day, the container clustering solutions are useful for both a traditional SOA architecture and for a more advanced microservices architecture in which each microservice owns its data model.</span></span> <span data-ttu-id="cff80-112">Ve birden çok veritabanı sayesinde, ayrıca SOA Hizmetleri tarafından paylaşılan tek parça veritabanlarıyla çalışmak yerine veri katmanı ölçeğini genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cff80-112">And thanks to multiple databases, you also can scale out the data tier instead of working with monolithic databases shared by the SOA services.</span></span> <span data-ttu-id="cff80-113">Ancak, verileri bölme hakkında bir tartışma tamamen mimari ve tasarım hakkında olur.</span><span class="sxs-lookup"><span data-stu-id="cff80-113">However, the discussion about splitting the data is purely about architecture and design.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="cff80-114">[Önceki](state-and-data-in-docker-applications.md)
>[İleri](orchestrate-high-scalability-availability.md)</span><span class="sxs-lookup"><span data-stu-id="cff80-114">[Previous](state-and-data-in-docker-applications.md)
[Next](orchestrate-high-scalability-availability.md)</span></span>
