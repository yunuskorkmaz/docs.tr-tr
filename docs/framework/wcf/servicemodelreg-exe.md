---
title: ServiceModel Kayıt Aracı (ServiceModelReg.exe)
ms.date: 03/30/2017
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
ms.openlocfilehash: a6f65ccc6caa0a7e496e7de8c83259ab48903753
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183103"
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a>ServiceModel Kayıt Aracı (ServiceModelReg.exe)
Bu komut satırı aracı, WCF ve WF bileşenlerinin tek bir makinede kaydını yönetme olanağı sağlar. Normal koşullarda, wcf ve WF bileşenleri yüklendiğinde yapılandırıldığından bu aracı kullanmanız gerekmez. Ancak hizmet etkinleştirme yle ilgili sorunlar yaşıyorsanız, bileşenleri bu aracı kullanarak kaydetmeyi deneyebilirsiniz.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Araç aşağıdaki konumda bulunabilir:  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\  
  
> [!NOTE]
> ServiceModel Kayıt Aracı Windows Vista'da çalıştırıldığında, **Windows Özellikleri** iletişim kutusu **Microsoft .NET Framework 3.0** altındaki **Windows Communication Foundation HTTP Etkinleştirme** seçeneğinin açık olduğunu yansıtmayabilir. **Windows Özellikleri** iletişim kutusuna **Başlat'ı**tıklatarak erişilebilir, ardından **Çalıştır'ı** tıklatın ve ardından **İsteğe Bağlı Özellikler**yazabilirsiniz.  
  
 Aşağıdaki tablolar ServiceModelReg.exe ile kullanılabilecek seçenekleri açıklar.  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|`-ia`|Tüm WCF ve WF bileşenlerini yükler.|  
|`-ua`|Tüm WCF ve WF bileşenlerini yükler.|  
|`-r`|Tüm WCF ve WF bileşenlerini onarır.|  
|`-i`|–c ile belirtilen WCF ve WF bileşenlerini yükler.|  
|`-u`|–c ile belirtilen WCF ve WF bileşenlerini yükler.|  
|`-c`|Bir bileşeni yükler veya yükler:<br /><br /> - httpnamespace – HTTP Namespace Rezervasyon<br />- tcpportsharing – TCP port paylaşım hizmeti<br />- tcpactivation – TCP aktivasyon hizmeti (.NET 4 İstemci Profili'nde desteklenmez)<br />- namedpipeactivation – Named pipe aktivasyon hizmeti (.NET 4 İstemci Profilinde desteklenmez<br />- msmqactivation – MSMQ aktivasyon hizmeti (.NET 4 İstemci Profilinde desteklenmez<br />- etw - ETW olay izleme manifestoları (Windows Vista veya daha sonra)|  
|`-q`|Sessiz mod (yalnızca hata günlüğe kaydetme)|  
|`-v`|Verbose modu.|  
|`-nologo`|Telif hakkı ve banner mesajını bastırır.|  
|`-?`|Yardım metnini görüntüler|  
  
## <a name="fixing-the-fileloadexception-error"></a>FileLoadException Hatası düzeltme  
 Makinenize WCF'nin önceki sürümlerini yüklediyseniz, `FileLoadFoundException` yeni bir yükleme kaydetmek için ServiceModelReg aracını çalıştırdığınızda bir hata alabilirsiniz. Bu, önceki yüklemeden dosyaları el ile kaldırdınız, ancak machine.config ayarlarını sağlam bıraksanız bile gerçekleşebilir.  
  
 Hata iletisi aşağıdakilere benzer.  
  
```console  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 System.ServiceModel Version 2.0.0.0 derlemesinin erken bir Müşteri Teknolojisi Önizleme (CTP) sürümü tarafından yüklenmiş olduğunu hata iletisinden not almalısınız. Yayımlanan System.ServiceModel derlemesinin geçerli sürümü 3.0.0.0 yerine. Bu nedenle, resmi WCF sürümü wcf erken CTP sürümü yüklü olduğu bir makineye yüklemek istediğinizde bu sorunla karşılaşılan, ancak tamamen kaldırıldı değil.  
  
 ServiceModelReg.exe önceki sürüm girişlerini temizleyemez ve yeni sürümün girişlerini kaydedemez. Tek geçici çözüm, machine.config'i el ile düzenliyor. Bu dosyayı aşağıdaki konumda bulabilirsiniz.  
  
```console  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config
```  
  
 WCF'yi 64 bit makinede çalıştırıyorsanız, aynı dosyayı bu konumda da değiştirmeniz gerekir.  
  
```console  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config
```  
  
 Bu dosyada "System.ServiceModel, Version=2.0.0.0" anlamına gelen XML düğümlerini bulun, bunları ve alt düğümleri silin. Dosyayı kaydedin ve ServiceModelReg.exe'yi yeniden çalıştırın bu sorunu giderir.  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki örnekler serviceModelReg.exe aracının en yaygın seçeneklerinin nasıl kullanılacağını gösterir.  
  
```console  
ServiceModelReg.exe -ia  
  Installs all components  
ServiceModelReg.exe -i -c:httpnamespace -c:etw  
  Installs HTTP namespace reservation and ETW manifests  
ServiceModelReg.exe -u -c:etw  
  Uninstalls ETW manifests  
ServiceModelReg.exe -r  
  Repairs an extended install  
```
