---
title: Windows kapsayıcıları Azure Container Service dağıtım zaman (yani, Kubernetes)
description: Azure bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirin | Windows kapsayıcıları Azure Container Service dağıtım zaman (yani, Kubernetes)
ms.date: 04/30/2018
ms.openlocfilehash: 903082deba635dd0dfc22d0186fbc589f8d05b92
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/08/2019
ms.locfileid: "68676912"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a><span data-ttu-id="025cd-103">Windows kapsayıcıları Azure Container Service dağıtım zaman (yani, Kubernetes)</span><span class="sxs-lookup"><span data-stu-id="025cd-103">When to deploy Windows Containers to Azure Container Service (that is, Kubernetes)</span></span>

<span data-ttu-id="025cd-104">Azure Container Service, popüler açık kaynaklı araçların ve teknolojilerin yapılandırmasını özellikle Azure için iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="025cd-104">Azure Container Service optimizes the configuration of popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="025cd-105">Kapsayıcılar ve uygulama yapılandırmanız için taşınabilirlik sağlayan açık bir çözüm alırsınız.</span><span class="sxs-lookup"><span data-stu-id="025cd-105">You get an open solution that offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="025cd-106">Boyut, ana bilgisayar sayısı ve Orchestrator Araçları ' nı seçersiniz.</span><span class="sxs-lookup"><span data-stu-id="025cd-106">You select the size, the number of hosts, and the orchestrator tools.</span></span> <span data-ttu-id="025cd-107">Azure Container Service altyapıyı sizin için işler.</span><span class="sxs-lookup"><span data-stu-id="025cd-107">Azure Container Service handles the infrastructure for you.</span></span>

<span data-ttu-id="025cd-108">Kubernetes, Docker Sısınma veya DC/OS gibi açık kaynaklı düzenleyiciler ile zaten çalışıyorsanız, kapsayıcı iş yüklerini buluta taşımak için mevcut yönetim uygulamalarınızı değiştirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="025cd-108">If you are already working with open-source orchestrators like Kubernetes, Docker Swarm, or DC/OS, you don't need to change your existing management practices to move container workloads to the cloud.</span></span> <span data-ttu-id="025cd-109">Zaten bildiğiniz uygulama yönetimi araçlarını kullanın ve seçtiğiniz Orchestrator için Standart API uç noktaları aracılığıyla bağlanın.</span><span class="sxs-lookup"><span data-stu-id="025cd-109">Use the application management tools that you're already familiar with and connect via the standard API endpoints for the orchestrator of your choice.</span></span>

<span data-ttu-id="025cd-110">Linux Docker Kapsayıcıları kullanıyorsanız, ancak yalnızca Windows kapsayıcıları önizleme durumunda olabilir.</span><span class="sxs-lookup"><span data-stu-id="025cd-110">All these orchestrators are mature environments if you are using Linux Docker containers, but might only be in Preview state for Windows Containers.</span></span>

<span data-ttu-id="025cd-111">Örneğin, Kubernetes 'te kapsayıcılar için destek yerel (birinci sınıf vatandaşlık), bu nedenle Kubernetes üzerinde Windows kapsayıcıları kullanmak da etkilidir (ACS 'nin erken 2018 itibariyle önizlemesi için).</span><span class="sxs-lookup"><span data-stu-id="025cd-111">For example, in Kubernetes, support for containers is native (first-class citizen), so using Windows Containers on Kubernetes is also effective (in preview in ACS as of early 2018).</span></span>

<span data-ttu-id="025cd-112">Önemli Not: Kubernetes için ACS (Azure Container Service) ile ilgili ve "daha PaaS" sürümü AKS (Azure Kubernetes hizmeti), ancak Windows kapsayıcıları, S2 2018 itibariyle hala desteklenmiyordur, ancak yakında desteklenecektir.</span><span class="sxs-lookup"><span data-stu-id="025cd-112">Important note: The evolved and “more PaaS” version of ACS (Azure Container Service) for Kubernetes is AKS (Azure Kubernetes Service), however, Windows Containers are still not supported as of Q2 2018, but it will be supported soon.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="025cd-113">[Önceki](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
>[İleri](choosing-azure-compute-options-for-container-based-applications.md)</span><span class="sxs-lookup"><span data-stu-id="025cd-113">[Previous](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
[Next](choosing-azure-compute-options-for-container-based-applications.md)</span></span>
