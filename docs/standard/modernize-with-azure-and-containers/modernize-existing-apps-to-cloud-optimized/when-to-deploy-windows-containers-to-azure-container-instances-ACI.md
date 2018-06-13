---
title: Azure kapsayıcı örnekleri (ACI) Windows kapsayıcıları dağıtma zamanı
description: Azure Bulut ve Windows kapsayıcılarla varolan .NET uygulamaları modernize | Azure kapsayıcı örnekleri (ACI) Windows kapsayıcıları dağıtma zamanı
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/29/2018
ms.openlocfilehash: 3dc23c96543d9611763b571105f52b150dfec06f
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
ms.locfileid: "33958226"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a>Azure kapsayıcı örnekleri (ACI) Windows kapsayıcıları dağıtma zamanı

Ana değer teklifinde hemen kapsayıcıları için dağıtabilirsiniz ve o ortamınızı sürdürmek gerekmeyen olan Azure kapsayıcı örnekleri, yükseltme / underlaying işletim sistemi veya tüm saydamdır VM'ler, düzeltme eki gerekmez ve yalnızca dağıtma kapsayıcıları bir kullanıma hazır ortamına.

Azure VM'ler ile kapsayıcıları, bu nedenle temelde kullandığınızda nedenleri ve ACI kullanmak istediğiniz zaman senaryoları ana senaryoları ile benzerdir, Azure kapsayıcı örneği kullanmak için ana senaryolar şunlardır:

-   **Geliştirme ve Test senaryoları**
-   **Görev Otomasyonu**
-   **CI/CD aracıları**
-   **Küçük/ölçek toplu işleme**
-   **Basit web uygulamaları**

Orta senaryo ACI için basit web apps senaryodur ancak ACI içinde yalnızca tek kapsayıcı örnek kapsayıcı görüntü başına olabileceği için yüksek oranda kullanılabilir olmaz ve yalnızca sınırlı ölçeklenebilirlik olduğunu dikkate alın.

Ancak, yalnızca tek kapsayıcı örnekleri sağladığından bile ACI altyapı olarak kabul edildiğinde, Windows Server ile normal Azure vm'lerine karşılaştırıldığında büyük bir yararı yoktur. ACI, kendi kendine tutulan ortamına yalnızca kapsayıcıları dağıtın ve yalnızca bu kapsayıcı için ödeme yaparsınız. Burada, VM'ler ile kapsayıcıları kullanabilecek Çoğu senaryoda daha iyi kadar platformu olacak şekilde korumak/güncelleştirme/düzeltme eki VM gerekmez. ACI kullanarak doğrudan İleri, yalnızca bir kapsayıcıyı dağıtmak, yalnızca kapsayıcıları dağıtın VM ortamı oluşturmak için gerek yoktur.

Azure kapsayıcı örnekleri (ACI) ana avantajları şunlardır:

-   Sunucuları yönetmek zorunda kalmadan kapsayıcıları çalıştırın
-   İsteğe bağlı kapsayıcılarla çeviklik artırın
-   Eşi görülmemiş Basitlik ve hız ile bulut kapsayıcıları dağıtın — tek bir komutla. 
-   Hiper yönetici yalıtımlı güvenli uygulamalar

Kısacası, ACI ile uygulamaları hızlı sanal makineleri yönetme veya yeni araçları öğrenmek zorunda kalmadan geliştirebilirsiniz. Yalnızca uygulamanız, bulutta çalışan bir kapsayıcıda değil.

>[!div class="step-by-step"]
[Önceki](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[sonraki](when-to-deploy-windows-containers-to-service-fabric.md)
