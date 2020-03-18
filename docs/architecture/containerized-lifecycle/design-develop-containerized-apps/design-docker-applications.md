---
title: Docker uygulamaları tasarlama
description: Burada mikro hizmetler mimarisi için ayrıntılı bir kılavuza bir başvuru bulabilirsiniz, çünkü bu kılavuzda ayrıntılı olarak belirtilmeyecek bir konudur.
ms.date: 02/15/2019
ms.openlocfilehash: b9539ff4edf405ab890d83be59a248ffa2360c99
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70295865"
---
# <a name="design-docker-applications"></a><span data-ttu-id="1fbed-103">Docker uygulamaları tasarlama</span><span class="sxs-lookup"><span data-stu-id="1fbed-103">Design Docker applications</span></span>

<span data-ttu-id="1fbed-104">Bölüm 1 konteyner ve Docker ile ilgili temel kavramları tanıttı.</span><span class="sxs-lookup"><span data-stu-id="1fbed-104">Chapter 1 introduced the fundamental concepts regarding containers and Docker.</span></span> <span data-ttu-id="1fbed-105">Bu bilgiler, başlamak için gereken temel bilgi düzeyidir.</span><span class="sxs-lookup"><span data-stu-id="1fbed-105">That information is the basic level of information you need to get started.</span></span> <span data-ttu-id="1fbed-106">Ancak, kurumsal uygulamalar karmaşık olabilir ve tek bir hizmet veya kapsayıcı yerine birden çok hizmetten oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="1fbed-106">But, enterprise applications can be complex and composed of multiple services instead of a single service or container.</span></span> <span data-ttu-id="1fbed-107">İsteğe bağlı kullanım örnekleri için, Hizmet Odaklı Mimari (SOA) ve daha gelişmiş microservices kavramları ve konteyner orkestrasyon kavramları gibi tasarıma ek yaklaşımları bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1fbed-107">For those optional use cases, you need to know additional approaches to design, such as Service-Oriented Architecture (SOA) and the more advanced microservices concepts and container orchestration concepts.</span></span> <span data-ttu-id="1fbed-108">Bu belgenin kapsamı mikro hizmetlerle sınırlı değildir, ancak docker uygulama yaşam döngüsü ile sınırlı değildir, bu nedenle, mikrohizmetler mimarisini derinlemesine keşfetmez, çünkü düzenli SOA, arka plan görevleri veya işleri ve hatta yekpare uygulama dağıtım yaklaşımları ile.</span><span class="sxs-lookup"><span data-stu-id="1fbed-108">The scope of this document is not limited to microservices but to any Docker application life cycle, therefore, it does not explore microservices architecture in depth because you also can use containers and Docker with regular SOA, background tasks or jobs, or even with monolithic application deployment approaches.</span></span>

<span data-ttu-id="1fbed-109">**Daha fazla bilgi** Kurumsal uygulamalar ve mikrohizmetler mimarisi hakkında daha fazla bilgi edinmek [için NET Microservices: Architecture for Containerized .NET Applications](../../microservices/index.md) adlı rehberi ni <https://aka.ms/MicroservicesEbook>okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1fbed-109">**More info** To learn more about enterprise applications and microservices architecture in depth, read the guide [NET Microservices: Architecture for Containerized .NET Applications](../../microservices/index.md) that you can also download from <https://aka.ms/MicroservicesEbook>.</span></span>

<span data-ttu-id="1fbed-110">Ancak, uygulama yaşam döngüsüne ve DevOps'lere girmeden önce, uygulamanızı nasıl tasarlayıp oluşturacağınız ve tasarım seçenekleriniz nelerdir bilmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="1fbed-110">However, before we get into the application life cycle and DevOps, it's important to know how you're going to design and construct your application and what are your design choices.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="1fbed-111">[Önceki](index.md)
>[Sonraki](common-container-design-principles.md)</span><span class="sxs-lookup"><span data-stu-id="1fbed-111">[Previous](index.md)
[Next](common-container-design-principles.md)</span></span>
