---
title: ".NET uygulamaları tasarlama ve birden çok kapsayıcı ve mikro hizmet geliştirirken dayalı"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | .NET uygulamaları tasarlama ve birden çok kapsayıcı ve mikro hizmet geliştirirken dayalı"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2a4c59c63cb3f76975173663948e94a7c64ef193
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="designing-and-developing-multi-container-and-microservice-based-net-applications"></a><span data-ttu-id="1bca4-104">Tasarlama ve birden çok kapsayıcı ve mikro hizmet tabanlı .NET uygulamaları geliştirme</span><span class="sxs-lookup"><span data-stu-id="1bca4-104">Designing and Developing Multi-Container and Microservice-Based .NET Applications</span></span>

<span data-ttu-id="1bca4-105">*Kapsayıcılı mikro hizmet uygulamaları geliştirme çok kapsayıcı uygulamaları oluşturmakta olduğunuz anlamına gelir. Ancak, birden çok kapsayıcı uygulama de daha basit olabilir — örneğin, üç katmanlı uygulama — ve mikro hizmet mimarisi girilmesine değil.*</span><span class="sxs-lookup"><span data-stu-id="1bca4-105">*Developing containerized microservice applications means you are building multi-container applications. However, a multi-container application could also be simpler—for example, a three-tier application—and might not be built using a microservice architecture.*</span></span>

<span data-ttu-id="1bca4-106">Daha önce biz "Docker mikro hizmet mimarisi oluştururken gerekli mi?" sorusunu gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="1bca4-106">Earlier we raised the question “Is Docker necessary when building a microservice architecture?”</span></span> <span data-ttu-id="1bca4-107">Yanıt bir Temizle Hayır'dır.</span><span class="sxs-lookup"><span data-stu-id="1bca4-107">The answer is a clear no.</span></span> <span data-ttu-id="1bca4-108">Docker bir etkinleştiricisi ve önemli avantajlar sağlar ancak kapsayıcıları ve Docker mikro için sabit bir gereklilik değildir.</span><span class="sxs-lookup"><span data-stu-id="1bca4-108">Docker is an enabler and can provide significant benefits, but containers and Docker are not a hard requirement for microservices.</span></span> <span data-ttu-id="1bca4-109">Örneğin, mikro tabanlı bir uygulama ile veya olmadan Docker basit işlemler veya Docker kapsayıcılar olarak çalışan mikro destekleyen Azure Service Fabric kullanırken oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1bca4-109">As an example, you could create a microservices-based application with or without Docker when using Azure Service Fabric, which supports microservices running as simple processes or as Docker containers.</span></span>

<span data-ttu-id="1bca4-110">Ayrıca Docker kapsayıcılarında tabanlı mikro tabanlı bir uygulama tasarlayıp nasıl biliyorsanız, diğer, daha basit uygulama modeli tasarlayıp mümkün olacaktır.</span><span class="sxs-lookup"><span data-stu-id="1bca4-110">However, if you know how to design and develop a microservices-based application that is also based on Docker containers, you will be able to design and develop any other, simpler application model.</span></span> <span data-ttu-id="1bca4-111">Örneğin, aynı zamanda birden çok kapsayıcı yaklaşımı gerektirir üç katmanlı uygulama tasarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1bca4-111">For example, you might design a three-tier application that also requires a multi-container approach.</span></span> <span data-ttu-id="1bca4-112">Nedeniyle ve mikro hizmet mimarisi önemli bir eğilim kapsayıcı world içinde olduğundan, bu alt bölüm Docker kapsayıcıları kullanma mikro hizmet mimarisi uygulama üzerinde odaklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="1bca4-112">Because of that, and because microservice architectures are an important trend within the container world, this section focuses on a microservice architecture implementation using Docker containers.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="1bca4-113">[Önceki] (.. /containerize-NET-Framework-Applications/index.MD) [sonraki] (mikro hizmet uygulama design.md)</span><span class="sxs-lookup"><span data-stu-id="1bca4-113">[Previous] (../containerize-net-framework-applications/index.md) [Next] (microservice-application-design.md)</span></span>
