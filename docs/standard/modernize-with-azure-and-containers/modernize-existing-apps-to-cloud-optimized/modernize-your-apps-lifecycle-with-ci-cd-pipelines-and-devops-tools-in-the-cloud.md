---
title: Uygulamanızın yaşam döngüsü ile CI/CD işlem hatları ve DevOps araçları bulutta modernleştirin
description: Azure Bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirme | Uygulamanızın yaşam döngüsü ile CI/CD işlem hatları ve DevOps araçları bulutta modernleştirin
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: c4d3eaa50f6c7645c954ca65bf42c6c1eab3a68d
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47070792"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a><span data-ttu-id="762cd-103">Uygulamanızın yaşam döngüsü ile CI/CD işlem hatları ve DevOps araçları bulutta modernleştirin</span><span class="sxs-lookup"><span data-stu-id="762cd-103">Modernize your app's lifecycle with CI/CD pipelines and DevOps tools in the cloud</span></span>

<span data-ttu-id="762cd-104">Bugünkü işletmeler Market'te rekabetçi hale gelmesini hızlı bir hızda yenilik gerekir.</span><span class="sxs-lookup"><span data-stu-id="762cd-104">Today’s businesses need to innovate at a rapid pace to be competitive in the marketplace.</span></span> <span data-ttu-id="762cd-105">Yüksek kaliteli, modern uygulamalar oluşturabilmek için DevOps araçları ve yenilik sabit bu döngüsünü uygulamak için kritik olan işlemleri.</span><span class="sxs-lookup"><span data-stu-id="762cd-105">Delivering high-quality, modern applications requires DevOps tools and processes that are critical to implement this constant cycle of innovation.</span></span> <span data-ttu-id="762cd-106">Doğru DevOps araçlarıyla geliştiriciler sürekli dağıtımını kolaylaştırın ve daha hızlı sunun yenilikçi uygulamalar kullanıcıların alma.</span><span class="sxs-lookup"><span data-stu-id="762cd-106">With the right DevOps tools, developers can streamline continuous deployment and get innovative applications into the hands of users more quickly.</span></span>

<span data-ttu-id="762cd-107">Sürekli tümleştirme ve dağıtım yöntemleri de oluşturulmuş olsa da, özellikle çok kapsayıcılı uygulamaları ile çalışırken giriş kapsayıcıların yeni konuları tanıtır.</span><span class="sxs-lookup"><span data-stu-id="762cd-107">Although continuous integration and deployment practices are well established, the introduction of containers introduces new considerations, particularly when you are working with multi-container applications.</span></span>

<span data-ttu-id="762cd-108">Azure DevOps hizmetleriyle, sürekli tümleştirme ve çeşitli ortamlarda resmi Azure DevOps Hizmetleri dağıtım görevleri aracılığıyla çoklu kapsayıcı uygulamalarının dağıtımını destekler:</span><span class="sxs-lookup"><span data-stu-id="762cd-108">Azure DevOps Services supports continuous integration and deployment of multi-container applications to a variety of environments through the official Azure DevOps Services deployment tasks:</span></span>

-   <span data-ttu-id="762cd-109">[Tek başına konak VM'ye Docker dağıtma](https://docs.microsoft.com/azure/devops/build-release/apps/cd/deploy-docker-windowsvm) (Linux veya Windows Server 2016 veya üzeri)</span><span class="sxs-lookup"><span data-stu-id="762cd-109">[Deploy to standalone Docker Host VM](https://docs.microsoft.com/azure/devops/build-release/apps/cd/deploy-docker-windowsvm) (Linux or Windows Server 2016 or later)</span></span>

-   [<span data-ttu-id="762cd-110">Service Fabric'e dağıtma</span><span class="sxs-lookup"><span data-stu-id="762cd-110">Deploy to Service Fabric</span></span>](https://docs.microsoft.com/azure/service-fabric/service-fabric-tutorial-deploy-app-with-cicd-vsts)

-   [<span data-ttu-id="762cd-111">Azure Container Service – Kubernetes dağıtımı</span><span class="sxs-lookup"><span data-stu-id="762cd-111">Deploy to Azure Container Service – Kubernetes</span></span>](https://docs.microsoft.com/azure/devops/build-release/apps/cd/azure/deploy-container-kubernetes)

<span data-ttu-id="762cd-112">Ancak ayrıca dağıtabileceğiniz [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) veya betik tabanlı Azure DevOps Hizmetleri'nin görevlerini kullanarak DC/OS.</span><span class="sxs-lookup"><span data-stu-id="762cd-112">But you also can deploy to [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) or DC/OS by using Azure DevOps Services script-based tasks.</span></span>

<span data-ttu-id="762cd-113">Hızlı Dağıtım etkinleştirme devam etmek için bu araçlar, geliştirme ve CI/CD çözümleri ile kapsayıcı iş yükleri için mükemmel bir geliştirme için-test-geliştirmeden üretime kadar dağıtım deneyimleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="762cd-113">To continue facilitating deployment agility, these tools provide excellent dev-to-test-to-production deployment experiences for container workloads, with a choice of development and CI/CD solutions.</span></span>

<span data-ttu-id="762cd-114">Şekil 4-12 Azure Container Service'te bir Kubernetes kümesi dağıtır sürekli dağıtım işlem hattı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="762cd-114">Figure 4-12 shows a continuous deployment pipeline that deploys to a Kubernetes cluster in Azure Container Service.</span></span>

![Azure DevOps Hizmetleri sürekli dağıtım ardışık, bir Kubernetes kümesine dağıtma](./media/image12.png)

> <span data-ttu-id="762cd-116">**Şekil 4-12.**</span><span class="sxs-lookup"><span data-stu-id="762cd-116">**Figure 4-12.**</span></span> <span data-ttu-id="762cd-117">Azure DevOps Hizmetleri sürekli dağıtım ardışık, bir Kubernetes kümesine dağıtma</span><span class="sxs-lookup"><span data-stu-id="762cd-117">Azure DevOps Services continuous deployment pipeline, deploying to a Kubernetes cluster</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="762cd-118">[Önceki](modernize-your-apps-with-monitoring-and-telemetry.md)
[İleri](migrate-to-hybrid-cloud-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="762cd-118">[Previous](modernize-your-apps-with-monitoring-and-telemetry.md)
[Next](migrate-to-hybrid-cloud-scenarios.md)</span></span>
