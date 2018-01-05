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
# <a name="ui-automation-security-overview"></a>UI Otomasyon Güvenliğine Genel Bakış
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu genel bakış için güvenlik modeli açıklanır [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] içinde [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)].  
  
<a name="User_Account_Control"></a>   
## <a name="user-account-control"></a>Kullanıcı Hesabı Denetimi  
 Güvenliği, bir ana odağını [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] ve yenilik arasında mutlaka, daha yüksek ayrıcalık gerektiren uygulamalar ve hizmetler çalıştırılmasının engellenme olmadan standart (yönetici olmayan) kullanıcı olarak çalıştırmak kullanıcılara.  
  
 İçinde [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)], çoğu uygulamalar standart veya bir yönetici belirteci ile sağlanır. Bir uygulama yönetim uygulaması tanımlanamaz, varsayılan olarak standart bir uygulama olarak başlatılır. Bir uygulama gibi yönetici tanımlanan önce başlatılan [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] yükseltilmiş uygulamanın çalışmasına izin kullanıcıya sorar. Bir uygulama veya yönetici kimlik bilgileri gerektiren sistem bileşeni çalıştırma izni isteklerini kadar Yöneticiler standart kullanıcı olarak çalıştığından kullanıcı yerel Administrators grubunun bir üyesi olsa bile, onay istemi varsayılan olarak görüntülenir.  
  
<a name="Tasks_Requiring_Higher_Privileges"></a>   
## <a name="tasks-requiring-higher-privileges"></a>Daha yüksek ayrıcalıklar gerektiren görevler  
 Bir kullanıcının yönetici ayrıcalıkları gerektiren bir görevi gerçekleştirmek çalıştığında [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] kullanıcı devam etmek onay için soran bir iletişim kutusu gösterir. Bu iletişim kutusunu işlem içi iletişimi, korumalı kötü amaçlı yazılımları kullanıcı girişi benzetimi yapamaz için. Benzer şekilde, masaüstü oturum açma ekranı normalde başka işlemler tarafından erişilemez.  
  
 UI Otomasyon istemcileri diğer işlemler, bazıları daha yüksek bir ayrıcalık düzeyinde belki de çalıştıran ile iletişim kurması gerekir. İstemciler ayrıca diğer işlemler için normal olarak görünmez sistem iletişim kutuları erişimi gerekebilir. Bu nedenle, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] istemciler sistem tarafından güvenilir olması gerekir ve özel ayrıcalıklarıyla çalıştırmanız gerekir.  
  
 Daha yüksek bir ayrıcalık düzeyinde çalışan uygulamalarla iletişim kurmak için güvenilecek şekilde uygulamaların yeniden imzalanması gerekir.  
  
<a name="Manifest_Files"></a>   
## <a name="manifest-files"></a>Dosyaları bildirimi  
 Korumalı sistem erişmek için [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], uygulamaları yerleşik, bildirim dosyasında özel bir öznitelik içeren bir bildirim dosyası ile. Bu `uiAccess` özniteliği dahil `requestedExecutionLevel` etiketi, aşağıdaki gibi:  
  
 `<trustInfo xmlns="urn:0073chemas-microsoft-com:asm.v3">`  
  
 `<security>`  
  
 `<requestedPrivileges>`  
  
 `<requestedExecutionLevel`  
  
 `level="highestAvailable"`  
  
 `UIAccess="true" />`  
  
 `</requestedPrivileges>`  
  
 `</security>`  
  
 `</trustInfo>`  
  
 Değeri `level` özniteliği bu kodda yalnızca bir örnek verilmiştir.  
  
 `UIAccess`Varsayılan olarak; "false" diğer bir deyişle, öznitelik atlanırsa veya derleme için hiçbir bildirim ise, uygulama korumalı erişim kazanmak mümkün olmaz [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
 Daha fazla bilgi için [!INCLUDE[TLA#tla_longhorn2](../../../includes/tlasharptla-longhorn2-md.md)] güvenlik, uygulamaları imzalamak ve derleme bildirimlerinin oluşturma gördüğünüz "Developer en iyi yöntemler ve yönergeleri için uygulama içinde bir en az ayrıcalıklı ortamında" [MSDN](http://msdn.microsoft.com/library/default.asp?url=/library/dnlong/html/AccProtVista.asp).
