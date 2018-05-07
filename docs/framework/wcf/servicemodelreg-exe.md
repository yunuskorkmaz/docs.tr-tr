---
title: ServiceModel Kayıt Aracı (ServiceModelReg.exe)
ms.date: 03/30/2017
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
ms.openlocfilehash: 660bad0b80a80a21936c9c8a5d485fe05b8c8acf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a>ServiceModel Kayıt Aracı (ServiceModelReg.exe)
Bu komut satırı aracı, WCF ve WF bileşenleri tek bir makinede kaydını yönetme olanağı sağlar. Normal koşullar altında WCF bu aracı kullanmak gerekmez ve WF bileşenler yüklendiğinde yapılandırılmıştır. Ancak, hizmeti etkinleştirme ile ilgili sorunlar yaşıyor varsa, bu aracı kullanarak bileşenleri kaydetmeyi deneyebilirsiniz.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Aracı şu konumda bulunabilir:  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows iletişim Foundation\  
  
> [!NOTE]
>  ServiceModel kayıt aracı çalıştırıldığında [!INCLUDE[wv](../../../includes/wv-md.md)], **Windows özelliklerini** iletişim değil yansıtmak, **Windows Communication Foundation HTTP etkinleştirmesi** seçeneği altında**Microsoft .NET Framework 3.0** açıktır. **Windows özelliklerini** iletişim erişilebilir tıklayarak **Başlat**, ardından **çalıştırmak** yazarak **OptionalFeatures**.  
  
 Aşağıdaki tablolarda ServiceModelReg.exe ile kullanılabilir seçenekleri açıklanmaktadır.  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|`-ia`|Tüm WCF ve WF bileşenleri yükler.|  
|`-ua`|Tüm WCF ve WF bileşenleri kaldırır.|  
|`-r`|Tüm WCF ve WF bileşenleri onarır.|  
|`-i`|– C ile belirtilen WCF ve WF bileşenleri yükler.|  
|`-u`|– C ile belirtilen WCF ve WF bileşenleri kaldırır.|  
|`-c`|Yükler veya bir bileşen kaldırır:<br /><br /> -httpnamespace – HTTP Namespace ayırma<br />-tcpportsharing – TCP bağlantı noktası Paylaşımı hizmeti<br />-tcpactivation – TCP Etkinleştirme Hizmeti (.NET 4 istemci profili üzerinde desteklenmeyen)<br />-namedpipeactivation – adlandırılmış kanal Etkinleştirme Hizmeti (.NET 4 istemci profili üzerinde desteklenmiyor<br />-msmqactivation – MSMQ Etkinleştirme Hizmeti (.NET 4 istemci profili üzerinde desteklenmiyor<br />-etw – ETW olay izleme bildirimleri (Windows Vista veya sonraki bir sürümü)|  
|`-q`|Sessiz mod (yalnızca görünen hata günlüğünü)|  
|`-v`|Ayrıntılı mod.|  
|`-nologo`|Telif hakkı ve başlık iletisi gizler.|  
|`-?`|Görüntüler Yardım metni|  
  
## <a name="fixing-the-fileloadexception-error"></a>FileLoadException hata düzeltme  
 Önceki sürümlerini yüklediyseniz [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] , makinenizde alabilirsiniz bir `FileLoadFoundException` yeni bir yükleme kaydetmek için ServiceModelReg aracı'nı çalıştırdığınızda hata. El ile önceki yükle dosyaları kaldırıldı, ancak machine.config ayarları dokunulmadan olsa bile bu durum oluşabilir.  
  
 Hata iletisi aşağıdakine benzer.  
  
```  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 System.ServiceModel 2.0.0.0 veya derleme yüklendi hata iletisinden unutmamalısınız erken bir müşteri teknolojisi Önizleme (CTP) sürümü tarafından. Geçerli yayımlanan System.ServiceModel derleme 3.0.0.0 yerine sürümüdür. Resmi yüklemek istediğinizde bu nedenle, bu sorunu ile karşılaşıldı [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] burada erken bir CTP sürümünün bir makinede sürüm [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] yüklü, ancak tamamen kaldırılır.  
  
 Önceki sürüm girdilerini ServiceModelReg.exe temizleyemiyor ya da yeni sürümün girişleri kaydedebilirsiniz. Machine.config el ile düzenlemek için yalnızca geçici bir çözüm değildir. Bu dosya şu konumda bulabilirsiniz.  
  
```  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config   
```  
  
 Çalıştırıyorsanız, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 64-bit makine üzerinde Ayrıca aynı dosyanın bu konumda düzenlemeniz gerekir.  
  
```  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config   
```  
  
 Başvurmak bu dosyadaki tüm XML düğümlerini bulun "System.ServiceModel, sürüm 2.0.0.0 =", bunları ve tüm alt düğümleri silin. Dosyayı kaydedin ve ServiceModelReg.exe yeniden çalıştırmak bu sorunu giderir.  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki örnekler ServiceModelReg.exe aracının en yaygın seçenekler kullanmayı gösterir.  
  
```  
ServiceModelReg.exe -ia  
  Installs all components  
ServiceModelReg.exe -i -c:httpnamespace -c:etw  
  Installs HTTP namespace reservation and ETW manifests  
ServiceModelReg.exe -u -c:etw  
  Uninstalls ETW manifests  
ServiceModelReg.exe -r  
  Repairs an extended install  
```
