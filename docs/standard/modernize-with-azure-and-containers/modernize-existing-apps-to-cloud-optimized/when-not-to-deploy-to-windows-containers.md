---
title: Ne zaman Windows kapsayıcıları dağıtma
description: Azure Bulut ve Windows kapsayıcılarla varolan .NET uygulamaları modernize | Ne zaman Windows kapsayıcıları dağıtma
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 819f32955ff019414bef8820d17d272eddc11bf8
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
---
# <a name="when-not-to-deploy-to-windows-containers"></a>Ne zaman Windows kapsayıcıları dağıtma

Bazı Windows teknolojileri Windows kapsayıcıları tarafından desteklenmez. Bu gibi durumlarda yine genellikle yalnızca Windows ve IIS ile standartları sanal makineleri geçirmek gerekir.

Durumları May 2018 itibariyle Windows kapsayıcılarında desteklenmiyor: 

-   Microsoft Message Queuing (MSMQ) şu anda yalnızca Windows Server v1803 yayımını temel alan Windows kapsayıcılardaki, ancak herhangi bir önceki sürümlerde kullanılabilir. 

    -   [UserVoice isteği Forumu](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

    -   [Tartışma Forumu](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

-   Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) Windows kapsayıcılarında şu anda desteklenmiyor.

    -   [GitHub sorunu](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

-   Microsoft Office kapsayıcıları şu anda desteklemiyor.

    -   [UserVoice isteği Forumu](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

-   UI uygulamaları (istemci uygulamaları bir görsel kullanıcı arabirimiyle) desteklenen senaryolar değildir.

-   Windows altyapı rolleri (DNS, DHCP, DC, NTP, yazdırma, dosya sunucusu, IAM vb.) desteklenen senaryolar verilmiştir.


Ek değil desteklenen senaryolar ve topluluk gelen istekleri için UserVoice Forumu Windows kapsayıcıları için bkz: <https://windowsserver.uservoice.com/forums/304624-containers>.

### <a name="additional-resources"></a>Ek kaynaklar

-   **Sanal makineler ve Azure kapsayıcı**

    [https://docs.microsoft.com/azure/virtual-machines/windows/containers](https://docs.microsoft.com/azure/virtual-machines/windows/containers)

>[!div class="step-by-step"]
[Önceki](deploy-existing-net-apps-as-windows-containers.md)
[sonraki](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
