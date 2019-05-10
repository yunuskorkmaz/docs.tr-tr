---
title: Azure VM’lere (IaaS bulutu) Windows Kapsayıcıları ne zaman dağıtılmalıdır?
description: Azure Bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirme | Azure Vm'lere (Iaas Bulutu) Windows kapsayıcıları dağıtma zamanı
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 8bff4297f99b6549b80604860985568445bbdc0b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625654"
---
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a>Azure VM’lere (IaaS bulutu) Windows Kapsayıcıları ne zaman dağıtılmalıdır?

Ayrıca Windows kapsayıcılarını kullanıyor olsanız bile kuruluşunuz Azure Vm'leri kullanıyor, Iaas uğraşmanızı hala demektir. Bir yük dengeli altyapısında birden çok VM dağıtmak ihtiyacınız olduğunda bu uğraşmanızı altyapı işlemleri, VM işletim sistemi düzeltme ekleri ve altyapı karmaşıklığını yüksek düzeyde ölçeklenebilir uygulamalar için anlamına gelir. Bir Azure sanal Makinesinde Windows kapsayıcılarını kullanmaya yönelik temel senaryolar şunlardır:

- **Geliştirme/test ortamı**: Bir VM bulut geliştirme ve test amacıyla buluta mükemmeldir. Hızlı bir şekilde oluşturabilir veya gereksinimlerinize bağlı olarak ortamı durdurun.

- **Küçük ve orta ölçekli ölçeklenebilirlik ihtiyacı**: Düzenleyiciler gibi daha gelişmiş PaaS ortamlara taşınana kadar burada yalnızca birkaç sanal makinelerinin üretim ortamınız için ihtiyacınız olabilecek senaryolarda, uygun maliyetli az sayıda VM yönetme olabilir.

- **Üretim ortamında var olan dağıtım araçlarıyla**: Bir şirket içi ortamdan sanal makineleri veya çıplak sunucuları (örneğin, Puppet veya benzer Araçlar) karmaşık dağıtımları yapmak için Araçlar, yatırım yapmış taşıma. Üretim ortamına dağıtım yordamları için minimum değişiklikle buluta taşımak için Azure Vm'leri dağıtmak için bu araçları kullanmaya devam edebilir. Ancak, Windows kapsayıcıları dağıtım deneyimini iyileştirmek üzere dağıtım birimi olarak kullanmak isteyebilirsiniz.

>[!div class="step-by-step"]
>[Önceki](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
>[İleri](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)