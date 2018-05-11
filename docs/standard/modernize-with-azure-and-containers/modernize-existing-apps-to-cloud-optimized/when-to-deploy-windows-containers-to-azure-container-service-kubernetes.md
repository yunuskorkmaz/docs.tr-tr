---
title: Azure kapsayıcı hizmeti (diğer bir deyişle, Kubernetes) Windows kapsayıcıları dağıtma zamanı
description: Azure Bulut ve Windows kapsayıcılarla varolan .NET uygulamaları modernize | Azure kapsayıcı hizmeti (diğer bir deyişle, Kubernetes) Windows kapsayıcıları dağıtma zamanı
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: b7f106e2b79a2c6bb24733debf7f4828505d66a6
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a>Azure kapsayıcı hizmeti (diğer bir deyişle, Kubernetes) Windows kapsayıcıları dağıtma zamanı

Azure kapsayıcı hizmeti popüler açık kaynak Araçlar ve teknolojiler yapılandırmasını özellikle Azure için en iyi duruma getirir. Taşınabilirlik kapsayıcılarınızı hem uygulama yapılandırmanızı sağlayan açık olan çözüm alın. Boyut, ana bilgisayar sayısı ve orchestrator araçları seçin. Azure kapsayıcı hizmeti altyapı işler.

Zaten açık kaynak orchestrators Kubernetes, Docker Swarm veya DC/OS gibi çalışıyorsanız kapsayıcı iş yüklerinin buluta taşımak için var olan Yönetim uygulamalarınızı değiştirmeniz gerekmez. Zaten aşina uygulama yönetim araçlarını kullanın ve tercih ettiğiniz orchestrator için standart API uç noktaları bağlanın.

Linux Docker kapsayıcıları kullanma, ancak yalnızca Windows kapsayıcıları için Önizleme durumda olabilir, bu orchestrators olgun ortamları demektir.

Kapsayıcıları için Kubernetes Örneğin, destek yerel (birinci sınıf citizen), bu nedenle Kubernetes üzerinde Windows kapsayıcıları kullanma (önizlemede ACS içindeki erken 2018 itibariyle) etkili de.

Önemli Not: sistem gereksinimleri ve "daha fazla PaaS" Kubernetes için ACS (Azure kapsayıcı hizmeti) sürümüdür AKS (Azure Kubernetes hizmeti), Windows kapsayıcıları hala desteklenmez S2 2018 itibariyle, ancak, yakında desteklenecek.

>[!div class="step-by-step"]
[Önceki](when-to-deploy-windows-containers-to-service-fabric.md)
[sonraki](choosing-azure-compute-options-for-container-based-applications.md)
