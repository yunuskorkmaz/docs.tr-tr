---
title: Azure VM’lere (IaaS bulutu) Windows Kapsayıcıları ne zaman dağıtılmalıdır?
description: Azure Bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernize edin | Windows Kapsayıcılarını Azure VM'lere (IaaS bulutu) ne zaman dağıtılır?
ms.date: 04/28/2018
ms.openlocfilehash: e9a2903662306b607977a7751018e24161ab80ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "68676900"
---
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a>Azure VM’lere (IaaS bulutu) Windows Kapsayıcıları ne zaman dağıtılmalıdır?

Kuruluşunuz Azure VM kullanıyorsa, Windows Kapsayıcıları kullanıyor sanız bile, Hala IaaS ile uğraşıyorsunuz. Bu, yük dengeli bir altyapıda birden fazla VM'ye dağıtmanız gerektiğinde, altyapı işlemleri, VM OS yamaları ve yüksek ölçeklenebilir uygulamalar için altyapı karmaşıklığı yla başa çıkmanız gerektiği anlamına gelir. Windows Kapsayıcılarını Azure VM'de kullanmak için temel senaryolar şunlardır:

- **Geliştirme/test ortamı**: Buluttaki Bir VM, bulutta geliştirme ve test için idealdir. İhtiyaçlarınıza bağlı olarak ortamı hızla oluşturabilir veya durdurabilirsiniz.

- **Küçük ve orta ölçeklenebilirlik gereksinimleri**: Üretim ortamınız için sadece birkaç VM'ye ihtiyaç duyabileceğiniz senaryolarda, orkestratörler gibi daha gelişmiş PaaS ortamlarına taşınana kadar az sayıda VM'yi yönetmek uygun fiyatlı olabilir.

- **Varolan dağıtım araçlarıyla üretim ortamı**: VM'lere veya çıplak metal sunuculara (Puppet veya benzeri araçlar gibi) karmaşık dağıtımlar yapmak için araçlara yatırım yaptığınız şirket içi bir ortamdan hareket ediyor olabilirsiniz. Üretim ortamı dağıtım yordamlarında en az değişiklikle buluta geçmek için, bu araçları Azure VM'lerine dağıtmak için kullanmaya devam edebilirsiniz. Ancak, dağıtım deneyimini geliştirmek için dağıtım birimi olarak Windows Kapsayıcıları kullanmak isteyeceksiniz.

>[!div class="step-by-step"]
>[Önceki](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
>[Sonraki](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
