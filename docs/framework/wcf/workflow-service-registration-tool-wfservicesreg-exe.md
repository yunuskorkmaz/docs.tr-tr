---
title: WorkFlow Hizmet Kayıt Aracı (WFServicesReg.exe)
ms.date: 03/30/2017
ms.assetid: 9e92c87b-99c5-4e8d-9d53-7944cc2b47d3
ms.openlocfilehash: 5e7d39062a8ad016eebf949daa625a5ba7848328
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76921224"
---
# <a name="workflow-service-registration-tool-wfservicesregexe"></a>WorkFlow Hizmet Kayıt Aracı (WFServicesReg.exe)
Workflow Services kayıt aracı (WFServicesReg. exe), Windows Workflow Foundation (WF) Hizmetleri için yapılandırma öğelerini eklemek, kaldırmak veya onarmak üzere kullanılabilecek tek başına bir araçtır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
WFServicesReg.exe [-c | -r | -v | -m | -i]  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Araç .NET Framework 3,5 yükleme konumunda, özellikle,%windir%\Microsoft.NET\Framework\v3.5 veya 64 bit makinelerde bulunan%windir%\Microsoft.NET\Framework64\v3.5 adresinde bulunabilir.  
  
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
  
- .NET Framework 3,5 başvuru derlemeleri.  
  
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
  
 Windows Server 2003 ve Windows XP makinelerinde (IIS 5,1 ve IIS 6,0), bir. xoml ve. Rules komut dosyası, bir kümesi kaydedilir.  
  
 64 bitlik makinelerde araç, `Enable32BitAppOnWin64` anahtarı etkinse WOW modu komut dosyası eşleştirmelerini veya `Enable32BitAppOnWin64` anahtarı devre dışıysa yerel 64 bit komut dosyası eşleştirmelerini kaydeder.  
  
 Windows Vista ve Windows Server 2008 (IIS 7,0 ve üzeri) makinelerinde, iki. xoml ve. Rules işleyicisi kümesi kaydedilir: biri tümleşik mod ve bir klasik mod için.  
  
 64 bit makinelerde, üç işleyici kümesi (`Enable32BitAppOnWin64` anahtarın durumundan bağımsız olarak) kaydedilir: bir adet, bir tane, WOW klasik mod ve diğeri yerel 64 bit klasik mod için bir adet tümleşik mod için.  
  
> [!NOTE]
> ServiceModelreg. exe ' den farklı olarak, WFServicesReg. exe ' nin belirli bir Web sitesi için komut dosyası veya işleyicileri ekleme, kaldırma veya onarma izni yoktur. Bu soruna geçici bir çözüm için, "komut dosyası eşleştirmelerini onarma" bölümüne bakın.  
  
## <a name="usage-scenarios"></a>Kullanım senaryoları  
  
### <a name="installing-iis-after-net-framework-35-is-installed"></a>.NET Framework 3,5 yüklendikten sonra IIS yükleme  
 Windows Server 2003 makinesinde, IIS yüklemesinden önce .NET Framework 3,5 yüklenir. IIS metatabanının KULLANILAMAMASINDAN dolayı, .NET Framework 3,5 yüklemesi. xoml ve. Rules komut dosyası yüklemeleri olmadan başarılı olur.  
  
 IIS yüklendikten sonra, bu özel komut dosyası eşleştirmelerini yüklemek için `/c` anahtarıyla WFServicesReg. exe aracını kullanabilirsiniz.  
  
### <a name="repairing-the-scriptmaps"></a>Kod haritalarını onarma  
  
#### <a name="scriptmap-deleted-under-web-sites-node"></a>ScriptMap Web siteleri düğümü altında silindi  
 Bir Windows Server 2003 makinesinde,. xoml veya. Rules, yanlışlıkla Web siteleri düğümünden silinir. Bu, WFServicesReg. exe aracı `/c` anahtarıyla çalıştırılarak onarılabilir.  
  
#### <a name="scriptmap-deleted-under-a-particular-web-site"></a>ScriptMap belirli bir Web sitesi altında silindi  
 Bir Windows Server 2003 makinesinde,. xoml veya. Rules, Web siteleri düğümünden değil, belirli bir Web sitesinden (örneğin, varsayılan Web sitesi) yanlışlıkla silinir.  
  
 Belirli bir Web sitesi için silinen işleyicileri onarmak üzere, tüm Web sitelerinden işleyicileri kaldırmak için "WFServicesReg. exe/r" komutunu çalıştırmanız ve sonra tüm Web siteleri için uygun işleyicileri oluşturmak üzere "WFServicesReg. exe/c" komutunu çalıştırmanız gerekir.  
  
### <a name="configuring-handlers-after-switching-iis-mode"></a>IIS moduna geçtikten sonra işleyicileri yapılandırma  
 IIS paylaşılan yapılandırma modundayken ve 3,5 .NET Framework yüklüyse, IIS metatabanı paylaşılan bir konum altında yapılandırılır. IIS 'yi paylaşılmayan yapılandırma moduna geçerseniz, yerel metatabanı gerekli işleyicileri içermez. Yerel metatabanını doğru şekilde yapılandırmak için, paylaşılan metatabanını yerel olarak içeri aktarabilir ya da yerel metatabanını yapılandıran "WFServicesReg. exe/c" komutunu çalıştırabilirsiniz.
