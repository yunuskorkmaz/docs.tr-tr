---
title: Kurulum Sorunlarını Giderme
ms.date: 03/30/2017
ms.assetid: 1644f885-c408-4d5f-a5c7-a1a907bc8acd
ms.openlocfilehash: 02e6446893e661a0ec0553b0ddf254c40595595c
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321351"
---
# <a name="troubleshooting-setup-issues"></a>Kurulum Sorunlarını Giderme
Bu konuda, Windows Communication Foundation (WCF) kurma sorunlarını nasıl giderebileceğiniz açıklanır.  
  
## <a name="some-windows-communication-foundation-registry-keys-are-not-repaired-by-performing-an-msi-repair-operation-on-the-net-framework-30"></a>Bazı Windows Communication Foundation kayıt defteri anahtarları, .NET Framework 3,0 üzerinde MSI onarım Işlemi gerçekleştirerek onarılmıyor  
 Aşağıdaki kayıt defteri anahtarlarından birini silerseniz:  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelService 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelOperation 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelEndpoint 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SMSvcHost 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSDTC Köprüsü 3.0.0.0  
  
 **Denetim Masası**'Ndaki **Program Ekle/kaldır** uygulamasından başlatılan .NET Framework 3,0 yükleyicisini kullanarak Onar 'ı çalıştırırsanız anahtarlar yeniden oluşturulmaz. Bu anahtarları doğru bir şekilde yeniden oluşturmak için, Kullanıcı .NET Framework 3,0 ' i kaldırmalı ve yeniden yüklemelisiniz.  
  
## <a name="wmi-service-corruption-blocks-installation-of-the-windows-communication-foundation-wmi-provider-during-installation-of-net-framework-30-package"></a>WMI hizmeti bozulması, .NET Framework 3,0 paketinin yüklenmesi sırasında Windows Communication Foundation WMI sağlayıcısının yüklenmesini engelliyor  
 WMI hizmeti bozulması Windows Communication Foundation WMI sağlayıcısının yüklenmesini engelleyebilir. Yükleme sırasında Windows Communication Foundation yükleyicisi, mofcomp. exe bileşenini kullanarak WCF. mof dosyasını kaydedemiyor. Belirtilerin listesi aşağıda verilmiştir:  
  
1. .NET Framework 3,0 yüklemesi başarıyla tamamlandı, ancak WCF WMI sağlayıcısı kayıtlı değil.  
  
2. Uygulama olay günlüğünde WCF için WMI sağlayıcısını kaydettirme veya mofcomp. exe ' yi çalıştırma sorunlarıyla ilgili sorunları karşılayan bir hata olayı görüntülenir.  
  
3. Kullanıcının% Temp% dizininde dd_wcf_retCA * adlı kurulum günlük dosyası, WCF WMI sağlayıcısı 'nı kaydetmek için hata başvurular içeriyor.  
  
4. Olay günlüğünde veya kurulum izleme günlük dosyasında aşağıdakiler gibi bir özel durum listelenebilir:  
  
     ServiceModelReg [11:09:59:046]: System. ApplicationException: beklenmeyen sonuç 3 "E:\WINDOWS\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModel.mof ile E:\WINDOWS\system32\wbem\mofcomp.exe yürütülüyor"  
  
     veya:  
  
     ServiceModelReg [07:19:33:843]: System. TypeInitializationException: ' System. Management. ManagementPath ' için tür başlatıcısı özel durum oluşturdu. ---> System. Runtime. InteropServices. COMException (0x80040154): CLSID {CF4CC405-E2C5-4DDD-B3CE-5E7582D8C9FA} olan bileşen için COM sınıfı fabrikasını alma işlemi şu hata nedeniyle başarısız oldu: 80040154.  
  
     veya:  
  
     ServiceModelReg [07:19:32:750]: System. ıO. FileNotFoundException: ' C:\WINDOWS\system32\wbem\mofcomp.exe ' dosyası veya bütünleştirilmiş kodu veya bağımlılıklarından biri yüklenemedi. Sistem belirtilen dosyayı bulamıyor.  
  
     Dosya adı: ' C:\WINDOWS\system32\wbem\mofcomp.exe  
  
 Daha önce açıklanan sorunu çözmek için aşağıdaki adımlar izlenmelidir.  
  
1. WMI hizmetini onarmak için [WMI diagnosis Utility sürüm 2,0 ' i](https://go.microsoft.com/fwlink/?LinkId=94685) çalıştırın. Bu aracı kullanma hakkında daha fazla bilgi için [WMI diagnosis Utility](https://go.microsoft.com/fwlink/?LinkId=94686) konusuna bakın.  
  
 **Denetim Masası**'Nda bulunan **Program Ekle/kaldır** uygulamasını kullanarak .NET Framework 3,0 yüklemesini onarın veya .NET Framework 3,0 ' i kaldırın/yeniden yükleyin.  
  
## <a name="repairing-net-framework-30-after-net-framework-35-installation-removes-configuration-elements-introduced-by-net-framework-35-in-machineconfig"></a>.NET Framework 3,5 yüklemesi sonrasında .NET Framework 3,0 onarma, Machine. config dosyasında .NET Framework 3,5 tarafından tanıtılan yapılandırma öğelerini kaldırır  
 @No__t-0 ' ı yükledikten sonra .NET Framework 3,0 ' yi onarırsanız, Machine. config dosyasında [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] tarafından tanıtılan yapılandırma öğeleri kaldırılır. Ancak, Web. config bozulmadan kalır. Geçici çözüm, bu ARP aracılığıyla [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] ' ı onarması veya `/c` anahtarıyla [Iş akışı hizmeti kayıt aracı 'nı (WFServicesReg. exe)](workflow-service-registration-tool-wfservicesreg-exe.md) kullanmaktır.  
  
 [Workflow Service kayıt aracı (WFServicesReg. exe)](workflow-service-registration-tool-wfservicesreg-exe.md) ,%windir%\Microsoft.NET\Framework\v3.5\ veya%windir%\Microsoft.NET\Framework64\v3.5\ adresinde bulunabilir  
  
## <a name="configure-iis-properly-for-wcfwf-webhost-after-installing-net-framework-35"></a>.NET Framework 3,5 yükledikten sonra IIS 'Yi WCF/WF Webhost için düzgün şekilde yapılandırma  
 @No__t-0 yüklemesi, WCF ile ilgili ek IIS yapılandırma ayarlarını yapılandıramazsa, yükleme günlüğünde bir hata kaydeder ve devam eder. Gerekli yapılandırma ayarları eksik olduğundan, WorkflowServices uygulamalarını çalıştırma girişimleri başarısız olur. Örneğin, xoml veya Rules hizmeti yüklenirken hata oluşabilir.  
  
 Bu soruna geçici bir çözüm olarak, makinede IIS betik eşlemelerini doğru şekilde yapılandırmak için `/c` anahtarıyla [Iş akışı hizmeti kayıt aracı 'nı (WFServicesReg. exe)](workflow-service-registration-tool-wfservicesreg-exe.md) kullanın. [Workflow Service kayıt aracı (WFServicesReg. exe)](workflow-service-registration-tool-wfservicesreg-exe.md) ,%windir%\Microsoft.NET\Framework\v3.5\ veya%windir%\Microsoft.NET\Framework64\v3.5\ adresinde bulunabilir  
  
## <a name="could-not-load-type-systemservicemodelactivationhttpmodule-from-assembly-systemservicemodel-version-3000-cultureneutral-publickeytokenb77a5c561934e089"></a>' System. ServiceModel. Activation. HttpModule ' türü, ' System. ServiceModel, Version 3.0.0.0, Culture = neutral, PublicKeyToken = b77a5c561934e089 ' derlemesinden yüklenemedi  
 Bu hata, [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] yüklüyse ve WCF HTTP etkinleştirmesi etkinleştirilmişse oluşur. Sorunu çözmek için, Visual Studio Geliştirici Komut İstemi içinden aşağıdaki komut satırını çalıştırın:  
  
```console
aspnet_regiis.exe -i -enable  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kurulum Yönergeleri](./samples/set-up-instructions.md)
