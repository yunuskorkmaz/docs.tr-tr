---
title: "Anlama WebRequest sorunlarını ve özel durumlar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 74a361a5-e912-42d3-8f2e-8e9a96880a2b
caps.latest.revision: "6"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d29321297a880ca961805687e51c7bb63f70ffbf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="understanding-webrequest-problems-and-exceptions"></a>Anlama WebRequest sorunlarını ve özel durumlar
<xref:System.Net.WebRequest>ve türetilmiş sınıflarının (<xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, ve <xref:System.Net.FileWebRequest>) olağan dışı bir koşul göstermek için özel durumlar oluşturma. Bazen bu sorunlar çözümleme açık değil.  
  
## <a name="solutions"></a>Çözümleri  
 İncelemek <xref:System.Net.WebException.Status%2A> özelliği <xref:System.Net.WebException> sorunu belirlemek için. Aşağıdaki tabloda, birkaç durum değerleri ve bazı olası çözümler gösterir.  
  
|Durum|Ayrıntılar|Çözüm|  
|------------|-------------|--------------|  
|<xref:System.Net.WebExceptionStatus.SendFailure><br /><br /> veya<br /><br /> <xref:System.Net.WebExceptionStatus.ReceiveFailure>|Temel alınan yuva ile ilgili bir sorun yoktur. Bağlantı sıfırlanmış.|Yeniden bağlanma ve isteği yeniden gönderin.<br /><br /> En son hizmet paketinin yüklü olduğundan emin olun.<br /><br /> Değerini artırın <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A?displayProperty=nameWithType> özelliği.<br /><br /> Ayarlama <xref:System.Net.HttpWebRequest.KeepAlive%2A?displayProperty=nameWithType> için `false`.<br /><br /> İle en fazla bağlantı sayısını artıracak <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> özelliği.<br /><br /> Proxy yapılandırmasını denetleyin.<br /><br /> SSL kullanıyorsanız, sunucu işlemi sertifika deposuna erişim izni olduğundan emin olun.<br /><br /> Büyük miktarda veri göndermek istiyorsanız, ayarlayın <xref:System.Net.HttpWebRequest.AllowWriteStreamBuffering%2A> için `false`.|  
|<xref:System.Net.WebExceptionStatus.TrustFailure>|Sunucu sertifikası doğrulanamadı.|Internet Explorer kullanarak URI açmayı deneyin. IE tarafından görüntülenen tüm güvenlik uyarıları çözümleyin. Güvenlik Uyarısı çözümlenemiyor sonra uygulayan bir sertifika ilkesi sınıf oluşturabilirsiniz <xref:System.Net.ICertificatePolicy> döndüren `true`ve ona geçirin <xref:System.Net.ServicePointManager.CertificatePolicy%2A>.<br /><br /> Başvurmak [http://support.microsoft.com/?id=823177](http://go.microsoft.com/fwlink/?LinkID=179653).<br /><br /> Sunucu sertifikası imzalı sertifika yetkilisinin sertifikayı Internet Explorer'da güvenilen sertifika yetkilisi listesine eklendiğinden emin olun.<br /><br /> Ana bilgisayar adı URL'de sunucu sertifikasının ortak adına eşleştiğinden emin olun.|  
|<xref:System.Net.WebExceptionStatus.SecureChannelFailure>|SSL işlem sırasında bir hata oluştu veya sertifika ile ilgili bir sorun yoktur.|.NET Framework sürüm 1.1 yalnızca SSL sürüm 3.0 destekler. Sunucu yalnızca TLS sürüm 1.0 veya 2.0 sürümünde SSL kullanıyorsa, özel durum oluşur. Yükseltme .NET Framework sürüm 2.0 ve ayarlayın <xref:System.Net.ServicePointManager.SecurityProtocol%2A> sunucu eşleşecek şekilde.<br /><br /> İstemci sertifikası, sunucunun güvenmediği bir sertifika yetkilisi (CA) tarafından imzalanmış. CA'ın sertifikasını sunucuya yükleyin. Bkz: [http://support.microsoft.com/?id=332077](http://go.microsoft.com/fwlink/?LinkID=179654).<br /><br /> En son hizmet paketine sahip olduğunuzdan emin olun.|  
|<xref:System.Net.WebExceptionStatus.ConnectFailure>|Bağlantı başarısız oldu.|Bir güvenlik duvarı veya proxy bağlantıyı engelliyor. Güvenlik Duvarı veya proxy bağlantıya izin verecek şekilde değiştirin.<br /><br /> Açıkça belirtmek bir <xref:System.Net.WebProxy> çağırarak istemci uygulamasında <xref:System.Net.WebProxy> Oluşturucusu (WebServiceProxyClass.Proxy yeni adımdaki ([http://server:80](http://server/), doğru)).<br /><br /> FileMon veya Regmon çalışan işlem kimliğini WSPWSP.dll, HKLM\System\CurrentControlSet\Services\DnsCache veya HKLM\System\CurrentControlSet\Services\WinSock2 erişmek için gerekli izinlere sahip olduğundan emin olmak için çalıştırın.|  
|<xref:System.Net.WebExceptionStatus.NameResolutionFailure>|Etki alanı adı hizmeti ana bilgisayar adı çözümlenemedi.|Proxy doğru şekilde yapılandırın. Bkz: [http://support.microsoft.com/?id=318140](http://go.microsoft.com/fwlink/?LinkID=179655).<br /><br /> Herhangi bir virüsten koruma yazılımı yüklü veya güvenlik duvarı bağlantıyı engellemediğinden emin olun.|  
|<xref:System.Net.WebExceptionStatus.RequestCanceled>|<xref:System.Net.WebRequest.Abort%2A>çağrılan, veya bir hata oldu.|Bu sorunun nedeni istemci veya sunucu üzerinde ağır bir yük. Yükü azaltın.<br /><br /> Artırmak <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> ayarı.<br /><br /> Bkz: [http://support.microsoft.com/?id=821268](http://go.microsoft.com/fwlink/?LinkID=179656) Web hizmeti performans ayarlarını değiştirmek için.|  
|<xref:System.Net.WebExceptionStatus.ConnectionClosed>|Uygulama zaten kapatılmış bir yuva yazma girişiminde bulunuldu.|İstemci veya sunucu aşırı yüklendi. Yükü azaltın.<br /><br /> Artırmak <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> ayarı.<br /><br /> Bkz: [http://support.microsoft.com/?id=821268](http://go.microsoft.com/fwlink/?LinkID=179656) Web hizmeti performans ayarlarını değiştirmek için.|  
|<xref:System.Net.WebExceptionStatus.MessageLengthLimitExceeded>|Belirlenen sınırı (<xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>) iletide uzunluğu aşıldı.|Değerini artırın <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A> özelliği.|  
|<xref:System.Net.WebExceptionStatus.ProxyNameResolutionFailure>|Etki alanı adı hizmeti proxy konak adı çözümlenemedi.|Proxy doğru şekilde yapılandırın. Bkz: [http://support.microsoft.com/?id=318140](http://go.microsoft.com/fwlink/?LinkID=179655).<br /><br /> Zorla <xref:System.Net.HttpWebRequest> ayarlayarak proxy kullanmayı <xref:System.Net.HttpWebRequest.Proxy%2A> özelliğine `null`.|  
|<xref:System.Net.WebExceptionStatus.ServerProtocolViolation>|Sunucudan gelen yanıtı geçerli bir HTTP yanıt değil. Sunucu yanıtı HTTP 1.1 RFC ile uyumlu değil, .NET Framework algıladığında, bu sorun oluşur. Yanıtı yanlış üstbilgilerinde veya yanlış üstbilgi ayırıcısı içeriyor. Bu sorun ortaya çıkabilir. RFC 2616 HTTP 1.1 ve sunucudan gelen yanıt geçerli biçimini tanımlar. Daha fazla bilgi için bkz: [http://www.ietf.org](http://go.microsoft.com/fwlink/?LinkID=147388).|İşlemin bir ağ izlemesi yapın ve yanıt üstbilgileri inceleyin.<br /><br /> Uygulamanız sunucu yanıtı olmadan gerektiriyorsa (Bu bir güvenlik sorunu olabilir) ayrıştırma, kümesi `useUnsafeHeaderParsing` için `true` yapılandırma dosyası. Bkz: [ \<httpWebRequest > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/httpwebrequest-element-network-settings.md).|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Net.HttpWebRequest>  
 <xref:System.Net.HttpWebResponse>  
 <xref:System.Net.Dns>
