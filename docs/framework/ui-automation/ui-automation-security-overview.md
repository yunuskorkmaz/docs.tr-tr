---
title: UI Otomasyon Güvenliğine Genel Bakış
description: Microsoft UI Otomasyonu için güvenlik modeline genel bakış konusunu okuyun. Kullanıcı hesabı denetimini, daha fazla ayrıcalık gerektiren görevleri ve bildirim dosyalarını anlayın.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, security model
- security model, UI Automation
ms.assetid: 1d853695-973c-48ae-b382-4132ae702805
ms.openlocfilehash: d483f282db8ce8e5653d6d83361fa44df05f63f5
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163149"
---
# <a name="ui-automation-security-overview"></a><span data-ttu-id="563ed-104">UI Otomasyon Güvenliğine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="563ed-104">UI Automation Security Overview</span></span>

> [!NOTE]
> <span data-ttu-id="563ed-105">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="563ed-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="563ed-106">Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="563ed-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>

<span data-ttu-id="563ed-107">Bu genel bakışta, Windows Vista 'da için güvenlik modeli açıklanır [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="563ed-107">This overview describes the security model for [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] in Windows Vista.</span></span>

<a name="User_Account_Control"></a>

## <a name="user-account-control"></a><span data-ttu-id="563ed-108">Kullanıcı Hesabı Denetimi</span><span class="sxs-lookup"><span data-stu-id="563ed-108">User Account Control</span></span>

<span data-ttu-id="563ed-109">Güvenlik, Windows Vista 'nın önemli bir odağında ve yeniliklerin arasında, kullanıcıların daha yüksek ayrıcalıklar gerektiren uygulama ve Hizmetleri çalıştırmanın engellenmesi gerekmeden standart (yönetici olmayan) kullanıcılar olarak çalıştırılmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="563ed-109">Security is a major focus of Windows Vista and among the innovations is the ability for users to run as standard (non-administrator) users without necessarily being blocked from running applications and services that require higher privileges.</span></span>

<span data-ttu-id="563ed-110">Windows Vista 'da çoğu uygulama, standart ya da bir yönetim belirteciyle sağlanır.</span><span class="sxs-lookup"><span data-stu-id="563ed-110">In Windows Vista, most applications are supplied with either a standard or an administrative token.</span></span> <span data-ttu-id="563ed-111">Bir uygulama bir yönetim uygulaması olarak tanımlanamıyorsa, varsayılan olarak standart bir uygulama olarak başlatılır.</span><span class="sxs-lookup"><span data-stu-id="563ed-111">If an application cannot be identified as an administrative application, it is launched as a standard application by default.</span></span> <span data-ttu-id="563ed-112">Yönetim olarak tanımlanan bir uygulama başlatılabilip, Windows Vista kullanıcıdan uygulamayı yükseltilmiş olarak çalıştırmasını ister.</span><span class="sxs-lookup"><span data-stu-id="563ed-112">Before an application identified as administrative can be launched, Windows Vista prompts the user for consent to run the application as elevated.</span></span> <span data-ttu-id="563ed-113">Kullanıcı yerel Administrators grubunun üyesi olsa bile, izin istemi varsayılan olarak görüntülenir, çünkü Yöneticiler, yönetici kimlik bilgileri isteyen bir uygulama veya sistem bileşeni için izin istemek için gerekli olan bir uygulama veya sistem bileşenine kadar standart kullanıcılar olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="563ed-113">The consent prompt is displayed by default, even if the user is a member of the local Administrators group, because administrators run as standard users until an application or system component that requires administrative credentials requests permission to run.</span></span>

<a name="Tasks_Requiring_Higher_Privileges"></a>

## <a name="tasks-requiring-higher-privileges"></a><span data-ttu-id="563ed-114">Daha yüksek ayrıcalıklar gerektiren görevler</span><span class="sxs-lookup"><span data-stu-id="563ed-114">Tasks Requiring Higher Privileges</span></span>

<span data-ttu-id="563ed-115">Bir Kullanıcı, yönetici ayrıcalıkları gerektiren bir görev gerçekleştirmeye çalıştığında, Windows Vista kullanıcıdan onay vermesini isteyen bir iletişim kutusu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="563ed-115">When a user attempts to perform a task that requires administrative privileges, Windows Vista presents a dialog box asking the user for consent to continue.</span></span> <span data-ttu-id="563ed-116">Bu iletişim kutusu, işlemler arası iletişimden korunur, böylece kötü amaçlı yazılımlar Kullanıcı girişinin benzetimini yapamaz.</span><span class="sxs-lookup"><span data-stu-id="563ed-116">This dialog box is protected from cross-process communication, so that malicious software cannot simulate user input.</span></span> <span data-ttu-id="563ed-117">Benzer şekilde, masaüstü oturum açma ekranına normalde başka süreçler tarafından erişilemez.</span><span class="sxs-lookup"><span data-stu-id="563ed-117">Similarly, the desktop logon screen cannot normally be accessed by other processes.</span></span>

<span data-ttu-id="563ed-118">UI Otomasyonu istemcilerinin bazıları büyük olasılıkla daha yüksek bir ayrıcalık düzeyinde çalışan diğer işlemlerle iletişim kurması gerekir.</span><span class="sxs-lookup"><span data-stu-id="563ed-118">UI Automation clients must communicate with other processes, some of them perhaps running at a higher privilege level.</span></span> <span data-ttu-id="563ed-119">Ayrıca istemciler, normal olarak diğer işlemlere görünmeyen sistem iletişim kutularına erişim gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="563ed-119">Clients also might need access to the system dialog boxes that are not normally visible to other processes.</span></span> <span data-ttu-id="563ed-120">Bu nedenle, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] istemcilere sistem tarafından güvenilmesi ve özel ayrıcalıklarla çalıştırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="563ed-120">Therefore, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] clients must be trusted by the system, and must run with special privileges.</span></span>

<span data-ttu-id="563ed-121">Daha yüksek bir ayrıcalık düzeyinde çalışan uygulamalarla iletişim kurmak için güvenilecek uygulamalar imzalanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="563ed-121">To be trusted to communicate with applications running at a higher privilege level, applications must be signed.</span></span>

<a name="Manifest_Files"></a>

## <a name="manifest-files"></a><span data-ttu-id="563ed-122">Bildirim dosyaları</span><span class="sxs-lookup"><span data-stu-id="563ed-122">Manifest Files</span></span>

<span data-ttu-id="563ed-123">Korunan sistem kullanıcı arabirimine erişim kazanmak için, uygulamalar `uiAccess` aşağıdaki gibi etiketteki özniteliğini içeren bir bildirim dosyası ile oluşturulmalıdır `requestedExecutionLevel` :</span><span class="sxs-lookup"><span data-stu-id="563ed-123">To gain access to the protected system UI, applications must be built with a manifest file that includes the `uiAccess` attribute in the `requestedExecutionLevel` tag, as follows:</span></span>

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

<span data-ttu-id="563ed-124">`level`Bu koddaki özniteliğin değeri yalnızca bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="563ed-124">The value of the `level` attribute in this code is an example only.</span></span>

<span data-ttu-id="563ed-125">`uiAccess`Varsayılan olarak "false" değeridir; diğer bir deyişle, özniteliği atlanırsa veya derleme için bildirim yoksa, uygulama korumalı Kullanıcı arabirimine erişim elde edemeyecektir.</span><span class="sxs-lookup"><span data-stu-id="563ed-125">`uiAccess` is "false" by default; that is, if the attribute is omitted, or if there is no manifest for the assembly, the application will not be able to gain access to protected UI.</span></span>
