---
title: Windows Kapsayıcıları ne zaman dağıtılmaz?
description: Azure Bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernize edin | Windows Kapsayıcılarına dağıtılmadığında
ms.date: 04/28/2018
ms.openlocfilehash: 65e793b846b495e9a1be6db9ddfa38bbf0d49445
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "68676915"
---
# <a name="when-not-to-deploy-to-windows-containers"></a>Windows Kapsayıcıları ne zaman dağıtılmaz?

Bazı Windows teknolojileri Windows Kapsayıcıları tarafından desteklenmez. Bu gibi durumlarda, genellikle sadece Windows ve IIS ile standartlara VM'lere geçiş yapmanız gerekir.

Mayıs 2018 itibariyle Windows Kapsayıcılarında desteklenmeyen durumlar:

- Microsoft İleti Sıralaması (MSMQ) şu anda yalnızca Windows Server v1803 sürümüne dayalı windows kapsayıcılarında kullanılabilir, ancak önceki sürümlerde kullanılamaz.

  - [UserVoice istek forumu](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

  - [Tartışma forumu](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

- Microsoft Dağıtılmış İşlem Koordinatörü (MSDTC) şu anda Windows Kapsayıcılarında desteklenmez.

  - [GitHub sorunu](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

- Microsoft Office şu anda kapsayıcıları desteklemez.

  - [UserVoice istek forumu](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

- Kullanıcı arabirimi uygulamaları (görsel kullanıcı arabirimine sahip istemci uygulamaları) desteklenmez.

- Windows altyapı rolleri (DNS, DHCP, DC, NTP, PRINT, File server, IAM vb.) desteklenmez.

Topluluktan desteklenmeyen ek senaryolar ve istekler için Windows Kapsayıcıları <https://windowsserver.uservoice.com/forums/304624-containers>için UserVoice forumuna bakın: .

### <a name="additional-resources"></a>Ek kaynaklar

- **Azure'da sanal makineler ve konteynerler**

    <https://azure.microsoft.com/overview/containers/>

> [!div class="step-by-step"]
> [Önceki](deploy-existing-net-apps-as-windows-containers.md)
> [Sonraki](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
