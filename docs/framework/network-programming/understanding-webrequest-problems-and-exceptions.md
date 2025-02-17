---
title: WebRequest Sorunlarını ve Özel Durumları Anlama
description: WebRequest ve türetilen sınıflar, olağan dışı koşullara sinyal vermek için özel durumlar oluşturur. .NET Framework bu koşulları çözmek için bu olası çözümleri kullanın.
ms.date: 03/30/2017
ms.assetid: 74a361a5-e912-42d3-8f2e-8e9a96880a2b
ms.openlocfilehash: 27fde2a3cf3e6a3469a47bdd9efe70d31620777d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236331"
---
# <a name="understanding-webrequest-problems-and-exceptions"></a>WebRequest Sorunlarını ve Özel Durumları Anlama

<xref:System.Net.WebRequest> ve türetilmiş sınıfları ( <xref:System.Net.HttpWebRequest> , <xref:System.Net.FtpWebRequest> ve <xref:System.Net.FileWebRequest> ) olağan dışı bir koşula işaret etmek için özel durumlar oluşturur. Bazen bu sorunların çözümlenmesi belirgin değildir.  
  
## <a name="solutions"></a>Çözümler  

 <xref:System.Net.WebException.Status%2A> <xref:System.Net.WebException> Sorunu anlamak için öğesinin özelliğini inceleyin. Aşağıdaki tabloda birkaç durum değeri ve olası bazı çözümler gösterilmektedir.  
  
|Durum|Ayrıntılar|Çözüm|  
|------------|-------------|--------------|  
|<xref:System.Net.WebExceptionStatus.SendFailure><br /><br /> -veya-<br /><br /> <xref:System.Net.WebExceptionStatus.ReceiveFailure>|Temeldeki yuvada bir sorun var. Bağlantı sıfırlanmış olabilir.|Yeniden bağlanın ve isteği yeniden gönderin.<br /><br /> En son hizmet paketinin yüklü olduğundan emin olun.<br /><br /> Özelliğin değerini artırın <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A?displayProperty=nameWithType> .<br /><br /> <xref:System.Net.HttpWebRequest.KeepAlive%2A?displayProperty=nameWithType>Olarak ayarlayın `false` .<br /><br /> Özelliği ile maksimum bağlantı sayısını artırın <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> .<br /><br /> Ara sunucu yapılandırmasını denetleyin.<br /><br /> SSL kullanıyorsanız, sunucu işleminin sertifika deposuna erişim izni olduğundan emin olun.<br /><br /> Büyük miktarda veri gönderiyorsanız, <xref:System.Net.HttpWebRequest.AllowWriteStreamBuffering%2A> olarak ayarlayın `false` .|  
|<xref:System.Net.WebExceptionStatus.TrustFailure>|Sunucu sertifikası doğrulanamadı.|Internet Explorer 'ı kullanarak URI 'yi açmayı deneyin. IE tarafından görünen tüm güvenlik uyarılarını çözün. Güvenlik uyarısını çözemezseniz, döndüren öğesini uygulayan bir sertifika ilkesi sınıfı oluşturabilir <xref:System.Net.ICertificatePolicy> `true` ve bunu öğesine geçitirsiniz <xref:System.Net.ServicePointManager.CertificatePolicy%2A> .<br /><br /> Adresine bakın <https://support.microsoft.com/?id=823177> .<br /><br /> Sunucu sertifikasını imzalayan sertifika yetkilisinin sertifikasının, Internet Explorer 'daki güvenilir sertifika yetkilisi listesine eklendiğinden emin olun.<br /><br /> URL 'deki ana bilgisayar adının Sunucu sertifikasındaki ortak ad ile eşleştiğinden emin olun.|  
|<xref:System.Net.WebExceptionStatus.SecureChannelFailure>|SSL işleminde bir hata oluştu veya bir sertifika sorunu var.|.NET Framework sürüm 1,1 yalnızca SSL sürüm 3,0 ' i destekler. Sunucu yalnızca TLS sürüm 1,0 veya SSL sürüm 2,0 kullanıyorsa, özel durum oluşturulur. .NET Framework sürüm 2,0 ' e yükseltin ve <xref:System.Net.ServicePointManager.SecurityProtocol%2A> sunucusuyla eşleşecek şekilde ayarlayın.<br /><br /> İstemci sertifikası, sunucunun güvenmediğinden bir sertifika yetkilisi (CA) tarafından imzalandı. CA 'nın sertifikasını sunucuya yükler. Bkz. <https://support.microsoft.com/?id=332077>.<br /><br /> En son hizmet paketinin yüklü olduğundan emin olun.|  
|<xref:System.Net.WebExceptionStatus.ConnectFailure>|Bağlantı başarısız oldu.|Bir güvenlik duvarı veya proxy bağlantıyı engelliyor. Güvenlik duvarını veya ara sunucuyu bağlantıya izin verecek şekilde değiştirin.<br /><br /> <xref:System.Net.WebProxy>Oluşturucuyu () çağırarak istemci uygulamasında açıkça bir belirleyin <xref:System.Net.WebProxy> `WebServiceProxyClass.Proxy = new WebProxy("http://server:80", true)` .<br /><br /> Çalışan işlem kimliğinin WSPWSP.dll, HKLM\System\CurrentControlSet\Services\DnsCache veya HKLM\System\CurrentControlSet\Services\WinSock2. erişmek için gerekli izinlere sahip olduğundan emin olmak için FileMon veya Regmon komutunu çalıştırın|  
|<xref:System.Net.WebExceptionStatus.NameResolutionFailure>|Etki alanı adı hizmeti ana bilgisayar adını çözümleyemedi.|Proxy 'yi doğru şekilde yapılandırın. Bkz. <https://support.microsoft.com/?id=318140>.<br /><br /> Yüklü olan tüm virüsten koruma yazılımlarının veya güvenlik duvarının bağlantıyı engellemediğinden emin olun.|  
|<xref:System.Net.WebExceptionStatus.RequestCanceled>|<xref:System.Net.WebRequest.Abort%2A> çağrıldı veya bir hata oluştu.|Bu sorun, istemci veya sunucu üzerindeki ağır yükün kaynaklanıyor olabilir. Yükü azaltın.<br /><br /> Ayarı arttırın <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> .<br /><br /> Bkz <https://support.microsoft.com/?id=821268> . Web hizmeti performans ayarlarını değiştirmek için.|  
|<xref:System.Net.WebExceptionStatus.ConnectionClosed>|Uygulama zaten kapatılmış olan bir yuvaya yazmaya çalıştı.|İstemci veya sunucu aşırı yüklendi. Yükü azaltın.<br /><br /> Ayarı arttırın <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> .<br /><br /> Bkz <https://support.microsoft.com/?id=821268> . Web hizmeti performans ayarlarını değiştirmek için.|  
|<xref:System.Net.WebExceptionStatus.MessageLengthLimitExceeded>|İleti uzunluğundaki sınır kümesi ( <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A> ) aşıldı.|Özelliğin değerini artırın <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A> .|  
|<xref:System.Net.WebExceptionStatus.ProxyNameResolutionFailure>|Etki alanı adı hizmeti, proxy ana bilgisayar adını çözümleyemedi.|Proxy 'yi doğru şekilde yapılandırın. Bkz. <https://support.microsoft.com/?id=318140>.<br /><br /> <xref:System.Net.HttpWebRequest>Özelliğini olarak ayarlayarak proxy olmadan kullanmaya zorlayın <xref:System.Net.HttpWebRequest.Proxy%2A> `null` .|  
|<xref:System.Net.WebExceptionStatus.ServerProtocolViolation>|Sunucudan gelen yanıt geçerli bir HTTP yanıtı değil. Bu sorun, .NET Framework sunucu yanıtının HTTP 1,1 RFC ile uyumlu olmadığı algıladığında oluşur. Yanıtta hatalı üstbilgiler veya yanlış üstbilgi sınırlayıcıları içerdiğinde bu sorun oluşabilir. RFC 2616, HTTP 1,1 ve sunucudan yanıt için geçerli biçimi tanımlar. Daha fazla bilgi için bkz. [RFC 2616-HyperText aktarım protokolü--](https://tools.ietf.org/html/rfc2616) [Internet Mühendisliği görev gücü (IETF)](https://www.ietf.org/) Web sitesinde http/1.1.|İşlemin bir ağ izlemesini alın ve yanıttaki üstbilgileri inceleyin.<br /><br /> Uygulamanız, ayrıştırma olmadan sunucu yanıtı gerektiriyorsa (Bu bir güvenlik sorunu olabilir) `useUnsafeHeaderParsing` `true` yapılandırma dosyasında olarak ayarlanır. Bkz. [ \<httpWebRequest> öğesi (ağ ayarları)](../configure-apps/file-schema/network/httpwebrequest-element-network-settings.md).|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.HttpWebRequest>
- <xref:System.Net.HttpWebResponse>
- <xref:System.Net.Dns>
