---
title: Docker uygulamaları tasarlama
description: Bu kılavuzda ayrıntılı olmadığından, mikro hizmetler mimarisine yönelik derinlemesine bir kılavuza yönelik bir başvuru bulabilirsiniz.
ms.date: 08/06/2020
ms.openlocfilehash: b63d4344abb358a393587bdacf91f6091b531af0
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87915984"
---
# <a name="design-docker-applications"></a><span data-ttu-id="271cf-103">Docker uygulamaları tasarlama</span><span class="sxs-lookup"><span data-stu-id="271cf-103">Design Docker applications</span></span>

<span data-ttu-id="271cf-104">Bölüm 1, kapsayıcılar ve Docker ile ilgili temel kavramları sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="271cf-104">Chapter 1 introduced the fundamental concepts regarding containers and Docker.</span></span> <span data-ttu-id="271cf-105">Bu bilgiler, başlamak için ihtiyacınız olan temel bilgi düzeyidir.</span><span class="sxs-lookup"><span data-stu-id="271cf-105">That information is the basic level of information you need to get started.</span></span> <span data-ttu-id="271cf-106">Ancak kurumsal uygulamalar, tek bir hizmet veya kapsayıcı yerine karmaşık ve birden çok hizmetten oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="271cf-106">But, enterprise applications can be complex and composed of multiple services instead of a single service or container.</span></span> <span data-ttu-id="271cf-107">Bu isteğe bağlı kullanım örnekleri için, hizmet odaklı mimari (SOA) ve daha gelişmiş mikro hizmet kavramları ve kapsayıcı düzenleme kavramları gibi tasarıma yönelik ek yaklaşımlar bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="271cf-107">For those optional use cases, you need to know additional approaches to design, such as Service-Oriented Architecture (SOA) and the more advanced microservices concepts and container orchestration concepts.</span></span> <span data-ttu-id="271cf-108">Bu belgenin kapsamı mikro hizmetlerle sınırlı değildir, ancak herhangi bir Docker uygulaması yaşam döngüsü ile, kapsayıcıları ve Docker 'ı normal SOA, arka plan görevleri veya işleriyle, hatta tek parçalı uygulama dağıtımı yaklaşımları ile de kullanabileceğiniz için, mikro hizmetler mimarisini derinlemesine bir şekilde araştırmaz.</span><span class="sxs-lookup"><span data-stu-id="271cf-108">The scope of this document is not limited to microservices but to any Docker application life cycle, therefore, it does not explore microservices architecture in depth because you can also use containers and Docker with regular SOA, background tasks or jobs, or even with monolithic application deployment approaches.</span></span>

<span data-ttu-id="271cf-109">**Daha fazla bilgi** Kurumsal uygulamalar ve mikro hizmetler mimarisi hakkında ayrıntılı bilgi edinmek için, ağ mikro hizmetleri: ' dan da indirebileceğiniz [Kapsayıcılı .NET uygulamaları Için mimari](../../microservices/index.md) makalesini okuyun <https://aka.ms/MicroservicesEbook> .</span><span class="sxs-lookup"><span data-stu-id="271cf-109">**More info** To learn more about enterprise applications and microservices architecture in depth, read the guide [NET Microservices: Architecture for Containerized .NET Applications](../../microservices/index.md) that you can also download from <https://aka.ms/MicroservicesEbook>.</span></span>

<span data-ttu-id="271cf-110">Ancak, uygulama yaşam döngüsü ve DevOps 'a girmeden önce, uygulamanızı nasıl tasarlayacağınızı ve tasarlayacağınızı ve tasarım seçimlerinizle karşılaşabileceğinizi bilmeniz önemlidir.</span><span class="sxs-lookup"><span data-stu-id="271cf-110">However, before you get into the application life cycle and DevOps, it's important to know how you're going to design and construct your application and what are your design choices.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="271cf-111">[Önceki](index.md) 
> [Sonraki](common-container-design-principles.md)</span><span class="sxs-lookup"><span data-stu-id="271cf-111">[Previous](index.md)
[Next](common-container-design-principles.md)</span></span>
