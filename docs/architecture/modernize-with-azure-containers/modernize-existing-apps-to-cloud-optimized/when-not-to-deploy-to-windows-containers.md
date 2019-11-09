---
title: Windows Kapsayıcıları ne zaman dağıtılmaz?
description: Azure bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirin | Windows kapsayıcılarına dağıtılmayan
ms.date: 04/28/2018
ms.openlocfilehash: 65e793b846b495e9a1be6db9ddfa38bbf0d49445
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/08/2019
ms.locfileid: "68676915"
---
# <a name="when-not-to-deploy-to-windows-containers"></a><span data-ttu-id="20d1d-103">Windows Kapsayıcıları ne zaman dağıtılmaz?</span><span class="sxs-lookup"><span data-stu-id="20d1d-103">When not to deploy to Windows Containers</span></span>

<span data-ttu-id="20d1d-104">Bazı Windows teknolojileri Windows kapsayıcıları tarafından desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="20d1d-104">Some Windows technologies are not supported by Windows Containers.</span></span> <span data-ttu-id="20d1d-105">Bu durumlarda, genellikle yalnızca Windows ve IIS ile standartları VM 'lerine geçiş yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="20d1d-105">In those cases, you still need to migrate to standards VMs, usually with just Windows and IIS.</span></span>

<span data-ttu-id="20d1d-106">Durum 2018 itibariyle Windows kapsayıcılarında desteklenmeyen durumlar:</span><span class="sxs-lookup"><span data-stu-id="20d1d-106">Cases not supported in Windows Containers, as of May 2018:</span></span>

- <span data-ttu-id="20d1d-107">Microsoft Message Queuing (MSMQ) Şu anda yalnızca Windows Server v1803 Release 'e dayalı, diğer önceki sürümlerde bulunmayan Windows kapsayıcılarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="20d1d-107">Microsoft Message Queuing (MSMQ) currently is only available in Windows Containers based on Windows Server v1803 release, but not in any other prior releases.</span></span>

  - [<span data-ttu-id="20d1d-108">UserVoice istek Forumu</span><span class="sxs-lookup"><span data-stu-id="20d1d-108">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

  - [<span data-ttu-id="20d1d-109">Tartışma forumu</span><span class="sxs-lookup"><span data-stu-id="20d1d-109">Discussion forum</span></span>](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

- <span data-ttu-id="20d1d-110">Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) Şu anda Windows kapsayıcılarında desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="20d1d-110">Microsoft Distributed Transaction Coordinator (MSDTC) currently is not supported in Windows Containers.</span></span>

  - [<span data-ttu-id="20d1d-111">GitHub sorunu</span><span class="sxs-lookup"><span data-stu-id="20d1d-111">GitHub issue</span></span>](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

- <span data-ttu-id="20d1d-112">Microsoft Office şu anda kapsayıcıları desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="20d1d-112">Microsoft Office currently does not support containers.</span></span>

  - [<span data-ttu-id="20d1d-113">UserVoice istek Forumu</span><span class="sxs-lookup"><span data-stu-id="20d1d-113">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

- <span data-ttu-id="20d1d-114">UI uygulamaları (bir görsel kullanıcı arabirimine sahip istemci uygulamaları), desteklenen senaryolar değildir.</span><span class="sxs-lookup"><span data-stu-id="20d1d-114">UI apps (client apps with a visual user interface) are not supported scenarios.</span></span>

- <span data-ttu-id="20d1d-115">Windows altyapı rolleri (DNS, DHCP, DC, NTP, yazdırma, dosya sunucusu, ıAM vb.), desteklenen senaryolar değildir.</span><span class="sxs-lookup"><span data-stu-id="20d1d-115">Windows infrastructure roles (DNS, DHCP, DC, NTP, PRINT, File server, IAM etc.) are not supported scenarios.</span></span>

<span data-ttu-id="20d1d-116">Topluluktaki desteklenmeyen ek senaryolar ve istekler için bkz. Windows kapsayıcıları için UserVoice Forumu: <https://windowsserver.uservoice.com/forums/304624-containers>.</span><span class="sxs-lookup"><span data-stu-id="20d1d-116">For additional not-supported scenarios and requests from the community, see the UserVoice forum for Windows Containers: <https://windowsserver.uservoice.com/forums/304624-containers>.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="20d1d-117">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="20d1d-117">Additional resources</span></span>

- <span data-ttu-id="20d1d-118">**Azure 'daki sanal makineler ve kapsayıcılar**</span><span class="sxs-lookup"><span data-stu-id="20d1d-118">**Virtual machines and containers in Azure**</span></span>

    <https://azure.microsoft.com/overview/containers/>

> [!div class="step-by-step"]
> <span data-ttu-id="20d1d-119">[Önceki](deploy-existing-net-apps-as-windows-containers.md)
> [İleri](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="20d1d-119">[Previous](deploy-existing-net-apps-as-windows-containers.md)
[Next](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span></span>
