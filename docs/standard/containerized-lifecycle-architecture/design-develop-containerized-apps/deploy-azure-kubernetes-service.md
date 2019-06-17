---
title: Yüksek ölçeklenebilirlik ve kullanılabilirlik için mikro hizmetleri ve çok kapsayıcılı uygulamaları yönetme
description: Azure Kubernetes hizmetini kullanarak bir uygulamayı dağıtmayı öğrenin.
ms.date: 02/15/2019
ms.openlocfilehash: 88e76b4b0a3686f4227a6aee1b7fbd2bfe55fdcc
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/13/2019
ms.locfileid: "65644632"
---
# <a name="deploy-to-azure-kubernetes-service-aks"></a><span data-ttu-id="20b1b-103">Azure Kubernetes Service’e (AKS) Dağıtma</span><span class="sxs-lookup"><span data-stu-id="20b1b-103">Deploy to Azure Kubernetes Service (AKS)</span></span>

<span data-ttu-id="20b1b-104">Tercih edilen istemci işletim sisteminizi kullanarak AKS ile etkileşim kurabilir, burada Microsoft Windows ve Windows, Ubuntu Linux katıştırılmış bir sürümü ile nasıl yapılacağını Bash komutları kullanarak göstereceğiz.</span><span class="sxs-lookup"><span data-stu-id="20b1b-104">You can interact with AKS using your preferred client operating system, here we show how to do it with Microsoft Windows and an embedded version of Ubuntu Linux in Windows, using Bash commands.</span></span>

<span data-ttu-id="20b1b-105">AKS kullanmadan önce için Önkoşullar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="20b1b-105">Prerequisites to have before using AKS are:</span></span>

- <span data-ttu-id="20b1b-106">Linux veya Mac geliştirme makinesi</span><span class="sxs-lookup"><span data-stu-id="20b1b-106">Linux or Mac development machine</span></span>
- <span data-ttu-id="20b1b-107">Windows geliştirme makinesi</span><span class="sxs-lookup"><span data-stu-id="20b1b-107">Windows development machine</span></span>
  - <span data-ttu-id="20b1b-108">Windows üzerinde etkin Geliştirici modu</span><span class="sxs-lookup"><span data-stu-id="20b1b-108">Developer Mode enabled on Windows</span></span>
  - <span data-ttu-id="20b1b-109">Linux için Windows alt sistemi</span><span class="sxs-lookup"><span data-stu-id="20b1b-109">Windows Subsystem for Linux</span></span>
- <span data-ttu-id="20b1b-110">Azure CLI yüklenmiş [Windows, Mac veya Linux](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest)</span><span class="sxs-lookup"><span data-stu-id="20b1b-110">Azure-CLI installed on [Windows, Mac or Linux](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest)</span></span>

> [!NOTE]
> <span data-ttu-id="20b1b-111">Hakkında tam bilgi almak için:</span><span class="sxs-lookup"><span data-stu-id="20b1b-111">To find complete information about:</span></span>
>
> <span data-ttu-id="20b1b-112">Azure-CLI: <https://docs.microsoft.com/cli/azure/index?view=azure-cli-latest></span><span class="sxs-lookup"><span data-stu-id="20b1b-112">Azure-CLI: <https://docs.microsoft.com/cli/azure/index?view=azure-cli-latest></span></span>
>
> <span data-ttu-id="20b1b-113">Linux için Windows alt sistemi: <https://docs.microsoft.com/windows/wsl/about></span><span class="sxs-lookup"><span data-stu-id="20b1b-113">Windows Subsystem for Linux: <https://docs.microsoft.com/windows/wsl/about></span></span>

## <a name="create-the-aks-environment-in-azure"></a><span data-ttu-id="20b1b-114">Azure'da AKS ortamı oluşturma</span><span class="sxs-lookup"><span data-stu-id="20b1b-114">Create the AKS environment in Azure</span></span>

<span data-ttu-id="20b1b-115">AKS ortamı oluşturmanın birkaç yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="20b1b-115">There are several ways to create the AKS Environment.</span></span> <span data-ttu-id="20b1b-116">Azure CLI komutlarını kullanarak veya Azure portalını kullanarak gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="20b1b-116">It can be done by using Azure-CLI commands or by using the Azure portal.</span></span>

<span data-ttu-id="20b1b-117">Aşağıda bazı örnekler, küme ve sonuçlarını gözden geçirmek için Azure portal'ı oluşturmak için Azure CLI kullanarak keşfedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="20b1b-117">Here you can explore some examples using the Azure-CLI to create the cluster and the Azure portal to review the results.</span></span> <span data-ttu-id="20b1b-118">Kubectl ve Docker geliştirme makinenizin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="20b1b-118">You also need to have Kubectl and Docker in your development machine.</span></span>  

## <a name="create-the-aks-cluster"></a><span data-ttu-id="20b1b-119">AKS kümesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="20b1b-119">Create the AKS cluster</span></span>

<span data-ttu-id="20b1b-120">Bu komutu kullanarak AKS kümesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="20b1b-120">Create the AKS cluster using this command:</span></span>

```console
az aks create --resource-group MSSampleResourceGroup --name MSSampleClusterK801 --agent-count 1 --generate-ssh-keys --location westus2
```

<span data-ttu-id="20b1b-121">Oluşturma işi tamamlandıktan sonra Azure portalında oluşturulan bir AKS görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="20b1b-121">After the creation job finishes, you can see the AKS created in the Azure portal:</span></span>

<span data-ttu-id="20b1b-122">Kaynak grubu:</span><span class="sxs-lookup"><span data-stu-id="20b1b-122">The resource group:</span></span>

![Tarayıcı Görünümü AKS Azure kaynak grubu.](media/aks-resource-group-view.png)

<span data-ttu-id="20b1b-124">**Şekil 4-17**.</span><span class="sxs-lookup"><span data-stu-id="20b1b-124">**Figure 4-17**.</span></span> <span data-ttu-id="20b1b-125">Azure'dan AKS kaynak grubu görünümü.</span><span class="sxs-lookup"><span data-stu-id="20b1b-125">AKS Resource Group view from Azure.</span></span>

<span data-ttu-id="20b1b-126">AKS kümesi:</span><span class="sxs-lookup"><span data-stu-id="20b1b-126">The AKS cluster:</span></span>

![Bir AKS kaynak grubunun tarayıcı görünümü.](media/aks-cluster-view.png)

<span data-ttu-id="20b1b-128">**Şekil 4-18**.</span><span class="sxs-lookup"><span data-stu-id="20b1b-128">**Figure 4-18**.</span></span> <span data-ttu-id="20b1b-129">AKS, Azure'dan görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="20b1b-129">AKS view from Azure.</span></span>

<span data-ttu-id="20b1b-130">Kullanılarak oluşturulan düğümü de görüntüleyebilirsiniz `Azure-CLI` ve `Kubectl`.</span><span class="sxs-lookup"><span data-stu-id="20b1b-130">You can also view the node created using `Azure-CLI` and `Kubectl`.</span></span>

<span data-ttu-id="20b1b-131">İlk olarak, kimlik bilgilerini alma:</span><span class="sxs-lookup"><span data-stu-id="20b1b-131">First, getting the credentials:</span></span>

```console
az aks get-credentials --resource-group MSSampleK8ClusterRG --name MSSampleK8Cluster
```

![Konsolu, yukarıdaki komuttan çıkış: Birleştirilmiş "MsSampleK8Cluster /root/.kube/config geçerli bağlamda olarak.](media/get-credentials-command-result.png)

<span data-ttu-id="20b1b-133">**Şekil 4-19**.</span><span class="sxs-lookup"><span data-stu-id="20b1b-133">**Figure 4-19**.</span></span> <span data-ttu-id="20b1b-134">`aks get-credentials` komut sonucu.</span><span class="sxs-lookup"><span data-stu-id="20b1b-134">`aks get-credentials` command result.</span></span>

<span data-ttu-id="20b1b-135">Ve ardından, Kubectl düğümleri alınıyor:</span><span class="sxs-lookup"><span data-stu-id="20b1b-135">And then, getting nodes from Kubectl:</span></span>

```console
kubectl get nodes
```

![Yukarıdaki komut çıktısı konsolu: Düğüm durumu ve geçerlilik süresi (saat çalışan) sürümü ile listesi](media/kubectl-get-nodes-command-result.png)

<span data-ttu-id="20b1b-137">**Şekil 4-20**.</span><span class="sxs-lookup"><span data-stu-id="20b1b-137">**Figure 4-20**.</span></span> <span data-ttu-id="20b1b-138">`kubectl get nodes` komut sonucu.</span><span class="sxs-lookup"><span data-stu-id="20b1b-138">`kubectl get nodes` command result.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="20b1b-139">[Önceki](orchestrate-high-scalability-availability.md)
>[İleri](docker-apps-development-environment.md)</span><span class="sxs-lookup"><span data-stu-id="20b1b-139">[Previous](orchestrate-high-scalability-availability.md)
[Next](docker-apps-development-environment.md)</span></span>
