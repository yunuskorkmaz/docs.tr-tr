---
title: Bulutta CI/CD işlem hatları ve DevOps araçları ile uygulama yaşam döngüsünü modernleştirme
description: Azure Bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirme | Uygulamanızın yaşam döngüsü ile CI/CD işlem hatları ve DevOps araçları bulutta modernleştirin
ms.date: 04/30/2018
ms.openlocfilehash: fb4bfab4a891e9c8a73867f18cb8249775f9b7b9
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833952"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a><span data-ttu-id="4d78d-103">Bulutta CI/CD işlem hatları ve DevOps araçları ile uygulama yaşam döngüsünü modernleştirme</span><span class="sxs-lookup"><span data-stu-id="4d78d-103">Modernize your app's lifecycle with CI/CD pipelines and DevOps tools in the cloud</span></span>

<span data-ttu-id="4d78d-104">Bugünkü işletmeler Market'te rekabetçi hale gelmesini hızlı bir hızda yenilik gerekir.</span><span class="sxs-lookup"><span data-stu-id="4d78d-104">Today’s businesses need to innovate at a rapid pace to be competitive in the marketplace.</span></span> <span data-ttu-id="4d78d-105">Yüksek kaliteli, modern uygulamalar oluşturabilmek için DevOps araçları ve yenilik sabit bu döngüsünü uygulamak için kritik olan işlemleri.</span><span class="sxs-lookup"><span data-stu-id="4d78d-105">Delivering high-quality, modern applications requires DevOps tools and processes that are critical to implement this constant cycle of innovation.</span></span> <span data-ttu-id="4d78d-106">Doğru DevOps araçlarıyla geliştiriciler sürekli dağıtımını kolaylaştırın ve daha hızlı sunun yenilikçi uygulamalar kullanıcıların alma.</span><span class="sxs-lookup"><span data-stu-id="4d78d-106">With the right DevOps tools, developers can streamline continuous deployment and get innovative applications into the hands of users more quickly.</span></span>

<span data-ttu-id="4d78d-107">Sürekli tümleştirme ve dağıtım yöntemleri de oluşturulmuş olsa da, özellikle çok kapsayıcılı uygulamaları ile çalışırken giriş kapsayıcıların yeni konuları tanıtır.</span><span class="sxs-lookup"><span data-stu-id="4d78d-107">Although continuous integration and deployment practices are well established, the introduction of containers introduces new considerations, particularly when you are working with multi-container applications.</span></span>

<span data-ttu-id="4d78d-108">Azure DevOps hizmetleriyle, sürekli tümleştirme ve çeşitli ortamlarda resmi Azure DevOps Hizmetleri dağıtım görevleri aracılığıyla çoklu kapsayıcı uygulamalarının dağıtımını destekler:</span><span class="sxs-lookup"><span data-stu-id="4d78d-108">Azure DevOps Services supports continuous integration and deployment of multi-container applications to a variety of environments through the official Azure DevOps Services deployment tasks:</span></span>

- [<span data-ttu-id="4d78d-109">Kapsayıcılar için bir Azure Web uygulamasına dağıtma</span><span class="sxs-lookup"><span data-stu-id="4d78d-109">Deploy to an Azure Web App for Containers</span></span>](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-docker-webapp?view=azure-devops)

- [<span data-ttu-id="4d78d-110">Azure Container Service – Kubernetes dağıtımı</span><span class="sxs-lookup"><span data-stu-id="4d78d-110">Deploy to Azure Container Service – Kubernetes</span></span>](https://docs.microsoft.com/azure/devops/build-release/apps/cd/azure/deploy-container-kubernetes)

<span data-ttu-id="4d78d-111">Ancak ayrıca dağıtabileceğiniz [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) veya betik tabanlı Azure DevOps Hizmetleri'nin görevlerini kullanarak DC/OS.</span><span class="sxs-lookup"><span data-stu-id="4d78d-111">But you also can deploy to [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) or DC/OS by using Azure DevOps Services script-based tasks.</span></span>

<span data-ttu-id="4d78d-112">Hızlı Dağıtım etkinleştirme devam etmek için bu araçlar, geliştirme ve CI/CD çözümleri ile kapsayıcı iş yükleri için mükemmel bir geliştirme için-test-geliştirmeden üretime kadar dağıtım deneyimleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="4d78d-112">To continue facilitating deployment agility, these tools provide excellent dev-to-test-to-production deployment experiences for container workloads, with a choice of development and CI/CD solutions.</span></span>

<span data-ttu-id="4d78d-113">Şekil 4-12 Azure Container Service'te bir Kubernetes kümesi dağıtır sürekli dağıtım işlem hattı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4d78d-113">Figure 4-12 shows a continuous deployment pipeline that deploys to a Kubernetes cluster in Azure Container Service.</span></span>

![Azure DevOps Hizmetleri sürekli dağıtım ardışık, bir Kubernetes kümesine dağıtma](./media/image12.png)

> <span data-ttu-id="4d78d-115">**Şekil 4-12.**</span><span class="sxs-lookup"><span data-stu-id="4d78d-115">**Figure 4-12.**</span></span> <span data-ttu-id="4d78d-116">Azure DevOps Hizmetleri sürekli dağıtım ardışık, bir Kubernetes kümesine dağıtma</span><span class="sxs-lookup"><span data-stu-id="4d78d-116">Azure DevOps Services continuous deployment pipeline, deploying to a Kubernetes cluster</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="4d78d-117">[Önceki](modernize-your-apps-with-monitoring-and-telemetry.md)
>[İleri](migrate-to-hybrid-cloud-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="4d78d-117">[Previous](modernize-your-apps-with-monitoring-and-telemetry.md)
[Next](migrate-to-hybrid-cloud-scenarios.md)</span></span>
