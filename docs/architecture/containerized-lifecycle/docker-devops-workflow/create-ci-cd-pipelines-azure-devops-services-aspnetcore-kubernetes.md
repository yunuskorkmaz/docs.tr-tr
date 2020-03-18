---
title: Bir Docker uygulaması için dış döngü DevOps iş akışındaki adımlar
description: Microsoft Platformu ve Araçları ile Kapsayıcı Docker Uygulaması Yaşam Döngüsü
ms.date: 02/15/2019
ms.openlocfilehash: 9fdc5acfd375e4f2266859f061ef1c854286b914
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70295780"
---
# <a name="creating-cicd-pipelines-in-azure-devops-services-for-a-net-core-20-application-on-containers-and-deploying-to-a-kubernetes-cluster"></a><span data-ttu-id="9c949-103">Azure DevOps Services içinde Kapsayıcılar üzerindeki bir .NET Core 2.0 uygulaması için CI/CD işlem hatları oluşturma ve bir Kubernetes kümesine dağıtma</span><span class="sxs-lookup"><span data-stu-id="9c949-103">Creating CI/CD pipelines in Azure DevOps Services for a .NET Core 2.0 application on Containers and deploying to a Kubernetes cluster</span></span>

<span data-ttu-id="9c949-104">Şekil 5-12'de kod yönetimi, kod derleme, Docker görüntüleri oluşturma, Docker görüntüleri ve son olarak Azure'daki bir Kubernetes kümesine dağıtımı kapsayan uçdan uca DevOps senaryosunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c949-104">In Figure 5-12 you can see the end-to-end DevOps scenario covering the code management, code compilation, Docker images build, Docker images push to a Docker registry and finally the deployment to a Kubernetes cluster in Azure.</span></span>

![İş akışı: Geliştirme makinesinde başlar.](media/docker-workflow-ci-cd-aks.png)

<span data-ttu-id="9c949-107">**Şekil 5-12**.</span><span class="sxs-lookup"><span data-stu-id="9c949-107">**Figure 5-12**.</span></span> <span data-ttu-id="9c949-108">Docker görüntüleri oluşturma ve Azure'daki bir Kubernetes kümesine dağıtma CI/CD senaryosu</span><span class="sxs-lookup"><span data-stu-id="9c949-108">CI/CD scenario creating Docker images and deploying to a Kubernetes cluster in Azure</span></span>

<span data-ttu-id="9c949-109">Yapı/CD ve sürüm/CD olmak üzere iki boru hattının Docker Registry (Docker Hub veya Azure Konteyner Kayıt Defteri gibi) aracılığıyla bağlandığı vurgulanması önemlidir.</span><span class="sxs-lookup"><span data-stu-id="9c949-109">It is important to highlight that the two pipelines, build/CI, and release/CD, are connected through the Docker Registry (such as Docker Hub or Azure Container Registry).</span></span> <span data-ttu-id="9c949-110">Docker kayıt defteri, Docker olmadan geleneksel CI/CD sürecine kıyasla en önemli farklardan biridir.</span><span class="sxs-lookup"><span data-stu-id="9c949-110">The Docker registry is one of the main differences compared to a traditional CI/CD process without Docker.</span></span>

<span data-ttu-id="9c949-111">Şekil 5-13'te gösterildiği gibi, ilk aşama yapı/CI boru hattıdır.</span><span class="sxs-lookup"><span data-stu-id="9c949-111">As shown in Figure 5-13, the first phase is the build/CI pipeline.</span></span> <span data-ttu-id="9c949-112">Azure DevOps Hizmetleri'nde kodu derleyecek, Docker görüntülerini oluşturacak ve docker hub veya Azure Konteyner Kayıt Defteri gibi docker registry'ye itecek yapı/CI ardışık hatları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c949-112">In Azure DevOps Services you can create build/CI pipelines that will compile the code, create the Docker images, and push them to a Docker Registry like Docker Hub or Azure Container Registry.</span></span>

![Azure DevOps tarayıcı görünümü, Oluşturma işlemi görev tanımı.](media/build-ci-pipeline-azure-devops-push-to-docker-registry.png)

<span data-ttu-id="9c949-114">**Şekil 5-13**.</span><span class="sxs-lookup"><span data-stu-id="9c949-114">**Figure 5-13**.</span></span> <span data-ttu-id="9c949-115">Azure DevOps'lerde Docker görüntüleri oluşturma ve görüntüleri Docker kayıt defterine itme de geliştirme/CI ardışık</span><span class="sxs-lookup"><span data-stu-id="9c949-115">Build/CI pipeline in Azure DevOps building Docker images and pushing images to a Docker registry</span></span>

<span data-ttu-id="9c949-116">İkinci aşama bir dağıtım/sürüm ardışık hattı oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="9c949-116">The second phase is to create a deployment/release pipeline.</span></span> <span data-ttu-id="9c949-117">Azure DevOps Hizmetlerinde, Şekil 5-14'te gösterildiği gibi Azure DevOps Hizmetleri için Kubernetes görevlerini kullanarak bir Kubernetes kümesini hedefleyen bir dağıtım ardışık hattı kolayca oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c949-117">In Azure DevOps Services, you can easily create a deployment pipeline targeting a Kubernetes cluster by using the Kubernetes tasks for Azure DevOps Services, as shown in Figure 5-14.</span></span>

![Azure DevOps tarayıcı görünümü, Kubernetes görev tanımına dağıtın.](media/release-cd-pipeline-azure-devops-deploy-to-kubernetes.png)

<span data-ttu-id="9c949-119">**Şekil 5-14**.</span><span class="sxs-lookup"><span data-stu-id="9c949-119">**Figure 5-14**.</span></span> <span data-ttu-id="9c949-120">Bir Kubernetes kümesine dağıtılan Azure DevOps Hizmetleri'nde sürüm/CD ardışık</span><span class="sxs-lookup"><span data-stu-id="9c949-120">Release/CD pipeline in Azure DevOps Services deploying to a Kubernetes cluster</span></span>

> [! Walkthrough]<span data-ttu-id="9c949-121"> Kubernetes için eShopModernized dağıtma:</span><span class="sxs-lookup"><span data-stu-id="9c949-121"> Deploying eShopModernized to Kubernetes:</span></span>
>
> <span data-ttu-id="9c949-122">Azure DevOps CI/CD ardışık birimlerinin Kubernetes'e dağıtışlarını ayrıntılı bir şekilde gözden geçirmek için aşağıdaki yazıya bakın: </span><span class="sxs-lookup"><span data-stu-id="9c949-122">For a detailed walkthrough of Azure DevOps CI/CD pipelines deploying to Kubernetes, see this post: </span></span>\
><https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

>[!div class="step-by-step"]
><span data-ttu-id="9c949-123">[Önceki](docker-application-outer-loop-devops-workflow.md)
>[Sonraki](../run-manage-monitor-docker-environments/index.md)</span><span class="sxs-lookup"><span data-stu-id="9c949-123">[Previous](docker-application-outer-loop-devops-workflow.md)
[Next](../run-manage-monitor-docker-environments/index.md)</span></span>
