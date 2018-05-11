---
title: Azure sanal makinelerini (Iaas bulut) Windows kapsayıcıları dağıtma zamanı
description: Azure Bulut ve Windows kapsayıcılarla varolan .NET uygulamaları modernize | Azure sanal makinelerini (Iaas bulut) Windows kapsayıcıları dağıtma zamanı
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 7472745577f414062b460fd71ab45bae85d7a62e
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
---
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a>Azure sanal makinelerini (Iaas bulut) Windows kapsayıcıları dağıtma zamanı

Ayrıca Windows kapsayıcıları bile kullanıyorsanız, kuruluşunuzun Azure VM'ler, kullanarak, Iaas postalarla hala demektir. Yük dengeli altyapısındaki birden çok VM dağıtmak gerektiğinde, yüksek düzeyde ölçeklenebilir uygulamalar için altyapı işlemler, VM OS düzeltme ekleri ve altyapı karmaşıklığı o postalarla anlamına gelir. Bir Azure VM Windows kapsayıcıları kullanma için ana senaryoları şunlardır:

-   **Geliştirme ve test ortamı**: A VM bulut geliştirme ve bulutta sınama için mükemmeldir. Hızlı bir şekilde oluşturmak veya ortamı gereksinimlerinize bağlı olarak durdur.

-   **Küçük ve orta ölçekli ölçeklenebilirlik gereken**: orchestrators gibi daha gelişmiş PaaS ortamlara taşıyabilirsiniz kadar burada ihtiyacınız olabilecek yalnızca VM'ler birkaç üretim ortamınıza senaryolarda, az sayıda sanal makineleri yönetme uygun maliyetli olabilir.

-   **Üretim ortamında var olan dağıtım araçlarıyla**: içinde yatırım VM'ler veya tam sunucuları (Puppet veya benzer araçları gibi) karmaşık dağıtımlar yapmak için Araçları'nda bir şirket içi ortamından taşıma. Üretim ortamında dağıtım yordamları için minimum değişiklikle buluta taşımak için Azure sanal makinelerini dağıtmak için bu araçları kullanın devam edebilir. Ancak, dağıtım deneyimini geliştirmek için dağıtım birimi olarak Windows kapsayıcılar kullanmak istersiniz.

>[!div class="step-by-step"]
[Önceki](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
[sonraki](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
