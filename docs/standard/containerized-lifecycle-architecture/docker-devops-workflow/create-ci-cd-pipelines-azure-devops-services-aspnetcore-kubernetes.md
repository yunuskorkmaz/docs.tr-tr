---
title: Bir Docker uygulaması için dış döngü DevOps iş akışındaki adımlar
description: Microsoft Platformu ve Araçları ile Kapsayıcı Docker Uygulaması Yaşam Döngüsü
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 2cd769ce9013a8521c53f36b44ea260ceccd48b7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61795388"
---
# <a name="creating-cicd-pipelines-in-azure-devops-services-for-a-net-core-20-application-on-containers-and-deploying-to-a-kubernetes-cluster"></a><span data-ttu-id="3592d-103">Azure DevOps Services içinde Kapsayıcılar üzerindeki bir .NET Core 2.0 uygulaması için CI/CD işlem hatları oluşturma ve bir Kubernetes kümesine dağıtma</span><span class="sxs-lookup"><span data-stu-id="3592d-103">Creating CI/CD pipelines in Azure DevOps Services for a .NET Core 2.0 application on Containers and deploying to a Kubernetes cluster</span></span>

<span data-ttu-id="3592d-104">Şekil 5-12'de, kod yönetimi, kod derleme kapsayan uçtan uca DevOps senaryo görebilirsiniz, Docker görüntülerinizi oluşturmak, bir Docker kayıt defteri ve son olarak dağıtım için azure'da bir Kubernetes kümesi için Docker görüntüleri gönderin.</span><span class="sxs-lookup"><span data-stu-id="3592d-104">In Figure 5-12 you can see the end-to-end DevOps scenario covering the code management, code compilation, Docker images build, Docker images push to a Docker registry and finally the deployment to a Kubernetes cluster in Azure.</span></span>

![İş akışı: Geliştirme makinesinde başlatılır.](media/docker-workflow-ci-cd-aks.png)

<span data-ttu-id="3592d-107">**Şekil 5-12**.</span><span class="sxs-lookup"><span data-stu-id="3592d-107">**Figure 5-12**.</span></span> <span data-ttu-id="3592d-108">CI/CD senaryo Docker görüntülerinizi oluşturmak ve azure'da bir Kubernetes kümesi dağıtma</span><span class="sxs-lookup"><span data-stu-id="3592d-108">CI/CD scenario creating Docker images and deploying to a Kubernetes cluster in Azure</span></span>

<span data-ttu-id="3592d-109">İki işlem hattı, derleme/CI ve yayın/CD, Docker kayıt defteri (örneğin, Docker Hub veya Azure Container Registry) üzerinden bağlı vurgulamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="3592d-109">It is important to highlight that the two pipelines, build/CI, and release/CD, are connected through the Docker Registry (such as Docker Hub or Azure Container Registry).</span></span> <span data-ttu-id="3592d-110">Docker kayıt defteri, Docker olmadan geleneksel bir CI/CD işlem karşılaştırıldığında temel farklar biridir.</span><span class="sxs-lookup"><span data-stu-id="3592d-110">The Docker registry is one of the main differences compared to a traditional CI/CD process without Docker.</span></span>

<span data-ttu-id="3592d-111">Şekil 5-13'te gösterildiği gibi ilk aşaması derleme/CI işlem hattı ' dir.</span><span class="sxs-lookup"><span data-stu-id="3592d-111">As shown in Figure 5-13, the first phase is the build/CI pipeline.</span></span> <span data-ttu-id="3592d-112">Azure DevOps Hizmetleri'nde, kodu derlemek, Docker görüntüleri oluşturun ve bunları gibi Docker Hub veya Azure Container Registry'den bir Docker kayıt defterine itme derleme/CD işlem hatları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3592d-112">In Azure DevOps Services you can create build/CD pipelines that will compile the code, create the Docker images, and push them to a Docker Registry like Docker Hub or Azure Container Registry.</span></span>

![Azure DevOps, yapı işlemi Görev tanımı tarayıcı görünümü.](media/build-ci-pipeline-azure-devops-push-to-docker-registry.png)

<span data-ttu-id="3592d-114">**Şekil 5-13**.</span><span class="sxs-lookup"><span data-stu-id="3592d-114">**Figure 5-13**.</span></span> <span data-ttu-id="3592d-115">Azure Docker görüntülerinizi oluşturmak ve bir Docker kayıt defterine görüntü gönderme DevOps derleme/CI işlem hattında</span><span class="sxs-lookup"><span data-stu-id="3592d-115">Build/CI pipeline in Azure DevOps building Docker images and pushing images to a Docker registry</span></span>

<span data-ttu-id="3592d-116">İkinci aşama dağıtımı/yayın işlem hattı oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="3592d-116">The second phase is to create a deployment/release pipeline.</span></span> <span data-ttu-id="3592d-117">Azure DevOps Hizmetleri'nde bir Kubernetes kümesi için Azure DevOps Services, Kubernetes görevlerini kullanarak Şekil 5-14'te gösterildiği gibi hedefleyen bir dağıtım işlem hattı kolayca oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3592d-117">In Azure DevOps Services, you can easily create a deployment pipeline targeting a Kubernetes cluster by using the Kubernetes tasks for Azure DevOps Services, as shown in Figure 5-14.</span></span>

![Azure DevOps, tarayıcı görünümünü Kubernetes görev tanımına dağıtın.](media/release-cd-pipeline-azure-devops-deploy-to-kubernetes.png)

<span data-ttu-id="3592d-119">**Şekil 5-14**.</span><span class="sxs-lookup"><span data-stu-id="3592d-119">**Figure 5-14**.</span></span> <span data-ttu-id="3592d-120">Azure DevOps Services Kubernetes kümesine dağıtmak, yayın/CD işlem hattı</span><span class="sxs-lookup"><span data-stu-id="3592d-120">Release/CD pipeline in Azure DevOps Services deploying to a Kubernetes cluster</span></span>

> [! İzlenecek yol]<span data-ttu-id="3592d-121"> eShopModernized Kubernetes dağıtımı:</span><span class="sxs-lookup"><span data-stu-id="3592d-121"> Deploying eShopModernized to Kubernetes:</span></span>
>
> <span data-ttu-id="3592d-122">Azure DevOps CI/CD işlem hatları ilişkin ayrıntılı bir kılavuz için Kubernetes dağıtımı yazıya bakın: \\</span><span class="sxs-lookup"><span data-stu-id="3592d-122">For a detailed walkthrough of Azure DevOps CI/CD pipelines deploying to Kubernetes, see this post: \\</span></span>
><https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

>[!div class="step-by-step"]
><span data-ttu-id="3592d-123">[Önceki](docker-application-outer-loop-devops-workflow.md)
>[İleri](../run-manage-monitor-docker-environments/index.md)</span><span class="sxs-lookup"><span data-stu-id="3592d-123">[Previous](docker-application-outer-loop-devops-workflow.md)
[Next](../run-manage-monitor-docker-environments/index.md)</span></span>
