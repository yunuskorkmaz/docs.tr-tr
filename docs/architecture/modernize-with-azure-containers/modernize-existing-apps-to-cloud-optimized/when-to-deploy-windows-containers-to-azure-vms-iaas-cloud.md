---
title: Azure VM’lere (IaaS bulutu) Windows Kapsayıcıları ne zaman dağıtılmalıdır?
description: Azure bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirin | Azure VM 'lerine (IaaS bulutu) Windows kapsayıcıları ne zaman dağıtılır
ms.date: 12/21/2020
ms.openlocfilehash: 64ba53fa56227266ee0e61a128d18373a2dbbc93
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025100"
---
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a>Azure VM’lere (IaaS bulutu) Windows Kapsayıcıları ne zaman dağıtılmalıdır?

Kuruluşunuz Azure VM 'Leri kullanıyorsa, aynı zamanda Windows kapsayıcıları kullanıyor olsanız bile IaaS ile ilgilenmeye devam edersiniz. Yani, yük dengeli bir altyapıda birden çok VM 'ye dağıtmanız gerektiğinde, yüksek düzeyde ölçeklenebilir uygulamalar için altyapı işlemleri, VM OS yamaları ve altyapı karmaşıklığı ile ilgilenme anlamına gelir. Azure VM 'de Windows kapsayıcıları kullanmaya yönelik temel senaryolar şunlardır:

- Geliştirme ve **test ortamı**: BULUTTAKI bir VM, bulutta geliştirme ve test için mükemmeldir. İhtiyaçlarınıza bağlı olarak ortamı hızlı bir şekilde oluşturabilir veya durdurabilirsiniz.

- **Küçük ve orta ölçeklenebilirlik ihtiyaçları**: üretim ortamınız için yalnızca birkaç VM 'niz olması gerekebileceği senaryolarda, daha gelişmiş PaaS ortamlarına geçiş yapana kadar birkaç sanal makineyi yönetmek uygun maliyetli olabilir.

- **Mevcut dağıtım araçlarıyla üretim ortamı**: VM 'lere veya çıplak sunuculara (Pupevcil hayvan veya benzer araçlar gibi) karmaşık dağıtımlar oluşturmak için, araçlara yatırım yaptığınız şirket içi bir ortamdan geçiş yapabilirsiniz. Üretim ortamı dağıtım yordamlarına en az değişiklikle buluta geçmek için bu araçları Azure VM 'lerine dağıtmak üzere kullanmaya devam edebilirsiniz. Ancak, dağıtım deneyimini geliştirmek için dağıtım birimi olarak Windows kapsayıcıları kullanmak isteyeceksiniz.

>[!div class="step-by-step"]
>[Önceki](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md) 
> [Sonraki](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
