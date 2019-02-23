---
title: Docker uygulamaları tasarlama
description: Mikro hizmet mimarisi için kapsamlı bir kılavuz başvuru, bir konu olduğu için burada bulabilirsiniz, bu kılavuzda ayrıntılı değil.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 5238ef8d9025f1518d513bfa7ff83eb51c2b88df
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56748628"
---
# <a name="design-docker-applications"></a><span data-ttu-id="9f564-103">Docker uygulamaları tasarlama</span><span class="sxs-lookup"><span data-stu-id="9f564-103">Design Docker applications</span></span>

<span data-ttu-id="9f564-104">Bölüm 1 kapsayıcıları ve Docker ile ilgili temel kavramları sundu.</span><span class="sxs-lookup"><span data-stu-id="9f564-104">Chapter 1 introduced the fundamental concepts regarding containers and Docker.</span></span> <span data-ttu-id="9f564-105">Bu bilgileri kullanmaya başlamak gereken bilgileri temel düzeyidir.</span><span class="sxs-lookup"><span data-stu-id="9f564-105">That information is the basic level of information you need to get started.</span></span> <span data-ttu-id="9f564-106">Ancak, Kurumsal uygulamaları, karmaşık ve oluştuğundan, birden çok hizmet yerine tek bir hizmet veya kapsayıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="9f564-106">But, enterprise applications can be complex and composed of multiple services instead of a single service or container.</span></span> <span data-ttu-id="9f564-107">Bu isteğe bağlı kullanım durumları için ek yaklaşımları Service-Oriented mimari (SOA) gibi tasarım ve daha gelişmiş mikro hizmetler kavramları ve kapsayıcı düzenleme kavramlarını bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9f564-107">For those optional use cases, you need to know additional approaches to design, such as Service-Oriented Architecture (SOA) and the more advanced microservices concepts and container orchestration concepts.</span></span> <span data-ttu-id="9f564-108">Bu belgenin kapsamı mikro hizmetler için sınırlı değildir, ancak ayrıca kapsayıcıları ve Docker ile normal SOA, arka plan görevleri veya işleri kullanın, veya hatta çünkü tüm Docker uygulaması yaşam döngüsü için bu nedenle, mikro hizmetler mimarisi derinlemesine keşfedin değil tek parçalı bir uygulama dağıtım yaklaşımları ile.</span><span class="sxs-lookup"><span data-stu-id="9f564-108">The scope of this document is not limited to microservices but to any Docker application life cycle, therefore, it does not explore microservices architecture in depth because you also can use containers and Docker with regular SOA, background tasks or jobs, or even with monolithic application deployment approaches.</span></span>

<span data-ttu-id="9f564-109">**Daha fazla bilgi** kurumsal uygulamalar ve mikro hizmet mimarisi derinlemesine hakkında daha fazla bilgi edinmek için Kılavuzu okuyun [NET mikro hizmetler: Kapsayıcılı .NET uygulamaları mimarisi](https://docs.microsoft.com/dotnet/standard/microservices-architecture) dan indirebileceğiniz <https://aka.ms/MicroservicesEbook>.</span><span class="sxs-lookup"><span data-stu-id="9f564-109">**More info** To learn more about enterprise applications and microservices architecture in depth, read the guide [NET Microservices: Architecture for Containerized .NET Applications](https://docs.microsoft.com/dotnet/standard/microservices-architecture) that you can also download from <https://aka.ms/MicroservicesEbook>.</span></span>

<span data-ttu-id="9f564-110">Ancak, DevOps ve uygulama yaşam döngüsü içinde aldığımız önce tasarım nasıl kalacaklarını bilmek ve uygulamanız ve tasarım seçimlerinizi nelerdir oluşturmak önem taşır.</span><span class="sxs-lookup"><span data-stu-id="9f564-110">However, before we get into the application life cycle and DevOps, it is important to know how you are going to design and construct your application and what are your design choices.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="9f564-111">[Önceki](index.md)
>[İleri](common-container-design-principles.md)</span><span class="sxs-lookup"><span data-stu-id="9f564-111">[Previous](index.md)
[Next](common-container-design-principles.md)</span></span>
