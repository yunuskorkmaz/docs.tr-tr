---
title: Çoklu kapsayıcı ve mikro hizmet tabanlı .NET uygulamaları tasarlama ve geliştirme
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Çoklu kapsayıcı ve mikro hizmet tabanlı .NET uygulamaları tasarlama ve geliştirme için dış mimariyi anlayın.
ms.date: 10/02/2018
ms.openlocfilehash: 8c2f828e9913a0efcdf580371124b0f624daeffe
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296628"
---
# <a name="designing-and-developing-multi-container-and-microservice-based-net-applications"></a><span data-ttu-id="a80f4-103">Çok Kapsayıcılı ve mikro hizmet tabanlı .NET uygulamaları tasarlama ve geliştirme</span><span class="sxs-lookup"><span data-stu-id="a80f4-103">Designing and Developing Multi-Container and Microservice-Based .NET Applications</span></span>

<span data-ttu-id="a80f4-104">*Kapsayıcılı mikro hizmet uygulamalarının geliştirilmesi, çok Kapsayıcılı uygulamalar oluşturduğunuz anlamına gelir. Ancak, çok kapsayıcılı bir uygulama da daha basit olabilir — Örneğin, üç katmanlı bir uygulama — ve mikro hizmet mimarisi kullanılarak derlenmeyebilir.*</span><span class="sxs-lookup"><span data-stu-id="a80f4-104">*Developing containerized microservice applications means you are building multi-container applications. However, a multi-container application could also be simpler—for example, a three-tier application—and might not be built using a microservice architecture.*</span></span>

<span data-ttu-id="a80f4-105">Daha önce "bir mikro hizmet mimarisi oluştururken Docker gereklidir?" sorusunu yaptık.</span><span class="sxs-lookup"><span data-stu-id="a80f4-105">Earlier we raised the question "Is Docker necessary when building a microservice architecture?"</span></span> <span data-ttu-id="a80f4-106">Yanıt, açık bir hayır.</span><span class="sxs-lookup"><span data-stu-id="a80f4-106">The answer is a clear no.</span></span> <span data-ttu-id="a80f4-107">Docker bir etkinleştiricisidir ve önemli avantajlar sağlayabilir, ancak kapsayıcılar ve Docker mikro hizmetler için bir sabit gereksinimdir.</span><span class="sxs-lookup"><span data-stu-id="a80f4-107">Docker is an enabler and can provide significant benefits, but containers and Docker are not a hard requirement for microservices.</span></span> <span data-ttu-id="a80f4-108">Örnek olarak, basit süreçler veya Docker Kapsayıcıları olarak çalışan mikro hizmetleri destekleyen Azure Service Fabric kullanırken Docker ile veya olmayan mikro hizmetler tabanlı bir uygulama oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a80f4-108">As an example, you could create a microservices-based application with or without Docker when using Azure Service Fabric, which supports microservices running as simple processes or as Docker containers.</span></span>

<span data-ttu-id="a80f4-109">Ancak, Docker kapsayıcılarına dayalı olarak da mikro hizmetler tabanlı bir uygulamayı tasarlamayı ve geliştirmeyi biliyorsanız, başka, daha basit bir uygulama modeli tasarlayabilecek ve geliştirebileceksiniz.</span><span class="sxs-lookup"><span data-stu-id="a80f4-109">However, if you know how to design and develop a microservices-based application that is also based on Docker containers, you will be able to design and develop any other, simpler application model.</span></span> <span data-ttu-id="a80f4-110">Örneğin, çok kapsayıcılı bir yaklaşım gerektiren üç katmanlı bir uygulama tasarlayabilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a80f4-110">For example, you might design a three-tier application that also requires a multi-container approach.</span></span> <span data-ttu-id="a80f4-111">Bu nedenle, mikro hizmet mimarileri kapsayıcı dünyasında önemli bir eğilim olduğundan, bu bölüm Docker Kapsayıcıları kullanılarak bir mikro hizmet mimarisi uygulamasına odaklanır.</span><span class="sxs-lookup"><span data-stu-id="a80f4-111">Because of that, and because microservice architectures are an important trend within the container world, this section focuses on a microservice architecture implementation using Docker containers.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a80f4-112">[Önceki](../docker-application-development-process/docker-app-development-workflow.md)İleri
>[](microservice-application-design.md)</span><span class="sxs-lookup"><span data-stu-id="a80f4-112">[Previous](../docker-application-development-process/docker-app-development-workflow.md)
[Next](microservice-application-design.md)</span></span>
