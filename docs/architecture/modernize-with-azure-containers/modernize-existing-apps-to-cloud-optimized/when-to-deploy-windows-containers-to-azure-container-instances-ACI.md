---
title: Windows Kapsayıcıları Azure Kapsayıcı Örneklerine (ACI) ne zaman dağıtılır?
description: Azure Bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernize edin | Windows Kapsayıcıları Azure Kapsayıcı Örneklerine (ACI) ne zaman dağıtılır?
ms.date: 04/29/2018
ms.openlocfilehash: 3b6ae1ced9c4e01f5ab400e2575947a396064ebd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "68676909"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a>Windows Kapsayıcıları Azure Kapsayıcı Örneklerine (ACI) ne zaman dağıtılır?

Azure Kapsayıcı Örnekleri ana değer teklifi, kapsayıcıları hemen ona dağıtabilmeniz ve bu ortamı korumanız gerekmemektedir, temel işletim sistemini veya VM'leri yükseltmeniz/düzeltmeniz gerekmez, tüm bunlar saydamdır ve kapsayıcıları kullanıma hazır bir ortama dağıtırsınız.

ACI kullanmak istediğiniz nedenler ve senaryolar, kapsayıcılarla Azure VM'leri kullandığınızda ana senaryolara benzer, bu nedenle temel olarak Azure Kapsayıcı Örnekleri'ni kullanmak için temel senaryolar şunlardır:

- **Dev/Test senaryoları**
- **Görev otomasyonu**
- **CI/CD aracıları**
- **Küçük/ölçekli toplu işleme**
- **Basit web uygulamaları**

Basit web uygulamaları senaryosu ACI için adil bir senaryodur, ancak ACI'da konteyner görüntüsü başına yalnızca tek bir kapsayıcı örneğine sahip olabileceğiniz için yüksek kullanılabilirliğe sahip olmanızı ve yalnızca ölçeklenebilirliğe sahip olduğunuzu göz önünde bulundurabilirsiniz.

Ancak, Yalnızca tek kapsayıcı örnekleri sağladığı için ACI altyapı olarak kabul edilse bile, Windows Server'a sahip normal Azure VM'lere kıyasla büyük bir avantaj sağlar. ACI ile, sadece kendi kendine bakımlı bir ortama konteyner dağıtmak ve sadece bu konteynerler için ödeme. VM'leri korumanız/güncellemeniz/yamanız gerekmez, bu nedenle kapsayıcılı VM'ler kullandığınız çoğu senaryo için çok daha iyi bir platformdur. ACI kullanarak düz, sadece bir kapsayıcı dağıtmak, sadece kapsayıcıdağıtmak bir VM ortamı oluşturmak için gerek yoktur.

Azure Kapsayıcı Örnekleri'nin (ACI) başlıca avantajları şunlardır:

- Sunucuları yönetmeden kapsayıcıları çalıştırma
- Talep üzerine konteynerler ile çevikliği artırın
- Tek bir komutla, daha önce görülmemiş basitlik ve hızile kapsayıcıları buluta dağıtın.
- Hipervizör izolasyonlu güvenli uygulamalar

Kısacası, ACI ile sanal makineleri yönetmeden veya yeni araçlar öğrenmek zorunda kalmadan uygulamaları hızlı bir şekilde geliştirebilirsiniz. Sadece uygulamanız, bir kapta, bulutta çalışıyor.

> [!div class="step-by-step"]
> [Önceki](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
> [Sonraki](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
