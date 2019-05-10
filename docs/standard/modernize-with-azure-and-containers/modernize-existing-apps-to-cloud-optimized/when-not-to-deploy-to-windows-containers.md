---
title: Windows Kapsayıcıları ne zaman dağıtılmaz?
description: Azure Bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirme | Windows kapsayıcıları için dağıtma zamanı
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: e06793065d1fd55bbef855576174b07dc9ace4c8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64751392"
---
# <a name="when-not-to-deploy-to-windows-containers"></a>Windows Kapsayıcıları ne zaman dağıtılmaz?

Bazı Windows teknolojileri ile Windows kapsayıcıları desteklenmez. Bu gibi durumlarda, yine de genellikle yalnızca Windows ve IIS ile standartları vm'lerine geçirmek gerekir.

Çalışmaları Mayıs 2018'den itibaren Windows kapsayıcıları desteklenmez:

- Microsoft Message Queuing (MSMQ) şu anda yalnızca Windows kapsayıcıları, Windows Server v1803 yayına göre ancak herhangi bir önceki sürümlerinde kullanılabilir.

  - [UserVoice isteğini Forumu](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

  - [Tartışma Forumu](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

- Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) Windows kapsayıcıları içinde şu anda desteklenmiyor.

  - [GitHub sorunu](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

- Microsoft Office kapsayıcılar şu anda desteklemiyor.

  - [UserVoice isteğini Forumu](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

- Kullanıcı Arabirimi uygulama (istemci uygulamalar bir görsel kullanıcı arabirimiyle) desteklenen bir senaryo değildir.

- Windows altyapısı rollerinin (DNS, DHCP, DC, NTP, yazdırma, dosya sunucusu, IAM vb.) desteklenen bir senaryo değildir.

Ek desteklenmeyen senaryolar ve topluluktan gelen istekleri için UserVoice forumumuzu Windows kapsayıcıları için bkz: <https://windowsserver.uservoice.com/forums/304624-containers>.

### <a name="additional-resources"></a>Ek kaynaklar

- **Sanal makineler ve azure'da kapsayıcılar**

    <https://azure.microsoft.com/overview/containers/>

> [!div class="step-by-step"]
> [Önceki](deploy-existing-net-apps-as-windows-containers.md)
> [İleri](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
