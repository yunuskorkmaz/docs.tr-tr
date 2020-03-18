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
# <a name="when-not-to-deploy-to-windows-containers"></a><span data-ttu-id="0bd58-103">Windows Kapsayıcıları ne zaman dağıtılmaz?</span><span class="sxs-lookup"><span data-stu-id="0bd58-103">When not to deploy to Windows Containers</span></span>

<span data-ttu-id="0bd58-104">Bazı Windows teknolojileri Windows Kapsayıcıları tarafından desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="0bd58-104">Some Windows technologies are not supported by Windows Containers.</span></span> <span data-ttu-id="0bd58-105">Bu gibi durumlarda, genellikle sadece Windows ve IIS ile standartlara VM'lere geçiş yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0bd58-105">In those cases, you still need to migrate to standards VMs, usually with just Windows and IIS.</span></span>

<span data-ttu-id="0bd58-106">Mayıs 2018 itibariyle Windows Kapsayıcılarında desteklenmeyen durumlar:</span><span class="sxs-lookup"><span data-stu-id="0bd58-106">Cases not supported in Windows Containers, as of May 2018:</span></span>

- <span data-ttu-id="0bd58-107">Microsoft İleti Sıralaması (MSMQ) şu anda yalnızca Windows Server v1803 sürümüne dayalı windows kapsayıcılarında kullanılabilir, ancak önceki sürümlerde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0bd58-107">Microsoft Message Queuing (MSMQ) currently is only available in Windows Containers based on Windows Server v1803 release, but not in any other prior releases.</span></span>

  - [<span data-ttu-id="0bd58-108">UserVoice istek forumu</span><span class="sxs-lookup"><span data-stu-id="0bd58-108">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

  - [<span data-ttu-id="0bd58-109">Tartışma forumu</span><span class="sxs-lookup"><span data-stu-id="0bd58-109">Discussion forum</span></span>](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

- <span data-ttu-id="0bd58-110">Microsoft Dağıtılmış İşlem Koordinatörü (MSDTC) şu anda Windows Kapsayıcılarında desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="0bd58-110">Microsoft Distributed Transaction Coordinator (MSDTC) currently is not supported in Windows Containers.</span></span>

  - [<span data-ttu-id="0bd58-111">GitHub sorunu</span><span class="sxs-lookup"><span data-stu-id="0bd58-111">GitHub issue</span></span>](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

- <span data-ttu-id="0bd58-112">Microsoft Office şu anda kapsayıcıları desteklemez.</span><span class="sxs-lookup"><span data-stu-id="0bd58-112">Microsoft Office currently does not support containers.</span></span>

  - [<span data-ttu-id="0bd58-113">UserVoice istek forumu</span><span class="sxs-lookup"><span data-stu-id="0bd58-113">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

- <span data-ttu-id="0bd58-114">Kullanıcı arabirimi uygulamaları (görsel kullanıcı arabirimine sahip istemci uygulamaları) desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="0bd58-114">UI apps (client apps with a visual user interface) are not supported scenarios.</span></span>

- <span data-ttu-id="0bd58-115">Windows altyapı rolleri (DNS, DHCP, DC, NTP, PRINT, File server, IAM vb.) desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="0bd58-115">Windows infrastructure roles (DNS, DHCP, DC, NTP, PRINT, File server, IAM etc.) are not supported scenarios.</span></span>

<span data-ttu-id="0bd58-116">Topluluktan desteklenmeyen ek senaryolar ve istekler için Windows Kapsayıcıları <https://windowsserver.uservoice.com/forums/304624-containers>için UserVoice forumuna bakın: .</span><span class="sxs-lookup"><span data-stu-id="0bd58-116">For additional not-supported scenarios and requests from the community, see the UserVoice forum for Windows Containers: <https://windowsserver.uservoice.com/forums/304624-containers>.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="0bd58-117">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="0bd58-117">Additional resources</span></span>

- <span data-ttu-id="0bd58-118">**Azure'da sanal makineler ve konteynerler**</span><span class="sxs-lookup"><span data-stu-id="0bd58-118">**Virtual machines and containers in Azure**</span></span>

    <https://azure.microsoft.com/overview/containers/>

> [!div class="step-by-step"]
> <span data-ttu-id="0bd58-119">[Önceki](deploy-existing-net-apps-as-windows-containers.md)
> [Sonraki](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="0bd58-119">[Previous](deploy-existing-net-apps-as-windows-containers.md)
[Next](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span></span>
