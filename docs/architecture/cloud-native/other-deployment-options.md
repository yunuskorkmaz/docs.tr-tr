---
title: Diğer kapsayıcı dağıtım seçenekleri
description: Azure kullanarak diğer kapsayıcı dağıtım seçenekleri
ms.date: 04/13/2020
ms.openlocfilehash: 3cae771b3877215a7fc91afd4f406fdfc9ff2771
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2020
ms.locfileid: "82200008"
---
# <a name="other-container-deployment-options"></a>Diğer kapsayıcı dağıtım seçenekleri

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Azure Kubernetes Service (AKS) dışında, kapsayıcılar ve Azure Container Instances için Azure App Service kapsayıcılar da dağıtabilirsiniz.

## <a name="when-does-it-make-sense-to-deploy-to-app-service-for-containers"></a>Ne zaman kapsayıcılar için App Service dağıtmayı mantıklı hale getirir?

Düzenleme gerektirmeyen basit üretim uygulamaları, kapsayıcılar için Azure App Service uygundur.

## <a name="how-to-deploy-to-app-service-for-containers"></a>Kapsayıcılar için App Service dağıtma

[Kapsayıcılar için Azure App Service](https://azure.microsoft.com/services/app-service/containers/)dağıtmak üzere bir Azure Container Registry (ACR) örneğine ve kimlik bilgilerine erişmeniz gerekir. Kapsayıcının görüntüsünü, Azure App Service çekmesi için ACR deposuna gönderin. Tamamlandıktan sonra, uygulamayı sürekli dağıtım için yapılandırabilirsiniz. Bunun yapılması, görüntü ACR 'de her değiştiğinde güncelleştirmeleri otomatik olarak dağıtır.

## <a name="when-does-it-make-sense-to-deploy-to-azure-container-instances"></a>Ne zaman Azure Container Instances dağıtım yapmak mantıklı midir?

[Azure Container Instances (acı)](https://azure.microsoft.com/services/container-instances/) , sanal makineler veya kümeler kurmak zorunda kalmadan, Docker kapsayıcılarını yönetilen, sunucusuz bir bulut ortamında çalıştırmanızı sağlar. Yalıtılmış bir kapsayıcıda çalışabilecek, kısa süreli iş yükleri için harika bir çözümdür. Basit hizmetler, test senaryoları, görev otomasyonu ve derleme işleri için ACI 'yi düşünün. ACı bir kapsayıcı örneği getirir, görevi gerçekleştirir ve ardından aşağı döner.

## <a name="how-to-deploy-an-app-to-azure-container-instances"></a>Azure Container Instances için uygulama dağıtma

[Azure Container Instances (ACI)](https://docs.microsoft.com/azure/container-instances/)uygulamasına dağıtmak için, buna erişmek için bir Azure Container Registry (ACR) ve kimlik bilgileri gerekir. Kapsayıcı görüntünüzü depoya gönderdikten sonra ACI 'ye çekmeniz gerekir. Azure portal veya komut satırı arabirimini kullanarak ACI ile çalışabilirsiniz. ACR, ACI ile sıkı tümleştirme sağlar. Şekil 3-14, tek bir kapsayıcı görüntüsünün ACR 'ye nasıl itilini gösterir.

![Azure Container Registry çalıştırma örneği](./media/acr-runinstance-contextmenu.png)

**Şekil 3-14**. Azure Container Registry çalıştırma örneği

ACI 'de örnek oluşturmak hızlı bir şekilde yapılabilir. Görüntü kayıt defteri, Azure Kaynak grubu bilgileri, ayrılacak bellek miktarı ve dinlemek istediğiniz bağlantı noktasını belirtin. Bu [hızlı başlangıçta, Azure Portal kullanarak bir kapsayıcı örneğinin nasıl dağıtılacağı gösterilmektedir](https://docs.microsoft.com/azure/container-instances/container-instances-quickstart-portal).

Dağıtım tamamlandıktan sonra, yeni dağıtılan kapsayıcının IP adresini bulun ve belirttiğiniz bağlantı noktası üzerinden iletişim kurun.

Azure Container Instances, Azure 'da basit kapsayıcı iş yüklerini çalıştırmanın en hızlı yolunu sunmaktadır. Bir App Service, Orchestrator veya sanal makine yapılandırmanız gerekmez. Tam kapsayıcı düzenlemesi, hizmet bulma, otomatik ölçeklendirme veya koordine edilmiş yükseltmeler gerektiren senaryolar için Azure Kubernetes hizmeti (AKS) önerilir.

## <a name="references"></a>Başvurular

- [Kubernetes nedir?](https://blog.newrelic.com/engineering/what-is-kubernetes/)
- [Minikube ile Kubernetes yükleme](https://kubernetes.io/docs/setup/learning-environment/minikube/)
- [MiniKube vs Docker Masaüstü](https://medium.com/containers-101/local-kubernetes-for-windows-minikube-vs-docker-desktop-25a1c6d3b766)
- [Docker için Visual Studio Araçları](https://docs.microsoft.com/dotnet/standard/containerized-lifecycle-architecture/design-develop-containerized-apps/visual-studio-tools-for-docker)
- [Sunucusuz soğuk başlangıcını anlama](https://azure.microsoft.com/blog/understanding-serverless-cold-start/)
- [Önceden çarpımış Azure Işlevleri örnekleri](https://docs.microsoft.com/azure/azure-functions/functions-premium-plan#pre-warmed-instances)
- [Linux üzerinde özel görüntü kullanarak bir işlev oluşturma](https://docs.microsoft.com/azure/azure-functions/functions-create-function-linux-custom-image)
- [Azure Işlevlerini bir Docker kapsayıcısında çalıştırma](https://markheath.net/post/azure-functions-docker)
- [Linux üzerinde özel görüntü kullanarak bir işlev oluşturma](https://docs.microsoft.com/azure/azure-functions/functions-create-function-linux-custom-image)
- [Kubernetes olay odaklı otomatik ölçeklendirmeyle Azure Işlevleri](https://docs.microsoft.com/azure/azure-functions/functions-kubernetes-keda)
- [Canary yayını](https://martinfowler.com/bliki/CanaryRelease.html)
- [VS Code Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/quickstart-netcore)
- [Visual Studio ile Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/quickstart-netcore-visualstudio)
- [Birden çok düğüm havuzu](https://docs.microsoft.com/azure/aks/use-multiple-node-pools)
- [AKS kümesi otomatik Scaler](https://docs.microsoft.com/azure/aks/cluster-autoscaler)
- [Öğretici: AKS 'de Uygulamaları ölçeklendirme](https://docs.microsoft.com/azure/aks/tutorial-kubernetes-scale)
- [Azure İşlevleri’ni ölçeklendirme ve barındırma](https://docs.microsoft.com/azure/azure-functions/functions-scale)
- [Azure Container Instances docs](https://docs.microsoft.com/azure/container-instances/)
- [ACR 'den kapsayıcı örneği dağıtma](https://docs.microsoft.com/azure/container-instances/container-instances-using-azure-container-registry#deploy-with-azure-portal)

>[!div class="step-by-step"]
>[Önceki](scale-containers-serverless.md)
>[İleri](communication-patterns.md)
