---
title: "CI/CD ardışık düzen ve bulutta DevOps araçları ile uygulama yaşam döngüsü modernize"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | CI/CD ardışık düzen ve bulutta DevOps araçları ile uygulama yaşam döngüsü modernize"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 668c48b64cab964da65625ef5326fb75e133b3b9
ms.sourcegitcommit: d3cfda0943364aaf6ccd574f55f584576c8a4fee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2018
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a><span data-ttu-id="95765-103">CI/CD ardışık düzen ve bulutta DevOps araçları ile uygulama yaşam döngüsü modernize</span><span class="sxs-lookup"><span data-stu-id="95765-103">Modernize your app's lifecycle with CI/CD pipelines and DevOps tools in the cloud</span></span>

<span data-ttu-id="95765-104">Günümüzün işletmeler markette rekabetçi olmasını hızlı hızda yenilik gerekir.</span><span class="sxs-lookup"><span data-stu-id="95765-104">Today’s businesses need to innovate at a rapid pace to be competitive in the marketplace.</span></span> <span data-ttu-id="95765-105">Yüksek kaliteli teslim etmek, modern uygulamalar gerektirir DevOps araçları ve yenilik sabit bu döngüsünü uygulamak için kritik olan işlemleri.</span><span class="sxs-lookup"><span data-stu-id="95765-105">Delivering high-quality, modern applications requires DevOps tools and processes that are critical to implement this constant cycle of innovation.</span></span> <span data-ttu-id="95765-106">Sağ DevOps araçları ile geliştiriciler sürekli dağıtım kolaylaştırmak ve ellerini yenilikçi uygulamalara kullanıcıların daha hızlı alın.</span><span class="sxs-lookup"><span data-stu-id="95765-106">With the right DevOps tools, developers can streamline continuous deployment and get innovative applications into the hands of users more quickly.</span></span>

<span data-ttu-id="95765-107">Sürekli tümleştirme ve dağıtım yöntemleri iyi oluşturulmuş olsa da, özellikle çok kapsayıcı uygulamaları ile çalışırken kapsayıcıları giriş yeni konuları tanıtır.</span><span class="sxs-lookup"><span data-stu-id="95765-107">Although continuous integration and deployment practices are well established, the introduction of containers introduces new considerations, particularly when you are working with multi-container applications.</span></span>

<span data-ttu-id="95765-108">Visual Studio Team Services sürekli tümleştirme ve resmi Team Services dağıtım görevleri aracılığıyla ortamları çeşitli çok kapsayıcı uygulamalarının dağıtımını destekler:</span><span class="sxs-lookup"><span data-stu-id="95765-108">Visual Studio Team Services supports continuous integration and deployment of multi-container applications to a variety of environments through the official Team Services deployment tasks:</span></span>

-   <span data-ttu-id="95765-109">[Tek başına Docker ana VM dağıtmak](https://docs.microsoft.com/vsts/build-release/apps/cd/deploy-docker-windowsvm) (Linux veya Windows Server 2016 veya üstü)</span><span class="sxs-lookup"><span data-stu-id="95765-109">[Deploy to standalone Docker Host VM](https://docs.microsoft.com/vsts/build-release/apps/cd/deploy-docker-windowsvm) (Linux or Windows Server 2016 or later)</span></span>

-   [<span data-ttu-id="95765-110">Service Fabric dağıtma</span><span class="sxs-lookup"><span data-stu-id="95765-110">Deploy to Service Fabric</span></span>](https://docs.microsoft.com/azure/service-fabric/service-fabric-tutorial-deploy-app-with-cicd-vsts)

-   [<span data-ttu-id="95765-111">Azure kapsayıcı hizmeti – Kubernetes dağıtma</span><span class="sxs-lookup"><span data-stu-id="95765-111">Deploy to Azure Container Service – Kubernetes</span></span>](https://docs.microsoft.com/vsts/build-release/apps/cd/azure/deploy-container-kubernetes)

<span data-ttu-id="95765-112">Ancak, aynı zamanda dağıtabilirsiniz [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) veya Team Services betik tabanlı görevleri kullanarak DC/OS.</span><span class="sxs-lookup"><span data-stu-id="95765-112">But you also can deploy to [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) or DC/OS by using Team Services script-based tasks.</span></span>

<span data-ttu-id="95765-113">Dağıtım çeviklik kolaylaştırmanın devam etmek için bir geliştirme ve CI/CD çözümleri seçimiyle kapsayıcı iş yükleri için mükemmel geliştirme için-test-için-Üretim dağıtımı karşılaştığında bu araçlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="95765-113">To continue facilitating deployment agility, these tools provide excellent dev-to-test-to-production deployment experiences for container workloads, with a choice of development and CI/CD solutions.</span></span>

<span data-ttu-id="95765-114">Şekil 4-12 Azure kapsayıcı hizmeti Kubernetes kümede dağıtır sürekli dağıtım ardışık gösterir.</span><span class="sxs-lookup"><span data-stu-id="95765-114">Figure 4-12 shows a continuous deployment pipeline that deploys to a Kubernetes cluster in Azure Container Service.</span></span>

![Visual Studio Team Services sürekli dağıtım ardışık, Kubernetes kümeye dağıtma](./media/image12.png)

> <span data-ttu-id="95765-116">**Şekil 4-12.**</span><span class="sxs-lookup"><span data-stu-id="95765-116">**Figure 4-12.**</span></span> <span data-ttu-id="95765-117">Visual Studio Team Services sürekli dağıtım ardışık, Kubernetes kümeye dağıtma</span><span class="sxs-lookup"><span data-stu-id="95765-117">Visual Studio Team Services continuous deployment pipeline, deploying to a Kubernetes cluster</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="95765-118">[Önceki](modernize-your-apps-with-monitoring-and-telemetry.md)
[sonraki](migrate-to-hybrid-cloud-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="95765-118">[Previous](modernize-your-apps-with-monitoring-and-telemetry.md)
[Next](migrate-to-hybrid-cloud-scenarios.md)</span></span>
