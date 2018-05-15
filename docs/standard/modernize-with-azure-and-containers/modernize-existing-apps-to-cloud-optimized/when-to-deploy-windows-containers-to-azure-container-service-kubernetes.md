---
title: Azure kapsayıcı hizmeti (diğer bir deyişle, Kubernetes) Windows kapsayıcıları dağıtma zamanı
description: Azure Bulut ve Windows kapsayıcılarla varolan .NET uygulamaları modernize | Azure kapsayıcı hizmeti (diğer bir deyişle, Kubernetes) Windows kapsayıcıları dağıtma zamanı
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: b7f106e2b79a2c6bb24733debf7f4828505d66a6
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a><span data-ttu-id="c15f9-103">Azure kapsayıcı hizmeti (diğer bir deyişle, Kubernetes) Windows kapsayıcıları dağıtma zamanı</span><span class="sxs-lookup"><span data-stu-id="c15f9-103">When to deploy Windows Containers to Azure Container Service (that is, Kubernetes)</span></span>

<span data-ttu-id="c15f9-104">Azure kapsayıcı hizmeti popüler açık kaynak Araçlar ve teknolojiler yapılandırmasını özellikle Azure için en iyi duruma getirir.</span><span class="sxs-lookup"><span data-stu-id="c15f9-104">Azure Container Service optimizes the configuration of popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="c15f9-105">Taşınabilirlik kapsayıcılarınızı hem uygulama yapılandırmanızı sağlayan açık olan çözüm alın.</span><span class="sxs-lookup"><span data-stu-id="c15f9-105">You get an open solution that offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="c15f9-106">Boyut, ana bilgisayar sayısı ve orchestrator araçları seçin.</span><span class="sxs-lookup"><span data-stu-id="c15f9-106">You select the size, the number of hosts, and the orchestrator tools.</span></span> <span data-ttu-id="c15f9-107">Azure kapsayıcı hizmeti altyapı işler.</span><span class="sxs-lookup"><span data-stu-id="c15f9-107">Azure Container Service handles the infrastructure for you.</span></span>

<span data-ttu-id="c15f9-108">Zaten açık kaynak orchestrators Kubernetes, Docker Swarm veya DC/OS gibi çalışıyorsanız kapsayıcı iş yüklerinin buluta taşımak için var olan Yönetim uygulamalarınızı değiştirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="c15f9-108">If you are already working with open-source orchestrators like Kubernetes, Docker Swarm, or DC/OS, you don't need to change your existing management practices to move container workloads to the cloud.</span></span> <span data-ttu-id="c15f9-109">Zaten aşina uygulama yönetim araçlarını kullanın ve tercih ettiğiniz orchestrator için standart API uç noktaları bağlanın.</span><span class="sxs-lookup"><span data-stu-id="c15f9-109">Use the application management tools that you're already familiar with and connect via the standard API endpoints for the orchestrator of your choice.</span></span>

<span data-ttu-id="c15f9-110">Linux Docker kapsayıcıları kullanma, ancak yalnızca Windows kapsayıcıları için Önizleme durumda olabilir, bu orchestrators olgun ortamları demektir.</span><span class="sxs-lookup"><span data-stu-id="c15f9-110">All these orchestrators are mature environments if you are using Linux Docker containers, but might only be in Preview state for Windows Containers.</span></span>

<span data-ttu-id="c15f9-111">Kapsayıcıları için Kubernetes Örneğin, destek yerel (birinci sınıf citizen), bu nedenle Kubernetes üzerinde Windows kapsayıcıları kullanma (önizlemede ACS içindeki erken 2018 itibariyle) etkili de.</span><span class="sxs-lookup"><span data-stu-id="c15f9-111">For example, in Kubernetes, support for containers is native (first-class citizen), so using Windows Containers on Kubernetes is also effective (in preview in ACS as of early 2018).</span></span>

<span data-ttu-id="c15f9-112">Önemli Not: sistem gereksinimleri ve "daha fazla PaaS" Kubernetes için ACS (Azure kapsayıcı hizmeti) sürümüdür AKS (Azure Kubernetes hizmeti), Windows kapsayıcıları hala desteklenmez S2 2018 itibariyle, ancak, yakında desteklenecek.</span><span class="sxs-lookup"><span data-stu-id="c15f9-112">Important note: The evolved and “more PaaS” version of ACS (Azure Container Service) for Kubernetes is AKS (Azure Kubernetes Service), however, Windows Containers are still not supported as of Q2 2018, but it will be supported soon.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="c15f9-113">[Önceki](when-to-deploy-windows-containers-to-service-fabric.md)
[sonraki](choosing-azure-compute-options-for-container-based-applications.md)</span><span class="sxs-lookup"><span data-stu-id="c15f9-113">[Previous](when-to-deploy-windows-containers-to-service-fabric.md)
[Next](choosing-azure-compute-options-for-container-based-applications.md)</span></span>
