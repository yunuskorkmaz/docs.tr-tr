---
title: Azure Container Service (Kubernetes) için Windows kapsayıcıları dağıtma zamanı
description: Azure Bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirme | Azure Container Service (Kubernetes) için Windows kapsayıcıları dağıtma zamanı
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: 0b803b104f905fddac7939d7b070c206aabffeda
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011976"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a><span data-ttu-id="23dc1-103">Azure Container Service (Kubernetes) için Windows kapsayıcıları dağıtma zamanı</span><span class="sxs-lookup"><span data-stu-id="23dc1-103">When to deploy Windows Containers to Azure Container Service (that is, Kubernetes)</span></span>

<span data-ttu-id="23dc1-104">Azure kapsayıcı hizmeti popüler açık kaynaklı araçların ve teknolojilerin yapılandırmasını özellikle Azure'a yönelik en iyi duruma getirir.</span><span class="sxs-lookup"><span data-stu-id="23dc1-104">Azure Container Service optimizes the configuration of popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="23dc1-105">Hem kapsayıcılarınız için hem de uygulama yapılandırmanız için taşınabilirlik sunan bir açık çözümü sahip olursunuz.</span><span class="sxs-lookup"><span data-stu-id="23dc1-105">You get an open solution that offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="23dc1-106">Boyutu, konak sayısını ve düzenleyici araçlarını seçmeniz.</span><span class="sxs-lookup"><span data-stu-id="23dc1-106">You select the size, the number of hosts, and the orchestrator tools.</span></span> <span data-ttu-id="23dc1-107">Azure Container Service, altyapı sizin yerinize çözer.</span><span class="sxs-lookup"><span data-stu-id="23dc1-107">Azure Container Service handles the infrastructure for you.</span></span>

<span data-ttu-id="23dc1-108">Zaten açık kaynak düzenleyicileri Kubernetes, Docker Swarm veya DC/OS gibi çalışıyorsanız kapsayıcı iş yüklerini buluta taşımak için mevcut yönetim uygulamalarınızı değiştirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="23dc1-108">If you are already working with open-source orchestrators like Kubernetes, Docker Swarm, or DC/OS, you don't need to change your existing management practices to move container workloads to the cloud.</span></span> <span data-ttu-id="23dc1-109">Zaten alışkın olduğunuz uygulama yönetimi araçlarını kullanın ve tercih ettiğiniz orchestrator için standart API uç noktaları aracılığıyla bağlanın.</span><span class="sxs-lookup"><span data-stu-id="23dc1-109">Use the application management tools that you're already familiar with and connect via the standard API endpoints for the orchestrator of your choice.</span></span>

<span data-ttu-id="23dc1-110">Linux Docker kapsayıcılarını kullanarak ancak yalnızca Windows kapsayıcıları için Önizleme durumunda olabilir, bu düzenleyicileri olgun ortamları vardır.</span><span class="sxs-lookup"><span data-stu-id="23dc1-110">All these orchestrators are mature environments if you are using Linux Docker containers, but might only be in Preview state for Windows Containers.</span></span>

<span data-ttu-id="23dc1-111">Kapsayıcılar için Kubernetes, örneğin, destek yerel (birinci sınıf Vatandaşlık), Windows kapsayıcıları azure'da Kubernetes kullanarak etkin (önizlemede ACS erken 2018'den itibaren) de.</span><span class="sxs-lookup"><span data-stu-id="23dc1-111">For example, in Kubernetes, support for containers is native (first-class citizen), so using Windows Containers on Kubernetes is also effective (in preview in ACS as of early 2018).</span></span>

<span data-ttu-id="23dc1-112">Önemli Not: Sistem gereksinimleri ve "daha fazla PaaS" sürümüdür (Azure Container Service) bir ACS kubernetes AKS (Azure Kubernetes hizmeti), ancak Windows kapsayıcıları hala desteklenmez S2 2018'den itibaren ancak yakında desteklenecek.</span><span class="sxs-lookup"><span data-stu-id="23dc1-112">Important note: The evolved and “more PaaS” version of ACS (Azure Container Service) for Kubernetes is AKS (Azure Kubernetes Service), however, Windows Containers are still not supported as of Q2 2018, but it will be supported soon.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="23dc1-113">[Önceki](when-to-deploy-windows-containers-to-service-fabric.md)
>[İleri](choosing-azure-compute-options-for-container-based-applications.md)</span><span class="sxs-lookup"><span data-stu-id="23dc1-113">[Previous](when-to-deploy-windows-containers-to-service-fabric.md)
[Next](choosing-azure-compute-options-for-container-based-applications.md)</span></span>