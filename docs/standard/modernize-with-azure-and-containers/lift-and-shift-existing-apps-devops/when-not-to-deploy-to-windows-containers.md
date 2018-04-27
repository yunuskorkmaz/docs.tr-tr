---
title: Ne zaman Windows kapsayıcıları dağıtma
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Ne zaman Windows kapsayıcıları dağıtma
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b8fb31a17d1f9d91fe053596685b7560a7fa1ee1
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="when-not-to-deploy-to-windows-containers"></a>Ne zaman Windows kapsayıcıları dağıtma

Bazı Windows teknolojileri Windows kapsayıcıları tarafından desteklenmez. Bu gibi durumlarda yine genellikle yalnızca Windows ve IIS ile standartları sanal makineleri geçirmek gerekir.

Durumlarda Windows kapsayıcılarında mid-2017 itibariyle desteklenmiyor:

-   Microsoft Message Queuing (MSMQ), Windows kapsayıcılarında şu anda desteklenmiyor.

    -   [UserVoice isteği Forumu](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

    -   [Tartışma Forumu](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

-   Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) Windows kapsayıcılarında şu anda desteklenmiyor

    -   [GitHub sorunu](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

-   Microsoft Office kapsayıcıları şu anda desteklemiyor

    -   [UserVoice isteği Forumu](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

Ek değil desteklenen senaryolar ve topluluk gelen istekleri için UserVoice Forumu Windows kapsayıcıları için bkz: <https://windowsserver.uservoice.com/forums/304624-containers>.

### <a name="additional-resources"></a>Ek kaynaklar

-   **Sanal makineler ve Azure kapsayıcı**

    [https://docs.microsoft.com/azure/virtual-machines/windows/containers](https://docs.microsoft.com/azure/virtual-machines/windows/containers)

>[!div class="step-by-step"]
[Önceki](deploy-existing-net-apps-as-windows-containers.md)
[sonraki](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
