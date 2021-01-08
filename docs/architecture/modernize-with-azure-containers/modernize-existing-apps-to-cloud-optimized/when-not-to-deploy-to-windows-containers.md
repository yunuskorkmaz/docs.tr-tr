---
title: Windows Kapsayıcıları ne zaman dağıtılmaz?
description: Azure bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirin | Windows kapsayıcılarına dağıtılmayan
ms.date: 12/21/2020
ms.openlocfilehash: 4eea24ab8deb3719c778b45b3ddc1309277a3f50
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025179"
---
# <a name="when-not-to-deploy-to-windows-containers"></a>Windows Kapsayıcıları ne zaman dağıtılmaz?

Bazı Windows teknolojileri Windows kapsayıcıları tarafından desteklenmez. Bu durumlarda, genellikle yalnızca Windows ve IIS ile standartları VM 'lerine geçiş yapmanız gerekir.

Durum 2018 itibariyle Windows kapsayıcılarında desteklenmeyen durumlar:

- Microsoft Message Queuing (MSMQ) Şu anda yalnızca Windows Server v1803 Release 'e dayalı, diğer önceki sürümlerde bulunmayan Windows kapsayıcılarında kullanılabilir.

  - [UserVoice istek Forumu](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

  - [Tartışma forumunuz](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

- Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) Şu anda Windows kapsayıcılarında desteklenmemektedir.

  - [GitHub sorunu](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

- Microsoft Office şu anda kapsayıcıları desteklemiyor.

  - [UserVoice istek Forumu](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

- UI uygulamaları (bir görsel kullanıcı arabirimine sahip istemci uygulamaları), desteklenen senaryolar değildir.

- Windows altyapı rolleri (DNS, DHCP, DC, NTP, yazdırma, dosya sunucusu, ıAM vb.), desteklenen senaryolar değildir.

Topluluktaki desteklenmeyen diğer senaryolar ve istekler için bkz. Windows kapsayıcıları için UserVoice Forumu: <https://windowsserver.uservoice.com/forums/304624-containers> .

### <a name="additional-resources"></a>Ek kaynaklar

- **Azure 'daki sanal makineler ve kapsayıcılar**

    <https://azure.microsoft.com/overview/containers/>

> [!div class="step-by-step"]
> [Önceki](deploy-existing-net-apps-as-windows-containers.md) 
>  [Sonraki](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
