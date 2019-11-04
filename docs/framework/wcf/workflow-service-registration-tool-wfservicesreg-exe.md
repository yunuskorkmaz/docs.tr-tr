---
title: WorkFlow Hizmet Kayıt Aracı (WFServicesReg.exe)
ms.date: 03/30/2017
ms.assetid: 9e92c87b-99c5-4e8d-9d53-7944cc2b47d3
ms.openlocfilehash: bb0989fb8747a5065ce3d7332311cdefba95b80d
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425296"
---
# <a name="workflow-service-registration-tool-wfservicesregexe"></a>WorkFlow Hizmet Kayıt Aracı (WFServicesReg.exe)
Workflow Services kayıt aracı (WFServicesReg. exe), Windows Workflow Foundation (WF) Hizmetleri için yapılandırma öğelerini eklemek, kaldırmak veya onarmak üzere kullanılabilecek tek başına bir araçtır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
WFServicesReg.exe [-c | -r | -v | -m | -i]  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Araç, [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] yükleme konumunda, özellikle,%windir%\Microsoft.NET\Framework\v3.5 veya 64 bitlik makinelerde bulunan%windir%\Microsoft.NET\Framework64\v3.5 adresinde bulunabilir.  
  
 Aşağıdaki tablolar, Iş akışı hizmetleri kayıt aracı (WFServicesReg. exe) ile kullanılabilen seçenekleri anlatmaktadır.  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|`/c`|Windows Workflow hizmetlerini yapılandırır. Install ve Repair senaryolarında kullanılır.|  
|`/r`|Windows Workflow Services yapılandırmasını kaldırır.|  
|`/v`|Ayrıntılı bilgileri yazdır (yapılandırma veya kaldırma için).|  
|`/m`|MSI günlük biçimini etkinleştir.|  
|`/i`|Uygulama çalıştığında pencereyi en aza indirir.|  
  
## <a name="registration"></a>Kayıt  
 Araç, Web. config dosyasını inceler ve aşağıdakileri kaydeder:  
  
- başvuru derlemelerini [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)].  
  
- . Xoml dosyaları için derleme sağlayıcısı.  
  
- . Xoml ve. Rules dosyaları için HTTP işleyicileri.  
  
 Araç, Machine. config dosyasını inceler ve aşağıdaki uzantıları kaydeder:  
  
- behaviorExtensions  
  
- bindingElementExtensions  
  
- bindingExtensions  
  
 Araç ayrıca aşağıdaki istemci meta veri içe aktarımlarını kaydeder:  
  
- policyImporters  
  
- wsdlImporters  
  
 Araç ayrıca. xoml ve. Rules komut dosyası eşleştirmelerini ve işleyicileri IIS metatabanında kaydeder.  
  
 [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../includes/wxp-md.md)] makinelerde (IIS 5,1 ve IIS 6,0), bir. xoml ve. Rules komut dosyası kümesinin bir kümesi kaydedilir.  
  
 64 bitlik makinelerde araç, `Enable32BitAppOnWin64` anahtarı etkinse WOW modu komut dosyası eşleştirmelerini veya `Enable32BitAppOnWin64` anahtarı devre dışıysa yerel 64 bit komut dosyası eşleştirmelerini kaydeder.  
  
 [!INCLUDE[wv](../../../includes/wv-md.md)] ve Windows Server 2008 (IIS 7,0 ve üzeri) makinelerinde, iki. xoml ve. Rules işleyicisi kümesi kaydedilir: biri tümleşik mod ve bir klasik mod için.  
  
 64 bit makinelerde, üç işleyici kümesi (`Enable32BitAppOnWin64` anahtarın durumundan bağımsız olarak) kaydedilir: bir adet, bir tane, WOW klasik mod ve diğeri yerel 64 bit klasik mod için bir adet tümleşik mod için.  
  
> [!NOTE]
> ServiceModelreg. exe ' den farklı olarak, WFServicesReg. exe ' nin belirli bir Web sitesi için komut dosyası veya işleyicileri ekleme, kaldırma veya onarma izni yoktur. Bu soruna geçici bir çözüm için, "komut dosyası eşleştirmelerini onarma" bölümüne bakın.  
  
## <a name="usage-scenarios"></a>Kullanım senaryoları  
  
### <a name="installing-iis-after-net-framework-35-is-installed"></a>.NET Framework 3,5 yüklendikten sonra IIS yükleme  
 [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] bir makinede, [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] IIS yüklemesinden önce yüklenir. IIS metatabanının KULLANILAMAMASINDAN dolayı, [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] yüklemesi. xoml ve. Rules komut dosyası yüklemeleri olmadan başarılı olur.  
  
 IIS yüklendikten sonra, bu özel komut dosyası eşleştirmelerini yüklemek için `/c` anahtarıyla WFServicesReg. exe aracını kullanabilirsiniz.  
  
### <a name="repairing-the-scriptmaps"></a>Kod haritalarını onarma  
  
#### <a name="scriptmap-deleted-under-web-sites-node"></a>ScriptMap Web siteleri düğümü altında silindi  
 Bir [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] makinesinde. xoml veya. Rules, yanlışlıkla Web siteleri düğümünden silinir. Bu, WFServicesReg. exe aracı `/c` anahtarıyla çalıştırılarak onarılabilir.  
  
#### <a name="scriptmap-deleted-under-a-particular-web-site"></a>ScriptMap belirli bir Web sitesi altında silindi  
 Bir [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] makinesinde. xoml veya. Rules, Web siteleri düğümünden değil, belirli bir Web sitesinden (örneğin, varsayılan Web sitesi) yanlışlıkla silinir.  
  
 Belirli bir Web sitesi için silinen işleyicileri onarmak üzere, tüm Web sitelerinden işleyicileri kaldırmak için "WFServicesReg. exe/r" komutunu çalıştırmanız ve sonra tüm Web siteleri için uygun işleyicileri oluşturmak üzere "WFServicesReg. exe/c" komutunu çalıştırmanız gerekir.  
  
### <a name="configuring-handlers-after-switching-iis-mode"></a>IIS moduna geçtikten sonra işleyicileri yapılandırma  
 IIS paylaşılan yapılandırma modundayken ve [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] yüklüyse, IIS metatabanı paylaşılan bir konum altında yapılandırılır. IIS 'yi paylaşılmayan yapılandırma moduna geçerseniz, yerel metatabanı gerekli işleyicileri içermez. Yerel metatabanını doğru şekilde yapılandırmak için, paylaşılan metatabanını yerel olarak içeri aktarabilir ya da yerel metatabanını yapılandıran "WFServicesReg. exe/c" komutunu çalıştırabilirsiniz.
