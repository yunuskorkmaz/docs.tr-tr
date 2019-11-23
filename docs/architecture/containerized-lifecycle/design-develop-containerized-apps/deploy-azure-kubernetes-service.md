---
title: Yüksek ölçeklenebilirlik ve kullanılabilirlik için mikro hizmetleri ve çok kapsayıcılı uygulamaları yönetme
description: Azure Kubernetes hizmetini kullanarak bir uygulamayı dağıtmayı öğrenin.
ms.date: 02/15/2019
ms.openlocfilehash: 0aa2f83fbf8f9a8815d65730002943cca748643d
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182364"
---
# <a name="deploy-to-azure-kubernetes-service-aks"></a><span data-ttu-id="d2dfb-103">Azure Kubernetes Service’e (AKS) Dağıtma</span><span class="sxs-lookup"><span data-stu-id="d2dfb-103">Deploy to Azure Kubernetes Service (AKS)</span></span>

<span data-ttu-id="d2dfb-104">Tercih ettiğiniz istemci işletim sistemini kullanarak AKS ile etkileşim kurabilirsiniz. burada, Windows 'da Bash komutlarını kullanarak Microsoft Windows ve Ubuntu Linux Embedded sürümü ile nasıl yapılacağını göstereceğiz.</span><span class="sxs-lookup"><span data-stu-id="d2dfb-104">You can interact with AKS using your preferred client operating system, here we show how to do it with Microsoft Windows and an embedded version of Ubuntu Linux in Windows, using Bash commands.</span></span>

<span data-ttu-id="d2dfb-105">AKS kullanılmadan önce sahip olmanın önkoşulları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d2dfb-105">Prerequisites to have before using AKS are:</span></span>

- <span data-ttu-id="d2dfb-106">Linux veya Mac geliştirme makinesi</span><span class="sxs-lookup"><span data-stu-id="d2dfb-106">Linux or Mac development machine</span></span>
- <span data-ttu-id="d2dfb-107">Windows geliştirme makinesi</span><span class="sxs-lookup"><span data-stu-id="d2dfb-107">Windows development machine</span></span>
  - <span data-ttu-id="d2dfb-108">Windows üzerinde geliştirici modu etkin</span><span class="sxs-lookup"><span data-stu-id="d2dfb-108">Developer Mode enabled on Windows</span></span>
  - <span data-ttu-id="d2dfb-109">Linux için Windows alt sistemi</span><span class="sxs-lookup"><span data-stu-id="d2dfb-109">Windows Subsystem for Linux</span></span>
- <span data-ttu-id="d2dfb-110">[Windows, Mac veya Linux](https://docs.microsoft.com/cli/azure/install-azure-cli) 'ta yüklü Azure-CLI</span><span class="sxs-lookup"><span data-stu-id="d2dfb-110">Azure-CLI installed on [Windows, Mac or Linux](https://docs.microsoft.com/cli/azure/install-azure-cli)</span></span>

> [!NOTE]
> <span data-ttu-id="d2dfb-111">Hakkında ayrıntılı bilgi edinmek için:</span><span class="sxs-lookup"><span data-stu-id="d2dfb-111">To find complete information about:</span></span>
>
> <span data-ttu-id="d2dfb-112">Azure-CLı: <https://docs.microsoft.com/cli/azure/index></span><span class="sxs-lookup"><span data-stu-id="d2dfb-112">Azure-CLI: <https://docs.microsoft.com/cli/azure/index></span></span>
>
> <span data-ttu-id="d2dfb-113">Linux için Windows alt sistemi: <https://docs.microsoft.com/windows/wsl/about></span><span class="sxs-lookup"><span data-stu-id="d2dfb-113">Windows Subsystem for Linux: <https://docs.microsoft.com/windows/wsl/about></span></span>

## <a name="create-the-aks-environment-in-azure"></a><span data-ttu-id="d2dfb-114">Azure 'da AKS ortamını oluşturma</span><span class="sxs-lookup"><span data-stu-id="d2dfb-114">Create the AKS environment in Azure</span></span>

<span data-ttu-id="d2dfb-115">AKS ortamını oluşturmanın birkaç yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="d2dfb-115">There are several ways to create the AKS Environment.</span></span> <span data-ttu-id="d2dfb-116">Bu, Azure-CLı komutları kullanılarak veya Azure portal kullanılarak yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="d2dfb-116">It can be done by using Azure-CLI commands or by using the Azure portal.</span></span>

<span data-ttu-id="d2dfb-117">Burada, kümeyi oluşturmak için Azure-CLı kullanarak bazı örnekleri keşfedebilirsiniz ve sonuçları gözden geçirmek için Azure portal.</span><span class="sxs-lookup"><span data-stu-id="d2dfb-117">Here you can explore some examples using the Azure-CLI to create the cluster and the Azure portal to review the results.</span></span> <span data-ttu-id="d2dfb-118">Geliştirme makinenizde Kubectl ve Docker de sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d2dfb-118">You also need to have Kubectl and Docker in your development machine.</span></span>  

## <a name="create-the-aks-cluster"></a><span data-ttu-id="d2dfb-119">AKS kümesini oluşturma</span><span class="sxs-lookup"><span data-stu-id="d2dfb-119">Create the AKS cluster</span></span>

<span data-ttu-id="d2dfb-120">Şu komutu kullanarak AKS kümesini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="d2dfb-120">Create the AKS cluster using this command:</span></span>

```console
az aks create --resource-group MSSampleResourceGroup --name MSSampleClusterK801 --agent-count 1 --generate-ssh-keys --location westus2
```

<span data-ttu-id="d2dfb-121">Oluşturma işi bittikten sonra, Azure portal oluşturulan AKS 'leri görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d2dfb-121">After the creation job finishes, you can see the AKS created in the Azure portal:</span></span>

<span data-ttu-id="d2dfb-122">Kaynak grubu:</span><span class="sxs-lookup"><span data-stu-id="d2dfb-122">The resource group:</span></span>

![Azure AKS kaynak grubunun tarayıcı görünümü.](media/aks-resource-group-view.png)

<span data-ttu-id="d2dfb-124">**Şekil 4-17**.</span><span class="sxs-lookup"><span data-stu-id="d2dfb-124">**Figure 4-17**.</span></span> <span data-ttu-id="d2dfb-125">Azure 'dan AKS kaynak grubu görünümü.</span><span class="sxs-lookup"><span data-stu-id="d2dfb-125">AKS Resource Group view from Azure.</span></span>

<span data-ttu-id="d2dfb-126">AKS kümesi:</span><span class="sxs-lookup"><span data-stu-id="d2dfb-126">The AKS cluster:</span></span>

![AKS kaynak grubunun tarayıcı görünümü.](media/aks-cluster-view.png)

<span data-ttu-id="d2dfb-128">**Şekil 4-18**.</span><span class="sxs-lookup"><span data-stu-id="d2dfb-128">**Figure 4-18**.</span></span> <span data-ttu-id="d2dfb-129">Azure 'dan AKS görünümü.</span><span class="sxs-lookup"><span data-stu-id="d2dfb-129">AKS view from Azure.</span></span>

<span data-ttu-id="d2dfb-130">Ayrıca, `Azure-CLI` ve `Kubectl`kullanarak oluşturulan düğümü görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2dfb-130">You can also view the node created using `Azure-CLI` and `Kubectl`.</span></span>

<span data-ttu-id="d2dfb-131">İlk olarak, kimlik bilgileri alınıyor:</span><span class="sxs-lookup"><span data-stu-id="d2dfb-131">First, getting the credentials:</span></span>

```console
az aks get-credentials --resource-group MSSampleK8ClusterRG --name MSSampleK8Cluster
```

![Yukarıdaki komuttan konsol çıkışı: "MsSampleK8Cluster,/root/. Kube/configiçinde geçerli bağlam olarak birleştirildi.](media/get-credentials-command-result.png)

<span data-ttu-id="d2dfb-133">**Şekil 4-19**.</span><span class="sxs-lookup"><span data-stu-id="d2dfb-133">**Figure 4-19**.</span></span> <span data-ttu-id="d2dfb-134">`aks get-credentials` komut sonucu.</span><span class="sxs-lookup"><span data-stu-id="d2dfb-134">`aks get-credentials` command result.</span></span>

<span data-ttu-id="d2dfb-135">Ardından, Kubectl 'den düğüm alma:</span><span class="sxs-lookup"><span data-stu-id="d2dfb-135">And then, getting nodes from Kubectl:</span></span>

```console
kubectl get nodes
```

![Yukarıdaki komutun konsol çıkışı: durum, Yaş (çalıştırma süresi) ve sürüm ile düğümlerin listesi](media/kubectl-get-nodes-command-result.png)

<span data-ttu-id="d2dfb-137">**Şekil 4-20**.</span><span class="sxs-lookup"><span data-stu-id="d2dfb-137">**Figure 4-20**.</span></span> <span data-ttu-id="d2dfb-138">`kubectl get nodes` komut sonucu.</span><span class="sxs-lookup"><span data-stu-id="d2dfb-138">`kubectl get nodes` command result.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="d2dfb-139">[Önceki](orchestrate-high-scalability-availability.md)
>[İleri](docker-apps-development-environment.md)</span><span class="sxs-lookup"><span data-stu-id="d2dfb-139">[Previous](orchestrate-high-scalability-availability.md)
[Next](docker-apps-development-environment.md)</span></span>
