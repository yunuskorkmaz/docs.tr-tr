---
title: WebRequest Sorunlarını ve Özel Durumları Anlama
ms.date: 03/30/2017
ms.assetid: 74a361a5-e912-42d3-8f2e-8e9a96880a2b
ms.openlocfilehash: 3a6dc06ed7abdbb6a28f9d6c09eda079157493d9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59215020"
---
# <a name="understanding-webrequest-problems-and-exceptions"></a>WebRequest Sorunlarını ve Özel Durumları Anlama
<xref:System.Net.WebRequest> türetilen sınıflar (<xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, ve <xref:System.Net.FileWebRequest>) olağan dışı bir koşul göstermek için özel durumlar. Bazı durumlarda bu sorunların çözümlenmesi belirgin değildir.  
  
## <a name="solutions"></a>Çözümler  
 İnceleme <xref:System.Net.WebException.Status%2A> özelliği <xref:System.Net.WebException> sorunu belirlemek için. Aşağıdaki tabloda, birkaç durum değerlerini ve bazı olası çözümleri gösterir.  
  
|Durum|Ayrıntılar|Çözüm|  
|------------|-------------|--------------|  
|<xref:System.Net.WebExceptionStatus.SendFailure><br /><br /> -veya-<br /><br /> <xref:System.Net.WebExceptionStatus.ReceiveFailure>|Temel alınan yuvası ile ilgili bir sorun yoktur. Bağlantı sıfırlandı.|Bağlanın ve isteği yeniden gönderin.<br /><br /> En son hizmet paketinin yüklü olduğundan emin olun.<br /><br /> Değeri Artır <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A?displayProperty=nameWithType> özelliği.<br /><br /> Ayarlama <xref:System.Net.HttpWebRequest.KeepAlive%2A?displayProperty=nameWithType> için `false`.<br /><br /> İle en fazla bağlantı sayısını artırmak <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> özelliği.<br /><br /> Proxy yapılandırmasını denetleyin.<br /><br /> SSL kullanıyorsanız, sunucu işlemi sertifika deposuna erişim izni olduğundan emin olun.<br /><br /> Büyük miktarda veri gönderme verilirse <xref:System.Net.HttpWebRequest.AllowWriteStreamBuffering%2A> için `false`.|  
|<xref:System.Net.WebExceptionStatus.TrustFailure>|Sunucu sertifikası doğrulanamadı.|Internet Explorer'ı kullanarak URI açmayı deneyin. IE tarafından görüntülenen tüm güvenlik uyarıları çözümleyin. Güvenlik Uyarısı çözümlenemiyor sonra uygulayan bir sertifika ilkesi sınıf oluşturabilirsiniz <xref:System.Net.ICertificatePolicy> döndüren `true`ve geçirin <xref:System.Net.ServicePointManager.CertificatePolicy%2A>.<br /><br /> Başvurmak <https://support.microsoft.com/?id=823177>.<br /><br /> İmzalı sunucu sertifikasının sertifika yetkilisinin sertifikayı Internet Explorer'da güvenilen sertifika yetkilisi listesine eklendiğinden emin olun.<br /><br /> URL ana bilgisayar adı sunucu sertifikasındaki ortak ad eşleştiğinden emin olun.|  
|<xref:System.Net.WebExceptionStatus.SecureChannelFailure>|SSL işlem sırasında bir hata oluştu veya sertifika ile ilgili bir sorun yoktur.|.NET Framework sürüm 1.1 yalnızca SSL 3.0 sürümünü destekler. Sunucu yalnızca TLS sürüm 1.0 veya sürüm 2.0 SSL kullanıyorsanız, özel durum oluşturulur. Yükseltme .NET Framework sürüm 2.0 ve ayarlama <xref:System.Net.ServicePointManager.SecurityProtocol%2A> sunucu eşleştirilecek.<br /><br /> İstemci sertifikası, sunucunun güvenmediği bir sertifika yetkilisi (CA) tarafından imzalanmış. CA sertifikasını sunucuya yükleyin. Bkz. <https://support.microsoft.com/?id=332077>.<br /><br /> En son hizmet paketinin yüklü olduğundan emin olun.|  
|<xref:System.Net.WebExceptionStatus.ConnectFailure>|Bağlantı başarısız oldu.|Bir güvenlik duvarı veya proxy bağlantıyı engelliyor. Güvenlik Duvarı veya proxy bağlantıya izin vermek için değiştirin.<br /><br /> Açıkça belirtmek bir <xref:System.Net.WebProxy> çağırarak istemci uygulamasındaki <xref:System.Net.WebProxy> Oluşturucusu (WebServiceProxyClass.Proxy yeni adımdaki ([http://server:80](http://server/), true)).<br /><br /> FileMon veya Regmon çalışan işlem kimliğini WSPWSP.dll, HKLM\System\CurrentControlSet\Services\DnsCache veya HKLM\System\CurrentControlSet\Services\WinSock2 erişmek için gerekli izinlere sahip olmamasını sağlamaya çalışır.|  
|<xref:System.Net.WebExceptionStatus.NameResolutionFailure>|Etki alanı adı hizmeti konak adı çözümlenemedi.|Proxy doğru şekilde yapılandırın. Bkz. <https://support.microsoft.com/?id=318140>.<br /><br /> Virüsten koruma yazılımının yüklü veya güvenlik duvarının bağlantıya engel olmadığından emin olun.|  
|<xref:System.Net.WebExceptionStatus.RequestCanceled>|<xref:System.Net.WebRequest.Abort%2A> çağrılan, veya bir hata oldu.|Bu sorunun nedeni istemci veya sunucu üzerinde ağır bir yük. Yükü azaltın.<br /><br /> Artırmak <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> ayarı.<br /><br /> Bkz: <https://support.microsoft.com/?id=821268> Web hizmeti performans ayarlarını değiştirmek için.|  
|<xref:System.Net.WebExceptionStatus.ConnectionClosed>|Uygulama zaten kapatılmış olan bir yuva yazılmaya çalışıldı.|İstemci veya sunucu aşırı yüklendi. Yükü azaltın.<br /><br /> Artırmak <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> ayarı.<br /><br /> Bkz: <https://support.microsoft.com/?id=821268> Web hizmeti performans ayarlarını değiştirmek için.|  
|<xref:System.Net.WebExceptionStatus.MessageLengthLimitExceeded>|Ayarlanan (<xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>) iletide uzunluğu aşıldı.|Değeri Artır <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A> özelliği.|  
|<xref:System.Net.WebExceptionStatus.ProxyNameResolutionFailure>|Etki alanı adı hizmeti proxy konak adı çözümlenemedi.|Proxy doğru şekilde yapılandırın. Bkz. <https://support.microsoft.com/?id=318140>.<br /><br /> Zorla <xref:System.Net.HttpWebRequest> hiçbir proxy ayarı kullanılacak <xref:System.Net.HttpWebRequest.Proxy%2A> özelliğini `null`.|  
|<xref:System.Net.WebExceptionStatus.ServerProtocolViolation>|Sunucudan yanıt, geçerli bir HTTP yanıt değil. .NET Framework sunucu yanıtı HTTP 1.1 RFC ile uyumlu değil algıladığında, bu sorun oluşur. Yanıt yanlış üst bilgiler veya yanlış başlık sınırlayıcılar içerdiğinde, bu sorun oluşabilir. RFC 2616'http 1.1 ve sunucudan yanıt geçerli biçimini tanımlar. Daha fazla bilgi için [RFC 2616 - Hypertext Transfer Protocol--HTTP/1.1](https://go.microsoft.com/fwlink/?LinkID=147388) adresindeki [Internet Engineering Task Force (IETF)](https://www.ietf.org/) Web sitesi.|Bir ağ izleme işlem alın ve yanıt üst bilgileri inceleyin.<br /><br /> Sunucu yanıtı olmadan uygulamanız gerekiyorsa (Bu bir güvenlik sorunu olabilir) ayrıştırma, kümesi `useUnsafeHeaderParsing` için `true` yapılandırma dosyası. Bkz: [ \<httpWebRequest > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/httpwebrequest-element-network-settings.md).|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.HttpWebRequest>
- <xref:System.Net.HttpWebResponse>
- <xref:System.Net.Dns>
