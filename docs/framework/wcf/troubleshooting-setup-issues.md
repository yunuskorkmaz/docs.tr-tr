---
title: "Kurulum Sorunlarını Giderme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1644f885-c408-4d5f-a5c7-a1a907bc8acd
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 284805f8ca1fb9778dc6bccd9807fa86dc7e2d77
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="troubleshooting-setup-issues"></a>Kurulum Sorunlarını Giderme
Bu konuda nasıl giderileceği açıklanmaktadır [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] sorunları ayarlayın.  
  
## <a name="some-windows-communication-foundation-registry-keys-are-not-repaired-by-performing-an-msi-repair-operation-on-the-net-framework-30"></a>Bazı Windows Communication Foundation kayıt defteri anahtarları .NET Framework 3.0 bir MSI onarım işlemi gerçekleştirilirken tarafından onarılır değil  
 Aşağıdaki kayıt defteri anahtarlarının silerseniz:  
  
-   HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelService 3.0.0.0  
  
-   HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelOperation 3.0.0.0  
  
-   HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelEndpoint 3.0.0.0  
  
-   HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SMSvcHost 3.0.0.0  
  
-   HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSDTC köprüsü 3.0.0.0  
  
 Gelen başlatılan .NET Framework 3.0 yükleyicisini kullanarak onarım çalıştırırsanız anahtarları yeniden oluşturulmaz **Program Ekle/Kaldır** uygulaması **Denetim Masası**. Bu anahtarlar doğru yeniden oluşturmak için kullanıcı kaldırın ve .NET Framework 3.0 yükleyin.  
  
## <a name="wmi-service-corruption-blocks-installation-of-the-windows-communication-foundation-wmi-provider-during-installation-of-net-framework-30-package"></a>WMI hizmeti Bozulması blokları yükleme .NET Framework 3.0 paketin yüklenmesi sırasında Windows Communication Foundation WMI sağlayıcısı  
 WMI hizmeti Bozulması Windows Communication Foundation WMI sağlayıcısı yüklenmesini engelleyebilir. Windows Communication Foundation yükleme sırasında yükleyici mofcomp.exe bileşenini kullanarak WCF .mof dosyasını kaydedemedi. Belirtilerin bir listesi verilmiştir:  
  
1.  .NET framework 3.0 yüklemenin başarıyla tamamlandığını ancak WCF WMI sağlayıcısı kayıtlı değil.  
  
2.  Bir hata olayı uygulama olay günlüğünde sorunları WCF için WMI sağlayıcısı Kaydediliyor veya mofcomp.exe çalıştıran başvuran görüntülenir.  
  
3.  Adlı kullanıcının % temp % dizininde dd_wcf_retCA * Kurulum günlük dosyası WCF WMI sağlayıcısı kaydetme hatası başvurular içeriyor.  
  
4.  Bir aşağıdaki gibi bir özel durum olay günlüğü veya Kurulum izleme günlük dosyasında listelenen:  
  
     ServiceModelReg [11:09:59:046]: System.ApplicationException: beklenmeyen bir sonuç 3 E:\WINDOWS\system32\wbem\mofcomp.exe "E:\WINDOWS\Microsoft.NET\Framework\v3.0\Windows iletişim Foundation\ServiceModel.mof" ile çalıştırma  
  
     veya:  
  
     ServiceModelReg [07:19:33:843]: System.typeınitializationexception: 'System.Management.ManagementPath' tür başlatıcısı özel durum oluşturdu. System.Runtime.InteropServices.COMException (0x80040154)--->: CLSID {CF4CC405-E2C5-4DDD-B3CE-5E7582D8C9FA} bileşeniyle COM üreteci alınırken şu hata nedeniyle başarısız oldu: 80040154.  
  
     veya:  
  
     ServiceModelReg [07:19:32:750]: System.IO.FileNotFoundException: dosya veya derleme 'C:\WINDOWS\system32\wbem\mofcomp.exe' ya da bağımlılıklarından biri yüklenemedi. Sistem belirtilen dosyayı bulamıyor.  
  
     Dosya adı: ' C:\WINDOWS\system32\wbem\mofcomp.exe  
  
 Daha önce açıklanan sorunu gidermek için aşağıdaki adımlar izlenmelidir.  
  
1.  Çalıştırma [WMI tanılama yardımcı programı, sürüm 2.0](http://go.microsoft.com/fwlink/?LinkId=94685) WMI hizmetinin onarmak için. [!INCLUDE[crabout](../../../includes/crabout-md.md)]Bu aracı kullanarak bkz [WMI tanılama yardımcı programı](http://go.microsoft.com/fwlink/?LinkId=94686) konu.  
  
 Kullanarak .NET Framework 3.0 yüklemesini onarmak **Program Ekle/Kaldır** uygulaması bulunan **Denetim Masası**, ya da kaldırma/yeniden .NET Framework 3.0.  
  
## <a name="repairing-net-framework-30-after-net-framework-35-installation-removes-configuration-elements-introduced-by-net-framework-35-in-machineconfig"></a>.NET Framework 3.5 yükleme yapılandırma öğeleri Machine.Config'deki .NET Framework 3.5 tarafından sunulan kaldırdıktan sonra .NET Framework 3.0 onarma  
 Yükledikten sonra .NET Framework 3.0 onarımını yaparsanız [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)], yapılandırma öğeleri tarafından sunulan [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] machine.config içinde kaldırılır. Ancak, web.config değişmeden kalır. Onarmak için geçici bir çözüm değildir [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] ARP veya kullanımı aracılığıyla sonra [WorkFlow hizmet Kayıt Aracı (WFServicesReg.exe)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md) ile `/c` geçin.  
  
 [WorkFlow hizmet Kayıt Aracı (WFServicesReg.exe)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md) %windir%\Microsoft.NET\framework\v3.5\ veya %windir%\Microsoft.NET\framework64\v3.5\ bulunabilir  
  
## <a name="configure-iis-properly-for-wcfwf-webhost-after-installing-net-framework-35"></a>Düzgün IIS'yi .NET Framework 3.5 yükledikten sonra WCF/WF Webhost için yapılandırın  
 Zaman [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] yükleme başarısız olursa ek yapılandırmak [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]-ilgili IIS yapılandırma ayarlarını, yükleme günlüğünde bir hatayı günlüğe kaydeder ve devam eder. Gerekli yapılandırma ayarları eksik olduğundan WorkflowServices uygulamaları çalıştırmak için her türlü girişim başarısız olur. Örneğin, xoml veya kuralları hizmeti yüklemesi başarısız olabilir.  
  
 Geçici çözüm için bu sorun, kullanım [WorkFlow hizmet Kayıt Aracı (WFServicesReg.exe)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md) ile `/c` IIS komut dosyası eşlemeleri makinede doğru şekilde yapılandırmak için anahtar. [WorkFlow hizmet Kayıt Aracı (WFServicesReg.exe)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md) %windir%\Microsoft.NET\framework\v3.5\ veya %windir%\Microsoft.NET\framework64\v3.5\ bulunabilir  
  
## <a name="could-not-load-type-systemservicemodelactivationhttpmodule-from-assembly-systemservicemodel-version-3000-cultureneutral-publickeytokenb77a5c561934e089"></a>Türü 'System.ServiceModel.Activation.HttpModule' derlemesinden yükleyemedi ' System.ServiceModel, sürüm 3.0.0.0, kültür = neutral, PublicKeyToken = b77a5c561934e089 '  
 Bu hata oluşur [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] yüklenir ve ardından [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] HTTP etkinleştirmesi etkindir. Aşağıdaki komut satırı ile içinde çalıştırmak bu sorunu çözmek için [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] komut istemi:  
  
```Output  
aspnet_regiis.exe -i -enable  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kurulum Yönergeleri](../../../docs/framework/wcf/samples/set-up-instructions.md)
