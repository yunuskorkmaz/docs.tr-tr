---
title: UI Otomasyon Güvenliğine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, security model
- security model, UI Automation
ms.assetid: 1d853695-973c-48ae-b382-4132ae702805
ms.openlocfilehash: 8b798aef528cccdedb1fcaa53c1782632037600d
ms.sourcegitcommit: 77e33b682db39955e331b8e8eda4ef1925a24e78
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/29/2019
ms.locfileid: "70133782"
---
# <a name="ui-automation-security-overview"></a><span data-ttu-id="1cce2-102">UI Otomasyon Güvenliğine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1cce2-102">UI Automation Security Overview</span></span>

> [!NOTE]
> <span data-ttu-id="1cce2-103">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="1cce2-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="1cce2-104">Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="1cce2-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>

<span data-ttu-id="1cce2-105">Bu genel bakış, içindeki [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)]için güvenlik modelini açıklar.</span><span class="sxs-lookup"><span data-stu-id="1cce2-105">This overview describes the security model for [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] in [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)].</span></span>

<a name="User_Account_Control"></a>

## <a name="user-account-control"></a><span data-ttu-id="1cce2-106">Kullanıcı Hesabı Denetimi</span><span class="sxs-lookup"><span data-stu-id="1cce2-106">User Account Control</span></span>

<span data-ttu-id="1cce2-107">Güvenlik, önemli bir odadır [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] ve yenilikler arasında, kullanıcıların daha yüksek ayrıcalıklar gerektiren uygulama ve Hizmetleri çalıştırmanın engellenmesi gerekmeden standart (yönetici olmayan) kullanıcılar olarak çalıştırılmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="1cce2-107">Security is a major focus of [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] and among the innovations is the ability for users to run as standard (non-administrator) users without necessarily being blocked from running applications and services that require higher privileges.</span></span>

<span data-ttu-id="1cce2-108">' [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)]De, çoğu uygulama standart ya da yönetim belirteci ile sağlanır.</span><span class="sxs-lookup"><span data-stu-id="1cce2-108">In [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)], most applications are supplied with either a standard or an administrative token.</span></span> <span data-ttu-id="1cce2-109">Bir uygulama bir yönetim uygulaması olarak tanımlanamıyorsa, varsayılan olarak standart bir uygulama olarak başlatılır.</span><span class="sxs-lookup"><span data-stu-id="1cce2-109">If an application cannot be identified as an administrative application, it is launched as a standard application by default.</span></span> <span data-ttu-id="1cce2-110">Yönetim olarak tanımlanan bir uygulama başlatılabilmediği [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] için kullanıcıdan uygulamayı yükseltilmiş olarak çalıştırmasını ister.</span><span class="sxs-lookup"><span data-stu-id="1cce2-110">Before an application identified as administrative can be launched, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] prompts the user for consent to run the application as elevated.</span></span> <span data-ttu-id="1cce2-111">Kullanıcı yerel Administrators grubunun üyesi olsa bile, izin istemi varsayılan olarak görüntülenir, çünkü Yöneticiler, yönetici kimlik bilgileri isteyen bir uygulama veya sistem bileşeni için izin istemek için gerekli olan bir uygulama veya sistem bileşenine kadar standart kullanıcılar olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="1cce2-111">The consent prompt is displayed by default, even if the user is a member of the local Administrators group, because administrators run as standard users until an application or system component that requires administrative credentials requests permission to run.</span></span>

<a name="Tasks_Requiring_Higher_Privileges"></a>

## <a name="tasks-requiring-higher-privileges"></a><span data-ttu-id="1cce2-112">Daha yüksek ayrıcalıklar gerektiren görevler</span><span class="sxs-lookup"><span data-stu-id="1cce2-112">Tasks Requiring Higher Privileges</span></span>

<span data-ttu-id="1cce2-113">Bir Kullanıcı, yönetici ayrıcalıkları gerektiren bir görev gerçekleştirmeye çalıştığında, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] kullanıcıdan onay vermesini isteyen bir iletişim kutusu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1cce2-113">When a user attempts to perform a task that requires administrative privileges, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] presents a dialog box asking the user for consent to continue.</span></span> <span data-ttu-id="1cce2-114">Bu iletişim kutusu, işlemler arası iletişimden korunur, böylece kötü amaçlı yazılımlar Kullanıcı girişinin benzetimini yapamaz.</span><span class="sxs-lookup"><span data-stu-id="1cce2-114">This dialog box is protected from cross-process communication, so that malicious software cannot simulate user input.</span></span> <span data-ttu-id="1cce2-115">Benzer şekilde, masaüstü oturum açma ekranına normalde başka süreçler tarafından erişilemez.</span><span class="sxs-lookup"><span data-stu-id="1cce2-115">Similarly, the desktop logon screen cannot normally be accessed by other processes.</span></span>

<span data-ttu-id="1cce2-116">UI Otomasyonu istemcilerinin bazıları büyük olasılıkla daha yüksek bir ayrıcalık düzeyinde çalışan diğer işlemlerle iletişim kurması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1cce2-116">UI Automation clients must communicate with other processes, some of them perhaps running at a higher privilege level.</span></span> <span data-ttu-id="1cce2-117">Ayrıca istemciler, normal olarak diğer işlemlere görünmeyen sistem iletişim kutularına erişim gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="1cce2-117">Clients also might need access to the system dialog boxes that are not normally visible to other processes.</span></span> <span data-ttu-id="1cce2-118">Bu nedenle [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , istemcilere sistem tarafından güvenilmesi ve özel ayrıcalıklarla çalıştırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1cce2-118">Therefore, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] clients must be trusted by the system, and must run with special privileges.</span></span>

<span data-ttu-id="1cce2-119">Daha yüksek bir ayrıcalık düzeyinde çalışan uygulamalarla iletişim kurmak için güvenilecek uygulamalar imzalanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1cce2-119">To be trusted to communicate with applications running at a higher privilege level, applications must be signed.</span></span>

<a name="Manifest_Files"></a>

## <a name="manifest-files"></a><span data-ttu-id="1cce2-120">Bildirim dosyaları</span><span class="sxs-lookup"><span data-stu-id="1cce2-120">Manifest Files</span></span>

<span data-ttu-id="1cce2-121">Korunan sistem kullanıcı arabirimine erişim kazanmak için, uygulamalar aşağıdaki gibi `uiAccess` `requestedExecutionLevel` etiketteki özniteliğini içeren bir bildirim dosyası ile oluşturulmalıdır:</span><span class="sxs-lookup"><span data-stu-id="1cce2-121">To gain access to the protected system UI, applications must be built with a manifest file that includes the `uiAccess` attribute in the `requestedExecutionLevel` tag, as follows:</span></span>

```xml
<trustInfo xmlns="urn:schemas-microsoft-com:asm.v3">
  <security>
    <requestedPrivileges>
      <requestedExecutionLevel
        level="highestAvailable"
        uiAccess="true" />
    </requestedPrivileges>
  </security>
</trustInfo>
```

<span data-ttu-id="1cce2-122">Bu koddaki `level` özniteliğin değeri yalnızca bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="1cce2-122">The value of the `level` attribute in this code is an example only.</span></span>

<span data-ttu-id="1cce2-123">`uiAccess`Varsayılan olarak "false" değeridir; diğer bir deyişle, özniteliği atlanırsa veya derleme için bildirim yoksa, uygulama korumalı Kullanıcı arabirimine erişim elde edemeyecektir.</span><span class="sxs-lookup"><span data-stu-id="1cce2-123">`uiAccess` is "false" by default; that is, if the attribute is omitted, or if there is no manifest for the assembly, the application will not be able to gain access to protected UI.</span></span>
