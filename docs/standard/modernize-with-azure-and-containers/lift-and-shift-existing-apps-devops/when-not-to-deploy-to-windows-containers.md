---
title: "Ne zaman Windows kapsayıcıları dağıtma"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Ne zaman Windows kapsayıcıları dağıtma"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: cb671ec88da7ff1aa5c960c210e0da5e9d753280
ms.sourcegitcommit: d3cfda0943364aaf6ccd574f55f584576c8a4fee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2018
---
# <a name="when-not-to-deploy-to-windows-containers"></a><span data-ttu-id="ea787-103">Ne zaman Windows kapsayıcıları dağıtma</span><span class="sxs-lookup"><span data-stu-id="ea787-103">When not to deploy to Windows Containers</span></span>

<span data-ttu-id="ea787-104">Bazı Windows teknolojileri Windows kapsayıcıları tarafından desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="ea787-104">Some Windows technologies are not supported by Windows Containers.</span></span> <span data-ttu-id="ea787-105">Bu gibi durumlarda yine genellikle yalnızca Windows ve IIS ile standartları sanal makineleri geçirmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="ea787-105">In those cases, you still need to migrate to standards VMs, usually with just Windows and IIS.</span></span>

<span data-ttu-id="ea787-106">Durumlarda Windows kapsayıcılarında mid-2017 itibariyle desteklenmiyor:</span><span class="sxs-lookup"><span data-stu-id="ea787-106">Cases not supported in Windows Containers, as of mid-2017:</span></span>

-   <span data-ttu-id="ea787-107">Microsoft Message Queuing (MSMQ), Windows kapsayıcılarında şu anda desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="ea787-107">Microsoft Message Queuing (MSMQ) currently is not supported in Windows Containers.</span></span>

    -   [<span data-ttu-id="ea787-108">UserVoice isteği Forumu</span><span class="sxs-lookup"><span data-stu-id="ea787-108">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

    -   [<span data-ttu-id="ea787-109">Tartışma Forumu</span><span class="sxs-lookup"><span data-stu-id="ea787-109">Discussion forum</span></span>](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

-   <span data-ttu-id="ea787-110">Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) Windows kapsayıcılarında şu anda desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="ea787-110">Microsoft Distributed Transaction Coordinator (MSDTC) currently is not supported in Windows Containers</span></span>

    -   [<span data-ttu-id="ea787-111">GitHub sorunu</span><span class="sxs-lookup"><span data-stu-id="ea787-111">GitHub issue</span></span>](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

-   <span data-ttu-id="ea787-112">Microsoft Office kapsayıcıları şu anda desteklemiyor</span><span class="sxs-lookup"><span data-stu-id="ea787-112">Microsoft Office currently does not support containers</span></span>

    -   [<span data-ttu-id="ea787-113">UserVoice isteği Forumu</span><span class="sxs-lookup"><span data-stu-id="ea787-113">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

<span data-ttu-id="ea787-114">Ek değil desteklenen senaryolar ve topluluk gelen istekleri için UserVoice Forumu Windows kapsayıcıları için bkz: <https://windowsserver.uservoice.com/forums/304624-containers>.</span><span class="sxs-lookup"><span data-stu-id="ea787-114">For additional not-supported scenarios and requests from the community, see the UserVoice forum for Windows Containers: <https://windowsserver.uservoice.com/forums/304624-containers>.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="ea787-115">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="ea787-115">Additional resources</span></span>

-   <span data-ttu-id="ea787-116">**Sanal makineler ve Azure kapsayıcı**</span><span class="sxs-lookup"><span data-stu-id="ea787-116">**Virtual machines and containers in Azure**</span></span>

    [<span data-ttu-id="ea787-117">https://docs.microsoft.com/azure/virtual-machines/windows/containers</span><span class="sxs-lookup"><span data-stu-id="ea787-117">https://docs.microsoft.com/azure/virtual-machines/windows/containers</span></span>](https://docs.microsoft.com/azure/virtual-machines/windows/containers)

>[!div class="step-by-step"]
<span data-ttu-id="ea787-118">[Önceki](deploy-existing-net-apps-as-windows-containers.md)
[sonraki](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="ea787-118">[Previous](deploy-existing-net-apps-as-windows-containers.md)
[Next](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span></span>
