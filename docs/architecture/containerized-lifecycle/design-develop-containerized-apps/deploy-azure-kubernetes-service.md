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
# <a name="deploy-to-azure-kubernetes-service-aks"></a>Azure Kubernetes Service’e (AKS) Dağıtma

Tercih ettiğiniz istemci işletim sistemini kullanarak AKS ile etkileşimkurabilirsiniz, burada Nasıl Microsoft Windows ve Windows Ubuntu Linux gömülü bir sürümünü, Bash komutları kullanarak bunu göstermek.

AKS kullanmadan önce sahip olması önkoşullar şunlardır:

- Linux veya Mac geliştirme makinesi
- Windows geliştirme makinesi
  - Windows'da Geliştirici Modu etkin
  - Linux için Windows Alt Sistemi
- [Windows, Mac veya Linux'ta](https://docs.microsoft.com/cli/azure/install-azure-cli) yüklü Azure-CLI

> [!NOTE]
> Hakkında tam bilgi bulmak için:
>
> Azure-CLI:<https://docs.microsoft.com/cli/azure/index>
>
> Linux için Windows Alt Sistemi:<https://docs.microsoft.com/windows/wsl/about>

## <a name="create-the-aks-environment-in-azure"></a>Azure'da AKS ortamını oluşturma

AKS Ortamını oluşturmanın birkaç yolu vardır. Azure-CLI komutlarını kullanarak veya Azure portalını kullanarak yapılabilir.

Burada, sonuçları gözden geçirmek için küme yi ve Azure portalını oluşturmak için Azure-CLI'yi kullanarak bazı örnekleri keşfedebilirsiniz. Ayrıca geliştirme makinenizde Kubectl ve Docker olması gerekir.  

## <a name="create-the-aks-cluster"></a>AKS kümesini oluşturma

Bu komutu kullanarak AKS kümesini oluşturun:

```console
az aks create --resource-group MSSampleResourceGroup --name MSSampleClusterK801 --agent-count 1 --generate-ssh-keys --location westus2
```

Oluşturma işi bittikten sonra Azure portalında oluşturulan AKS'yi görebilirsiniz:

Kaynak grubu:

![Azure AKS kaynak grubunun tarayıcı görünümü.](media/aks-resource-group-view.png)

**Şekil 4-17**. Azure'dan AKS Kaynak Grubu görünümü.

AKS kümesi:

![AKS kaynak grubunun tarayıcı görünümü.](media/aks-cluster-view.png)

**Şekil 4-18**. Azure'dan AKS görünümü.

Ayrıca kullanarak `Azure-CLI` oluşturulan düğümü görüntüleyebilir `Kubectl`ve.

İlk olarak, kimlik bilgilerini alma:

```console
az aks get-credentials --resource-group MSSampleK8ClusterRG --name MSSampleK8Cluster
```

![Yukarıdaki komuttan konsol çıkışı: Birleştirilmiş "MsSampleK8Cluster geçerli bağlam olarak /root/.kube/config.](media/get-credentials-command-result.png)

**Şekil 4-19**. `aks get-credentials`komut sonucu.

Ve sonra, Kubectl gelen düğümleri alma:

```console
kubectl get nodes
```

![Yukarıdaki komuttan konsol çıkışı: Durum, yaş (zaman çalışan) ve sürüm ile düğümlistesi](media/kubectl-get-nodes-command-result.png)

**Şekil 4-20**. `kubectl get nodes`komut sonucu.

>[!div class="step-by-step"]
>[Önceki](orchestrate-high-scalability-availability.md)
>[Sonraki](docker-apps-development-environment.md)
