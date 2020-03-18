---
title: Multi Konteyner ve Microservice Tabanlı .NET Uygulamalarının Tasarımı ve Geliştirilmesi
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | Multi Container ve Microservice Based .NET Uygulamaları Tasarlamak ve Geliştirmek için dış mimariyi anlayın.
ms.date: 10/02/2018
ms.openlocfilehash: 8c2f828e9913a0efcdf580371124b0f624daeffe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "70296628"
---
# <a name="designing-and-developing-multi-container-and-microservice-based-net-applications"></a><span data-ttu-id="97e6d-103">Multi-Konteyner ve Microservice Tabanlı .NET Uygulamaları nın Tasarımı ve Geliştirilmesi</span><span class="sxs-lookup"><span data-stu-id="97e6d-103">Designing and Developing Multi-Container and Microservice-Based .NET Applications</span></span>

<span data-ttu-id="97e6d-104">*Konteynerleştirilmiş mikrohizmet uygulamaları geliştirmek, çok konteyner uygulamaları geliştirdiğiniz anlamına gelir. Ancak, çok kapsayıcılı bir uygulama da daha basit olabilir (örneğin, üç katmanlı bir uygulama) ve bir microservice mimarisi kullanılarak oluşturulmayabilir.*</span><span class="sxs-lookup"><span data-stu-id="97e6d-104">*Developing containerized microservice applications means you are building multi-container applications. However, a multi-container application could also be simpler—for example, a three-tier application—and might not be built using a microservice architecture.*</span></span>

<span data-ttu-id="97e6d-105">Daha önce "Docker bir mikro hizmet mimarisi inşa ederken gerekli mi?" sorusunu gündeme getirdi.</span><span class="sxs-lookup"><span data-stu-id="97e6d-105">Earlier we raised the question "Is Docker necessary when building a microservice architecture?"</span></span> <span data-ttu-id="97e6d-106">Cevap açık bir hayır.</span><span class="sxs-lookup"><span data-stu-id="97e6d-106">The answer is a clear no.</span></span> <span data-ttu-id="97e6d-107">Docker bir etkinleştirici ve önemli faydalar sağlayabilir, ancak konteyner ve Docker mikro hizmetler için zor bir gereklilik değildir.</span><span class="sxs-lookup"><span data-stu-id="97e6d-107">Docker is an enabler and can provide significant benefits, but containers and Docker are not a hard requirement for microservices.</span></span> <span data-ttu-id="97e6d-108">Örnek olarak, basit işlemler veya Docker kapsayıcıları gibi çalışan mikro hizmetleri destekleyen Azure Hizmet Kumaşı'nı kullanırken Docker ile veya Docker olmadan mikro hizmet tabanlı bir uygulama oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97e6d-108">As an example, you could create a microservices-based application with or without Docker when using Azure Service Fabric, which supports microservices running as simple processes or as Docker containers.</span></span>

<span data-ttu-id="97e6d-109">Ancak, Docker kaplarına da dayanan mikrohizmet tabanlı bir uygulamanın nasıl tasarlanıp geliştireceğinibiliyorsanız, diğer, daha basit bir uygulama modelini tasarlayıp geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97e6d-109">However, if you know how to design and develop a microservices-based application that is also based on Docker containers, you will be able to design and develop any other, simpler application model.</span></span> <span data-ttu-id="97e6d-110">Örneğin, çok kapsayıcı lı bir yaklaşım da gerektiren üç katmanlı bir uygulama tasarlaabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97e6d-110">For example, you might design a three-tier application that also requires a multi-container approach.</span></span> <span data-ttu-id="97e6d-111">Bu nedenle ve mikrohizmet mimarileri konteyner dünyasında önemli bir eğilim olduğundan, bu bölümde Docker kapsayıcıları kullanılarak bir mikrohizmet mimarisi uygulaması üzerinde duruluyor.</span><span class="sxs-lookup"><span data-stu-id="97e6d-111">Because of that, and because microservice architectures are an important trend within the container world, this section focuses on a microservice architecture implementation using Docker containers.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="97e6d-112">[Önceki](../docker-application-development-process/docker-app-development-workflow.md)
>[Sonraki](microservice-application-design.md)</span><span class="sxs-lookup"><span data-stu-id="97e6d-112">[Previous](../docker-application-development-process/docker-app-development-workflow.md)
[Next](microservice-application-design.md)</span></span>
