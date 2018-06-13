---
title: WorkFlow Hizmet Kayıt Aracı (WFServicesReg.exe)
ms.date: 03/30/2017
ms.assetid: 9e92c87b-99c5-4e8d-9d53-7944cc2b47d3
ms.openlocfilehash: 3ea0f737cc050ec3f918044e0e105a41011a3e25
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33506567"
---
# <a name="workflow-service-registration-tool-wfservicesregexe"></a>WorkFlow Hizmet Kayıt Aracı (WFServicesReg.exe)
İş akışı hizmetleri kayıt aracı (WFServicesReg.exe) eklemek, kaldırmak veya Windows Workflow Foundation (WF) Hizmetleri için yapılandırma öğeleri onarmak için kullanılan tek başına bir araçtır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
WFServicesReg.exe [-c | -r | -v | -m | -i]  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Aracı bulunabilir [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] yükleme konumu, özellikle, % windir%\Microsoft.NET\Framework\v3.5 veya 64-bit makinelerde %windir%\Microsoft.NET\Framework64\v3.5.  
  
 Aşağıdaki tablolarda, iş akışı hizmetleri kayıt aracı (WFServicesReg.exe) ile kullanılabilir seçenekleri açıklanmaktadır.  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|`/c`|Windows iş akışı hizmetleri yapılandırır. Yüklemek için kullanılan ve senaryoları onarın.|  
|`/r`|Windows iş akışı Hizmetleri yapılandırmasını kaldırır.|  
|`/v`|Yazdırma ayrıntılı bilgilerini (yapılandırma veya kaldırma).|  
|`/m`|MSI günlük biçimini sağlar.|  
|`/i`|Uygulamayı çalıştırdığında, pencerenin en aza indirir.|  
  
## <a name="registration"></a>Kayıt  
 Aracı Web.config dosyasını inceler ve aşağıdaki kaydeder:  
  
-   [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] başvuru derlemeleri.  
  
-   Derleme Sağlayıcısı .xoml dosyaları için.  
  
-   HTTP işleyicileri .xoml ve .rules dosyaları.  
  
 Aracı Machine.config dosyasının inceler ve aşağıdaki uzantılar kaydeder:  
  
-   behaviorExtensions  
  
-   bindingElementExtensions  
  
-   bindingExtensions  
  
 Araç ayrıca aşağıdaki istemci meta veri ımporters kaydeder:  
  
-   policyImporters  
  
-   wsdlImporters  
  
 Aracı, IIS metatabanı .xoml ve .rules kod haritalarını ve işleyicileri de kaydeder.  
  
 Üzerinde [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../includes/wxp-md.md)] makineler (IIS 5.1 ve [!INCLUDE[iis601](../../../includes/iis601-md.md)]), .xoml ayarlayın ve .rules kod haritalarını kayıtlı.  
  
 64-bit makinelerde aracı WOW modu kod haritalarını kaydeder `Enable32BitAppOnWin64` anahtarı ise etkin ya da yerel 64 bit kod haritalarını `Enable32BitAppOnWin64` anahtar devre dışıdır.  
  
 Üzerinde [!INCLUDE[wv](../../../includes/wv-md.md)] ve Windows Server 2008 (IIS 7.0 ve üstü) makineler, iki adet .xoml ve .rules işleyicileri kayıtlı: tümleşik mod, diğeri Klasik mod için.  
  
 64-bit makinelerde işleyicileri üç kümesi kaydedilir (durumu ne olursa olsun `Enable32BitAppOnWin64` geçiş): tümleşik mod, biri WOW Klasik mod için ve biri yerel 64 bit Klasik mod için bir tane.  
  
> [!NOTE]
>  ServiceModelreg.exe WFServicesReg.exe ekleme, kaldırma veya kod haritalarını veya belirli bir Web sitesi için işleyiciler onarma izin vermiyor. Bu sorun için bir geçici çözüm için "Kod haritalarını onarma" bölümüne bakın.  
  
## <a name="usage-scenarios"></a>Kullanım senaryoları  
  
### <a name="installing-iis-after-net-framework-35-is-installed"></a>.NET Framework 3.5 yüklendikten sonra IIS yükleme  
 Üzerinde bir [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] makine [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] IIS yükleme önce yüklenir. IIS metatabanı yüklenmesi kullanılamazlık nedeniyle [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] .xoml ve .rules kod haritalarını yüklemeden başarılı olur.  
  
 IIS yüklendikten sonra WFServicesReg.exe aracıyla kullanabilirsiniz `/c` bu belirli kod haritalarını yüklemek için anahtar.  
  
### <a name="repairing-the-scriptmaps"></a>Komut dosyası eşleştirmelerini onarma  
  
#### <a name="scriptmap-deleted-under-web-sites-node"></a>Komut dosyası eşlemesini Web siteleri düğümünde silindi  
 Üzerinde bir [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] makine, .xoml ya da .rules Web siteleri düğümden silinmiş yanlışlıkla. Bu WFServicesReg.exe aracıyla çalıştırarak onarılabilir `/c` geçin.  
  
#### <a name="scriptmap-deleted-under-a-particular-web-site"></a>Komut dosyası eşlemesini altında belirli bir Web sitesi silindi  
 Üzerinde bir [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] makine, .xoml ya da .rules yanlışlıkla silindiğinden belirli bir Web sitesinden (örneğin, varsayılan Web sitesi) yerine, Web siteleri düğümü.  
  
 Belirli bir Web sitesi için silinen işleyiciler onarmak için "WFServicesReg.exe r" çalışması gerektiğini işleyicileri tüm Web sitelerinden kaldırmak için ardından "WFServicesReg.exe c" çalıştırın uygun işleyicileri için tüm Web siteleri oluşturmak için.  
  
### <a name="configuring-handlers-after-switching-iis-mode"></a>IIS modu değiştirdikten sonra işleyicileri yapılandırma  
 IIS paylaşılan Yapılandırması modunda olduğunda ve [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] olan yüklü, IIS metatabanı paylaşılan bir konum altında yapılandırılır. IIS yapılandırma paylaşılmayan moduna geçiş yaparsanız yerel metatabanı gerekli işleyicileri içermez. Yerel metatabanı düzgün bir şekilde yapılandırmak için "yerel metatabanı yapılandıran yerel ya da çalışma WFServicesReg.exe /c", paylaşılan metabase ya da içeri aktarabilirsiniz.
