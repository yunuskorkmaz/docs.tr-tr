---
title: "UI Otomasyon Güvenliğine Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, security model
- security model, UI Automation
ms.assetid: 1d853695-973c-48ae-b382-4132ae702805
caps.latest.revision: "23"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: c9cec20d2ab011f2ec6d44dc5d899e3d83c4dba5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ui-automation-security-overview"></a><span data-ttu-id="7b7df-102">UI Otomasyon Güvenliğine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7b7df-102">UI Automation Security Overview</span></span>
> [!NOTE]
>  <span data-ttu-id="7b7df-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="7b7df-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="7b7df-104">Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="7b7df-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="7b7df-105">Bu genel bakış için güvenlik modeli açıklanır [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] içinde [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7b7df-105">This overview describes the security model for [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] in [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)].</span></span>  
  
<a name="User_Account_Control"></a>   
## <a name="user-account-control"></a><span data-ttu-id="7b7df-106">Kullanıcı Hesabı Denetimi</span><span class="sxs-lookup"><span data-stu-id="7b7df-106">User Account Control</span></span>  
 <span data-ttu-id="7b7df-107">Güvenliği, bir ana odağını [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] ve yenilik arasında mutlaka, daha yüksek ayrıcalık gerektiren uygulamalar ve hizmetler çalıştırılmasının engellenme olmadan standart (yönetici olmayan) kullanıcı olarak çalıştırmak kullanıcılara.</span><span class="sxs-lookup"><span data-stu-id="7b7df-107">Security is a major focus of [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] and among the innovations is the ability for users to run as standard (non-administrator) users without necessarily being blocked from running applications and services that require higher privileges.</span></span>  
  
 <span data-ttu-id="7b7df-108">İçinde [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)], çoğu uygulamalar standart veya bir yönetici belirteci ile sağlanır.</span><span class="sxs-lookup"><span data-stu-id="7b7df-108">In [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)], most applications are supplied with either a standard or an administrative token.</span></span> <span data-ttu-id="7b7df-109">Bir uygulama yönetim uygulaması tanımlanamaz, varsayılan olarak standart bir uygulama olarak başlatılır.</span><span class="sxs-lookup"><span data-stu-id="7b7df-109">If an application cannot be identified as an administrative application, it is launched as a standard application by default.</span></span> <span data-ttu-id="7b7df-110">Bir uygulama gibi yönetici tanımlanan önce başlatılan [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] yükseltilmiş uygulamanın çalışmasına izin kullanıcıya sorar.</span><span class="sxs-lookup"><span data-stu-id="7b7df-110">Before an application identified as administrative can be launched, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] prompts the user for consent to run the application as elevated.</span></span> <span data-ttu-id="7b7df-111">Bir uygulama veya yönetici kimlik bilgileri gerektiren sistem bileşeni çalıştırma izni isteklerini kadar Yöneticiler standart kullanıcı olarak çalıştığından kullanıcı yerel Administrators grubunun bir üyesi olsa bile, onay istemi varsayılan olarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7b7df-111">The consent prompt is displayed by default, even if the user is a member of the local Administrators group, because administrators run as standard users until an application or system component that requires administrative credentials requests permission to run.</span></span>  
  
<a name="Tasks_Requiring_Higher_Privileges"></a>   
## <a name="tasks-requiring-higher-privileges"></a><span data-ttu-id="7b7df-112">Daha yüksek ayrıcalıklar gerektiren görevler</span><span class="sxs-lookup"><span data-stu-id="7b7df-112">Tasks Requiring Higher Privileges</span></span>  
 <span data-ttu-id="7b7df-113">Bir kullanıcının yönetici ayrıcalıkları gerektiren bir görevi gerçekleştirmek çalıştığında [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] kullanıcı devam etmek onay için soran bir iletişim kutusu gösterir.</span><span class="sxs-lookup"><span data-stu-id="7b7df-113">When a user attempts to perform a task that requires administrative privileges, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] presents a dialog box asking the user for consent to continue.</span></span> <span data-ttu-id="7b7df-114">Bu iletişim kutusunu işlem içi iletişimi, korumalı kötü amaçlı yazılımları kullanıcı girişi benzetimi yapamaz için.</span><span class="sxs-lookup"><span data-stu-id="7b7df-114">This dialog box is protected from cross-process communication, so that malicious software cannot simulate user input.</span></span> <span data-ttu-id="7b7df-115">Benzer şekilde, masaüstü oturum açma ekranı normalde başka işlemler tarafından erişilemez.</span><span class="sxs-lookup"><span data-stu-id="7b7df-115">Similarly, the desktop logon screen cannot normally be accessed by other processes.</span></span>  
  
 <span data-ttu-id="7b7df-116">UI Otomasyon istemcileri diğer işlemler, bazıları daha yüksek bir ayrıcalık düzeyinde belki de çalıştıran ile iletişim kurması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7b7df-116">UI Automation clients must communicate with other processes, some of them perhaps running at a higher privilege level.</span></span> <span data-ttu-id="7b7df-117">İstemciler ayrıca diğer işlemler için normal olarak görünmez sistem iletişim kutuları erişimi gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="7b7df-117">Clients also might need access to the system dialog boxes that are not normally visible to other processes.</span></span> <span data-ttu-id="7b7df-118">Bu nedenle, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] istemciler sistem tarafından güvenilir olması gerekir ve özel ayrıcalıklarıyla çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7b7df-118">Therefore, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] clients must be trusted by the system, and must run with special privileges.</span></span>  
  
 <span data-ttu-id="7b7df-119">Daha yüksek bir ayrıcalık düzeyinde çalışan uygulamalarla iletişim kurmak için güvenilecek şekilde uygulamaların yeniden imzalanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7b7df-119">To be trusted to communicate with applications running at a higher privilege level, applications must be signed.</span></span>  
  
<a name="Manifest_Files"></a>   
## <a name="manifest-files"></a><span data-ttu-id="7b7df-120">Dosyaları bildirimi</span><span class="sxs-lookup"><span data-stu-id="7b7df-120">Manifest Files</span></span>  
 <span data-ttu-id="7b7df-121">Korumalı sistem erişmek için [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], uygulamaları yerleşik, bildirim dosyasında özel bir öznitelik içeren bir bildirim dosyası ile.</span><span class="sxs-lookup"><span data-stu-id="7b7df-121">To gain access to the protected system [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], applications must be built with a manifest file that includes a special attribute in the manifest file.</span></span> <span data-ttu-id="7b7df-122">Bu `uiAccess` özniteliği dahil `requestedExecutionLevel` etiketi, aşağıdaki gibi:</span><span class="sxs-lookup"><span data-stu-id="7b7df-122">This `uiAccess` attribute is included in the `requestedExecutionLevel` tag, as follows:</span></span>  
  
 `<trustInfo xmlns="urn:0073chemas-microsoft-com:asm.v3">`  
  
 `<security>`  
  
 `<requestedPrivileges>`  
  
 `<requestedExecutionLevel`  
  
 `level="highestAvailable"`  
  
 `UIAccess="true" />`  
  
 `</requestedPrivileges>`  
  
 `</security>`  
  
 `</trustInfo>`  
  
 <span data-ttu-id="7b7df-123">Değeri `level` özniteliği bu kodda yalnızca bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7b7df-123">The value of the `level` attribute in this code is an example only.</span></span>  
  
 <span data-ttu-id="7b7df-124">`UIAccess`Varsayılan olarak; "false" diğer bir deyişle, öznitelik atlanırsa veya derleme için hiçbir bildirim ise, uygulama korumalı erişim kazanmak mümkün olmaz [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7b7df-124">`UIAccess` is "false" by default; that is, if the attribute is omitted, or if there is no manifest for the assembly, the application will not be able to gain access to protected [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].</span></span>  
  
 <span data-ttu-id="7b7df-125">Daha fazla bilgi için [!INCLUDE[TLA#tla_longhorn2](../../../includes/tlasharptla-longhorn2-md.md)] güvenlik, uygulamaları imzalamak ve derleme bildirimlerinin oluşturma gördüğünüz "Developer en iyi yöntemler ve yönergeleri için uygulama içinde bir en az ayrıcalıklı ortamında" [MSDN](http://msdn.microsoft.com/library/default.asp?url=/library/dnlong/html/AccProtVista.asp).</span><span class="sxs-lookup"><span data-stu-id="7b7df-125">For more information on [!INCLUDE[TLA#tla_longhorn2](../../../includes/tlasharptla-longhorn2-md.md)] security, on signing applications, and on creating assembly manifests, see "Developer Best Practices and Guidelines for Applications in a Least Privileged Environment" on  [MSDN](http://msdn.microsoft.com/library/default.asp?url=/library/dnlong/html/AccProtVista.asp).</span></span>
