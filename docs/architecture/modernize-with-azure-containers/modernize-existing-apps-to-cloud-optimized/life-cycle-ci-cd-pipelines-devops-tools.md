---
title: Bulutta CI/CD işlem hatları ve DevOps araçları ile uygulama yaşam döngüsünü modernleştirme
description: Azure bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirin | Bulutta CI/CD işlem hatları ve DevOps araçları ile uygulamanızın yaşam döngüsünü modernleştirin
ms.date: 04/30/2018
ms.openlocfilehash: 17a78c108bfc61471128a34191ec7a5d7cc28289
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503855"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a><span data-ttu-id="c9a05-103">Bulutta CI/CD işlem hatları ve DevOps araçları ile uygulama yaşam döngüsünü modernleştirme</span><span class="sxs-lookup"><span data-stu-id="c9a05-103">Modernize your app's lifecycle with CI/CD pipelines and DevOps tools in the cloud</span></span>

<span data-ttu-id="c9a05-104">Günümüzde işletmelerin Market 'te rekabet etmek için hızlı bir hızla yenilik yapın gerekir.</span><span class="sxs-lookup"><span data-stu-id="c9a05-104">Today’s businesses need to innovate at a rapid pace to be competitive in the marketplace.</span></span> <span data-ttu-id="c9a05-105">Yüksek kaliteli, modern uygulamalar sunma, bu sabit yenilik döngüsünü uygulamak için kritik olan DevOps araçları ve işlemleri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c9a05-105">Delivering high-quality, modern applications requires DevOps tools and processes that are critical to implement this constant cycle of innovation.</span></span> <span data-ttu-id="c9a05-106">Geliştiriciler doğru DevOps araçlarıyla sürekli dağıtımı kolaylaştırabilir ve yenilikçi uygulamaları kullanıcılara daha hızlı bir şekilde alabilir.</span><span class="sxs-lookup"><span data-stu-id="c9a05-106">With the right DevOps tools, developers can streamline continuous deployment and get innovative applications into the hands of users more quickly.</span></span>

<span data-ttu-id="c9a05-107">Sürekli tümleştirme ve dağıtım uygulamaları iyi şekilde kurulabilse de, kapsayıcıların tanıtımı özellikle çok Kapsayıcılı uygulamalarla çalışırken yeni hususlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="c9a05-107">Although continuous integration and deployment practices are well established, the introduction of containers introduces new considerations, particularly when you are working with multi-container applications.</span></span>

<span data-ttu-id="c9a05-108">Azure DevOps Services, çok Kapsayıcılı uygulamaların, resmi Azure DevOps Services dağıtım görevleri aracılığıyla çeşitli ortamlara sürekli tümleştirmeyi ve dağıtılmasını destekler:</span><span class="sxs-lookup"><span data-stu-id="c9a05-108">Azure DevOps Services supports continuous integration and deployment of multi-container applications to a variety of environments through the official Azure DevOps Services deployment tasks:</span></span>

- [<span data-ttu-id="c9a05-109">Azure Kapsayıcılar için Web App dağıtma</span><span class="sxs-lookup"><span data-stu-id="c9a05-109">Deploy to an Azure Web App for Containers</span></span>](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-docker-webapp?tabs=dotnet-core)

- [<span data-ttu-id="c9a05-110">Azure Kubernetes hizmetine dağıtma</span><span class="sxs-lookup"><span data-stu-id="c9a05-110">Deploy to Azure Kubernetes Service</span></span>](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-aks?tabs=dotnet-core)

<span data-ttu-id="c9a05-111">Ancak, komut dosyası tabanlı görevleri Azure DevOps Services kullanarak [Docker Sısınma](https://blog.jcorioland.io/archives/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services.html) veya DC/OS 'a da dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9a05-111">But you also can deploy to [Docker Swarm](https://blog.jcorioland.io/archives/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services.html) or DC/OS by using Azure DevOps Services script-based tasks.</span></span>

<span data-ttu-id="c9a05-112">Dağıtım çevikliğini kolaylaştırmaya devam etmek için bu araçlar, bir geliştirme ve CI/CD çözümleri seçimiyle kapsayıcı iş yükleri için mükemmel geliştirme ve test aşamasına dağıtım deneyimleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c9a05-112">To continue facilitating deployment agility, these tools provide excellent dev-to-test-to-production deployment experiences for container workloads, with a choice of development and CI/CD solutions.</span></span>

<span data-ttu-id="c9a05-113">Şekil 4-12 Azure Container Service bir Kubernetes kümesine dağıtan bir sürekli dağıtım işlem hattı gösterir.</span><span class="sxs-lookup"><span data-stu-id="c9a05-113">Figure 4-12 shows a continuous deployment pipeline that deploys to a Kubernetes cluster in Azure Container Service.</span></span>

![Bir Kubernetes kümesine dağıtmanın Azure DevOps Services ekran görüntüsü.](./media/life-cycle-ci-cd-pipelines-devops-tools/deploy-mvc-app-container-kubernetes.png)

<span data-ttu-id="c9a05-115">**Şekil 4-12.**</span><span class="sxs-lookup"><span data-stu-id="c9a05-115">**Figure 4-12.**</span></span> <span data-ttu-id="c9a05-116">Azure DevOps Services sürekli dağıtım işlem hattı, bir Kubernetes kümesine dağıtma</span><span class="sxs-lookup"><span data-stu-id="c9a05-116">Azure DevOps Services continuous deployment pipeline, deploying to a Kubernetes cluster</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c9a05-117">[Önceki](modernize-your-apps-with-monitoring-and-telemetry.md)
>[İleri](migrate-to-hybrid-cloud-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="c9a05-117">[Previous](modernize-your-apps-with-monitoring-and-telemetry.md)
[Next](migrate-to-hybrid-cloud-scenarios.md)</span></span>
