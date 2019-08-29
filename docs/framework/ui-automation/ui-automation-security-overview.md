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
# <a name="ui-automation-security-overview"></a>UI Otomasyon Güvenliğine Genel Bakış

> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).

Bu genel bakış, içindeki [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)]için güvenlik modelini açıklar.

<a name="User_Account_Control"></a>

## <a name="user-account-control"></a>Kullanıcı Hesabı Denetimi

Güvenlik, önemli bir odadır [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] ve yenilikler arasında, kullanıcıların daha yüksek ayrıcalıklar gerektiren uygulama ve Hizmetleri çalıştırmanın engellenmesi gerekmeden standart (yönetici olmayan) kullanıcılar olarak çalıştırılmasına olanak tanır.

' [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)]De, çoğu uygulama standart ya da yönetim belirteci ile sağlanır. Bir uygulama bir yönetim uygulaması olarak tanımlanamıyorsa, varsayılan olarak standart bir uygulama olarak başlatılır. Yönetim olarak tanımlanan bir uygulama başlatılabilmediği [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] için kullanıcıdan uygulamayı yükseltilmiş olarak çalıştırmasını ister. Kullanıcı yerel Administrators grubunun üyesi olsa bile, izin istemi varsayılan olarak görüntülenir, çünkü Yöneticiler, yönetici kimlik bilgileri isteyen bir uygulama veya sistem bileşeni için izin istemek için gerekli olan bir uygulama veya sistem bileşenine kadar standart kullanıcılar olarak çalışır.

<a name="Tasks_Requiring_Higher_Privileges"></a>

## <a name="tasks-requiring-higher-privileges"></a>Daha yüksek ayrıcalıklar gerektiren görevler

Bir Kullanıcı, yönetici ayrıcalıkları gerektiren bir görev gerçekleştirmeye çalıştığında, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] kullanıcıdan onay vermesini isteyen bir iletişim kutusu görüntüler. Bu iletişim kutusu, işlemler arası iletişimden korunur, böylece kötü amaçlı yazılımlar Kullanıcı girişinin benzetimini yapamaz. Benzer şekilde, masaüstü oturum açma ekranına normalde başka süreçler tarafından erişilemez.

UI Otomasyonu istemcilerinin bazıları büyük olasılıkla daha yüksek bir ayrıcalık düzeyinde çalışan diğer işlemlerle iletişim kurması gerekir. Ayrıca istemciler, normal olarak diğer işlemlere görünmeyen sistem iletişim kutularına erişim gerektirebilir. Bu nedenle [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , istemcilere sistem tarafından güvenilmesi ve özel ayrıcalıklarla çalıştırılması gerekir.

Daha yüksek bir ayrıcalık düzeyinde çalışan uygulamalarla iletişim kurmak için güvenilecek uygulamalar imzalanmalıdır.

<a name="Manifest_Files"></a>

## <a name="manifest-files"></a>Bildirim dosyaları

Korunan sistem kullanıcı arabirimine erişim kazanmak için, uygulamalar aşağıdaki gibi `uiAccess` `requestedExecutionLevel` etiketteki özniteliğini içeren bir bildirim dosyası ile oluşturulmalıdır:

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

Bu koddaki `level` özniteliğin değeri yalnızca bir örnektir.

`uiAccess`Varsayılan olarak "false" değeridir; diğer bir deyişle, özniteliği atlanırsa veya derleme için bildirim yoksa, uygulama korumalı Kullanıcı arabirimine erişim elde edemeyecektir.
