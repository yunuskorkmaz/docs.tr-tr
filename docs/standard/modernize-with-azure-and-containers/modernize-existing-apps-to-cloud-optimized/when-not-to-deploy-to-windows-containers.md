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
# <a name="when-not-to-deploy-to-windows-containers"></a><span data-ttu-id="16337-103">Ne zaman Windows kapsayıcıları dağıtma</span><span class="sxs-lookup"><span data-stu-id="16337-103">When not to deploy to Windows Containers</span></span>

<span data-ttu-id="16337-104">Bazı Windows teknolojileri Windows kapsayıcıları tarafından desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="16337-104">Some Windows technologies are not supported by Windows Containers.</span></span> <span data-ttu-id="16337-105">Bu gibi durumlarda yine genellikle yalnızca Windows ve IIS ile standartları sanal makineleri geçirmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="16337-105">In those cases, you still need to migrate to standards VMs, usually with just Windows and IIS.</span></span>

<span data-ttu-id="16337-106">Durumları May 2018 itibariyle Windows kapsayıcılarında desteklenmiyor:</span><span class="sxs-lookup"><span data-stu-id="16337-106">Cases not supported in Windows Containers, as of May 2018:</span></span> 

-   <span data-ttu-id="16337-107">Microsoft Message Queuing (MSMQ) şu anda yalnızca Windows Server v1803 yayımını temel alan Windows kapsayıcılardaki, ancak herhangi bir önceki sürümlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="16337-107">Microsoft Message Queuing (MSMQ) currently is only available in Windows Containers based on Windows Server v1803 release, but not in any other prior releases.</span></span> 

    -   [<span data-ttu-id="16337-108">UserVoice isteği Forumu</span><span class="sxs-lookup"><span data-stu-id="16337-108">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

    -   [<span data-ttu-id="16337-109">Tartışma Forumu</span><span class="sxs-lookup"><span data-stu-id="16337-109">Discussion forum</span></span>](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

-   <span data-ttu-id="16337-110">Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) Windows kapsayıcılarında şu anda desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="16337-110">Microsoft Distributed Transaction Coordinator (MSDTC) currently is not supported in Windows Containers.</span></span>

    -   [<span data-ttu-id="16337-111">GitHub sorunu</span><span class="sxs-lookup"><span data-stu-id="16337-111">GitHub issue</span></span>](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

-   <span data-ttu-id="16337-112">Microsoft Office kapsayıcıları şu anda desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="16337-112">Microsoft Office currently does not support containers.</span></span>

    -   [<span data-ttu-id="16337-113">UserVoice isteği Forumu</span><span class="sxs-lookup"><span data-stu-id="16337-113">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

-   <span data-ttu-id="16337-114">UI uygulamaları (istemci uygulamaları bir görsel kullanıcı arabirimiyle) desteklenen senaryolar değildir.</span><span class="sxs-lookup"><span data-stu-id="16337-114">UI apps (client apps with a visual user interface) are not supported scenarios.</span></span>

-   <span data-ttu-id="16337-115">Windows altyapı rolleri (DNS, DHCP, DC, NTP, yazdırma, dosya sunucusu, IAM vb.) desteklenen senaryolar verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="16337-115">Windows infrastructure roles (DNS, DHCP, DC, NTP, PRINT, File server, IAM etc.) are not supported scenarios.</span></span>


<span data-ttu-id="16337-116">Ek değil desteklenen senaryolar ve topluluk gelen istekleri için UserVoice Forumu Windows kapsayıcıları için bkz: <https://windowsserver.uservoice.com/forums/304624-containers>.</span><span class="sxs-lookup"><span data-stu-id="16337-116">For additional not-supported scenarios and requests from the community, see the UserVoice forum for Windows Containers: <https://windowsserver.uservoice.com/forums/304624-containers>.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="16337-117">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="16337-117">Additional resources</span></span>

-   <span data-ttu-id="16337-118">**Sanal makineler ve Azure kapsayıcı**</span><span class="sxs-lookup"><span data-stu-id="16337-118">**Virtual machines and containers in Azure**</span></span>

    [https://docs.microsoft.com/azure/virtual-machines/windows/containers](https://docs.microsoft.com/azure/virtual-machines/windows/containers)

>[!div class="step-by-step"]
<span data-ttu-id="16337-119">[Önceki](deploy-existing-net-apps-as-windows-containers.md)
[sonraki](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="16337-119">[Previous](deploy-existing-net-apps-as-windows-containers.md)
[Next](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span></span>
