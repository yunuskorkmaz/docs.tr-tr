---
title: Windows Kapsayıcıları Azure Kapsayıcı Hizmetine ne zaman dağıtılır (diğer bir şekilde, Kubernetes)
description: Azure Bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernize edin | Windows Kapsayıcıları Azure Kapsayıcı Hizmetine ne zaman dağıtılır (diğer bir şekilde, Kubernetes)
ms.date: 04/30/2018
ms.openlocfilehash: 903082deba635dd0dfc22d0186fbc589f8d05b92
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "68676912"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a>Windows Kapsayıcıları Azure Kapsayıcı Hizmetine ne zaman dağıtılır (diğer bir şekilde, Kubernetes)

Azure Kapsayıcı Hizmeti, azure için özel olarak popüler açık kaynak araçları nın ve teknolojilerin yapılandırmasını optimize eder. Hem kapsayıcılarınız hem de uygulama yapılandırmanız için taşınabilirlik sunan açık bir çözüme sahip olursunuz. Boyutu, ana bilgisayar sayısını ve orkestratör araçlarını seçersiniz. Azure Kapsayıcı Hizmeti, altyapıyı sizin için işler.

Zaten Kubernetes, Docker Swarm veya DC/OS gibi açık kaynak kodlu orkestratörlerle çalışıyorsanız, kapsayıcı iş yüklerini buluta taşımak için mevcut yönetim uygulamalarınızı değiştirmeniz gerekmez. Zaten aşina olduğunuz uygulama yönetim araçlarını kullanın ve seçtiğiniz orkestratör için standart API uç noktaları üzerinden bağlanın.

Linux Docker kapsayıcıları kullanıyorsanız, tüm bu orkestratörler olgun ortamlardır, ancak yalnızca Windows Kapsayıcıları için Önizleme durumunda olabilir.

Örneğin, Kubernetes'te kapsayıcıdesteği yereldir (birinci sınıf vatandaştır), bu nedenle Kubernetes'te Windows Kapsayıcıları kullanmak da etkilidir (2018'in başlarından itibaren ACS'de önizlemede).

Önemli not: Kubernetes için ACS'nin (Azure Konteyner Hizmeti) gelişmiş ve "daha fazla PaaS" sürümü AKS 'dir (Azure Kubernetes Hizmeti), Ancak Windows Kapsayıcıları Q2 2018 itibariyle hala desteklenmez, ancak yakında desteklenir.

>[!div class="step-by-step"]
>[Önceki](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
>[Sonraki](choosing-azure-compute-options-for-container-based-applications.md)
