---
title: "Azure sanal makinelerini (Iaas bulut) Windows kapsayıcıları dağıtma zamanı"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Azure sanal makinelerini (Iaas bulut) Windows kapsayıcıları dağıtma zamanı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 37a37f91bb910004128c96511f585bea03a51d3a
ms.sourcegitcommit: d3cfda0943364aaf6ccd574f55f584576c8a4fee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2018
---
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a>Azure sanal makinelerini (Iaas bulut) Windows kapsayıcıları dağıtma zamanı

Ayrıca Windows kapsayıcıları bile kullanıyorsanız, kuruluşunuzun Azure VM'ler, kullanarak, Iaas postalarla hala demektir. Yük dengeli altyapısındaki birden çok VM dağıtmak gerektiğinde, yüksek düzeyde ölçeklenebilir uygulamalar için altyapı işlemler, VM OS düzeltme ekleri ve altyapı karmaşıklığı o postalarla anlamına gelir. Bir Azure VM Windows kapsayıcıları kullanma için ana senaryoları şunlardır:

-   **Geliştirme ve test ortamı**: A VM bulut geliştirme ve bulutta sınama için mükemmeldir. Hızlı bir şekilde oluşturmak veya ortamı gereksinimlerinize bağlı olarak durdur.

-   **Küçük ve orta ölçekli ölçeklenebilirlik gereken**: orchestrators gibi daha gelişmiş PaaS ortamlara taşıyabilirsiniz kadar burada ihtiyacınız olabilecek yalnızca VM'ler birkaç üretim ortamınıza senaryolarda, az sayıda sanal makineleri yönetme uygun maliyetli olabilir.

-   **Üretim ortamında var olan dağıtım araçlarıyla**: içinde yatırım VM'ler veya tam sunucuları (Puppet veya benzer araçları gibi) karmaşık dağıtımlar yapmak için Araçları'nda bir şirket içi ortamından taşıma. Üretim ortamında dağıtım yordamları için minimum değişiklikle buluta taşımak için Azure sanal makinelerini dağıtmak için bu araçları kullanın devam edebilir. Ancak, dağıtım deneyimini geliştirmek için dağıtım birimi olarak Windows kapsayıcılar kullanmak istersiniz.

>[!div class="step-by-step"]
[Önceki](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
[sonraki](when-to-deploy-windows-containers-to-service-fabric.md)
