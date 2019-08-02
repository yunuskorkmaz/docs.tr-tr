---
title: Windows kapsayıcıları Azure Container Service dağıtım zaman (yani, Kubernetes)
description: Azure bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirin | Windows kapsayıcıları Azure Container Service dağıtım zaman (yani, Kubernetes)
ms.date: 04/30/2018
ms.openlocfilehash: 903082deba635dd0dfc22d0186fbc589f8d05b92
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68676912"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a>Windows kapsayıcıları Azure Container Service dağıtım zaman (yani, Kubernetes)

Azure Container Service, popüler açık kaynaklı araçların ve teknolojilerin yapılandırmasını özellikle Azure için iyileştirir. Kapsayıcılar ve uygulama yapılandırmanız için taşınabilirlik sağlayan açık bir çözüm alırsınız. Boyut, ana bilgisayar sayısı ve Orchestrator Araçları ' nı seçersiniz. Azure Container Service altyapıyı sizin için işler.

Kubernetes, Docker Sısınma veya DC/OS gibi açık kaynaklı düzenleyiciler ile zaten çalışıyorsanız, kapsayıcı iş yüklerini buluta taşımak için mevcut yönetim uygulamalarınızı değiştirmeniz gerekmez. Zaten bildiğiniz uygulama yönetimi araçlarını kullanın ve seçtiğiniz Orchestrator için Standart API uç noktaları aracılığıyla bağlanın.

Linux Docker Kapsayıcıları kullanıyorsanız, ancak yalnızca Windows kapsayıcıları önizleme durumunda olabilir.

Örneğin, Kubernetes 'te kapsayıcılar için destek yerel (birinci sınıf vatandaşlık), bu nedenle Kubernetes üzerinde Windows kapsayıcıları kullanmak da etkilidir (ACS 'nin erken 2018 itibariyle önizlemesi için).

Önemli bir dikkat: Kubernetes 'nin Azure Container Service (Azure Kubernetes hizmeti) (örneğin, Kubernetes) ve "diğer PaaS" sürümü AKS (Azure Kubernetes hizmeti), ancak Windows kapsayıcıları, S2 2018 itibariyle hala desteklenmiyordur, ancak yakında desteklenecektir.

>[!div class="step-by-step"]
>[Önceki](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)İleri
>[](choosing-azure-compute-options-for-container-based-applications.md)
