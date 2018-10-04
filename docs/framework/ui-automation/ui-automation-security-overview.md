---
title: UI Otomasyon Güvenliğine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, security model
- security model, UI Automation
ms.assetid: 1d853695-973c-48ae-b382-4132ae702805
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: b35014993f10c3a60c16f784e7dd11b9a20f4f4c
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48582141"
---
# <a name="ui-automation-security-overview"></a>UI Otomasyon Güvenliğine Genel Bakış
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu genel bakış için güvenlik modeli açıklanır [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] içinde [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)].  
  
<a name="User_Account_Control"></a>   
## <a name="user-account-control"></a>Kullanıcı Hesabı Denetimi  
 Security'dir önemli odak noktası, [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] ve yenilikleri arasında olması, daha yüksek ayrıcalıklar gerektiren uygulamalar ve hizmetler çalışmasını engellenme olmadan standart (yönetici olmayan) kullanıcı olarak çalıştırmak kullanıcılar için.  
  
 İçinde [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)], çoğu uygulama standart veya bir yönetim belirteci ile sağlanır. Bir uygulama yönetim uygulaması tanımlanamaz, varsayılan olarak standart bir uygulama olarak başlatılır. Bir uygulama gibi yönetici tanımlanan önce başlatılabilir, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] kullanıcıdan Uygulamayı yükseltilmiş çalıştırmak için bir onay ister. Bir uygulama veya yönetici kimlik bilgileri gerektiren sistem bileşeni çalıştırma izni isteklerini kadar Yöneticiler standart kullanıcı olarak çalıştığından, kullanıcı yerel Administrators grubunun üyesi olsa bile varsayılan olarak onay istemi görüntülenir.  
  
<a name="Tasks_Requiring_Higher_Privileges"></a>   
## <a name="tasks-requiring-higher-privileges"></a>Daha yüksek ayrıcalıklar gerektiren görevler  
 Bir kullanıcının yönetici ayrıcalıkları gerektiren bir görevi gerçekleştirmeye çalıştığında [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] kullanıcı devam etmek onay için soran bir iletişim kutusu sunar. Bu iletişim kutusunu, böylece kötü amaçlı yazılım, kullanıcı girişini benzetimi yapamaz çapraz işlem iletişiminden korunur. Benzer şekilde, masaüstü oturum açma ekranında normalde başka işlemler tarafından erişilemez.  
  
 UI Otomasyon istemcileri diğer işlemler, belki de daha yüksek bir ayrıcalık düzeyinde çalıştırmak bunlardan bazıları ile iletişim kurması gerekir. İstemciler ayrıca diğer işlemler için normal olarak görünür olmayan sistem iletişim kutularına erişim gerekebilir. Bu nedenle, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] istemciler sistem tarafından güvenilir ve özel ayrıcalıklarıyla çalıştırmanız gerekir.  
  
 Daha yüksek bir ayrıcalık düzeyinde çalışan uygulamalarla iletişim kurmak için güvenilecek şekilde uygulamaların yeniden imzalanması gerekir.  
  
<a name="Manifest_Files"></a>   
## <a name="manifest-files"></a>Bildirim dosyaları  
 Sonlanmakta erişim kazanmak için [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], uygulama yerleşik, bildirim dosyasında bir özel özniteliği içeren bir bildirim dosyası ile. Bu `uiAccess` özniteliği dahil `requestedExecutionLevel` , aşağıda gösterildiği gibi etiketleyin:  
  
 `<trustInfo xmlns="urn:0073chemas-microsoft-com:asm.v3">`  
  
 `<security>`  
  
 `<requestedPrivileges>`  
  
 `<requestedExecutionLevel`  
  
 `level="highestAvailable"`  
  
 `UIAccess="true" />`  
  
 `</requestedPrivileges>`  
  
 `</security>`  
  
 `</trustInfo>`  
  
 Değerini `level` bu kodu özniteliği, yalnızca bir örnek verilmiştir.  
  
 `UIAccess` "varsayılan olarak; false" diğer bir deyişle, öznitelik belirtilmezse veya derleme için hiçbir bildirim ise, uygulama koruma için erişim elde etmek mümkün olmayacaktır [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
 Daha fazla bilgi için [!INCLUDE[TLA#tla_longhorn2](../../../includes/tlasharptla-longhorn2-md.md)] güvenlik, uygulamaları imzalamak ve derleme bildirimleri oluşturma bakın "Geliştirici en iyi yöntemler ve yönergeleri için uygulamalar bir en az ayrıcalıklı ortam" [MSDN](https://msdn.microsoft.com/library/default.asp?url=/library/dnlong/html/AccProtVista.asp).
