---
title: .NET uygulamaları tasarlayıp geliştirerek çok kapsayıcılı ve mikro hizmet tabanlı
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Dış mimarisi tasarlama ve geliştirme çok kapsayıcılı ve mikro hizmet tabanlı .NET uygulamaları için anlayın.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/02/2018
ms.openlocfilehash: 3bbf746aa9c0b66a097b8c4df2964b5679342fd0
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53144149"
---
# <a name="designing-and-developing-multi-container-and-microservice-based-net-applications"></a><span data-ttu-id="6c673-103">.NET çok kapsayıcılı ve mikro hizmet tabanlı uygulamalar tasarlayıp geliştirerek</span><span class="sxs-lookup"><span data-stu-id="6c673-103">Designing and Developing Multi-Container and Microservice-Based .NET Applications</span></span>

<span data-ttu-id="6c673-104">*Kapsayıcılı mikro hizmet uygulamaları geliştirme, çok kapsayıcılı uygulamalar oluşturmakta olduğunuz anlamına gelir. Ancak, çok kapsayıcılı bir uygulama aynı zamanda daha basit olabilir — örneğin, bir üç katmanlı uygulama — ve mikro hizmet mimarisi kullanılarak oluşturulmamış olabilir.*</span><span class="sxs-lookup"><span data-stu-id="6c673-104">*Developing containerized microservice applications means you are building multi-container applications. However, a multi-container application could also be simpler—for example, a three-tier application—and might not be built using a microservice architecture.*</span></span>

<span data-ttu-id="6c673-105">Daha önce biz "Docker mikro hizmet mimarisi oluşturma sırasında gerekli mi?" sorusunu oluşturuldu</span><span class="sxs-lookup"><span data-stu-id="6c673-105">Earlier we raised the question "Is Docker necessary when building a microservice architecture?"</span></span> <span data-ttu-id="6c673-106">Yanıttır Temizle yok.</span><span class="sxs-lookup"><span data-stu-id="6c673-106">The answer is a clear no.</span></span> <span data-ttu-id="6c673-107">Docker bir Etkinleştirici ve önemli avantajlar sağlayabilir, ancak kapsayıcıları ve Docker mikro hizmetlere yönelik bir gereksinim değildir.</span><span class="sxs-lookup"><span data-stu-id="6c673-107">Docker is an enabler and can provide significant benefits, but containers and Docker are not a hard requirement for microservices.</span></span> <span data-ttu-id="6c673-108">Örneğin, bir mikro hizmet tabanlı uygulama ile veya olmadan Docker basit işlemler veya Docker kapsayıcıları olarak çalışan mikro hizmetler destekleyen Azure Service Fabric kullanırken oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c673-108">As an example, you could create a microservices-based application with or without Docker when using Azure Service Fabric, which supports microservices running as simple processes or as Docker containers.</span></span>

<span data-ttu-id="6c673-109">Ayrıca Docker kapsayıcılarında alan bir mikro hizmet tabanlı uygulama tasarlayıp oluşturmayı biliyorsanız, diğer herhangi bir basit uygulama modeli tasarlayıp mümkün olacaktır.</span><span class="sxs-lookup"><span data-stu-id="6c673-109">However, if you know how to design and develop a microservices-based application that is also based on Docker containers, you will be able to design and develop any other, simpler application model.</span></span> <span data-ttu-id="6c673-110">Örneğin, aynı zamanda çok kapsayıcılı bir yaklaşım gerektirir ve üç katmanlı bir uygulama tasarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c673-110">For example, you might design a three-tier application that also requires a multi-container approach.</span></span> <span data-ttu-id="6c673-111">Nedeniyle ve mikro hizmet mimarileri kapsayıcı dünyanın içinde önemli bir eğilim olduğundan, bu bölüm Docker kapsayıcılarını kullanarak bir mikro hizmet mimarisi uygulaması üzerinde odaklanır.</span><span class="sxs-lookup"><span data-stu-id="6c673-111">Because of that, and because microservice architectures are an important trend within the container world, this section focuses on a microservice architecture implementation using Docker containers.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="6c673-112">[Önceki](../docker-application-development-process/docker-app-development-workflow.md)
>[İleri](microservice-application-design.md)</span><span class="sxs-lookup"><span data-stu-id="6c673-112">[Previous](../docker-application-development-process/docker-app-development-workflow.md)
[Next](microservice-application-design.md)</span></span>