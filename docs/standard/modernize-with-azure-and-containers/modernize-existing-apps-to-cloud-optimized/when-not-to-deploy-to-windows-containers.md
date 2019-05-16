---
title: Windows Kapsayıcıları ne zaman dağıtılmaz?
description: Azure Bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirme | Windows kapsayıcıları için dağıtma zamanı
ms.date: 04/28/2018
ms.openlocfilehash: 65e793b846b495e9a1be6db9ddfa38bbf0d49445
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65638907"
---
# <a name="when-not-to-deploy-to-windows-containers"></a><span data-ttu-id="13b91-103">Windows Kapsayıcıları ne zaman dağıtılmaz?</span><span class="sxs-lookup"><span data-stu-id="13b91-103">When not to deploy to Windows Containers</span></span>

<span data-ttu-id="13b91-104">Bazı Windows teknolojileri ile Windows kapsayıcıları desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="13b91-104">Some Windows technologies are not supported by Windows Containers.</span></span> <span data-ttu-id="13b91-105">Bu gibi durumlarda, yine de genellikle yalnızca Windows ve IIS ile standartları vm'lerine geçirmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="13b91-105">In those cases, you still need to migrate to standards VMs, usually with just Windows and IIS.</span></span>

<span data-ttu-id="13b91-106">Çalışmaları Mayıs 2018'den itibaren Windows kapsayıcıları desteklenmez:</span><span class="sxs-lookup"><span data-stu-id="13b91-106">Cases not supported in Windows Containers, as of May 2018:</span></span>

- <span data-ttu-id="13b91-107">Microsoft Message Queuing (MSMQ) şu anda yalnızca Windows kapsayıcıları, Windows Server v1803 yayına göre ancak herhangi bir önceki sürümlerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="13b91-107">Microsoft Message Queuing (MSMQ) currently is only available in Windows Containers based on Windows Server v1803 release, but not in any other prior releases.</span></span>

  - [<span data-ttu-id="13b91-108">UserVoice isteğini Forumu</span><span class="sxs-lookup"><span data-stu-id="13b91-108">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

  - [<span data-ttu-id="13b91-109">Tartışma Forumu</span><span class="sxs-lookup"><span data-stu-id="13b91-109">Discussion forum</span></span>](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

- <span data-ttu-id="13b91-110">Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) Windows kapsayıcıları içinde şu anda desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="13b91-110">Microsoft Distributed Transaction Coordinator (MSDTC) currently is not supported in Windows Containers.</span></span>

  - [<span data-ttu-id="13b91-111">GitHub sorunu</span><span class="sxs-lookup"><span data-stu-id="13b91-111">GitHub issue</span></span>](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

- <span data-ttu-id="13b91-112">Microsoft Office kapsayıcılar şu anda desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="13b91-112">Microsoft Office currently does not support containers.</span></span>

  - [<span data-ttu-id="13b91-113">UserVoice isteğini Forumu</span><span class="sxs-lookup"><span data-stu-id="13b91-113">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

- <span data-ttu-id="13b91-114">Kullanıcı Arabirimi uygulama (istemci uygulamalar bir görsel kullanıcı arabirimiyle) desteklenen bir senaryo değildir.</span><span class="sxs-lookup"><span data-stu-id="13b91-114">UI apps (client apps with a visual user interface) are not supported scenarios.</span></span>

- <span data-ttu-id="13b91-115">Windows altyapısı rollerinin (DNS, DHCP, DC, NTP, yazdırma, dosya sunucusu, IAM vb.) desteklenen bir senaryo değildir.</span><span class="sxs-lookup"><span data-stu-id="13b91-115">Windows infrastructure roles (DNS, DHCP, DC, NTP, PRINT, File server, IAM etc.) are not supported scenarios.</span></span>

<span data-ttu-id="13b91-116">Ek desteklenmeyen senaryolar ve topluluktan gelen istekleri için UserVoice forumumuzu Windows kapsayıcıları için bkz: <https://windowsserver.uservoice.com/forums/304624-containers>.</span><span class="sxs-lookup"><span data-stu-id="13b91-116">For additional not-supported scenarios and requests from the community, see the UserVoice forum for Windows Containers: <https://windowsserver.uservoice.com/forums/304624-containers>.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="13b91-117">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="13b91-117">Additional resources</span></span>

- <span data-ttu-id="13b91-118">**Sanal makineler ve azure'da kapsayıcılar**</span><span class="sxs-lookup"><span data-stu-id="13b91-118">**Virtual machines and containers in Azure**</span></span>

    <https://azure.microsoft.com/overview/containers/>

> [!div class="step-by-step"]
> <span data-ttu-id="13b91-119">[Önceki](deploy-existing-net-apps-as-windows-containers.md)
> [İleri](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="13b91-119">[Previous](deploy-existing-net-apps-as-windows-containers.md)
[Next](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span></span>
