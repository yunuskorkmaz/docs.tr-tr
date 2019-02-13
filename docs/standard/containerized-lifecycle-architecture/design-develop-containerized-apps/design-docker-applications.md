---
title: Docker uygulamaları tasarlama
description: Mikro hizmet mimarisi için kapsamlı bir kılavuz başvuru, bir konu olduğu için burada bulabilirsiniz, bu kılavuzda ayrıntılı değil.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: f31421cab7d2072441999231adfbe771a3f9a0f5
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56220211"
---
# <a name="design-docker-applications"></a><span data-ttu-id="9c368-103">Docker uygulamaları tasarlama</span><span class="sxs-lookup"><span data-stu-id="9c368-103">Design Docker applications</span></span>

<span data-ttu-id="9c368-104">Bölüm 1 kapsayıcıları ve Docker ile ilgili temel kavramları sundu.</span><span class="sxs-lookup"><span data-stu-id="9c368-104">Chapter 1 introduced the fundamental concepts regarding containers and Docker.</span></span> <span data-ttu-id="9c368-105">Bu bilgileri kullanmaya başlamak gereken bilgileri temel düzeyidir.</span><span class="sxs-lookup"><span data-stu-id="9c368-105">That information is the basic level of information you need to get started.</span></span> <span data-ttu-id="9c368-106">Ancak, Kurumsal uygulamaları, karmaşık ve oluştuğundan, birden çok hizmet yerine tek bir hizmet veya kapsayıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="9c368-106">But, enterprise applications can be complex and composed of multiple services instead of a single service or container.</span></span> <span data-ttu-id="9c368-107">Bu isteğe bağlı kullanım durumları için ek yaklaşımları Service-Oriented mimari (SOA) gibi tasarım ve daha gelişmiş mikro hizmetler kavramları ve kapsayıcı düzenleme kavramlarını bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9c368-107">For those optional use cases, you need to know additional approaches to design, such as Service-Oriented Architecture (SOA) and the more advanced microservices concepts and container orchestration concepts.</span></span> <span data-ttu-id="9c368-108">Bu belgenin kapsamı mikro hizmetler için sınırlı değildir, ancak ayrıca kapsayıcıları ve Docker ile normal SAO, arka plan görevleri veya işleri kullanın, veya hatta çünkü tüm Docker uygulaması yaşam döngüsü için bu nedenle, mikro hizmetler mimarisi derinlemesine keşfedin değil tek parçalı bir uygulama dağıtım yaklaşımları ile.</span><span class="sxs-lookup"><span data-stu-id="9c368-108">The scope of this document is not limited to microservices but to any Docker application life cycle, therefore, it does not explore microservices architecture in depth because you also can use containers and Docker with regular SAO, background tasks or jobs, or even with monolithic application deployment approaches.</span></span>

<span data-ttu-id="9c368-109">Ancak, DevOps ve uygulama yaşam döngüsü içinde aldığımız önce tasarım nasıl kalacaklarını bilmek ve uygulamanız ve tasarım seçimlerinizi nelerdir oluşturmak önem taşır.</span><span class="sxs-lookup"><span data-stu-id="9c368-109">However, before we get into the application life cycle and DevOps, it is important to know how you are going to design and construct your application and what are your design choices.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="9c368-110">[Önceki](index.md)
>[İleri](common-container-design-principles.md)</span><span class="sxs-lookup"><span data-stu-id="9c368-110">[Previous](index.md)
[Next](common-container-design-principles.md)</span></span>