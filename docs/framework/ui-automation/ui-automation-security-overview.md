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
# <a name="ui-automation-security-overview"></a>UI Otomasyon Güvenliğine Genel Bakış

> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).

Bu genel bakışta, Windows Vista 'da için güvenlik modeli açıklanır [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] .

<a name="User_Account_Control"></a>

## <a name="user-account-control"></a>Kullanıcı Hesabı Denetimi

Güvenlik, Windows Vista 'nın önemli bir odağında ve yeniliklerin arasında, kullanıcıların daha yüksek ayrıcalıklar gerektiren uygulama ve Hizmetleri çalıştırmanın engellenmesi gerekmeden standart (yönetici olmayan) kullanıcılar olarak çalıştırılmasına olanak tanır.

Windows Vista 'da çoğu uygulama, standart ya da bir yönetim belirteciyle sağlanır. Bir uygulama bir yönetim uygulaması olarak tanımlanamıyorsa, varsayılan olarak standart bir uygulama olarak başlatılır. Yönetim olarak tanımlanan bir uygulama başlatılabilip, Windows Vista kullanıcıdan uygulamayı yükseltilmiş olarak çalıştırmasını ister. Kullanıcı yerel Administrators grubunun üyesi olsa bile, izin istemi varsayılan olarak görüntülenir, çünkü Yöneticiler, yönetici kimlik bilgileri isteyen bir uygulama veya sistem bileşeni için izin istemek için gerekli olan bir uygulama veya sistem bileşenine kadar standart kullanıcılar olarak çalışır.

<a name="Tasks_Requiring_Higher_Privileges"></a>

## <a name="tasks-requiring-higher-privileges"></a>Daha yüksek ayrıcalıklar gerektiren görevler

Bir Kullanıcı, yönetici ayrıcalıkları gerektiren bir görev gerçekleştirmeye çalıştığında, Windows Vista kullanıcıdan onay vermesini isteyen bir iletişim kutusu görüntüler. Bu iletişim kutusu, işlemler arası iletişimden korunur, böylece kötü amaçlı yazılımlar Kullanıcı girişinin benzetimini yapamaz. Benzer şekilde, masaüstü oturum açma ekranına normalde başka süreçler tarafından erişilemez.

UI Otomasyonu istemcilerinin bazıları büyük olasılıkla daha yüksek bir ayrıcalık düzeyinde çalışan diğer işlemlerle iletişim kurması gerekir. Ayrıca istemciler, normal olarak diğer işlemlere görünmeyen sistem iletişim kutularına erişim gerektirebilir. Bu nedenle, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] istemcilere sistem tarafından güvenilmesi ve özel ayrıcalıklarla çalıştırılması gerekir.

Daha yüksek bir ayrıcalık düzeyinde çalışan uygulamalarla iletişim kurmak için güvenilecek uygulamalar imzalanmalıdır.

<a name="Manifest_Files"></a>

## <a name="manifest-files"></a>Bildirim dosyaları

Korunan sistem kullanıcı arabirimine erişim kazanmak için, uygulamalar `uiAccess` aşağıdaki gibi etiketteki özniteliğini içeren bir bildirim dosyası ile oluşturulmalıdır `requestedExecutionLevel` :

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

`level`Bu koddaki özniteliğin değeri yalnızca bir örnektir.

`uiAccess`Varsayılan olarak "false" değeridir; diğer bir deyişle, özniteliği atlanırsa veya derleme için bildirim yoksa, uygulama korumalı Kullanıcı arabirimine erişim elde edemeyecektir.
