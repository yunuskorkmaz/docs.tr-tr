---
title: .NET Framework'te Ağ Programlaması
description: .NET Framework tarafından sunulan Internet hizmetlerinin katmanlı, genişletilebilir ve yönetilen uygulamasını uygulamalarınıza bütünleştirmek için bu kaynakları kullanın.
ms.date: 03/30/2017
helpviewer_keywords:
- Networking
- Internet
- Internet, .NET Framework Internet services
- Network Resources
ms.assetid: 8d455610-67a0-4fa8-a62f-7747064a9256
ms.openlocfilehash: 117fce887a04def7f9b3f7654a8e9e675ea462d2
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502411"
---
# <a name="network-programming-in-the-net-framework"></a>.NET Framework'te Ağ Programlaması
Microsoft .NET Framework, uygulamalarınızla hızlı ve kolay bir şekilde tümleştirilebilen katmanlı, genişletilebilir ve yönetilen Internet hizmetleri sağlar. Ağ uygulamalarınız, yeni Internet protokollerinden otomatik olarak yararlanabilmek için takılabilir protokolleri temel alabilir veya ağ ile yuva düzeyinde çalışmak için Windows yuva arabiriminin yönetilen uygulamasını kullanabilir.  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [Takılabilir Protokollere Giriş](introducing-pluggable-protocols.md)  
 Bir Internet kaynağına, ihtiyaç duyduğu erişim protokolüne bakılmaksızın nasıl erişileceğini açıklar.  
  
 [Veri İsteme](requesting-data.md)  
 Internet kaynaklarında veri yüklemek ve indirmek için takılabilir protokollerin nasıl kullanılacağını açıklar.  
  
 [Takılabilir Protokoller Programlama](programming-pluggable-protocols.md)  
 Takılabilir protokoller uygulamak için protokole özgü sınıfların nasıl türetileceğini açıklar.  
  
 [Uygulama Protokolleri Kullanma](using-application-protocols.md)  
 TCP, UDP ve HTTP gibi ağ protokollerinden yararlanan programlama uygulamalarını açıklar.  
  
 [Internet Protokolü sürüm 6](internet-protocol-version-6.md)  
 Internet Protokolü sürüm 6'nın (IPv6) Internet Protokolü paketinin geçerli sürümüne (IPv4) göre avantajlarını, IPv6 adresini, yönlendirmeyi, otomatik yapılandırmayı ve IPv6'nın nasıl etkinleştirileceğini ve devre dışı bırakılacağını açıklar.  
  
 [İnternet Uygulamalarını Yapılandırma](configuring-internet-applications.md)  
 .NET Framework yapılandırma dosyalarının Internet uygulamalarını yapılandırmak için nasıl kullanılacağını açıklar.  
  
 [.NET Framework'te Ağ İzleme](network-tracing.md)  
 Ağ izlemenin yönetilen uygulama tarafından oluşturulan yöntem çağrıları ve ağ trafiğiyle ilgili bilgiler almak için nasıl kullanılacağını açıklar.  
  
 [Ağ Uygulamaları için Önbellek Yönetimi](cache-management-for-network-applications.md)  
 <xref:System.Net.WebClient?displayProperty=nameWithType>, Ve sınıflarını kullanan uygulamalar için önbelleğe almanın nasıl kullanılacağını açıklar <xref:System.Net.WebRequest?displayProperty=nameWithType> <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> .  
  
 [Ağ Programlama Güvenliği](security-in-network-programming.md)  
 Standart Internet güvenliği ve kimlik doğrulama tekniklerinin nasıl kullanılacağını açıklar.  
  
 [System.Net Sınıfları için En İyi Yöntemler](best-practices-for-system-net-classes.md)  
 Internet uygulamalarınızdan en iyi şekilde yararlanmanız için ipuçları ve püf noktaları sağlar.  
  
 [Ara Sunucu Üzerinden İnternet Erişimi](accessing-the-internet-through-a-proxy.md)  
 Proxy'lerin nasıl yapılandırılacağını açıklar.  
  
 [NetworkInformation](networkinformation.md)  
 Ağ olayları, değişiklikler, istatistikler ve özellikler hakkında bilgi toplama işlemini açıklar ve ayrıca sınıfı kullanılarak uzak bir ana bilgisayarın erişilebilir olup olmadığını nasıl belirleyebileceğinizi açıklar <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> .  
  
 [System.Uri ad alanında sürüm 2.0’da yapılan değişiklikler](changes-to-the-system-uri-namespace-in-version-2-0.md)  
 <xref:System.Uri?displayProperty=nameWithType>Sürüm 2,0 ' de, yanlış davranışa düzeltilen, Kullanılabilirliği geliştiren ve güvenliği geliştiren birkaç değişikliği açıklar.  
  
 [System.Uri’de Uluslararası Kaynak Tanımlayıcı Desteği](international-resource-identifier-support-in-system-uri.md)  
 <xref:System.Uri?displayProperty=nameWithType>Uluslararası kaynak tanımlayıcı (IRI) ve uluslararası etki alanı adı (IDN) desteği için 3,5, 3,0 SP1 ve 2,0 SP1 sürümündeki sınıfa yönelik geliştirmeleri açıklar.  
  
 [Sürüm 3.5’teki Yuva Performansı Geliştirmeleri](socket-performance-enhancements-in-version-3-5.md)  
 <xref:System.Net.Sockets.Socket?displayProperty=nameWithType>Özel yüksek performanslı yuva uygulamaları tarafından kullanılabilen alternatif bir zaman uyumsuz model sağlayan sürüm 3,5, 3,0 SP1 ve 2,0 SP1 içindeki sınıfa yönelik iyileştirmeler kümesini açıklar.  
  
 [Eş Adı Çözümleme Protokolü](peer-name-resolution-protocol.md)  
 Sunucusuz ve dinamik ad kayıt ve ad çözümleme protokolü olan Eş Adı Çözümleme Protokolü'nü (PNRP) desteklemek için Sürüm 3.5'e eklenen desteği açıklar. Bu yeni özellikler ad alanı tarafından desteklenir <xref:System.Net.PeerToPeer?displayProperty=nameWithType> .  
  
 [Eşler Arası İş Birliği](peer-to-peer-collaboration.md)  
 PNRP'yi temel alan Eşler Arası İşbirliği'ni desteklemek için Sürüm 3.5'e eklenen desteği açıklar. Bu yeni özellikler ad alanı tarafından desteklenir <xref:System.Net.PeerToPeer.Collaboration?displayProperty=nameWithType> .  
  
 [Sürüm 3.5 SP1’de HttpWebRequest için NTLM kimlik doğrulamasındaki değişiklikler](changes-to-ntlm-authentication-for-httpwebrequest-in-version-3-5-sp1.md)  
 Tümleşik Windows kimlik doğrulamasının,,, <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> <xref:System.Net.HttpListener?displayProperty=nameWithType> <xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType> ve System.net ad alanındaki ilgili sınıflar tarafından nasıl işlendiğini etkileyen sürüm 3,5 SP1 'de yapılan güvenlik değişikliklerini açıklar.  
  
 [Genişletilmiş Koruma ile Tümleşik Windows Kimlik Doğrulaması](integrated-windows-authentication-with-extended-protection.md)  
 Tümleşik Windows kimlik doğrulamasının <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> <xref:System.Net.HttpListener?displayProperty=nameWithType> <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> <xref:System.Net.Security.SslStream?displayProperty=nameWithType> <xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType> <xref:System.Net?displayProperty=nameWithType> ve ilgili ad alanlarında,,,, ve ilgili sınıfların işlenme biçimini etkileyen genişletilmiş korumaya yönelik geliştirmeleri açıklar.  
  
 [IPv6 ve Teredo kullanarak NAT Geçişi](nat-traversal-using-ipv6-and-teredo.md)  
 <xref:System.Net?displayProperty=nameWithType> <xref:System.Net.NetworkInformation?displayProperty=nameWithType> <xref:System.Net.Sockets?displayProperty=nameWithType> IPv6 ve Teredo kullanılarak NAT geçişini desteklemek için, ve ad alanlarına eklenen geliştirmeleri açıklar.  
  
 [Windows Mağazası Uygulamaları için Ağ Yalıtımı](network-isolation-for-windows-store-apps.md)  
 <xref:System.Net>, <xref:System.Net.Http> , Ve ad alanlarındaki sınıflar <xref:System.Net.Http.Headers> Windows 8. x Mağaza uygulamalarında kullanıldığında ağ yalıtımının etkilerini açıklar.  
  
 [Ağ Programlama Örnekleri](network-programming-samples.md)  
 ,,,,,, <xref:System.Net> <xref:System.Net.Cache> ,, <xref:System.Net.Configuration> <xref:System.Net.Mail> <xref:System.Net.Mime> <xref:System.Net.NetworkInformation> <xref:System.Net.PeerToPeer> <xref:System.Net.Security> <xref:System.Net.Sockets> Ad alanlarında sınıfları kullanan indirilebilir ağ programlama örneklerine bağlantılar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Net?displayProperty=nameWithType>  
 Günümüzde ağlarda kullanılan birçok protokol için basit bir programlama arabirimi sağlar. <xref:System.Net.WebRequest?displayProperty=nameWithType> <xref:System.Net.WebResponse?displayProperty=nameWithType> Bu ad alanındaki ve sınıfları takılabilir protokollerin temelini oluşturur.  
  
 <xref:System.Net.Cache?displayProperty=nameWithType>  
 Ve sınıfları kullanılarak elde edilen kaynaklar için önbellek ilkelerini tanımlamak üzere kullanılan türleri ve numaralandırmaları <xref:System.Net.WebRequest?displayProperty=nameWithType> tanımlar <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> .  
  
 <xref:System.Net.Configuration?displayProperty=nameWithType>  
 Uygulamaların System.Net ad alanlarının yapılandırma ayarlarına programlı bir şekilde erişmek ve bunları güncelleştirmek için kullandığı sınıflar.  
  
 <xref:System.Net.Http?displayProperty=nameWithType>  
 Modern HTTP uygulamaları için programlama arabirimi sağlayan sınıflar.  
  
 <xref:System.Net.Http.Headers?displayProperty=nameWithType>  
 Ad alanı tarafından kullanılan HTTP üst bilgileri koleksiyonları için destek sağlar <xref:System.Net.Http?displayProperty=nameWithType>  
  
 <xref:System.Net.Mail?displayProperty=nameWithType>  
 SMTP protokolünü kullanarak e-posta oluşturan ve gönderen sınıflar.  
  
 <xref:System.Net.Mime?displayProperty=nameWithType>  
 Ad alanındaki sınıflar tarafından kullanılan çok amaçlı Internet posta değişimi (MIME) üstbilgilerini temsil etmek için kullanılan türleri tanımlar <xref:System.Net.Mail?displayProperty=nameWithType> .  
  
 <xref:System.Net.NetworkInformation?displayProperty=nameWithType>  
 Ağ olayları, değişiklikler, istatistikler ve özellikler hakkında programlı bir şekilde bilgi toplayan sınıflar.  
  
 <xref:System.Net.PeerToPeer?displayProperty=nameWithType>  
 Geliştiriciler için Eş Adı Çözümleme Protokolü'nün (PNRP) yönetilen bir uygulamasını sağlar.  
  
 <xref:System.Net.PeerToPeer.Collaboration?displayProperty=nameWithType>  
 Geliştiriciler için Eşler Arası İşbirliği'nin yönetilen bir uygulamasını sağlar.  
  
 <xref:System.Net.Security?displayProperty=nameWithType>  
 Ana bilgisayarlar arasında güvenli iletişim için ağ akışlarını sağlayan sınıflar.  
  
 <xref:System.Net.Sockets?displayProperty=nameWithType>  
 Ağa erişimin denetlenmesine yardımcı olmak isteyen geliştiriciler için Windows Sockets'in (Winsock) yönetilen bir uygulamasını sağlar.  
  
 <xref:System.Net.WebSockets?displayProperty=nameWithType>  
 Geliştiriciler için WebSocket'in yönetilen bir uygulamasını sağlar.  
  
 <xref:System.Uri?displayProperty=nameWithType>  
 Tekdüzen kaynak tanımlayıcısının (URI) nesne temsilini ve URI'nin bölümlerine kolay erişim sağlar.  
  
 <xref:System.Security.Authentication.ExtendedProtection?displayProperty=nameWithType>  
 Uygulamalar için genişletilmiş koruma kullanarak kimlik doğrulama desteği sağlar.  
  
 <xref:System.Security.Authentication.ExtendedProtection.Configuration?displayProperty=nameWithType>  
 Uygulamalar için genişletilmiş koruma kullanarak kimlik doğrulama yapılandırmasına yönelik destek sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework ile Aktarım Katmanı Güvenliği (TLS) en iyi uygulamaları](tls.md)
- [Görsel Katman Programlama ile İlgili Nasıl Yapılır Konuları](network-programming-how-to-topics.md)
- [Ağ Programlama Örnekleri](network-programming-samples.md)
- [HttpClient örneği](https://code.msdn.microsoft.com/windowsapps/HttpClient-sample-55700664)
