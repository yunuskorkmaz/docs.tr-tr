---
title: Bulutta CI/CD işlem hatları ve DevOps araçları ile uygulama yaşam döngüsünü modernleştirme
description: Azure bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirin | Bulutta CI/CD işlem hatları ve DevOps araçları ile uygulamanızın yaşam döngüsünü modernleştirin
ms.date: 04/30/2018
ms.openlocfilehash: fb4bfab4a891e9c8a73867f18cb8249775f9b7b9
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68676978"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a><span data-ttu-id="f3f36-103">Bulutta CI/CD işlem hatları ve DevOps araçları ile uygulama yaşam döngüsünü modernleştirme</span><span class="sxs-lookup"><span data-stu-id="f3f36-103">Modernize your app's lifecycle with CI/CD pipelines and DevOps tools in the cloud</span></span>

<span data-ttu-id="f3f36-104">Günümüzde işletmelerin Market 'te rekabet etmek için hızlı bir hızla yenilik yapın gerekir.</span><span class="sxs-lookup"><span data-stu-id="f3f36-104">Today’s businesses need to innovate at a rapid pace to be competitive in the marketplace.</span></span> <span data-ttu-id="f3f36-105">Yüksek kaliteli, modern uygulamalar sunma, bu sabit yenilik döngüsünü uygulamak için kritik olan DevOps araçları ve işlemleri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f3f36-105">Delivering high-quality, modern applications requires DevOps tools and processes that are critical to implement this constant cycle of innovation.</span></span> <span data-ttu-id="f3f36-106">Geliştiriciler doğru DevOps araçlarıyla sürekli dağıtımı kolaylaştırabilir ve yenilikçi uygulamaları kullanıcılara daha hızlı bir şekilde alabilir.</span><span class="sxs-lookup"><span data-stu-id="f3f36-106">With the right DevOps tools, developers can streamline continuous deployment and get innovative applications into the hands of users more quickly.</span></span>

<span data-ttu-id="f3f36-107">Sürekli tümleştirme ve dağıtım uygulamaları iyi şekilde kurulabilse de, kapsayıcıların tanıtımı özellikle çok Kapsayıcılı uygulamalarla çalışırken yeni hususlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="f3f36-107">Although continuous integration and deployment practices are well established, the introduction of containers introduces new considerations, particularly when you are working with multi-container applications.</span></span>

<span data-ttu-id="f3f36-108">Azure DevOps Services, çok Kapsayıcılı uygulamaların, resmi Azure DevOps Services dağıtım görevleri aracılığıyla çeşitli ortamlara sürekli tümleştirmeyi ve dağıtılmasını destekler:</span><span class="sxs-lookup"><span data-stu-id="f3f36-108">Azure DevOps Services supports continuous integration and deployment of multi-container applications to a variety of environments through the official Azure DevOps Services deployment tasks:</span></span>

- [<span data-ttu-id="f3f36-109">Azure Kapsayıcılar için Web App dağıtma</span><span class="sxs-lookup"><span data-stu-id="f3f36-109">Deploy to an Azure Web App for Containers</span></span>](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-docker-webapp?view=azure-devops)

- [<span data-ttu-id="f3f36-110">Azure Container Service dağıtma-Kubernetes</span><span class="sxs-lookup"><span data-stu-id="f3f36-110">Deploy to Azure Container Service – Kubernetes</span></span>](https://docs.microsoft.com/azure/devops/build-release/apps/cd/azure/deploy-container-kubernetes)

<span data-ttu-id="f3f36-111">Ancak, komut dosyası tabanlı görevleri Azure DevOps Services kullanarak [Docker Sısınma](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) veya DC/OS 'a da dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3f36-111">But you also can deploy to [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) or DC/OS by using Azure DevOps Services script-based tasks.</span></span>

<span data-ttu-id="f3f36-112">Dağıtım çevikliğini kolaylaştırmaya devam etmek için bu araçlar, bir geliştirme ve CI/CD çözümleri seçimiyle kapsayıcı iş yükleri için mükemmel geliştirme ve test aşamasına dağıtım deneyimleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="f3f36-112">To continue facilitating deployment agility, these tools provide excellent dev-to-test-to-production deployment experiences for container workloads, with a choice of development and CI/CD solutions.</span></span>

<span data-ttu-id="f3f36-113">Şekil 4-12 Azure Container Service bir Kubernetes kümesine dağıtan bir sürekli dağıtım işlem hattı gösterir.</span><span class="sxs-lookup"><span data-stu-id="f3f36-113">Figure 4-12 shows a continuous deployment pipeline that deploys to a Kubernetes cluster in Azure Container Service.</span></span>

![Azure DevOps Services sürekli dağıtım işlem hattı, bir Kubernetes kümesine dağıtma](./media/image12.png)

> <span data-ttu-id="f3f36-115">**Şekil 4-12.**</span><span class="sxs-lookup"><span data-stu-id="f3f36-115">**Figure 4-12.**</span></span> <span data-ttu-id="f3f36-116">Azure DevOps Services sürekli dağıtım işlem hattı, bir Kubernetes kümesine dağıtma</span><span class="sxs-lookup"><span data-stu-id="f3f36-116">Azure DevOps Services continuous deployment pipeline, deploying to a Kubernetes cluster</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f3f36-117">[Önceki](modernize-your-apps-with-monitoring-and-telemetry.md)İleri
>[](migrate-to-hybrid-cloud-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="f3f36-117">[Previous](modernize-your-apps-with-monitoring-and-telemetry.md)
[Next](migrate-to-hybrid-cloud-scenarios.md)</span></span>
