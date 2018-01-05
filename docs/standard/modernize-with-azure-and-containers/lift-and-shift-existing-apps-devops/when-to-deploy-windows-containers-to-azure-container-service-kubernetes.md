---
title: "Azure kapsayıcı hizmeti (diğer bir deyişle, Kubernetes) Windows kapsayıcıları dağıtma zamanı"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Azure kapsayıcı hizmeti (diğer bir deyişle, Kubernetes) Windows kapsayıcıları dağıtma zamanı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2f7ed0c9ebf1c80ae6cae4311b2682d3cc161623
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a><span data-ttu-id="abcdd-103">Azure kapsayıcı hizmeti (diğer bir deyişle, Kubernetes) Windows kapsayıcıları dağıtma zamanı</span><span class="sxs-lookup"><span data-stu-id="abcdd-103">When to deploy Windows Containers to Azure Container Service (that is, Kubernetes)</span></span>

<span data-ttu-id="abcdd-104">Azure kapsayıcı hizmeti popüler açık kaynak Araçlar ve teknolojiler yapılandırmasını özellikle Azure için en iyi duruma getirir.</span><span class="sxs-lookup"><span data-stu-id="abcdd-104">Azure Container Service optimizes the configuration of popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="abcdd-105">Taşınabilirlik kapsayıcılarınızı hem uygulama yapılandırmanızı sağlayan açık olan çözüm alın.</span><span class="sxs-lookup"><span data-stu-id="abcdd-105">You get an open solution that offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="abcdd-106">Boyut, ana bilgisayar sayısı ve orchestrator araçları seçin.</span><span class="sxs-lookup"><span data-stu-id="abcdd-106">You select the size, the number of hosts, and the orchestrator tools.</span></span> <span data-ttu-id="abcdd-107">Azure kapsayıcı hizmeti altyapı işler.</span><span class="sxs-lookup"><span data-stu-id="abcdd-107">Azure Container Service handles the infrastructure for you.</span></span>

<span data-ttu-id="abcdd-108">Zaten açık kaynak orchestrators Kubernetes, Docker Swarm veya DC/OS gibi çalışıyorsanız kapsayıcı iş yüklerinin buluta taşımak için var olan Yönetim uygulamalarınızı değiştirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="abcdd-108">If you are already working with open-source orchestrators like Kubernetes, Docker Swarm, or DC/OS, you don't need to change your existing management practices to move container workloads to the cloud.</span></span> <span data-ttu-id="abcdd-109">Zaten aşina ve tercih ettiğiniz orchestrator için standart API uç noktaları bağlanma uygulama yönetim araçlarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="abcdd-109">Use the application management tools that you're already familiar with, and connect via the standard API endpoints for the orchestrator of your choice.</span></span>

<span data-ttu-id="abcdd-110">Bu orchestrators Linux Docker kapsayıcılar, ancak bunlar da destek Windows kapsayıcıları 2017 gibi (bazıları daha önce bazıları daha yakın zamanda üzerinde orchestrator bağlı olarak), kullanmakta olduğunuz olgun ortamları demektir.</span><span class="sxs-lookup"><span data-stu-id="abcdd-110">All these orchestrators are mature environments if you are using Linux Docker containers, but they also support Windows Containers as of 2017 (some earlier, some more recently, depending on the orchestrator).</span></span>

<span data-ttu-id="abcdd-111">Kapsayıcıları için Kubernetes Örneğin, destek Windows kapsayıcıları üzerinde Kubernetes bunu kullanarak yerel (birinci sınıf citizen), ayrıca çok etkili ve güvenilir (kadar önizlemede erken 2017 kalan).</span><span class="sxs-lookup"><span data-stu-id="abcdd-111">For example, in Kubernetes, support for containers is native (first-class citizen), so using Windows Containers on Kubernetes is also very effective and reliable (in preview until early fall 2017).</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="abcdd-112">[Önceki](when-to-deploy-windows-containers-to-service-fabric.md)
[sonraki](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="abcdd-112">[Previous](when-to-deploy-windows-containers-to-service-fabric.md)
[Next](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span></span>
