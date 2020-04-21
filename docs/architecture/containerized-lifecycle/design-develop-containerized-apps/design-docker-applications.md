---
title: Docker uygulamaları tasarlama
description: Burada mikro hizmetler mimarisi için ayrıntılı bir kılavuza bir başvuru bulabilirsiniz, çünkü bu kılavuzda ayrıntılı olarak belirtilmeyecek bir konudur.
ms.date: 02/15/2019
ms.openlocfilehash: b8a08658ec6c3df3e1aed596a0240223768dd647
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738458"
---
# <a name="design-docker-applications"></a><span data-ttu-id="106d5-103">Docker uygulamaları tasarlama</span><span class="sxs-lookup"><span data-stu-id="106d5-103">Design Docker applications</span></span>

<span data-ttu-id="106d5-104">Bölüm 1 konteyner ve Docker ile ilgili temel kavramları tanıttı.</span><span class="sxs-lookup"><span data-stu-id="106d5-104">Chapter 1 introduced the fundamental concepts regarding containers and Docker.</span></span> <span data-ttu-id="106d5-105">Bu bilgiler, başlamak için gereken temel bilgi düzeyidir.</span><span class="sxs-lookup"><span data-stu-id="106d5-105">That information is the basic level of information you need to get started.</span></span> <span data-ttu-id="106d5-106">Ancak, kurumsal uygulamalar karmaşık olabilir ve tek bir hizmet veya kapsayıcı yerine birden çok hizmetten oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="106d5-106">But, enterprise applications can be complex and composed of multiple services instead of a single service or container.</span></span> <span data-ttu-id="106d5-107">İsteğe bağlı kullanım örnekleri için, Hizmet Odaklı Mimari (SOA) ve daha gelişmiş microservices kavramları ve konteyner orkestrasyon kavramları gibi tasarıma ek yaklaşımları bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="106d5-107">For those optional use cases, you need to know additional approaches to design, such as Service-Oriented Architecture (SOA) and the more advanced microservices concepts and container orchestration concepts.</span></span> <span data-ttu-id="106d5-108">Bu belgenin kapsamı mikro hizmetlerle sınırlı değildir, ancak herhangi bir Docker uygulama yaşam döngüsüyle sınırlı değildir, bu nedenle, düzenli SOA, arka plan görevleri veya işleri, hatta yekpare uygulama dağıtım yaklaşımları ile kaplar ve Docker kullanabilirsiniz, çünkü derinlemesine mikrohizmetler mimarisi keşfetmek değildir.</span><span class="sxs-lookup"><span data-stu-id="106d5-108">The scope of this document is not limited to microservices but to any Docker application life cycle, therefore, it does not explore microservices architecture in depth because you can also use containers and Docker with regular SOA, background tasks or jobs, or even with monolithic application deployment approaches.</span></span>

<span data-ttu-id="106d5-109">**Daha fazla bilgi** Kurumsal uygulamalar ve mikrohizmetler mimarisi hakkında daha fazla bilgi edinmek [için NET Microservices: Architecture for Containerized .NET Applications](../../microservices/index.md) adlı rehberi ni <https://aka.ms/MicroservicesEbook>okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="106d5-109">**More info** To learn more about enterprise applications and microservices architecture in depth, read the guide [NET Microservices: Architecture for Containerized .NET Applications](../../microservices/index.md) that you can also download from <https://aka.ms/MicroservicesEbook>.</span></span>

<span data-ttu-id="106d5-110">Ancak, uygulama yaşam döngüsüne ve DevOps'lere girmeden önce, uygulamanızı nasıl tasarlayıp oluşturacağınız ve tasarım seçenekleriniz nelerdir bilmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="106d5-110">However, before we get into the application life cycle and DevOps, it's important to know how you're going to design and construct your application and what are your design choices.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="106d5-111">[Önceki](index.md)
>[Sonraki](common-container-design-principles.md)</span><span class="sxs-lookup"><span data-stu-id="106d5-111">[Previous](index.md)
[Next](common-container-design-principles.md)</span></span>
