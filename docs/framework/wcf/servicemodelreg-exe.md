---
title: ServiceModel Kayıt Aracı (ServiceModelReg.exe)
description: Hizmet etkinleştirmesiyle ilgili sorunlar yaşıyorsanız, tek bir makineye WCF ve WF bileşenlerinin kaydedilmesini yönetmek için bu komut satırı aracını kullanın.
ms.date: 03/30/2017
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
ms.openlocfilehash: d8d5bc4dc3de021e2110fb953dbc4d6c7d7972d0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96235928"
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a>ServiceModel Kayıt Aracı (ServiceModelReg.exe)

Bu komut satırı aracı, WCF ve WF bileşenlerinin tek bir makinede kaydını yönetme olanağı sağlar. Normal koşullarda, WCF ve WF bileşenleri yüklendiğinde yapılandırıldığı için bu aracı kullanmanız gerekmez. Ancak hizmet etkinleştirme ile ilgili sorun yaşıyorsanız, bu aracı kullanarak bileşenleri kaydetmeyi deneyebilirsiniz.  
  
## <a name="syntax"></a>Syntax  
  
```console  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a>Açıklamalar  

 Araç aşağıdaki konumda bulunabilir:  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation \  
  
> [!NOTE]
> Windows Vista 'da ServiceModel Kayıt Aracı çalıştırıldığında, **Windows özellikleri** iletişim kutusu **Microsoft .NET Framework 3,0** altında **Windows Communication Foundation HTTP Etkinleştirme** seçeneğinin açık olduğunu yansıtmayabilir. **Windows özellikleri** Iletişim kutusuna **Başlat**' a ve ardından **Çalıştır** ' a tıklayıp **OptionalFeatures** yazarak erişilebilir.  
  
 Aşağıdaki tablolarda ServiceModelReg.exe ile kullanılabilecek seçenekler açıklanır.  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|`-ia`|Tüm WCF ve WF bileşenlerini yükleme.|  
|`-ua`|Tüm WCF ve WF bileşenlerini kaldırır.|  
|`-r`|Tüm WCF ve WF bileşenlerini onarır.|  
|`-i`|– C ile belirtilen WCF ve WF bileşenlerini yükleme.|  
|`-u`|– C ile belirtilen WCF ve WF bileşenlerini kaldırır.|  
|`-c`|Bir bileşeni yüklüyor veya kaldırır:<br /><br /> -httpnamespace – HTTP ad alanı ayırma<br />-tcpportsharing – TCP bağlantı noktası paylaşım hizmeti<br />-tcpactivation – TCP etkinleştirme hizmeti (.NET 4 Istemci profilinde desteklenmez)<br />-namedpipeactivation-adlandırılmış kanal etkinleştirme hizmeti (.NET 4 Istemci profilinde desteklenmez<br />-MsmqActivation – MSMQ etkinleştirme hizmeti (.NET 4 Istemci profilinde desteklenmez<br />-ETW – ETW olay izleme bildirimleri (Windows Vista veya üzeri)|  
|`-q`|Sessiz mod (yalnızca hata günlüğünü görüntüle)|  
|`-v`|Ayrıntılı mod.|  
|`-nologo`|Telif hakkı ve başlık iletisini bastırır.|  
|`-?`|Yardım metnini görüntüler|  
  
## <a name="fixing-the-fileloadexception-error"></a>FileLoadException hatası düzeltiliyor  

 Daha önceki WCF sürümlerini makinenize yüklediyseniz, `FileLoadFoundException` Yeni bir yükleme kaydetmek Için ServiceModelReg aracını çalıştırdığınızda bir hata alabilirsiniz. Bu, önceki yüklemeden dosyaları el ile kaldırmış olsanız bile bu durum oluşabilir, ancak machine.config ayarları değişmeden kalır.  
  
 Hata iletisi aşağıdakine benzer.  
  
```console  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 System. ServiceModel sürüm 2.0.0.0 derlemesinin erken bir müşteri teknolojisi Önizleme (CTP) sürümü tarafından yüklendiği hata iletisinden emin olmalısınız. System. ServiceModel derlemesinin geçerli sürümü bunun yerine 3.0.0.0. Bu nedenle, bir WCF 'nin ilk CTP sürümünün yüklendiği ancak tamamen kaldırılmadığı bir makineye resmi WCF sürümü yüklemek istediğinizde bu sorunla karşılaşıldı.  
  
 ServiceModelReg.exe önceki sürüm girdilerini temizleyemiyor veya yeni sürümün girdilerini kaydedemezler. Tek geçici çözüm machine.config el ile düzenlemedir. Bu dosyayı aşağıdaki konumda bulabilirsiniz.  
  
```console  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config
```  
  
 WCF 'yi 64 bitlik bir makinede çalıştırıyorsanız aynı dosyayı da bu konumda düzenlemeniz gerekir.  
  
```console  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config
```  
  
 Bu dosyadaki "System. ServiceModel, Version = 2.0.0.0" öğesine başvuran XML düğümlerini bulun, bunları ve tüm alt düğümleri silin. Dosyayı kaydedin ve yeniden çalıştırın ServiceModelReg.exe bu sorunu çözer.  
  
## <a name="examples"></a>Örnekler  

 Aşağıdaki örneklerde ServiceModelReg.exe aracının en yaygın seçeneklerinin nasıl kullanılacağı gösterilmektedir.  
  
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
