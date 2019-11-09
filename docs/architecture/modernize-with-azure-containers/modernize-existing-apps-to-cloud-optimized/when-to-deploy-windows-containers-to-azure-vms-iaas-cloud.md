---
title: Azure VM’lere (IaaS bulutu) Windows Kapsayıcıları ne zaman dağıtılmalıdır?
description: Azure bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirin | Azure VM 'lerine (IaaS bulutu) Windows kapsayıcıları ne zaman dağıtılır
ms.date: 04/28/2018
ms.openlocfilehash: e9a2903662306b607977a7751018e24161ab80ab
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/08/2019
ms.locfileid: "68676900"
---
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a>Azure VM’lere (IaaS bulutu) Windows Kapsayıcıları ne zaman dağıtılmalıdır?

Kuruluşunuz Azure VM 'Leri kullanıyorsa, aynı zamanda Windows kapsayıcıları kullanıyor olsanız bile IaaS ile ilgilenmeye devam edersiniz. Yani, yük dengeli bir altyapıda birden çok VM 'ye dağıtmanız gerektiğinde, yüksek düzeyde ölçeklenebilir uygulamalar için altyapı işlemleri, VM OS yamaları ve altyapı karmaşıklığı ile ilgilenme anlamına gelir. Azure VM 'de Windows kapsayıcıları kullanmaya yönelik temel senaryolar şunlardır:

- Geliştirme ve **test ortamı**: BULUTTAKI bir VM, bulutta geliştirme ve test için mükemmeldir. İhtiyaçlarınıza bağlı olarak ortamı hızlı bir şekilde oluşturabilir veya durdurabilirsiniz.

- **Küçük ve orta ölçeklenebilirlik ihtiyaçları**: üretim ortamınız için yalnızca birkaç VM 'niz olması gerekebileceği senaryolarda, daha gelişmiş PaaS ortamlarına geçiş yapılıncaya kadar, az sayıda sanal makineyi yönetmek uygun maliyetli olabilir.

- **Mevcut dağıtım araçlarıyla üretim ortamı**: VM 'lere veya çıplak sunuculara (Pupevcil hayvan veya benzer araçlar gibi) karmaşık dağıtımlar oluşturmak için, araçlara yatırım yaptığınız şirket içi bir ortamdan geçiş yapabilirsiniz. Üretim ortamı dağıtım yordamlarına en az değişiklikle buluta geçmek için bu araçları Azure VM 'lerine dağıtmak üzere kullanmaya devam edebilirsiniz. Ancak, dağıtım deneyimini geliştirmek için dağıtım birimi olarak Windows kapsayıcıları kullanmak isteyeceksiniz.

>[!div class="step-by-step"]
>[Önceki](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
>[İleri](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
