---
title: Yüksek ölçeklenebilirlik ve kullanılabilirlik için mikro hizmetleri ve çok kapsayıcılı uygulamaları yönetme
description: Azure Kubernetes Hizmetini kullanarak bir uygulamayı nasıl dağıtacaklarını öğrenin.
ms.date: 02/15/2019
ms.openlocfilehash: 0aa2f83fbf8f9a8815d65730002943cca748643d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "71182364"
---
# <a name="deploy-to-azure-kubernetes-service-aks"></a><span data-ttu-id="8e032-103">Azure Kubernetes Service’e (AKS) Dağıtma</span><span class="sxs-lookup"><span data-stu-id="8e032-103">Deploy to Azure Kubernetes Service (AKS)</span></span>

<span data-ttu-id="8e032-104">Tercih ettiğiniz istemci işletim sistemini kullanarak AKS ile etkileşimkurabilirsiniz, burada Nasıl Microsoft Windows ve Windows Ubuntu Linux gömülü bir sürümünü, Bash komutları kullanarak bunu göstermek.</span><span class="sxs-lookup"><span data-stu-id="8e032-104">You can interact with AKS using your preferred client operating system, here we show how to do it with Microsoft Windows and an embedded version of Ubuntu Linux in Windows, using Bash commands.</span></span>

<span data-ttu-id="8e032-105">AKS kullanmadan önce sahip olması önkoşullar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="8e032-105">Prerequisites to have before using AKS are:</span></span>

- <span data-ttu-id="8e032-106">Linux veya Mac geliştirme makinesi</span><span class="sxs-lookup"><span data-stu-id="8e032-106">Linux or Mac development machine</span></span>
- <span data-ttu-id="8e032-107">Windows geliştirme makinesi</span><span class="sxs-lookup"><span data-stu-id="8e032-107">Windows development machine</span></span>
  - <span data-ttu-id="8e032-108">Windows'da Geliştirici Modu etkin</span><span class="sxs-lookup"><span data-stu-id="8e032-108">Developer Mode enabled on Windows</span></span>
  - <span data-ttu-id="8e032-109">Linux için Windows Alt Sistemi</span><span class="sxs-lookup"><span data-stu-id="8e032-109">Windows Subsystem for Linux</span></span>
- <span data-ttu-id="8e032-110">[Windows, Mac veya Linux'ta](https://docs.microsoft.com/cli/azure/install-azure-cli) yüklü Azure-CLI</span><span class="sxs-lookup"><span data-stu-id="8e032-110">Azure-CLI installed on [Windows, Mac or Linux](https://docs.microsoft.com/cli/azure/install-azure-cli)</span></span>

> [!NOTE]
> <span data-ttu-id="8e032-111">Hakkında tam bilgi bulmak için:</span><span class="sxs-lookup"><span data-stu-id="8e032-111">To find complete information about:</span></span>
>
> <span data-ttu-id="8e032-112">Azure-CLI:<https://docs.microsoft.com/cli/azure/index></span><span class="sxs-lookup"><span data-stu-id="8e032-112">Azure-CLI: <https://docs.microsoft.com/cli/azure/index></span></span>
>
> <span data-ttu-id="8e032-113">Linux için Windows Alt Sistemi:<https://docs.microsoft.com/windows/wsl/about></span><span class="sxs-lookup"><span data-stu-id="8e032-113">Windows Subsystem for Linux: <https://docs.microsoft.com/windows/wsl/about></span></span>

## <a name="create-the-aks-environment-in-azure"></a><span data-ttu-id="8e032-114">Azure'da AKS ortamını oluşturma</span><span class="sxs-lookup"><span data-stu-id="8e032-114">Create the AKS environment in Azure</span></span>

<span data-ttu-id="8e032-115">AKS Ortamını oluşturmanın birkaç yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="8e032-115">There are several ways to create the AKS Environment.</span></span> <span data-ttu-id="8e032-116">Azure-CLI komutlarını kullanarak veya Azure portalını kullanarak yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="8e032-116">It can be done by using Azure-CLI commands or by using the Azure portal.</span></span>

<span data-ttu-id="8e032-117">Burada, sonuçları gözden geçirmek için küme yi ve Azure portalını oluşturmak için Azure-CLI'yi kullanarak bazı örnekleri keşfedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8e032-117">Here you can explore some examples using the Azure-CLI to create the cluster and the Azure portal to review the results.</span></span> <span data-ttu-id="8e032-118">Ayrıca geliştirme makinenizde Kubectl ve Docker olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8e032-118">You also need to have Kubectl and Docker in your development machine.</span></span>  

## <a name="create-the-aks-cluster"></a><span data-ttu-id="8e032-119">AKS kümesini oluşturma</span><span class="sxs-lookup"><span data-stu-id="8e032-119">Create the AKS cluster</span></span>

<span data-ttu-id="8e032-120">Bu komutu kullanarak AKS kümesini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="8e032-120">Create the AKS cluster using this command:</span></span>

```console
az aks create --resource-group MSSampleResourceGroup --name MSSampleClusterK801 --agent-count 1 --generate-ssh-keys --location westus2
```

<span data-ttu-id="8e032-121">Oluşturma işi bittikten sonra Azure portalında oluşturulan AKS'yi görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8e032-121">After the creation job finishes, you can see the AKS created in the Azure portal:</span></span>

<span data-ttu-id="8e032-122">Kaynak grubu:</span><span class="sxs-lookup"><span data-stu-id="8e032-122">The resource group:</span></span>

![Azure AKS kaynak grubunun tarayıcı görünümü.](media/aks-resource-group-view.png)

<span data-ttu-id="8e032-124">**Şekil 4-17**.</span><span class="sxs-lookup"><span data-stu-id="8e032-124">**Figure 4-17**.</span></span> <span data-ttu-id="8e032-125">Azure'dan AKS Kaynak Grubu görünümü.</span><span class="sxs-lookup"><span data-stu-id="8e032-125">AKS Resource Group view from Azure.</span></span>

<span data-ttu-id="8e032-126">AKS kümesi:</span><span class="sxs-lookup"><span data-stu-id="8e032-126">The AKS cluster:</span></span>

![AKS kaynak grubunun tarayıcı görünümü.](media/aks-cluster-view.png)

<span data-ttu-id="8e032-128">**Şekil 4-18**.</span><span class="sxs-lookup"><span data-stu-id="8e032-128">**Figure 4-18**.</span></span> <span data-ttu-id="8e032-129">Azure'dan AKS görünümü.</span><span class="sxs-lookup"><span data-stu-id="8e032-129">AKS view from Azure.</span></span>

<span data-ttu-id="8e032-130">Ayrıca kullanarak `Azure-CLI` oluşturulan düğümü görüntüleyebilir `Kubectl`ve.</span><span class="sxs-lookup"><span data-stu-id="8e032-130">You can also view the node created using `Azure-CLI` and `Kubectl`.</span></span>

<span data-ttu-id="8e032-131">İlk olarak, kimlik bilgilerini alma:</span><span class="sxs-lookup"><span data-stu-id="8e032-131">First, getting the credentials:</span></span>

```console
az aks get-credentials --resource-group MSSampleK8ClusterRG --name MSSampleK8Cluster
```

![Yukarıdaki komuttan konsol çıkışı: Birleştirilmiş "MsSampleK8Cluster geçerli bağlam olarak /root/.kube/config.](media/get-credentials-command-result.png)

<span data-ttu-id="8e032-133">**Şekil 4-19**.</span><span class="sxs-lookup"><span data-stu-id="8e032-133">**Figure 4-19**.</span></span> <span data-ttu-id="8e032-134">`aks get-credentials`komut sonucu.</span><span class="sxs-lookup"><span data-stu-id="8e032-134">`aks get-credentials` command result.</span></span>

<span data-ttu-id="8e032-135">Ve sonra, Kubectl gelen düğümleri alma:</span><span class="sxs-lookup"><span data-stu-id="8e032-135">And then, getting nodes from Kubectl:</span></span>

```console
kubectl get nodes
```

![Yukarıdaki komuttan konsol çıkışı: Durum, yaş (zaman çalışan) ve sürüm ile düğümlistesi](media/kubectl-get-nodes-command-result.png)

<span data-ttu-id="8e032-137">**Şekil 4-20**.</span><span class="sxs-lookup"><span data-stu-id="8e032-137">**Figure 4-20**.</span></span> <span data-ttu-id="8e032-138">`kubectl get nodes`komut sonucu.</span><span class="sxs-lookup"><span data-stu-id="8e032-138">`kubectl get nodes` command result.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="8e032-139">[Önceki](orchestrate-high-scalability-availability.md)
>[Sonraki](docker-apps-development-environment.md)</span><span class="sxs-lookup"><span data-stu-id="8e032-139">[Previous](orchestrate-high-scalability-availability.md)
[Next](docker-apps-development-environment.md)</span></span>
