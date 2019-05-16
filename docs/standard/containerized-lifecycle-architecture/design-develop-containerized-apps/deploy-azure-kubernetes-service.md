---
title: Yüksek ölçeklenebilirlik ve kullanılabilirlik için mikro hizmetleri ve çok kapsayıcılı uygulamaları yönetme
description: Azure Kubernetes hizmetini kullanarak bir uygulamayı dağıtmayı öğrenin.
ms.date: 02/15/2019
ms.openlocfilehash: 88e76b4b0a3686f4227a6aee1b7fbd2bfe55fdcc
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644632"
---
# <a name="deploy-to-azure-kubernetes-service-aks"></a>Azure Kubernetes Service’e (AKS) Dağıtma

Tercih edilen istemci işletim sisteminizi kullanarak AKS ile etkileşim kurabilir, burada Microsoft Windows ve Windows, Ubuntu Linux katıştırılmış bir sürümü ile nasıl yapılacağını Bash komutları kullanarak göstereceğiz.

AKS kullanmadan önce için Önkoşullar şunlardır:

- Linux veya Mac geliştirme makinesi
- Windows geliştirme makinesi
  - Windows üzerinde etkin Geliştirici modu
  - Linux için Windows alt sistemi
- Azure CLI yüklenmiş [Windows, Mac veya Linux](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest)

> [!NOTE]
> Hakkında tam bilgi almak için:
>
> Azure-CLI: <https://docs.microsoft.com/cli/azure/index?view=azure-cli-latest>
>
> Linux için Windows alt sistemi: <https://docs.microsoft.com/windows/wsl/about>

## <a name="create-the-aks-environment-in-azure"></a>Azure'da AKS ortamı oluşturma

AKS ortamı oluşturmanın birkaç yolu vardır. Azure CLI komutlarını kullanarak veya Azure portalını kullanarak gerçekleştirilebilir.

Aşağıda bazı örnekler, küme ve sonuçlarını gözden geçirmek için Azure portal'ı oluşturmak için Azure CLI kullanarak keşfedebilirsiniz. Kubectl ve Docker geliştirme makinenizin olması gerekir.  

## <a name="create-the-aks-cluster"></a>AKS kümesi oluşturma

Bu komutu kullanarak AKS kümesi oluşturun:

```console
az aks create --resource-group MSSampleResourceGroup --name MSSampleClusterK801 --agent-count 1 --generate-ssh-keys --location westus2
```

Oluşturma işi tamamlandıktan sonra Azure portalında oluşturulan bir AKS görebilirsiniz:

Kaynak grubu:

![Tarayıcı Görünümü AKS Azure kaynak grubu.](media/aks-resource-group-view.png)

**Şekil 4-17**. Azure'dan AKS kaynak grubu görünümü.

AKS kümesi:

![Bir AKS kaynak grubunun tarayıcı görünümü.](media/aks-cluster-view.png)

**Şekil 4-18**. AKS, Azure'dan görüntüleyin.

Kullanılarak oluşturulan düğümü de görüntüleyebilirsiniz `Azure-CLI` ve `Kubectl`.

İlk olarak, kimlik bilgilerini alma:

```console
az aks get-credentials --resource-group MSSampleK8ClusterRG --name MSSampleK8Cluster
```

![Konsolu, yukarıdaki komuttan çıkış: Birleştirilmiş "MsSampleK8Cluster /root/.kube/config geçerli bağlamda olarak.](media/get-credentials-command-result.png)

**Şekil 4-19**. `aks get-credentials` komut sonucu.

Ve ardından, Kubectl düğümleri alınıyor:

```console
kubectl get nodes
```

![Yukarıdaki komut çıktısı konsolu: Düğüm durumu ve geçerlilik süresi (saat çalışan) sürümü ile listesi](media/kubectl-get-nodes-command-result.png)

**Şekil 4-20**. `kubectl get nodes` komut sonucu.

>[!div class="step-by-step"]
>[Önceki](orchestrate-high-scalability-availability.md)
>[İleri](docker-apps-development-environment.md)
