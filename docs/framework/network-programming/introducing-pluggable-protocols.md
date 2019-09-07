---
title: Takılabilir Protokollere Giriş
ms.date: 03/30/2017
helpviewer_keywords:
- data requests, pluggable protocols
- WebRequest class, pluggable protocols
- response to Internet request, pluggable protocols
- URI
- Windows Sockets
- request/response model
- sending data, pluggable protocols
- pluggable protocols
- WebClient class, about WebClient class
- pluggable protocols, about pluggable protocols
- Internet, pluggable protocols
- path identifiers
- Uniform Resource Identifier
- application development [.NET Framework], pluggable protocols
- requesting data from Internet, pluggable protocols
- receiving data, pluggable protocols
- protocols, pluggable
- server identifiers
- scheme identifiers
ms.assetid: 4b48e22d-e4e5-48f0-be80-d549bda97415
ms.openlocfilehash: 41a55df53f8b0dfd4eefc9bc4ecf6b2eef122c8d
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70394271"
---
# <a name="introducing-pluggable-protocols"></a>Takılabilir Protokollere Giriş
Microsoft .NET Framework, uygulamalarınıza hızlı ve kolay bir şekilde tümleştirilebilen Internet hizmetlerinin katmanlı, genişletilebilir ve yönetilen bir uygulamasını sağlar. <xref:System.Net> Ve<xref:System.Net.Sockets> ad alanlarındaki Internet erişim sınıfları hem Web tabanlı hem de internet tabanlı uygulamaları uygulamak için kullanılabilir.  
  
## <a name="internet-applications"></a>Internet uygulamaları  
 Internet uygulamaları iki tür için de sınıflandırılabilir: istemcilerden gelen bilgi isteklerine yanıt veren bilgi ve sunucu uygulamaları isteyen istemci uygulamalar. Klasik Internet istemci-sunucu uygulaması, kullanıcıların belgeleri ve dünya genelindeki Web sunucularında depolanan diğer verilere erişmek için tarayıcıları kullandıkları World Wide Web.  
  
 Uygulamalar bu rollerden yalnızca biri ile sınırlı değildir; Örneğin, tanıdık orta katmanlı uygulama sunucusu, başka bir sunucudan veri isteyerek istemcilerden gelen isteklere yanıt verir ve bu durumda hem sunucu hem de istemci olarak hareket eder.  
  
 İstemci uygulaması, istek ve yanıt için kullanılacak istenen Internet kaynağını ve iletişim protokolünü tanımlayarak bir istek yapar. Gerekirse, istemci, isteği tamamlaması için gereken ek verileri (örneğin, proxy konumu veya kimlik doğrulama bilgileri (Kullanıcı adı, parola vb.) de sağlar. İstek oluşturulduktan sonra, istek sunucuya gönderilebilir.  
  
## <a name="identifying-resources"></a>Kaynakları tanımlama  
 .NET Framework, istenen Internet kaynağını ve iletişim protokolünü belirlemek için Tekdüzen Kaynak tanımlayıcısı (URI) kullanır. URI, en az üç ve muhtemelen dört, parça içerir: istek ve yanıt için iletişim protokolünü tanımlayan düzen tanımlayıcısı; Sunucu tanımlayıcısı, bir etki alanı adı sistemi (DNS) ana bilgisayar adından ya da sunucuyu Internet 'te benzersiz bir şekilde tanımlayan bir TCP adresinden oluşur; sunucuda istenen bilgileri bulan yol tanımlayıcısı; ve istemciden sunucuya bilgi geçiren isteğe bağlı bir sorgu dizesi. `http://www.contoso.com/whatsnew.aspx?date=today` Örneğin, URI, şema tanımlayıcısından `www.contoso.com` `http`, sunucu tanımlayıcısından, yoldan `/whatsnew.aspx`ve sorgu dizesinden `?date=today`oluşur.  
  
 Sunucu isteği aldıktan ve yanıtı işledikten sonra, istemci uygulamasına yanıtı döndürür. Yanıt, içerik türü (örneğin ham metin veya XML verileri) gibi ek bilgiler içerir.  
  
## <a name="requests-and-responses-in-the-net-framework"></a>.NET Framework istekler ve yanıtlar  
 .NET Framework, bir istek/yanıt modeli aracılığıyla internet kaynaklarına erişmek için gereken üç bilgi parçasını sağlamak üzere belirli sınıfları kullanır: <xref:System.Uri> Aradığınız <xref:System.Net.WebRequest>İnternetkaynağınınURI'siniiçerensınıf.kaynak için bir istek içeren sınıf; ve gelen yanıt için bir kapsayıcı sağlayan sınıfı.<xref:System.Net.WebResponse>  
  
 İstemci uygulamaları, `WebRequest` ağ kaynağının <xref:System.Net.WebRequest.Create%2A> URI 'sini yöntemine geçirerek örnek oluşturur. Bu statik yöntem, http `WebRequest` gibi belirli bir protokol için oluşturur. Döndürülen `WebRequest` , hem sunucuya yönelik isteği denetleyen hem de istek yapıldığında gönderilen veri akışına erişen özelliklere erişim sağlar. İçindeki yöntemi, istemci uygulamasından URI 'de tanımlanan sunucuya isteği gönderir.`WebRequest` <xref:System.Net.WebRequest.GetResponse%2A> Yanıtın gecikildiği durumlarda, istek <xref:System.Net.WebRequest.BeginGetResponse%2A> **Web isteğindeki**yöntemi kullanılarak zaman uyumsuz olarak yapılabilir ve yanıt <xref:System.Net.WebRequest.EndGetResponse%2A> daha sonra yöntemi kullanılarak döndürülebilir.  
  
 **GetResponse** ve **EndGetResponse** yöntemleri, sunucu tarafından döndürülen verilere erişim sağlayan bir **WebResponse** döndürür. Bu veriler, istek yapan uygulamaya <xref:System.Net.WebResponse.GetResponseStream%2A> yöntem tarafından bir akış olarak sağlandığı için veri akışlarının kullanıldığı her yerde kullanılabilir.  
  
 **WebRequest** ve **WebResponse** sınıfları takılabilir protokollerin temelini oluşturur. bu sayede, Internet kaynaklarını kullanan uygulamalar geliştirmenize olanak tanıyan bir ağ hizmetleri uygulaması; Her bir kaynağın kullandığı protokol. **WebRequest** 'in alt sınıfları, gerçek bağlantıları Internet kaynaklarına yapma ayrıntılarını yönetmek Için **WebRequest** sınıfına kaydedilir.  
  
 Örnek olarak, <xref:System.Net.HttpWebRequest> sınıfı http kullanarak bir Internet kaynağına bağlanma ayrıntılarını yönetir. Varsayılan olarak, **WebRequest. Create** yöntemi "http:" ya da "https:" ile başlayan bir URI ile KARŞıLAŞTıĞıNDA (http ve Secure http için protokol tanımlayıcıları), döndürülen **WebRequest** olduğu gibi kullanılabilir veya türüne **tür atanabilir** Protokol özgü özelliklere erişim Için HttpWebRequest. Çoğu durumda, **WebRequest** bir istek oluşturmak için gerekli tüm bilgileri sağlar.  
  
 İstek/yanıt işlemi olarak gösterilebilen herhangi bir protokol **WebRequest**içinde kullanılabilir. **WebRequest** ve **WebResponse** 'dan protokole özgü sınıflar türetebilir ve ardından bunları statik <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> yöntemle uygulama tarafından kullanılmak üzere kaydedebilirsiniz.  
  
 Internet istekleri için istemci yetkilendirmesi gerektiğinde, <xref:System.Net.WebRequest.Credentials%2A> **WebRequest** 'in özelliği gerekli kimlik bilgilerini sağlar. Bu kimlik bilgileri, temel HTTP veya Özet kimlik doğrulaması için bir basit ad/parola çifti ya da NTLM veya Kerberos kimlik doğrulaması için bir ad/parola/etki alanı kümesi olabilir. Bir dizi kimlik bilgisi bir <xref:System.Net.NetworkCredential> örnek içinde depolanabilir veya birden çok küme aynı anda bir <xref:System.Net.CredentialCache> örnek içinde depolanabilir. **CredentialCache** , isteğin URI 'sini ve sunucunun hangi kimlik bilgilerini sunucuya gönderileceğini belirlemede desteklediği kimlik doğrulama şemasını kullanır.  
  
## <a name="simple-requests-with-webclient"></a>WebClient ile basit Istekler  
 Internet kaynakları için basit istekler yapması gereken uygulamalar için, <xref:System.Net.WebClient> sınıfı bir internet sunucusuna veri yüklemek veya verileri indirmek için sık kullanılan yöntemler sağlar. **WebClient** , Internet kaynaklarına erişim sağlamak Için **WebRequest** sınıfına bağımlıdır; Bu nedenle, **WebClient** sınıfı kayıtlı herhangi bir takılabilir protokolünü kullanabilir.  
  
 İstek/yanıt modelini veya ağ üzerinde dinlemesi gereken uygulamalar için ya da istekleri göndermek için, **sistem .net. Sockets** ad alanı <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>ve <xref:System.Net.Sockets.UdpClient> sınıflarını sağlar. Bu sınıflar, farklı aktarım protokollerini kullanarak bağlantı yapma ayrıntılarını işler ve ağ bağlantısını bir akış olarak kullanıma sunar.  
  
 Windows Sockets arabirimini veya yuva düzeyinde programlama tarafından sunulan denetime ihtiyaç duyan geliştiriciler, **sistem .net. Sockets** sınıflarının ihtiyaçlarını karşıladığını fark eder. **System .net. Sockets** sınıfları, yönetilen sunucudan **System.net** sınıfları içindeki yerel koda bir geçiş noktasıdır. Çoğu durumda, **sistem .net. Sockets** sınıfları, verileri Windows 32 bit karşılıklarına ve gerekli güvenlik denetimlerini işlemeye göre sıralayamaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Takılabilir Protokoller Programlama](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
- [.NET Framework'te Ağ Programlaması](../../../docs/framework/network-programming/index.md)
- [Ağ Programlama Örnekleri](../../../docs/framework/network-programming/network-programming-samples.md)
