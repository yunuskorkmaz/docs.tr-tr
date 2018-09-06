---
title: Kurulum Sorunlarını Giderme
ms.date: 03/30/2017
ms.assetid: 1644f885-c408-4d5f-a5c7-a1a907bc8acd
ms.openlocfilehash: 0270bd8c1006b39805e3486c4fef0cb379089ea8
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43805136"
---
# <a name="troubleshooting-setup-issues"></a>Kurulum Sorunlarını Giderme
Bu konu, Windows Communication Foundation (WCF) sorunları kümesi sorun giderme açıklar.  
  
## <a name="some-windows-communication-foundation-registry-keys-are-not-repaired-by-performing-an-msi-repair-operation-on-the-net-framework-30"></a>Bazı Windows Communication Foundation kayıt defteri anahtarlarını bir .NET Framework 3.0 MSI onarım işlemi gerçekleştirerek onarılır değil  
 Aşağıdaki kayıt defteri anahtarlarını silerseniz:  
  
-   HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelService 3.0.0.0  
  
-   HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelOperation 3.0.0.0  
  
-   HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelEndpoint 3.0.0.0  
  
-   HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SMSvcHost 3.0.0.0  
  
-   3.0.0.0 HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSDTC köprüsü  
  
 Onarım dan başlatılan .NET Framework 3.0 yükleyicisini kullanarak çalıştırırsanız anahtarları yeniden oluşturulmaz **Program Ekle/Kaldır** uygulaması **Denetim Masası**. Bu anahtarları düzgün yeniden oluşturmak için kullanıcı kaldırın ve .NET Framework 3. 0'ı yeniden yüklemeniz gerekir.  
  
## <a name="wmi-service-corruption-blocks-installation-of-the-windows-communication-foundation-wmi-provider-during-installation-of-net-framework-30-package"></a>WMI hizmeti Bozulması blokları yüklemesi .NET Framework 3.0 paketi yüklemesi sırasında Windows Communication Foundation WMI sağlayıcısı  
 WMI hizmeti Bozulması Windows Communication Foundation WMI sağlayıcısı yüklenmesini engelleyebilir. Yükleme sırasında Windows Communication Foundation yükleyici mofcomp.exe bileşenini kullanarak WCF .mof dosyasına kaydedilemedi. Belirtiler listesi verilmiştir:  
  
1.  .NET framework 3.0 yüklemenin başarıyla tamamlandığını belirten ancak WCF WMI sağlayıcısına kayıtlı değil.  
  
2.  Uygulama olay günlüğüne WCF için WMI sağlayıcısını kaydetme veya mofcomp.exe çalıştıran sorunları başvuran bir hata olayı görünür.  
  
3.  Adlı kullanıcının % temp % dizininde dd_wcf_retCA * Kurulum günlük dosyası WCF WMI sağlayıcısı kaydetme hatası başvurular içerir.  
  
4.  Bir aşağıdaki gibi bir özel durum olay günlüğü veya Kurulum izleme günlük dosyasında listelenen:  
  
     ServiceModelReg [11:09:59:046]: System.ApplicationException: beklenmeyen bir sonuç 3 E:\WINDOWS\system32\wbem\mofcomp.exe "E:\WINDOWS\Microsoft.NET\Framework\v3.0\Windows iletişim Foundation\ServiceModel.mof" ile çalıştırma  
  
     veya:  
  
     ServiceModelReg [07:19:33:843]: System.typeınitializationexception: türü Başlatıcı 'System.Management.ManagementPath' için bir özel durum oluşturdu. ---> System.Runtime.InteropServices.COMException (0x80040154): COM sınıf üreteci CLSID {CF4CC405-E2C5-4DDD-B3CE-5E7582D8C9FA} bileşeni için alınırken aşağıdaki hata nedeniyle başarısız oldu: 80040154.  
  
     veya:  
  
     ServiceModelReg [07:19:32:750]: System.IO.FileNotFoundException: dosya veya derleme 'C:\WINDOWS\system32\wbem\mofcomp.exe' veya bağımlılıklarından biri yüklenemedi. Sistem belirtilen dosyayı bulamıyor.  
  
     Dosya adı: ' C:\WINDOWS\system32\wbem\mofcomp.exe  
  
 Aşağıdaki adımlar, daha önce açıklanan sorunu gidermek için izlenmesi gerekir.  
  
1.  Çalıştırma [WMI tanılama yardımcı programını, sürüm 2.0](https://go.microsoft.com/fwlink/?LinkId=94685) WMI hizmetinin onarmak için. Bu aracı kullanma hakkında daha fazla bilgi için bkz. [WMI tanılama yardımcı programını](https://go.microsoft.com/fwlink/?LinkId=94686) konu.  
  
 Kullanarak .NET Framework 3.0 yüklemesini onarmak **Program Ekle/Kaldır** uygulaması bulunan **Denetim Masası**, ya da .NET Framework 3.0 kaldırın/yeniden.  
  
## <a name="repairing-net-framework-30-after-net-framework-35-installation-removes-configuration-elements-introduced-by-net-framework-35-in-machineconfig"></a>.NET Framework 3.5 yüklemesi .NET Framework 3.5 machine.config tarafından tanıtılan yapılandırma öğeleri kaldırdıktan sonra .NET Framework 3.0 onarılıyor  
 Yüklü .NET Framework 3.0 onarılması bunu yaparsanız [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)], yapılandırma öğeleri tarafından tanıtılan [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] Machine.config dosyasına kaldırılır. Ancak, web.config değişmeden kalır. Geçici çözüm onarmak için olan [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] ARP veya kullanımı aracılığıyla daha sonra [WorkFlow hizmet Kayıt Aracı (WFServicesReg.exe)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md) ile `/c` geçiş.  
  
 [WorkFlow hizmet Kayıt Aracı (WFServicesReg.exe)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md) %windir%\Microsoft.NET\framework\v3.5\ veya %windir%\Microsoft.NET\framework64\v3.5\ bulunabilir  
  
## <a name="configure-iis-properly-for-wcfwf-webhost-after-installing-net-framework-35"></a>WCF/WF Webhost için düzgün şekilde yapılandırmak .NET Framework 3.5 yükledikten sonra IIS  
 Zaman [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] yükleme başarısız olursa ek IIS WCF ile ilgili yapılandırma ayarlarını, yükleme günlüğünde bir hata kaydeder ve devam eder. Gerekli yapılandırma ayarları eksik olduğundan WorkflowServices uygulamaları çalıştırmak için her türlü girişim başarısız olur. Örneğin, xoml veya kuralları hizmeti yükleme başarısız olabilir.  
  
 Geçici çözüm için bu sorun, kullanım [WorkFlow hizmet Kayıt Aracı (WFServicesReg.exe)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md) ile `/c` IIS betik eşlemeleri makine üzerinde düzgün şekilde yapılandırmak için anahtar. [WorkFlow hizmet Kayıt Aracı (WFServicesReg.exe)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md) %windir%\Microsoft.NET\framework\v3.5\ veya %windir%\Microsoft.NET\framework64\v3.5\ bulunabilir  
  
## <a name="could-not-load-type-systemservicemodelactivationhttpmodule-from-assembly-systemservicemodel-version-3000-cultureneutral-publickeytokenb77a5c561934e089"></a>Türü 'System.ServiceModel.Activation.HttpModule' derlemesinden yüklenemiyor ' System.ServiceModel, sürüm 3.0.0.0, kültür neutral, PublicKeyToken = b77a5c561934e089 '  
 Bu hata oluşur [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] yüklenir ve WCF HTTP etkinleştirmesi sonra etkinleştirilir. İçinde komut satırından aşağıdaki komutu çalıştırın sorunu gidermek için [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] komut istemi:  
  
```Output  
aspnet_regiis.exe -i -enable  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kurulum Yönergeleri](../../../docs/framework/wcf/samples/set-up-instructions.md)
