---
title: Bulutta CI/CD işlem hatları ve DevOps araçları ile uygulama yaşam döngüsünü modernleştirme
description: Azure Bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernize edin | Buluttaki CI/CD boru hatları ve DevOps araçlarıyla uygulamanızın yaşam döngüsünü modernize edin
ms.date: 04/30/2018
ms.openlocfilehash: 17a78c108bfc61471128a34191ec7a5d7cc28289
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503855"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a><span data-ttu-id="6f9a2-103">Bulutta CI/CD işlem hatları ve DevOps araçları ile uygulama yaşam döngüsünü modernleştirme</span><span class="sxs-lookup"><span data-stu-id="6f9a2-103">Modernize your app's lifecycle with CI/CD pipelines and DevOps tools in the cloud</span></span>

<span data-ttu-id="6f9a2-104">Günümüzün işletmeleri pazarda rekabetçi olmak için hızlı bir hızda yenilik yapmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="6f9a2-104">Today’s businesses need to innovate at a rapid pace to be competitive in the marketplace.</span></span> <span data-ttu-id="6f9a2-105">Yüksek kaliteli, modern uygulamalar sunmak, bu sürekli yenilik döngüsünü uygulamak için kritik öneme sahip DevOps araçları ve süreçleri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="6f9a2-105">Delivering high-quality, modern applications requires DevOps tools and processes that are critical to implement this constant cycle of innovation.</span></span> <span data-ttu-id="6f9a2-106">Doğru DevOps araçlarıyla, geliştiriciler sürekli dağıtımı düzene sokabilir ve yenilikçi uygulamaları kullanıcıların eline daha hızlı bir şekilde aktarabilir.</span><span class="sxs-lookup"><span data-stu-id="6f9a2-106">With the right DevOps tools, developers can streamline continuous deployment and get innovative applications into the hands of users more quickly.</span></span>

<span data-ttu-id="6f9a2-107">Sürekli tümleştirme ve dağıtım uygulamaları iyi kurulmuş olsa da, kapsayıcıların başlatılması, özellikle çok kapsayıcılı uygulamalarla çalışırken yeni hususlar sunar.</span><span class="sxs-lookup"><span data-stu-id="6f9a2-107">Although continuous integration and deployment practices are well established, the introduction of containers introduces new considerations, particularly when you are working with multi-container applications.</span></span>

<span data-ttu-id="6f9a2-108">Azure DevOps Hizmetleri, resmi Azure DevOps Hizmetleri dağıtım görevleri aracılığıyla çoklu kapsayıcı uygulamalarının çeşitli ortamlara sürekli entegrasyonunu ve dağıtımını destekler:</span><span class="sxs-lookup"><span data-stu-id="6f9a2-108">Azure DevOps Services supports continuous integration and deployment of multi-container applications to a variety of environments through the official Azure DevOps Services deployment tasks:</span></span>

- [<span data-ttu-id="6f9a2-109">Kapsayıcılar için Bir Azure Web Uygulamasına dağıtma</span><span class="sxs-lookup"><span data-stu-id="6f9a2-109">Deploy to an Azure Web App for Containers</span></span>](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-docker-webapp?tabs=dotnet-core)

- [<span data-ttu-id="6f9a2-110">Azure Kubernetes Service’e dağıtma</span><span class="sxs-lookup"><span data-stu-id="6f9a2-110">Deploy to Azure Kubernetes Service</span></span>](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-aks?tabs=dotnet-core)

<span data-ttu-id="6f9a2-111">Ancak, Azure DevOps Hizmetleri komut dosyası tabanlı görevleri kullanarak [Docker Swarm](https://blog.jcorioland.io/archives/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services.html) veya DC/OS'ye de dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f9a2-111">But you also can deploy to [Docker Swarm](https://blog.jcorioland.io/archives/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services.html) or DC/OS by using Azure DevOps Services script-based tasks.</span></span>

<span data-ttu-id="6f9a2-112">Dağıtım çevikliğini kolaylaştırmaya devam etmek için bu araçlar, geliştirme ve CI/CD çözümleri seçenekleriyle konteyner iş yükleri için mükemmel geliştirme-test-üretim dağıtım deneyimleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f9a2-112">To continue facilitating deployment agility, these tools provide excellent dev-to-test-to-production deployment experiences for container workloads, with a choice of development and CI/CD solutions.</span></span>

<span data-ttu-id="6f9a2-113">Şekil 4-12, Azure Kapsayıcı Hizmeti'nde bir Kubernetes kümesine dağıtılan sürekli bir dağıtım ardışık hattını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6f9a2-113">Figure 4-12 shows a continuous deployment pipeline that deploys to a Kubernetes cluster in Azure Container Service.</span></span>

![Bir Kubernetes kümesine dağıtılatan Azure DevOps Hizmetlerinin ekran görüntüsü.](./media/life-cycle-ci-cd-pipelines-devops-tools/deploy-mvc-app-container-kubernetes.png)

<span data-ttu-id="6f9a2-115">**Şekil 4-12.**</span><span class="sxs-lookup"><span data-stu-id="6f9a2-115">**Figure 4-12.**</span></span> <span data-ttu-id="6f9a2-116">Azure DevOps Hizmetleri sürekli dağıtım boru hattı, bir Kubernetes kümesine dağıtım</span><span class="sxs-lookup"><span data-stu-id="6f9a2-116">Azure DevOps Services continuous deployment pipeline, deploying to a Kubernetes cluster</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="6f9a2-117">[Önceki](modernize-your-apps-with-monitoring-and-telemetry.md)
>[Sonraki](migrate-to-hybrid-cloud-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="6f9a2-117">[Previous](modernize-your-apps-with-monitoring-and-telemetry.md)
[Next](migrate-to-hybrid-cloud-scenarios.md)</span></span>
