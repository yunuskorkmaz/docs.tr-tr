---
title: Kurulum Sorunlarını Giderme
ms.date: 03/30/2017
ms.assetid: 1644f885-c408-4d5f-a5c7-a1a907bc8acd
ms.openlocfilehash: 2cd9ced4f0780b1a6f63e4a5833e20ac91870121
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121590"
---
# <a name="troubleshoot-setup-issues"></a>Sorun giderme kurulum sorunları

Bu makalede, Windows Communication Foundation (WCF) ayar sorunlarının nasıl giderilen giderilmesi açıklanmaktadır.  
  
## <a name="some-windows-communication-foundation-registry-keys-are-not-repaired-by-performing-an-msi-repair-operation-on-the-net-framework-30"></a>Bazı Windows Communication Foundation Registry Keys.NET Framework 3.0 üzerinde MSI Onarım İşlemi Yaparak Onarılamaz  
 Aşağıdaki kayıt defteri anahtarlarından herhangi birini silerseniz:  
  
- HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\ServiceModelService 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\ServiceModelOperation 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\ServiceModelEndpoint 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\SMSvcHost 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\MSDTC Köprüsü 3.0.0.0  
  
 **Denetim Masası'ndaki** **Programları Ekle/Kaldır'dan** başlatılan .NET Framework 3.0 yükleyicisini kullanarak onarımı çalıştırdığınızda anahtarlar yeniden oluşturulmaz. Bu anahtarları doğru şekilde yeniden oluşturmak için, kullanıcının .NET Framework 3.0'ı kaldırması ve yeniden yüklemesi gerekir.  
  
## <a name="wmi-service-corruption-blocks-installation-of-the-windows-communication-foundation-wmi-provider-during-installation-of-net-framework-30-package"></a>WMI Hizmet Bozulması .NET Framework 3.0 paketinin yüklenmesi sırasında Windows Communication Foundation WMI sağlayıcısının kurulumu  
 WMI Hizmet Bozulması, Windows Communication Foundation WMI sağlayıcısının yüklenmesini engelleyebilir. Yükleme sırasında Windows Communication Foundation yükleyicisi mofcomp.exe bileşenini kullanarak WCF .mof dosyasını kaydedemez. Aşağıdaki belirtilerin bir listesi:  
  
1. .NET Framework 3.0 yüklemesi başarıyla tamamlanır, ancak WCF WMI sağlayıcısı kayıtlı değildir.  
  
2. WCF için WMI sağlayıcısını kaydetme veya mofcomp.exe çalıştıran sorunlara başvuran uygulama olayı günlüğünde bir hata olayı görüntülenir.  
  
3. Kullanıcının %geçici% dizininde dd_wcf_retCA* adlı kurulum günlüğü dosyası, WCF WMI sağlayıcısının kaydedilmemesine atıfta bulunmaktadır.  
  
4. Aşağıdakilerden biri gibi bir özel durum olay günlüğü veya kurulum izleme günlüğü dosyasında listelenebilir:  
  
     ServiceModelReg [11:09:59:046]: System.ApplicationException: Beklenmeyen sonuç 3 yürütme E:\WINDOWS\system32\wbem\mofcomp.exe ile "E:\WINDOWS\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModel.mof"  
  
     veya:  
  
     ServiceModelReg [07:19:33:843]: System.TypeInitializationException: 'System.Management.ManagementPath' için tür başharfi bir özel durum attı. ---> System.Runtime.InteropServices.COMException (0x80040154): CLSID {CF4CC405-E2C5-4DDD-B3CE-5E7582D8C9FA} bileşen için COM sınıfı fabrikanın alınması aşağıdaki hata nedeniyle başarısız oldu: 80040154.  
  
     veya:  
  
     ServiceModelReg [07:19:32:750]: System.IO.FileNotFoundException: Dosya veya montaj 'C:\WINDOWS\system32\wbem\mofcomp.exe' veya bağımlılıklarından birini yükleyemedi. Sistem belirtilen dosyayı bulamıyor.  
  
     Dosya adı: 'C:\WINDOWS\system32\wbem\mofcomp.exe  
  
 Daha önce açıklanan sorunu çözmek için aşağıdaki adımların izlenmesi gerekir.  
  
1. WMI hizmetini onarmak için [WMI Diagnosis Utility'yi](https://www.microsoft.com/download/details.aspx?id=7684) çalıştırın. Bu aracı kullanma hakkında daha fazla bilgi için [WMI Diagnosis Utility'ye](https://docs.microsoft.com/previous-versions/tn-archive/ff404265(v%3dmsdn.10))bakın.  
  
 **Denetim Masası'nda**bulunan **Programları Ekle/Kaldır'ı** kullanarak .NET Framework 3.0 kurulumunu onarın veya .NET Framework 3.0'ı kaldırın/yeniden yükleyin.  
  
## <a name="repairing-net-framework-30-after-net-framework-35-installation-removes-configuration-elements-introduced-by-net-framework-35-in-machineconfig"></a>.NET Framework 3.5 Kurulumdan sonra .NET Framework 3.0'ın Onarılması Machine.config'de .NET Framework 3.5 tarafından Tanıtılan Yapılandırma Elemanlarını Kaldırır  
 .NET Framework 3.5'i yükledikten sonra .NET Framework 3.0 onarımı yaparsanız, machine.config'de .NET Framework 3.5 tarafından getirilen yapılandırma öğeleri kaldırılır. Ancak, web.config bozulmadan kalır. Geçici çözüm, .NET Framework 3.5'i arp üzerinden onarmak veya `/c` [anahtarla Birlikte İş Akışı Hizmet Kayıt Aracı'nı (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) kullanmaktır.  
  
 [İş Akışı Hizmeti Kayıt Aracı (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) %windir%\Microsoft.NET\framework\v3.5\ veya %windir%\Microsoft.NET\framework64\v3.5\ adresinde bulunabilir.  
  
## <a name="configure-iis-properly-for-wcfwf-webhost-after-installing-net-framework-35"></a>.NET Framework 3.5'i Yükledikten sonra WCF/WF Web host için IIS'yi düzgün bir şekilde yapılandırın  
 .NET Framework 3.5 yüklemesi WCF ile ilgili diğer IIS yapılandırma ayarlarını yapılandırmayı başaramayınca, yükleme günlüğünde bir hata kaydeder ve devam eder. Gerekli yapılandırma ayarları eksik olduğundan, İş Akışı Hizmetleri uygulamalarını çalıştırma girişimi başarısız olur. Örneğin, xoml veya kurallar hizmeti yükleme başarısız olabilir.  
  
 Bu sorunu çözüme getirmek için, makinedeki IIS komut dosyası eşlemlerini düzgün bir şekilde yapılandırmak için `/c` anahtarla birlikte İş Akışı Hizmeti Kayıt Aracı'nı [(WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) kullanın. [İş Akışı Hizmeti Kayıt Aracı (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) %windir%\Microsoft.NET\framework\v3.5\ veya %windir%\Microsoft.NET\framework64\v3.5\ adresinde bulunabilir.  
  
## <a name="could-not-load-type-systemservicemodelactivationhttpmodule-from-assembly-systemservicemodel-version-3000-cultureneutral-publickeytokenb77a5c561934e089"></a>'System.ServiceModel.Activation.HttpModule' türünü montajdan yükleyemedi 'System.ServiceModel, Sürüm 3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
 .NET Framework 4 yüklüyse ve wcf HTTP Etkinleştirme etkinleştirilmişse bu hata oluşur. Sorunu çözmek için Visual Studio için Geliştirici Komut Komut Istem içinden aşağıdaki komut satırı çalıştırın:  
  
```console
aspnet_regiis.exe -i -enable  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kurulum Yönergeleri](./samples/set-up-instructions.md)
