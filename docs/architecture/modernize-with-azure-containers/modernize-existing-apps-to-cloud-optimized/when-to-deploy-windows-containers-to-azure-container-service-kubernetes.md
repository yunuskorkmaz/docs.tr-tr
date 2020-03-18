---
title: Windows Kapsayıcıları Azure Kapsayıcı Hizmetine ne zaman dağıtılır (diğer bir şekilde, Kubernetes)
description: Azure Bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernize edin | Windows Kapsayıcıları Azure Kapsayıcı Hizmetine ne zaman dağıtılır (diğer bir şekilde, Kubernetes)
ms.date: 04/30/2018
ms.openlocfilehash: 903082deba635dd0dfc22d0186fbc589f8d05b92
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "68676912"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a><span data-ttu-id="31251-103">Windows Kapsayıcıları Azure Kapsayıcı Hizmetine ne zaman dağıtılır (diğer bir şekilde, Kubernetes)</span><span class="sxs-lookup"><span data-stu-id="31251-103">When to deploy Windows Containers to Azure Container Service (that is, Kubernetes)</span></span>

<span data-ttu-id="31251-104">Azure Kapsayıcı Hizmeti, azure için özel olarak popüler açık kaynak araçları nın ve teknolojilerin yapılandırmasını optimize eder.</span><span class="sxs-lookup"><span data-stu-id="31251-104">Azure Container Service optimizes the configuration of popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="31251-105">Hem kapsayıcılarınız hem de uygulama yapılandırmanız için taşınabilirlik sunan açık bir çözüme sahip olursunuz.</span><span class="sxs-lookup"><span data-stu-id="31251-105">You get an open solution that offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="31251-106">Boyutu, ana bilgisayar sayısını ve orkestratör araçlarını seçersiniz.</span><span class="sxs-lookup"><span data-stu-id="31251-106">You select the size, the number of hosts, and the orchestrator tools.</span></span> <span data-ttu-id="31251-107">Azure Kapsayıcı Hizmeti, altyapıyı sizin için işler.</span><span class="sxs-lookup"><span data-stu-id="31251-107">Azure Container Service handles the infrastructure for you.</span></span>

<span data-ttu-id="31251-108">Zaten Kubernetes, Docker Swarm veya DC/OS gibi açık kaynak kodlu orkestratörlerle çalışıyorsanız, kapsayıcı iş yüklerini buluta taşımak için mevcut yönetim uygulamalarınızı değiştirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="31251-108">If you are already working with open-source orchestrators like Kubernetes, Docker Swarm, or DC/OS, you don't need to change your existing management practices to move container workloads to the cloud.</span></span> <span data-ttu-id="31251-109">Zaten aşina olduğunuz uygulama yönetim araçlarını kullanın ve seçtiğiniz orkestratör için standart API uç noktaları üzerinden bağlanın.</span><span class="sxs-lookup"><span data-stu-id="31251-109">Use the application management tools that you're already familiar with and connect via the standard API endpoints for the orchestrator of your choice.</span></span>

<span data-ttu-id="31251-110">Linux Docker kapsayıcıları kullanıyorsanız, tüm bu orkestratörler olgun ortamlardır, ancak yalnızca Windows Kapsayıcıları için Önizleme durumunda olabilir.</span><span class="sxs-lookup"><span data-stu-id="31251-110">All these orchestrators are mature environments if you are using Linux Docker containers, but might only be in Preview state for Windows Containers.</span></span>

<span data-ttu-id="31251-111">Örneğin, Kubernetes'te kapsayıcıdesteği yereldir (birinci sınıf vatandaştır), bu nedenle Kubernetes'te Windows Kapsayıcıları kullanmak da etkilidir (2018'in başlarından itibaren ACS'de önizlemede).</span><span class="sxs-lookup"><span data-stu-id="31251-111">For example, in Kubernetes, support for containers is native (first-class citizen), so using Windows Containers on Kubernetes is also effective (in preview in ACS as of early 2018).</span></span>

<span data-ttu-id="31251-112">Önemli not: Kubernetes için ACS'nin (Azure Konteyner Hizmeti) gelişmiş ve "daha fazla PaaS" sürümü AKS 'dir (Azure Kubernetes Hizmeti), Ancak Windows Kapsayıcıları Q2 2018 itibariyle hala desteklenmez, ancak yakında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="31251-112">Important note: The evolved and “more PaaS” version of ACS (Azure Container Service) for Kubernetes is AKS (Azure Kubernetes Service), however, Windows Containers are still not supported as of Q2 2018, but it will be supported soon.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="31251-113">[Önceki](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
>[Sonraki](choosing-azure-compute-options-for-container-based-applications.md)</span><span class="sxs-lookup"><span data-stu-id="31251-113">[Previous](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
[Next](choosing-azure-compute-options-for-container-based-applications.md)</span></span>
