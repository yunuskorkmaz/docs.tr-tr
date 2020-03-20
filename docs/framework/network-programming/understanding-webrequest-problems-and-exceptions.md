---
title: WebRequest Sorunlarını ve Özel Durumları Anlama
ms.date: 03/30/2017
ms.assetid: 74a361a5-e912-42d3-8f2e-8e9a96880a2b
ms.openlocfilehash: 172ad7508bdcac94cc278faab65a2e265b3c6a65
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "76743894"
---
# <a name="understanding-webrequest-problems-and-exceptions"></a>WebRequest Sorunlarını ve Özel Durumları Anlama
<xref:System.Net.WebRequest>ve türetilmiş<xref:System.Net.HttpWebRequest> <xref:System.Net.FtpWebRequest>sınıfları <xref:System.Net.FileWebRequest>( , , ve ) anormal bir durum sinyal istisnaları atmak. Bazen bu sorunların çözümü açık değildir.  
  
## <a name="solutions"></a>Çözümler  
 Sorunu <xref:System.Net.WebException.Status%2A> belirlemek <xref:System.Net.WebException> için özelliğini inceleyin. Aşağıdaki tabloda birkaç durum değerleri ve bazı olası çözümler gösterilmektedir.  
  
|Durum|Ayrıntılar|Çözüm|  
|------------|-------------|--------------|  
|<xref:System.Net.WebExceptionStatus.SendFailure><br /><br /> -veya-<br /><br /> <xref:System.Net.WebExceptionStatus.ReceiveFailure>|Altta yatan soket ile ilgili bir sorun var. Bağlantı sıfırlanmış olabilir.|İsteği yeniden bağlayın ve yeniden gönderin.<br /><br /> En son servis paketinin yüklü olduğundan emin olun.<br /><br /> Özelliğin değerini <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A?displayProperty=nameWithType> artırın.<br /><br /> `false`Ayarlayın. <xref:System.Net.HttpWebRequest.KeepAlive%2A?displayProperty=nameWithType><br /><br /> Özellik ile maksimum bağlantı sayısını <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> artırın.<br /><br /> Proxy yapılandırmasını denetleyin.<br /><br /> SSL kullanıyorsanız, sunucu işleminin Sertifika deposuna erişmek için izni olduğundan emin olun.<br /><br /> Büyük miktarda veri gönderiyorsanız, <xref:System.Net.HttpWebRequest.AllowWriteStreamBuffering%2A> `false`'' olarak ayarlayın.|  
|<xref:System.Net.WebExceptionStatus.TrustFailure>|Sunucu sertifikası doğrulanamadı.|Internet Explorer kullanarak URI'yi açmayı deneyin. IE tarafından görüntülenen güvenlik uyarılarını çözümleyin. Güvenlik uyarısını çözemiyorsanız, <xref:System.Net.ICertificatePolicy> döndüren `true`bir sertifika ilkesi sınıfı oluşturabilir ve <xref:System.Net.ServicePointManager.CertificatePolicy%2A>bunu ' ya aktarabilirsiniz.<br /><br /> <https://support.microsoft.com/?id=823177>Bkz. .<br /><br /> Sunucu sertifikasını imzalayan Sertifika Yetkilisi sertifikasının Internet Explorer'daki Güvenilir Sertifika Yetkilisi listesine eklenmiş olduğundan emin olun.<br /><br /> URL'deki ana bilgisayar adının sunucu sertifikasındaki ortak adla eşleştiğinden emin olun.|  
|<xref:System.Net.WebExceptionStatus.SecureChannelFailure>|SSL hareketinde bir hata oluştu veya bir sertifika sorunu var.|.NET Framework sürüm 1.1 yalnızca SSL sürüm 3.0'ı destekler. Sunucu yalnızca TLS sürüm 1.0 veya SSL sürüm 2.0 kullanıyorsa, özel durum atılır. .NET Framework sürüm 2.0'a <xref:System.Net.ServicePointManager.SecurityProtocol%2A> yükseltin ve sunucuyla eşleşecek şekilde ayarlayın.<br /><br /> İstemci sertifikası, sunucunun güvenmediği bir Sertifika Yetkilisi (CA) tarafından imzalanmıştır. CA sertifikasını sunucuya yükleyin. Bkz. <https://support.microsoft.com/?id=332077>.<br /><br /> En son servis paketinin yüklü olduğundan emin olun.|  
|<xref:System.Net.WebExceptionStatus.ConnectFailure>|Bağlantı başarısız oldu.|Bir güvenlik duvarı veya proxy bağlantıyı engelliyor. Bağlantıya izin vermek için güvenlik duvarını veya proxy'yi değiştirin.<br /><br /> İstemci <xref:System.Net.WebProxy> uygulamasında açıkça <xref:System.Net.WebProxy> bir oluşturucuyu`WebServiceProxyClass.Proxy = new WebProxy("http://server:80", true)`arayarak bir belir( ).<br /><br /> İşçi işlem kimliğinin WSPWSP.dll, HKLM\System\CurrentControlSet\Services\DnsCache veya HKLM\System\CurrentControlSet\Services\WinSock2'ye erişmek için gerekli izinlere sahip olduğundan emin olmak için Filemon veya Regmon çalıştırın.|  
|<xref:System.Net.WebExceptionStatus.NameResolutionFailure>|Alan Adı Hizmeti ana bilgisayar adını çözümlemedi.|Proxy'yi doğru şekilde yapılandırın. Bkz. <https://support.microsoft.com/?id=318140>.<br /><br /> Yüklü herhangi bir virüsten koruma yazılımının veya güvenlik duvarının bağlantıyı engellemediğinden emin olun.|  
|<xref:System.Net.WebExceptionStatus.RequestCanceled>|<xref:System.Net.WebRequest.Abort%2A>çağrıldı veya bir hata oluştu.|Bu sorun istemci veya sunucuüzerinde ağır bir yük neden olabilir. Yükü azaltın.<br /><br /> Ayarı <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> artırın.<br /><br /> Web <https://support.microsoft.com/?id=821268> hizmeti performans ayarlarını değiştirmeye bakın.|  
|<xref:System.Net.WebExceptionStatus.ConnectionClosed>|Uygulama zaten kapatılan bir sokete yazmaya çalıştı.|İstemci veya sunucu aşırı yüklenmiş. Yükü azaltın.<br /><br /> Ayarı <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> artırın.<br /><br /> Web <https://support.microsoft.com/?id=821268> hizmeti performans ayarlarını değiştirmeye bakın.|  
|<xref:System.Net.WebExceptionStatus.MessageLengthLimitExceeded>|İleti uzunluğundaki<xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>sınır kümesi ( ) aşıldı.|Özelliğin değerini <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A> artırın.|  
|<xref:System.Net.WebExceptionStatus.ProxyNameResolutionFailure>|Alan Adı Hizmeti proxy ana bilgisayar adını çözemedi.|Proxy'yi doğru şekilde yapılandırın. Bkz. <https://support.microsoft.com/?id=318140>.<br /><br /> <xref:System.Net.HttpWebRequest.Proxy%2A> Özelliği `null`' ye ayarlayarak proxy kullanmaya zorlama <xref:System.Net.HttpWebRequest>|  
|<xref:System.Net.WebExceptionStatus.ServerProtocolViolation>|Sunucudan gelen yanıt geçerli bir HTTP yanıtı değildir. Bu sorun, .NET Framework sunucu yanıtının HTTP 1.1 RFC'ye uymadığını algıladığında oluşur. Bu sorun, yanıt yanlış üstbilgi veya yanlış üstbilgi sınırlayıcılar içerdiğinde oluşabilir. RFC 2616, HTTP 1.1'i ve sunucudan gelen yanıt için geçerli biçimi tanımlar. Daha fazla bilgi için, [Internet Engineering Task Force (IETF)](https://www.ietf.org/) web sitesinden [RFC 2616 - Hypertext Transfer Protocol - HTTP/1.1'e](https://tools.ietf.org/html/rfc2616) bakın.|İşlemin ağ izlemesini alın ve yanıttaki üstbilgiinceleyin.<br /><br /> Uygulamanız ayrışma olmadan sunucu yanıtını gerektiriyorsa (bu `useUnsafeHeaderParsing` bir `true` güvenlik sorunu olabilir), yapılandırma dosyasında ayarlayın. [ \<Bkz. httpWebRequest> Öğesi (Ağ Ayarları)](../configure-apps/file-schema/network/httpwebrequest-element-network-settings.md).|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.HttpWebRequest>
- <xref:System.Net.HttpWebResponse>
- <xref:System.Net.Dns>
