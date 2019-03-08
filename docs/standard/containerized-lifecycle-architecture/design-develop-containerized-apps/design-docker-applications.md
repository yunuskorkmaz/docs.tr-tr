---
title: Docker uygulamaları tasarlama
description: Mikro hizmet mimarisi için kapsamlı bir kılavuz başvuru, bir konu olduğu için burada bulabilirsiniz, bu kılavuzda ayrıntılı değil.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 858147883b3b4a5a5f487856028fdbfa84f6cca9
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57675192"
---
# <a name="design-docker-applications"></a><span data-ttu-id="9b766-103">Docker uygulamaları tasarlama</span><span class="sxs-lookup"><span data-stu-id="9b766-103">Design Docker applications</span></span>

<span data-ttu-id="9b766-104">Bölüm 1 kapsayıcıları ve Docker ile ilgili temel kavramları sundu.</span><span class="sxs-lookup"><span data-stu-id="9b766-104">Chapter 1 introduced the fundamental concepts regarding containers and Docker.</span></span> <span data-ttu-id="9b766-105">Bu bilgileri kullanmaya başlamak gereken bilgileri temel düzeyidir.</span><span class="sxs-lookup"><span data-stu-id="9b766-105">That information is the basic level of information you need to get started.</span></span> <span data-ttu-id="9b766-106">Ancak, Kurumsal uygulamaları, karmaşık ve oluştuğundan, birden çok hizmet yerine tek bir hizmet veya kapsayıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="9b766-106">But, enterprise applications can be complex and composed of multiple services instead of a single service or container.</span></span> <span data-ttu-id="9b766-107">Bu isteğe bağlı kullanım durumları için ek yaklaşımları Service-Oriented mimari (SOA) gibi tasarım ve daha gelişmiş mikro hizmetler kavramları ve kapsayıcı düzenleme kavramlarını bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9b766-107">For those optional use cases, you need to know additional approaches to design, such as Service-Oriented Architecture (SOA) and the more advanced microservices concepts and container orchestration concepts.</span></span> <span data-ttu-id="9b766-108">Bu belgenin kapsamı mikro hizmetler için sınırlı değildir, ancak ayrıca kapsayıcıları ve Docker ile normal SOA, arka plan görevleri veya işleri kullanın, veya hatta çünkü tüm Docker uygulaması yaşam döngüsü için bu nedenle, mikro hizmetler mimarisi derinlemesine keşfedin değil tek parçalı bir uygulama dağıtım yaklaşımları ile.</span><span class="sxs-lookup"><span data-stu-id="9b766-108">The scope of this document is not limited to microservices but to any Docker application life cycle, therefore, it does not explore microservices architecture in depth because you also can use containers and Docker with regular SOA, background tasks or jobs, or even with monolithic application deployment approaches.</span></span>

<span data-ttu-id="9b766-109">**Daha fazla bilgi** kurumsal uygulamalar ve mikro hizmet mimarisi derinlemesine hakkında daha fazla bilgi edinmek için Kılavuzu okuyun [NET mikro hizmetler: Kapsayıcılı .NET uygulamaları mimarisi](https://docs.microsoft.com/dotnet/standard/microservices-architecture) dan indirebileceğiniz <https://aka.ms/MicroservicesEbook>.</span><span class="sxs-lookup"><span data-stu-id="9b766-109">**More info** To learn more about enterprise applications and microservices architecture in depth, read the guide [NET Microservices: Architecture for Containerized .NET Applications](https://docs.microsoft.com/dotnet/standard/microservices-architecture) that you can also download from <https://aka.ms/MicroservicesEbook>.</span></span>

<span data-ttu-id="9b766-110">Ancak, DevOps ve uygulama yaşam döngüsü içinde aldığımız önce tasarım nasıl duyacağınızı biliyorsanız ve uygulamanız ve tasarım seçimlerinizi nelerdir oluşturmak önem taşır.</span><span class="sxs-lookup"><span data-stu-id="9b766-110">However, before we get into the application life cycle and DevOps, it's important to know how you're going to design and construct your application and what are your design choices.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="9b766-111">[Önceki](index.md)
>[İleri](common-container-design-principles.md)</span><span class="sxs-lookup"><span data-stu-id="9b766-111">[Previous](index.md)
[Next](common-container-design-principles.md)</span></span>
