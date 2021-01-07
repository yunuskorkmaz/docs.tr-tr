---
title: Kapsayıcılar üzerinde bir .NET uygulaması ve bir Kubernetes kümesine dağıtım için Azure DevOps Services CI/CD işlem hatları oluşturma
description: Microsoft Platformu ve Araçları ile Kapsayıcı Docker Uygulaması Yaşam Döngüsü
ms.date: 01/06/2021
ms.openlocfilehash: ef994f132716547ee402237016ee71013528d779
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970492"
---
# <a name="create-cicd-pipelines-in-azure-devops-services-for-a-net-application-on-containers-and-deploying-to-a-kubernetes-cluster"></a><span data-ttu-id="f82cb-103">Kapsayıcılar üzerinde bir .NET uygulaması ve bir Kubernetes kümesine dağıtım için Azure DevOps Services CI/CD işlem hatları oluşturma</span><span class="sxs-lookup"><span data-stu-id="f82cb-103">Create CI/CD pipelines in Azure DevOps Services for a .NET application on Containers and deploying to a Kubernetes cluster</span></span>

<span data-ttu-id="f82cb-104">Şekil 5-12 ' de, kod yönetimi, kod derleme, Docker görüntüleri oluşturma, Docker görüntüleri bir Docker kayıt defterine gönderme ve son olarak Azure 'daki bir Kubernetes kümesine dağıtım gibi uçtan uca DevOps senaryosunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f82cb-104">In Figure 5-12 you can see the end-to-end DevOps scenario covering the code management, code compilation, Docker images build, Docker images push to a Docker registry and finally the deployment to a Kubernetes cluster in Azure.</span></span>

![İş akışı: geliştirme makinesinde başlatılır.](media/docker-workflow-ci-cd-aks.png)

<span data-ttu-id="f82cb-107">**Şekil 5-12**.</span><span class="sxs-lookup"><span data-stu-id="f82cb-107">**Figure 5-12**.</span></span> <span data-ttu-id="f82cb-108">Azure 'da Docker görüntüleri oluşturma ve bir Kubernetes kümesine dağıtma CI/CD senaryosu</span><span class="sxs-lookup"><span data-stu-id="f82cb-108">CI/CD scenario creating Docker images and deploying to a Kubernetes cluster in Azure</span></span>

<span data-ttu-id="f82cb-109">İki işlem hattı, derleme/CI ve yayın/CD 'nin Docker kayıt defteri (Docker Hub veya Azure Container Registry gibi) aracılığıyla bağlandığını vurgulamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="f82cb-109">It is important to highlight that the two pipelines, build/CI, and release/CD, are connected through the Docker Registry (such as Docker Hub or Azure Container Registry).</span></span> <span data-ttu-id="f82cb-110">Docker kayıt defteri, Docker olmadan geleneksel bir CI/CD işlemine kıyasla ana farklardan biridir.</span><span class="sxs-lookup"><span data-stu-id="f82cb-110">The Docker registry is one of the main differences compared to a traditional CI/CD process without Docker.</span></span>

<span data-ttu-id="f82cb-111">Şekil 5-13 ' de gösterildiği gibi, ilk aşama Build/CI ardışık düzeni olur.</span><span class="sxs-lookup"><span data-stu-id="f82cb-111">As shown in Figure 5-13, the first phase is the build/CI pipeline.</span></span> <span data-ttu-id="f82cb-112">Azure DevOps Services, kodu derlemek, Docker görüntülerini oluşturmak ve bunları Docker Hub veya Azure Container Registry gibi bir Docker kayıt defterine göndermek için derleme/CI işlem hatları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f82cb-112">In Azure DevOps Services you can create build/CI pipelines that will compile the code, create the Docker images, and push them to a Docker Registry like Docker Hub or Azure Container Registry.</span></span>

![Azure DevOps 'un tarayıcı görünümü, derleme işlemi görev tanımı.](media/build-ci-pipeline-azure-devops-push-to-docker-registry.png)

<span data-ttu-id="f82cb-114">**Şekil 5-13**.</span><span class="sxs-lookup"><span data-stu-id="f82cb-114">**Figure 5-13**.</span></span> <span data-ttu-id="f82cb-115">Azure DevOps 'daki derleme/CI işlem hattı Docker görüntülerini oluşturma ve görüntüleri bir Docker kayıt defterine iletme</span><span class="sxs-lookup"><span data-stu-id="f82cb-115">Build/CI pipeline in Azure DevOps building Docker images and pushing images to a Docker registry</span></span>

<span data-ttu-id="f82cb-116">İkinci aşama, bir dağıtım/yayın işlem hattı oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="f82cb-116">The second phase is to create a deployment/release pipeline.</span></span> <span data-ttu-id="f82cb-117">Azure DevOps Services, Şekil 5-14 ' de gösterildiği gibi, Azure DevOps Services için Kubernetes görevlerini kullanarak bir Kubernetes kümesini hedefleyen bir dağıtım işlem hattını kolayca oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f82cb-117">In Azure DevOps Services, you can easily create a deployment pipeline targeting a Kubernetes cluster by using the Kubernetes tasks for Azure DevOps Services, as shown in Figure 5-14.</span></span>

![Azure DevOps tarayıcı görünümü, Kubernetes görev tanımına dağıtın.](media/release-cd-pipeline-azure-devops-deploy-to-kubernetes.png)

<span data-ttu-id="f82cb-119">**Şekil 5-14**.</span><span class="sxs-lookup"><span data-stu-id="f82cb-119">**Figure 5-14**.</span></span> <span data-ttu-id="f82cb-120">Bir Kubernetes kümesine dağıtma Azure DevOps Services içindeki yayın/CD işlem hattı</span><span class="sxs-lookup"><span data-stu-id="f82cb-120">Release/CD pipeline in Azure DevOps Services deploying to a Kubernetes cluster</span></span>

> <span data-ttu-id="f82cb-121">[! İzlenecek yol] Kubernetes 'e Eshopmodernıtes dağıtma:</span><span class="sxs-lookup"><span data-stu-id="f82cb-121">[!Walkthrough] Deploying eShopModernized to Kubernetes:</span></span>
>
> <span data-ttu-id="f82cb-122">Kubernetes 'e dağıtan Azure DevOps CI/CD işlem hatları hakkında ayrıntılı bir anlatım için şu gönderiyi inceleyin: </span><span class="sxs-lookup"><span data-stu-id="f82cb-122">For a detailed walkthrough of Azure DevOps CI/CD pipelines deploying to Kubernetes, see this post: </span></span>\
><https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

>[!div class="step-by-step"]
><span data-ttu-id="f82cb-123">[Önceki](docker-application-outer-loop-devops-workflow.md) 
> [Sonraki](../run-manage-monitor-docker-environments/index.md)</span><span class="sxs-lookup"><span data-stu-id="f82cb-123">[Previous](docker-application-outer-loop-devops-workflow.md)
[Next](../run-manage-monitor-docker-environments/index.md)</span></span>
