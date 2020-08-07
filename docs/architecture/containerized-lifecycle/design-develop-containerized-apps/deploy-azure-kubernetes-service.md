---
title: Yüksek ölçeklenebilirlik ve kullanılabilirlik için mikro hizmetleri ve çok kapsayıcılı uygulamaları yönetme
description: Azure Kubernetes hizmetini kullanarak bir uygulamayı dağıtmayı öğrenin.
ms.date: 08/06/2020
ms.openlocfilehash: b4deb9906e0fece7fb611b6988df576e8b07fe46
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916113"
---
# <a name="deploy-to-azure-kubernetes-service-aks"></a>Azure Kubernetes Service’e (AKS) Dağıtma

Azure komut satırı arabirimi (Azure CLı) yüklü olan tercih ettiğiniz istemci işletim sistemini (Windows, macOS veya Linux) kullanarak AKS ile etkileşim kurabilirsiniz. Daha fazla ayrıntı için, kullanılabilir ortamlar için [Azure CLI belgelerine](https://docs.microsoft.com/cli/azure/?view=azure-cli-latest) ve [yükleme kılavuzuna](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest) bakın.

## <a name="create-the-aks-environment-in-azure"></a>Azure 'da AKS ortamını oluşturma

AKS ortamını oluşturmanın birkaç yolu vardır. Azure CLı komutları kullanılarak veya Azure portal kullanılarak yapılabilir.

Burada, kümeyi oluşturmak için Azure CLı kullanarak bazı örnekleri keşfedebilirsiniz ve sonuçları gözden geçirmek için Azure portal. Geliştirme makinenizde Kubectl ve Docker de sahip olmanız gerekir.

## <a name="create-the-aks-cluster"></a>AKS kümesini oluşturma

Bu komutu kullanarak AKS kümesini oluşturun (kaynak grubu mevcut olmalıdır):

```console
az aks create --resource-group explore-docker-aks-rg --name explore-docker-aks --node-vm-size Standard_B2s --node-count 1 --generate-ssh-keys --location westeurope
```

> [!NOTE]
> `--node-vm-size`Ve `--node-count` parametre değerleri bir örnek/dev uygulaması için yeterince iyidir.

Oluşturma işi tamamlandıktan sonra aşağıdakileri görebilirsiniz:

- İlk kaynak grubunda oluşturulan AKS kümesi
- Aşağıdaki görüntülerde gösterildiği gibi, AKS kümesiyle ilgili kaynakları içeren yeni, ilişkili bir kaynak grubu.

AKS kümesi ile ilk kaynak grubu:

![AKS kaynak grubunun tarayıcı görünümü.](media/deploy-azure-kubernetes-service/aks-cluster-view.png)

**Şekil 4-17**. Azure 'dan AKS kaynak grubu görünümü.

AKS kümesi kaynak grubu:

![Azure AKS kaynak grubunun tarayıcı görünümü.](media/deploy-azure-kubernetes-service/aks-resource-group-view.png)

**Şekil 4-18**. Azure 'dan AKS görünümü.

> [!IMPORTANT]
> Genel olarak, AKS kümesi kaynak grubundaki kaynakları değiştirmeniz gerekmez. Örneğin, AKS kümesini sildiğinizde kaynak grubu silinir.

Ve kullanılarak oluşturulan düğümü de görüntüleyebilirsiniz `Azure CLI` `Kubectl` .

İlk olarak, kimlik bilgileri alınıyor:

```console
az aks get-credentials --resource-group explore-docker-aks-rg --name explore-docker-aks
```

![Yukarıdaki komuttan konsol çıktısı: "keşfet-Docker-aks" i/Home/MIGUEL/.exe içindeki geçerli bağlam olarak birleştirildi.](media/deploy-azure-kubernetes-service/get-credentials-command-result.png)

**Şekil 4-19**. `aks get-credentials`komut sonucu.

Ardından, Kubectl 'den düğüm alma:

```console
kubectl get nodes
```

![Yukarıdaki komuttan konsol çıktısı: durum, Yaş (çalıştırma süresi) ve sürüm içeren düğümlerin listesi](media/deploy-azure-kubernetes-service/kubectl-get-nodes-command-result.png)

**Şekil 4-20**. `kubectl get nodes`komut sonucu.

> [!div class="step-by-step"]
> [Önceki](orchestrate-high-scalability-availability.md) 
>  [Sonraki](docker-apps-development-environment.md)
