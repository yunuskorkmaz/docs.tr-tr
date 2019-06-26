---
title: WorkFlow Hizmet Kayıt Aracı (WFServicesReg.exe)
ms.date: 03/30/2017
ms.assetid: 9e92c87b-99c5-4e8d-9d53-7944cc2b47d3
ms.openlocfilehash: 211af75c04dfe971228bc1710fbe1fc4d7aaee60
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67402477"
---
# <a name="workflow-service-registration-tool-wfservicesregexe"></a>WorkFlow Hizmet Kayıt Aracı (WFServicesReg.exe)
Workflow hizmet Kayıt Aracı (WFServicesReg.exe) eklemek, kaldırmak veya Windows Workflow Foundation (WF) Hizmetleri için yapılandırma öğeleri onarmak için kullanılan bağımsız bir araçtır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
WFServicesReg.exe [-c | -r | -v | -m | -i]  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Araç şu yolda bulunabilir: [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] yükleme konumu, özellikle de % windir%\Microsoft.NET\Framework\v3.5 veya 64 bit makinelerde %windir%\Microsoft.NET\Framework64\v3.5.  
  
 Aşağıdaki tablolarda, iş akışı hizmetleri kayıt aracı (WFServicesReg.exe) kullanılabilir seçenekler açıklanmaktadır.  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|`/c`|Windows iş akışı hizmetleri yapılandırır. Yüklemede kullanılan ve onarım senaryoları.|  
|`/r`|Windows iş akışı Hizmetleri yapılandırmasını kaldırır.|  
|`/v`|Ayrıntılı bilgi (yapılandırma veya temizleme) yazdırın.|  
|`/m`|MSI günlük biçimini sağlar.|  
|`/i`|Uygulama çalışırken pencerenin en aza indirir.|  
  
## <a name="registration"></a>Kayıt  
 Araç, Web.config dosyasını inceler ve aşağıdaki kaydeder:  
  
- [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] başvuru bütünleştirilmiş kodları.  
  
- Bir oluşturma sağlayıcısını .xoml dosyaları.  
  
- HTTP işleyicileri .xoml ve .rules dosyaları.  
  
 Aracı Machine.config dosyasının inceler ve aşağıdaki uzantılar kaydeder:  
  
- behaviorExtensions  
  
- bindingElementExtensions  
  
- bindingExtensions  
  
 Araç ayrıca aşağıdaki istemci meta verileri ımporters kaydeder:  
  
- policyImporters  
  
- wsdlImporters  
  
 Aracı, IIS metabase içinde .xoml ve .rules kod haritalarını ve işleyicileri de kaydeder.  
  
 Üzerinde [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../includes/wxp-md.md)] makineler .xoml ve .rules kod haritalarını (IIS 5.1 ve IIS 6.0), bir dizi kayıtlı.  
  
 64 bit makinelerde ise araç WOW modunda kod haritalarını kaydeder `Enable32BitAppOnWin64` anahtar etkin veya yerel 64 bit kod haritalarını olup olmadığını `Enable32BitAppOnWin64` anahtarını devre dışı bırakıldı.  
  
 Üzerinde [!INCLUDE[wv](../../../includes/wv-md.md)] ve Windows Server 2008 (IIS 7.0 ve üstü) makineleri iki .xoml ve .rules işleyicileri kayıtlı: biri tümleşik modu, diğeri Klasik mod için.  
  
 64 bit makinelerde işleyicileri üç adet kaydedilir (durumundan bağımsız olarak `Enable32BitAppOnWin64` geçiş): bir tümleşik modu, WOW Klasik mod için ve yerel 64 bit Klasik mod için bir tane.  
  
> [!NOTE]
>  ServiceModelreg.exe WFServicesReg.exe ekleme, kaldırma veya kod haritalarını veya belirli bir Web sitesi için işleyiciler onarma izin vermez. Bu soruna bir geçici çözüm için "Kod haritalarını onarma" bölümüne bakın.  
  
## <a name="usage-scenarios"></a>Kullanım senaryoları  
  
### <a name="installing-iis-after-net-framework-35-is-installed"></a>.NET Framework 3.5 yüklendikten sonra IIS yükleme  
 Üzerinde bir [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] makine [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] IIS yüklemeden önce yüklenir. IIS metatabanı yüklenmesini olmadığından [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] .xoml ve .rules kod haritalarını yüklemeden başarılı olur.  
  
 IIS yüklendikten sonra WFServicesReg.exe aracı ile kullanabileceğiniz `/c` bu belirli kod haritalarını yüklemek için anahtar.  
  
### <a name="repairing-the-scriptmaps"></a>Kod haritalarını onarılıyor  
  
#### <a name="scriptmap-deleted-under-web-sites-node"></a>Komut dosyası eşlemesini Web siteleri düğümü altında silindi  
 Üzerinde bir [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] makine, .xoml veya .rules Web siteleri düğümünden silinmiş yanlışlıkla. Bu WFServicesReg.exe aracıyla çalıştırarak onarılabilir `/c` geçin.  
  
#### <a name="scriptmap-deleted-under-a-particular-web-site"></a>Komut dosyası eşlemesini altında belirli bir Web sitesi silindi  
 Üzerinde bir [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] makine, .xoml veya .rules yanlışlıkla silindiğinde belirli bir Web sitesi (örneğin, varsayılan Web sitesi) yerine Web siteleri düğümü.  
  
 Belirli bir Web sitesi için silinen işleyicileri onarmak için "WFServicesReg.exe r" çalıştırmalısınız tüm Web sitelerinden işleyicilerini kaldırmak için ardından "WFServicesReg.exe c" çalıştırın uygun işleyicileri için tüm Web siteleri oluşturmak için.  
  
### <a name="configuring-handlers-after-switching-iis-mode"></a>IIS moduna geçtikten sonra işleyicileri yapılandırma  
 IIS paylaşılan Yapılandırması modunda olduğunda ve [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] olan yüklü IIS metabase bir paylaşılan konuma altında yapılandırılır. IIS yapılandırma paylaşılmayan moduna geçiş yapıyorsanız, yerel gerekli işleyicileri içermez. Yerel düzgün şekilde yapılandırmak için "yerel yapılandıran yerel ya da çalışma WFServicesReg.exe /c", paylaşılan metatabanına ya da içeri aktarabilirsiniz.
