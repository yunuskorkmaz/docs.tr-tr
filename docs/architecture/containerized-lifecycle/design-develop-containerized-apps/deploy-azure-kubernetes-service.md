---
title: Yüksek ölçeklenebilirlik ve kullanılabilirlik için mikro hizmetleri ve çok kapsayıcılı uygulamaları yönetme
description: Azure Kubernetes hizmetini kullanarak bir uygulamayı dağıtmayı öğrenin.
ms.date: 08/06/2020
ms.openlocfilehash: ba9887c0a4837c16a60ebeb006416c0fa8c105e0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91163602"
---
# <a name="deploy-to-azure-kubernetes-service-aks"></a><span data-ttu-id="747fb-103">Azure Kubernetes Service’e (AKS) Dağıtma</span><span class="sxs-lookup"><span data-stu-id="747fb-103">Deploy to Azure Kubernetes Service (AKS)</span></span>

<span data-ttu-id="747fb-104">Azure komut satırı arabirimi (Azure CLı) yüklü olan tercih ettiğiniz istemci işletim sistemini (Windows, macOS veya Linux) kullanarak AKS ile etkileşim kurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="747fb-104">You can interact with AKS using your preferred client operating system (Windows, macOS, or Linux) with Azure command-line interface(Azure CLI) installed.</span></span> <span data-ttu-id="747fb-105">Daha fazla ayrıntı için, kullanılabilir ortamlar için [Azure CLI belgelerine](/cli/azure/?view=azure-cli-latest) ve [yükleme kılavuzuna](/cli/azure/install-azure-cli?view=azure-cli-latest) bakın.</span><span class="sxs-lookup"><span data-stu-id="747fb-105">For more details, refer [Azure CLI documentation](/cli/azure/?view=azure-cli-latest) and [Installation guide](/cli/azure/install-azure-cli?view=azure-cli-latest) for the available environments.</span></span>

## <a name="create-the-aks-environment-in-azure"></a><span data-ttu-id="747fb-106">Azure 'da AKS ortamını oluşturma</span><span class="sxs-lookup"><span data-stu-id="747fb-106">Create the AKS environment in Azure</span></span>

<span data-ttu-id="747fb-107">AKS ortamını oluşturmanın birkaç yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="747fb-107">There are several ways to create the AKS Environment.</span></span> <span data-ttu-id="747fb-108">Azure CLı komutları kullanılarak veya Azure portal kullanılarak yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="747fb-108">It can be done by using Azure CLI commands or by using the Azure portal.</span></span>

<span data-ttu-id="747fb-109">Burada, kümeyi oluşturmak için Azure CLı kullanarak bazı örnekleri keşfedebilirsiniz ve sonuçları gözden geçirmek için Azure portal.</span><span class="sxs-lookup"><span data-stu-id="747fb-109">Here you can explore some examples using the Azure CLI to create the cluster and the Azure portal to review the results.</span></span> <span data-ttu-id="747fb-110">Geliştirme makinenizde Kubectl ve Docker de sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="747fb-110">You also need to have Kubectl and Docker in your development machine.</span></span>

## <a name="create-the-aks-cluster"></a><span data-ttu-id="747fb-111">AKS kümesini oluşturma</span><span class="sxs-lookup"><span data-stu-id="747fb-111">Create the AKS cluster</span></span>

<span data-ttu-id="747fb-112">Bu komutu kullanarak AKS kümesini oluşturun (kaynak grubu mevcut olmalıdır):</span><span class="sxs-lookup"><span data-stu-id="747fb-112">Create the AKS cluster using this command (the resource group must exist):</span></span>

```console
az aks create --resource-group explore-docker-aks-rg --name explore-docker-aks --node-vm-size Standard_B2s --node-count 1 --generate-ssh-keys --location westeurope
```

> [!NOTE]
> <span data-ttu-id="747fb-113">`--node-vm-size`Ve `--node-count` parametre değerleri bir örnek/dev uygulaması için yeterince iyidir.</span><span class="sxs-lookup"><span data-stu-id="747fb-113">The `--node-vm-size` and `--node-count` parameter values are good enough for a sample/dev application.</span></span>

<span data-ttu-id="747fb-114">Oluşturma işi tamamlandıktan sonra aşağıdakileri görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="747fb-114">After the creation job finishes, you can see:</span></span>

- <span data-ttu-id="747fb-115">İlk kaynak grubunda oluşturulan AKS kümesi</span><span class="sxs-lookup"><span data-stu-id="747fb-115">The AKS cluster created in the initial resource group</span></span>
- <span data-ttu-id="747fb-116">Aşağıdaki görüntülerde gösterildiği gibi, AKS kümesiyle ilgili kaynakları içeren yeni, ilişkili bir kaynak grubu.</span><span class="sxs-lookup"><span data-stu-id="747fb-116">A new, related resource group, containing the resources related to the AKS cluster, as show in the following images.</span></span>

<span data-ttu-id="747fb-117">AKS kümesi ile ilk kaynak grubu:</span><span class="sxs-lookup"><span data-stu-id="747fb-117">The initial resource group, with the AKS cluster:</span></span>

![AKS kaynak grubunun tarayıcı görünümü.](media/deploy-azure-kubernetes-service/aks-cluster-view.png)

<span data-ttu-id="747fb-119">**Şekil 4-17**.</span><span class="sxs-lookup"><span data-stu-id="747fb-119">**Figure 4-17**.</span></span> <span data-ttu-id="747fb-120">Azure 'dan AKS kaynak grubu görünümü.</span><span class="sxs-lookup"><span data-stu-id="747fb-120">AKS Resource Group view from Azure.</span></span>

<span data-ttu-id="747fb-121">AKS kümesi kaynak grubu:</span><span class="sxs-lookup"><span data-stu-id="747fb-121">The AKS cluster resource group:</span></span>

![Azure AKS kaynak grubunun tarayıcı görünümü.](media/deploy-azure-kubernetes-service/aks-resource-group-view.png)

<span data-ttu-id="747fb-123">**Şekil 4-18**.</span><span class="sxs-lookup"><span data-stu-id="747fb-123">**Figure 4-18**.</span></span> <span data-ttu-id="747fb-124">Azure 'dan AKS görünümü.</span><span class="sxs-lookup"><span data-stu-id="747fb-124">AKS view from Azure.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="747fb-125">Genel olarak, AKS kümesi kaynak grubundaki kaynakları değiştirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="747fb-125">In general, you shouldn't need to modify the resources in the AKS cluster resource group.</span></span> <span data-ttu-id="747fb-126">Örneğin, AKS kümesini sildiğinizde kaynak grubu silinir.</span><span class="sxs-lookup"><span data-stu-id="747fb-126">For example, the resource group is deleted when you delete the AKS cluster.</span></span>

<span data-ttu-id="747fb-127">Ve kullanılarak oluşturulan düğümü de görüntüleyebilirsiniz `Azure CLI` `Kubectl` .</span><span class="sxs-lookup"><span data-stu-id="747fb-127">You can also view the node created using `Azure CLI` and `Kubectl`.</span></span>

<span data-ttu-id="747fb-128">İlk olarak, kimlik bilgileri alınıyor:</span><span class="sxs-lookup"><span data-stu-id="747fb-128">First, getting the credentials:</span></span>

```console
az aks get-credentials --resource-group explore-docker-aks-rg --name explore-docker-aks
```

![Yukarıdaki komuttan konsol çıktısı: "keşfet-Docker-aks" i/Home/MIGUEL/.exe içindeki geçerli bağlam olarak birleştirildi.](media/deploy-azure-kubernetes-service/get-credentials-command-result.png)

<span data-ttu-id="747fb-130">**Şekil 4-19**.</span><span class="sxs-lookup"><span data-stu-id="747fb-130">**Figure 4-19**.</span></span> <span data-ttu-id="747fb-131">`aks get-credentials` komut sonucu.</span><span class="sxs-lookup"><span data-stu-id="747fb-131">`aks get-credentials` command result.</span></span>

<span data-ttu-id="747fb-132">Ardından, Kubectl 'den düğüm alma:</span><span class="sxs-lookup"><span data-stu-id="747fb-132">And then, getting nodes from Kubectl:</span></span>

```console
kubectl get nodes
```

![Yukarıdaki komuttan konsol çıktısı: durum, Yaş (çalıştırma süresi) ve sürüm içeren düğümlerin listesi](media/deploy-azure-kubernetes-service/kubectl-get-nodes-command-result.png)

<span data-ttu-id="747fb-134">**Şekil 4-20**.</span><span class="sxs-lookup"><span data-stu-id="747fb-134">**Figure 4-20**.</span></span> <span data-ttu-id="747fb-135">`kubectl get nodes` komut sonucu.</span><span class="sxs-lookup"><span data-stu-id="747fb-135">`kubectl get nodes` command result.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="747fb-136">[Önceki](orchestrate-high-scalability-availability.md) 
>  [Sonraki](docker-apps-development-environment.md)</span><span class="sxs-lookup"><span data-stu-id="747fb-136">[Previous](orchestrate-high-scalability-availability.md)
[Next](docker-apps-development-environment.md)</span></span>
