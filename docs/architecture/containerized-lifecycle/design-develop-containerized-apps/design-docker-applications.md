---
title: Docker uygulamaları tasarlama
description: Bu kılavuzda ayrıntılı olmadığından, mikro hizmetler mimarisine yönelik derinlemesine bir kılavuza yönelik bir başvuru bulabilirsiniz.
ms.date: 02/15/2019
ms.openlocfilehash: b9539ff4edf405ab890d83be59a248ffa2360c99
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295865"
---
# <a name="design-docker-applications"></a><span data-ttu-id="cf950-103">Docker uygulamaları tasarlama</span><span class="sxs-lookup"><span data-stu-id="cf950-103">Design Docker applications</span></span>

<span data-ttu-id="cf950-104">Bölüm 1, kapsayıcılar ve Docker ile ilgili temel kavramları sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="cf950-104">Chapter 1 introduced the fundamental concepts regarding containers and Docker.</span></span> <span data-ttu-id="cf950-105">Bu bilgiler, başlamak için ihtiyacınız olan temel bilgi düzeyidir.</span><span class="sxs-lookup"><span data-stu-id="cf950-105">That information is the basic level of information you need to get started.</span></span> <span data-ttu-id="cf950-106">Ancak kurumsal uygulamalar, tek bir hizmet veya kapsayıcı yerine karmaşık ve birden çok hizmetten oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="cf950-106">But, enterprise applications can be complex and composed of multiple services instead of a single service or container.</span></span> <span data-ttu-id="cf950-107">Bu isteğe bağlı kullanım örnekleri için, hizmet odaklı mimari (SOA) ve daha gelişmiş mikro hizmet kavramları ve kapsayıcı düzenleme kavramları gibi tasarıma yönelik ek yaklaşımlar bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="cf950-107">For those optional use cases, you need to know additional approaches to design, such as Service-Oriented Architecture (SOA) and the more advanced microservices concepts and container orchestration concepts.</span></span> <span data-ttu-id="cf950-108">Bu belgenin kapsamı mikro hizmetlerle sınırlı değildir, ancak herhangi bir Docker uygulaması yaşam döngüsü için, normal SOA, arka plan görevleri veya işleri ile kapsayıcılar ve Docker 'ı da kullanabileceğiniz veya hatta tek parçalı uygulama dağıtımı yaklaşımının bulunduğu.</span><span class="sxs-lookup"><span data-stu-id="cf950-108">The scope of this document is not limited to microservices but to any Docker application life cycle, therefore, it does not explore microservices architecture in depth because you also can use containers and Docker with regular SOA, background tasks or jobs, or even with monolithic application deployment approaches.</span></span>

<span data-ttu-id="cf950-109">**Daha fazla bilgi** Kurumsal uygulamalar ve mikro hizmetler mimarisi hakkında daha fazla bilgi edinmek için ağ mikro Hizmetleri Kılavuzu [' nu okuyun: ](../../microservices/index.md) İçinden<https://aka.ms/MicroservicesEbook>de indirebileceğiniz Kapsayıcılı .NET uygulamaları için mimari.</span><span class="sxs-lookup"><span data-stu-id="cf950-109">**More info** To learn more about enterprise applications and microservices architecture in depth, read the guide [NET Microservices: Architecture for Containerized .NET Applications](../../microservices/index.md) that you can also download from <https://aka.ms/MicroservicesEbook>.</span></span>

<span data-ttu-id="cf950-110">Bununla birlikte, uygulama yaşam döngüsü ve DevOps 'a girmeden önce, uygulamanızı nasıl tasarlayacağınızı ve tasarlayacağınızı ve tasarım seçimleriniz olduğunu bilmeniz önemlidir.</span><span class="sxs-lookup"><span data-stu-id="cf950-110">However, before we get into the application life cycle and DevOps, it's important to know how you're going to design and construct your application and what are your design choices.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="cf950-111">[Önceki](index.md)İleri
>[](common-container-design-principles.md)</span><span class="sxs-lookup"><span data-stu-id="cf950-111">[Previous](index.md)
[Next](common-container-design-principles.md)</span></span>
