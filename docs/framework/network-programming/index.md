---
title: .NET Framework'te Ağ Programlaması
ms.date: 03/30/2017
helpviewer_keywords:
- Networking
- Internet
- Internet, .NET Framework Internet services
- Network Resources
ms.assetid: 8d455610-67a0-4fa8-a62f-7747064a9256
ms.openlocfilehash: 1e7f0123ab07fd4e83eea957b72bf79eeeecef2b
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204690"
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
  
 [İnternet Protokolü Sürüm 6](internet-protocol-version-6.md)  
 Internet Protokolü sürüm 6'nın (IPv6) Internet Protokolü paketinin geçerli sürümüne (IPv4) göre avantajlarını, IPv6 adresini, yönlendirmeyi, otomatik yapılandırmayı ve IPv6'nın nasıl etkinleştirileceğini ve devre dışı bırakılacağını açıklar.  
  
 [İnternet Uygulamalarını Yapılandırma](configuring-internet-applications.md)  
 .NET Framework yapılandırma dosyalarının Internet uygulamalarını yapılandırmak için nasıl kullanılacağını açıklar.  
  
 [.NET Framework'te Ağ İzleme](network-tracing.md)  
 Ağ izlemenin yönetilen uygulama tarafından oluşturulan yöntem çağrıları ve ağ trafiğiyle ilgili bilgiler almak için nasıl kullanılacağını açıklar.  
  
 [Ağ Uygulamaları için Önbellek Yönetimi](cache-management-for-network-applications.md)  
 <xref:System.Net.WebClient?displayProperty=nameWithType>, <xref:System.Net.WebRequest?displayProperty=nameWithType>ve <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> sınıflarını kullanan uygulamalar için önbelleğe almanın nasıl kullanılacağını açıklar.  
  
 [Ağ Programlama Güvenliği](security-in-network-programming.md)  
 Standart Internet güvenliği ve kimlik doğrulama tekniklerinin nasıl kullanılacağını açıklar.  
  
 [System.Net Sınıfları için En İyi Yöntemler](best-practices-for-system-net-classes.md)  
 Internet uygulamalarınızdan en iyi şekilde yararlanmanız için ipuçları ve püf noktaları sağlar.  
  
 [Ara Sunucu Üzerinden İnternet Erişimi](accessing-the-internet-through-a-proxy.md)  
 Proxy'lerin nasıl yapılandırılacağını açıklar.  
  
 [NetworkInformation](networkinformation.md)  
 Ağ olayları, değişiklikler, istatistikler ve özellikler hakkında nasıl bilgi toplayabileceğinizi ve ayrıca, <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> sınıfı kullanılarak uzak bir ana bilgisayarın erişilebilir olup olmadığını nasıl belirleyebileceğinizi açıklar.  
  
 [System.Uri ad alanında sürüm 2.0’da yapılan değişiklikler](changes-to-the-system-uri-namespace-in-version-2-0.md)  
 Sürüm 2,0 ' de <xref:System.Uri?displayProperty=nameWithType> sınıfında yapılan, yanlış davranışı düzeltilen, Kullanılabilirliği geliştiren ve güvenliği geliştiren çeşitli değişiklikler açıklanmaktadır.  
  
 [System.Uri’de Uluslararası Kaynak Tanımlayıcı Desteği](international-resource-identifier-support-in-system-uri.md)  
 Uluslararası kaynak tanımlayıcı (IRI) ve uluslararası etki alanı adı (ıDN) desteği için 3,5, 3,0 SP1 ve 2,0 SP1 sürümündeki <xref:System.Uri?displayProperty=nameWithType> sınıfına yönelik geliştirmeleri açıklar.  
  
 [Sürüm 3.5’teki Yuva Performansı Geliştirmeleri](socket-performance-enhancements-in-version-3-5.md)  
 Özel yüksek performanslı yuva uygulamaları tarafından kullanılabilen alternatif bir zaman uyumsuz model sağlayan 3,5, 3,0 SP1 ve 2,0 SP1 sürümündeki <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> sınıfına yönelik iyileştirmeler kümesini açıklar.  
  
 [Eş Adı Çözümleme Protokolü](peer-name-resolution-protocol.md)  
 Sunucusuz ve dinamik ad kayıt ve ad çözümleme protokolü olan Eş Adı Çözümleme Protokolü'nü (PNRP) desteklemek için Sürüm 3.5'e eklenen desteği açıklar. Bu yeni özellikler <xref:System.Net.PeerToPeer?displayProperty=nameWithType> ad alanı tarafından desteklenir.  
  
 [Eşler Arası İş Birliği](peer-to-peer-collaboration.md)  
 PNRP'yi temel alan Eşler Arası İşbirliği'ni desteklemek için Sürüm 3.5'e eklenen desteği açıklar. Bu yeni özellikler <xref:System.Net.PeerToPeer.Collaboration?displayProperty=nameWithType> ad alanı tarafından desteklenir.  
  
 [Sürüm 3.5 SP1’de HttpWebRequest için NTLM kimlik doğrulamasındaki değişiklikler](changes-to-ntlm-authentication-for-httpwebrequest-in-version-3-5-sp1.md)  
 Tümleşik Windows kimlik doğrulamasının, System.Net ad alanındaki <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>, <xref:System.Net.HttpListener?displayProperty=nameWithType>, <xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType>ve ilgili sınıfların nasıl işlendiğini etkileyen sürüm 3,5 SP1 'de yapılan güvenlik değişikliklerini açıklar.  
  
 [Genişletilmiş Koruma ile Tümleşik Windows Kimlik Doğrulaması](integrated-windows-authentication-with-extended-protection.md)  
 Tümleşik Windows kimlik doğrulamasının, <xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType>ve ilgili ad alanlarında <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>, <xref:System.Net.HttpListener?displayProperty=nameWithType>, <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>, <xref:System.Net.Security.SslStream?displayProperty=nameWithType>, <xref:System.Net?displayProperty=nameWithType> ve ilgili sınıflar tarafından nasıl işlendiğini etkileyen genişletilmiş korumaya yönelik geliştirmeleri açıklar.  
  
 [IPv6 ve Teredo kullanarak NAT Geçişi](nat-traversal-using-ipv6-and-teredo.md)  
 IPv6 ve Teredo kullanarak NAT geçişini desteklemek için <xref:System.Net?displayProperty=nameWithType>, <xref:System.Net.NetworkInformation?displayProperty=nameWithType>ve <xref:System.Net.Sockets?displayProperty=nameWithType> ad alanlarına eklenen geliştirmeleri açıklar.  
  
 [Windows Mağazası Uygulamaları için Ağ Yalıtımı](network-isolation-for-windows-store-apps.md)  
 <xref:System.Net>, <xref:System.Net.Http>ve <xref:System.Net.Http.Headers> ad alanları Windows 8. x Mağaza uygulamalarında kullanıldığında ağ yalıtımının etkilerini açıklar.  
  
 [Ağ Programlama Örnekleri](network-programming-samples.md)  
 <xref:System.Net>, <xref:System.Net.Cache>, <xref:System.Net.Configuration>, <xref:System.Net.Mail>, <xref:System.Net.Mime>, <xref:System.Net.NetworkInformation>, <xref:System.Net.PeerToPeer>, <xref:System.Net.Security>, <xref:System.Net.Sockets> ad alanlarında sınıfları kullanan indirilebilir ağ programlama örneklerine bağlantılar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Net?displayProperty=nameWithType>  
 Günümüzde ağlarda kullanılan birçok protokol için basit bir programlama arabirimi sağlar. Bu ad alanındaki <xref:System.Net.WebRequest?displayProperty=nameWithType> ve <xref:System.Net.WebResponse?displayProperty=nameWithType> sınıfları takılabilir protokollerin temelini oluşturur.  
  
 <xref:System.Net.Cache?displayProperty=nameWithType>  
 <xref:System.Net.WebRequest?displayProperty=nameWithType> ve <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> sınıfları kullanılarak elde edilen kaynaklar için önbellek ilkelerini tanımlamak üzere kullanılan türleri ve numaralandırmaları tanımlar.  
  
 <xref:System.Net.Configuration?displayProperty=nameWithType>  
 Uygulamaların System.Net ad alanlarının yapılandırma ayarlarına programlı bir şekilde erişmek ve bunları güncelleştirmek için kullandığı sınıflar.  
  
 <xref:System.Net.Http?displayProperty=nameWithType>  
 Modern HTTP uygulamaları için programlama arabirimi sağlayan sınıflar.  
  
 <xref:System.Net.Http.Headers?displayProperty=nameWithType>  
 <xref:System.Net.Http?displayProperty=nameWithType> ad alanı tarafından kullanılan HTTP üstbilgileri koleksiyonları için destek sağlar  
  
 <xref:System.Net.Mail?displayProperty=nameWithType>  
 SMTP protokolünü kullanarak e-posta oluşturan ve gönderen sınıflar.  
  
 <xref:System.Net.Mime?displayProperty=nameWithType>  
 <xref:System.Net.Mail?displayProperty=nameWithType> ad alanındaki sınıflar tarafından kullanılan çok amaçlı Internet posta değişimi (MIME) üstbilgilerini temsil etmek için kullanılan türleri tanımlar.  
  
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
