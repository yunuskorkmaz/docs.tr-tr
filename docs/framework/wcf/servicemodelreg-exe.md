---
title: ServiceModel Kayıt Aracı (ServiceModelReg.exe)
ms.date: 03/30/2017
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
ms.openlocfilehash: 5fab1a356cd035ed006bfe90d713e179907e0137
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051799"
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a>ServiceModel Kayıt Aracı (ServiceModelReg.exe)
Bu komut satırı aracı, WCF ve WF bileşenleri tek bir makinede kaydını yönetme olanağı sağlar. Normal koşullar altında bu aracı WCF kullanın gerekmez ve WF bileşenler yüklendiğinde yapılandırılmıştır. Ancak, hizmeti etkinleştirme ile ilgili sorunlar yaşıyorsanız, bu aracı kullanarak bileşenleri kaydetmek deneyebilirsiniz.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Aracı şu konumda bulunabilir:  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\  
  
> [!NOTE]
>  ServiceModel kayıt aracı çalıştığında [!INCLUDE[wv](../../../includes/wv-md.md)], **Windows özellikleri** iletişim değil yansıtmak, **Windows Communication Foundation HTTP etkinleştirme** seçeneğinde**Microsoft .NET Framework 3.0** açıktır. **Windows özellikleri** tıklayarak iletişim erişilebilir **Başlat**, ardından **çalıştırma** ardından yazarak **OptionalFeatures**.  
  
 Aşağıdaki tablolar ile ServiceModelReg.exe kullanılabilir seçenekleri açıklar.  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|`-ia`|WCF ve WF tüm bileşenlerini yükler.|  
|`-ua`|Tüm WCF ve WF bileşenleri kaldırır.|  
|`-r`|Tüm WCF ve WF bileşenleri onarır.|  
|`-i`|– C ile belirtilen WCF ve WF bileşenlerini yükler.|  
|`-u`|– C ile belirtilen WCF ve WF bileşenleri kaldırır.|  
|`-c`|Yükler veya bir bileşeni kaldırır:<br /><br /> -httpnamespace – HTTP Namespace ayırma<br />-tcpportsharing – TCP bağlantı noktası Paylaşım Hizmeti<br />-tcpactivation – TCP Etkinleştirme Hizmeti (.NET 4 istemci profili üzerinde desteklenmez)<br />-namedpipeactivation – adlandırılmış kanal etkinleştirmesi hizmet (.NET 4 istemci profili üzerinde desteklenmiyor<br />-msmqactivation – MSMQ Etkinleştirme Hizmeti (.NET 4 istemci profili üzerinde desteklenmiyor<br />-etw – ETW olay izleme bildirimleri (Windows Vista veya üzeri)|  
|`-q`|Sessiz modu (yalnızca görünen hata günlüğü)|  
|`-v`|Ayrıntılı modu.|  
|`-nologo`|Telif hakkı ve başlık iletisini bastırır.|  
|`-?`|Yardım metni görüntüler|  
  
## <a name="fixing-the-fileloadexception-error"></a>FileLoadException hata düzeltme  
 WCF'ın önceki sürümlerini makinenizde yüklü değilse, alabilirsiniz bir `FileLoadFoundException` yeni bir yükleme kaydedilecek ServiceModelReg aracı'nı çalıştırdığınızda hata. El ile dosyaları önceki yükle kaldırıldı ancak machine.config ayarları dokunulmadan olsa bile bu durum oluşabilir.  
  
 Hata iletisi aşağıdakine benzer.  
  
```  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 System.ServiceModel sürüm 2.0.0.0 derleme yüklendiğini hata iletisindeki unutmamalısınız erken bir müşteri Technology Preview (CTP) sürümü tarafından. Geçerli yayımlanan System.ServiceModel derlemenin 3.0.0.0 yerine sürümüdür. Resmi WCF yayın burada WCF erken bir CTP sürümü yüklü, ancak tamamen kaldırılmış bir makineye yüklemek istediğinizde, bu nedenle, bu sorunla karşılaşılır.  
  
 ServiceModelReg.exe önceki sürümünü girdilerin temizlenmesini olamaz ya da yeni sürümün girişleri kaydedebilirsiniz. Machine.config el ile düzenlemek için yalnızca çözüm olabilir. Bu dosya şu konumda bulabilirsiniz.  
  
```  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config   
```  
  
 WCF 64 bit makine üzerinde çalıştırıyorsanız, aynı dosyanın bu konumda da düzenlemeniz gerekir.  
  
```  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config   
```  
  
 Bu dosyadaki başvuran hiçbir XML düğümüyle bulun "System.ServiceModel, sürüm 2.0.0.0 =", bunları ve tüm alt düğümleri silin. Dosyayı kaydedin ve ServiceModelReg.exe yeniden çalıştırmak bu sorunu çözer.  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki örnekler, en yaygın seçenekler ServiceModelReg.exe aracı kullanmayı gösterir.  
  
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
