---
title: Diğer kapsayıcı dağıtım seçenekleri
description: Azure kullanarak diğer kapsayıcı dağıtım seçenekleri
ms.date: 06/30/2019
ms.openlocfilehash: 1fcb57eedec8c9f5574fffcf409b316332032062
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214449"
---
# <a name="other-container-deployment-options"></a>Diğer kapsayıcı dağıtım seçenekleri

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

AKS 'e dağıtmanın yanı sıra kapsayıcılar ve Azure Container Instances için Azure App Service kapsayıcıları da dağıtabilirsiniz.

## <a name="when-does-it-make-sense-to-deploy-to-app-service-for-containers"></a>Ne zaman kapsayıcılar için App Service dağıtmayı mantıklı hale getirir?

Düzenleme gerektirmeyen basit üretim uygulamaları, kapsayıcılar için Azure App Service uygundur.

## <a name="how-to-deploy-to-app-service-for-containers"></a>Kapsayıcılar için App Service dağıtma

[Kapsayıcılar için Azure App Service](https://azure.microsoft.com/services/app-service/containers/)dağıtmak üzere, bu uygulamaya erişmek için bir Azure Container Registry (ACR) ve kimlik bilgileri yapılandırmış olmanız gerekir. Azure App Service, barındırmak için istediğiniz kapsayıcıyı kayıt defterine göndererek, çekmesini sağlayın. Oluşturulduktan sonra, uygulamayı sürekli dağıtım için yapılandırabilirsiniz, bu, ilgili görüntüsünü ACR 'de güncelleştirdiğinizde otomatik olarak uygulamaya güncelleştirmeleri dağıtır.

## <a name="when-does-it-make-sense-to-deploy-to-azure-container-instances"></a>Ne zaman Azure Container Instances dağıtım yapmak mantıklı midir?

Azure Container Instances, sınama senaryolarında en iyi şekilde kullanılır. Bu uygulamalar, bir uygulamayı bulutta barındırılan bir kapsayıcı örneğine dağıtmanın hızlı ve kolay bir yolunu sunar. Azure Kubernetes hizmeti tarafından sunulan ölçekleme ve düzenleme özelliklerine ihtiyaç duymuyorsanız uygulamaları test etmek veya tanıtım etmek için kullanın.

## <a name="how-to-deploy-an-app-to-azure-container-instances"></a>Azure Container Instances için uygulama dağıtma

[Azure Container Instances (ACI)](https://docs.microsoft.com/azure/container-instances/)uygulamasına dağıtmak için, bu uygulamaya erişmek için bir Azure Container Registry (ACR) ve kimlik bilgileri yapılandırmış olmanız gerekir. Ayrıca, kapsayıcı görüntünüzü daha önce kayıt defterine göndermiş olmanız gerekir, bu nedenle ACI 'ye çekmek için kullanılabilir. Azure CLı kullanarak veya Portal üzerinden ACI ile çalışabilirsiniz. Şekil 3-14 ' de gösterildiği gibi Azure Container Registry, bağımsız kapsayıcı örneklerinin doğrudan kayıt içinden doğrudan bir şekilde dağıtılmasını kolaylaştırır.

![Azure Container Registry çalıştırma örneği](./media/acr-runinstance-contextmenu.png)

**Şekil 3-14**. Azure Container Registry çalıştırma örneği

Kayıt defterinden bir kapsayıcı örneği oluşturmak için, yalnızca olağan Azure ayarlarını (ad, abonelik, kaynak grubu ve konum), kapsayıcıya ne kadar bellek ayrılacağını ve hangi bağlantı noktasını dinleyebileceğini belirtmeniz gerekir. Bu [hızlı başlangıçta, Azure Portal kullanarak bir kapsayıcı örneğinin nasıl dağıtılacağı gösterilmektedir](https://docs.microsoft.com/azure/container-instances/container-instances-quickstart-portal).

Dağıtım tamamlandıktan sonra, yeni dağıtılan kapsayıcının IP adresini bulun ve belirttiğiniz bağlantı noktası üzerinden iletişim kurun.

Azure Container Instances, Azure 'da kapsayıcı çalıştırmanın en hızlı ve en kolay yolunu sunmaktadır. Bir App Service veya Orchestrator yapılandırmaya ya da sanal makinelerle uğraşmanıza gerek yoktur. Bununla birlikte, basitliği nedeniyle öncelikle test amacıyla acı kullanılmalıdır. Uygulamanız için otomatik ölçeklenebilirlik, birlikte çalışacak şekilde yapılandırılmış birden çok kapsayıcı veya ek karmaşık özellikler gerekiyorsa, uygulamanızı barındırmak için kullanabileceğiniz başka bir daha uygun Azure hizmeti vardır.

## <a name="references"></a>Referanslar

- [Azure Container Instances docs](https://docs.microsoft.com/azure/container-instances/)
- [ACR 'den kapsayıcı örneği dağıtma](https://docs.microsoft.com/azure/container-instances/container-instances-using-azure-container-registry#deploy-with-azure-portal)

>[!div class="step-by-step"]
>[Önceki](scale-containers-serverless.md)
>[İleri](communication-patterns.md)
