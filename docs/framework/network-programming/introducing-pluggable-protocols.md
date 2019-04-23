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
ms.openlocfilehash: 25d7b0e8b8b98d68a0fb4a3cadab3d9f3e8747bd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59146152"
---
# <a name="introducing-pluggable-protocols"></a>Takılabilir Protokollere Giriş
Microsoft .NET Framework, uygulamalarınızla hızlı ve kolay bir şekilde tümleştirilebilir Internet Services katmanlı, genişletilebilir ve yönetilen bir uygulamasını sağlar. Internet erişimi yer alan sınıfları <xref:System.Net> ve <xref:System.Net.Sockets> ad alanları, hem Web hem de Internet tabanlı uygulamalarını uygulamak için kullanılabilir.  
  
## <a name="internet-applications"></a>Internet uygulamaları  
 Internet uygulamaları sınıflandırıldığı problem iki tür: istemcilerden bilgi isteklerine yanıt bilgileri ve sunucu uygulamaları istek istemci uygulamaları. Klasik Internet istemci-sunucu erişim belgelere ve diğer verileri dünya çapında Web sunucularına depolanmış tarayıcılar burada kullandığını World Wide Web uygulamasıdır.  
  
 Uygulamalar bu rollerden yalnızca birine sınırlı değildir; Örneğin, istekte bulunan verileri başka bir sunucudan tarafından istemcilerden tanıdık orta katman uygulama sunucusu isteklerine yanıt bu durumda, bir sunucu ve bir istemci davranır.  
  
 İstemci uygulaması, istenen Internet kaynağının ve kullanıcının iletişim protokolü istek ve yanıt için kullanılacak tanımlayarak bir istek gönderir. Gerekirse, istemci proxy konumu veya kimlik bilgilerini (kullanıcı adı, parola vb.) gibi isteğini tamamlamak için gereken herhangi bir ek veriyi de sağlar. İstek oluşturulduğunda, istek sunucuya gönderilebilir.  
  
## <a name="identifying-resources"></a>Kaynakları tanımlama  
 .NET Framework, kaynak ve iletişimi istenen Internet Protokolü tanımlamak için bir Tekdüzen Kaynak Tanımlayıcısı (URI) kullanır. URI en az üç ve dört, parçalarını oluşur: iletişim protokolü için istek ve yanıt; tanımlayan düzen tanımlayıcısı Sunucu tanımlayıcısı bir etki alanı adı sistemi (DNS) konak adı veya sunucunun Internet'teki benzersiz olarak tanımlayan bir TCP adresi oluşur; Sunucu üzerinde istenen bilgileri bulur yolu tanımlayıcısı; ve bilgi istemciden sunucuya aktarır. bir isteğe bağlı bir sorgu dizesi. Örneğin, URI `http://www.contoso.com/whatsnew.aspx?date=today` düzen tanımlayıcısı oluşur `http`, sunucu tanımlayıcısı `www.contoso.com`, yolun `/whatsnew.aspx`ve sorgu dizesi `?date=today`.  
  
 Sunucu isteği aldı ve yanıt işlenen sonra yanıtı istemci uygulamasına döndürür. Yanıt (ham metin veya XML verileri, örneğin) bir içerik türü gibi ek bilgileri içerir.  
  
## <a name="requests-and-responses-in-the-net-framework"></a>İsteklerin ve yanıtların .NET Framework  
 .NET Framework, üç parça istek/yanıt modeli aracılığıyla Internet kaynaklarına erişebilmesi için gerekli bilgileri sağlamak için belirli sınıfları kullanır: <xref:System.Uri> dağıtımınızla Internet kaynağın URI'sini içeren sınıf; <xref:System.Net.WebRequest>; kaynak talebi içeren sınıfı ve <xref:System.Net.WebResponse> gelen yanıtları için bir kapsayıcı sağlar sınıfını.  
  
 İstemci uygulamaları oluşturmayı `WebRequest` ağ kaynağına URI'sini geçirerek örnekleri <xref:System.Net.WebRequest.Create%2A> yöntemi. Bu statik bir yöntem oluşturur bir `WebRequest` HTTP gibi belirli bir protokol için. `WebRequest` , Döndürülen her iki sunucuya gönderilen istek ve istek yapıldığında, gönderilen veri akışına erişim denetimi özellikleri erişim sağlar. <xref:System.Net.WebRequest.GetResponse%2A> Metodunda `WebRequest` URI'de belirtilen sunucuya istemci uygulamadan alınan isteği gönderir. Zaman uyumsuz olarak kullanarak istek, yanıt ertelenebilir durumlarda yapılabilir <xref:System.Net.WebRequest.BeginGetResponse%2A> metodunda **WebRequest**, ve bir sonraki kullanarak sırasında yanıt döndürülebilir <xref:System.Net.WebRequest.EndGetResponse%2A> yöntemi.  
  
 **GetResponse yanıtına** ve **EndGetResponse** yöntemleri döndürür bir **WebResponse** sunucu tarafından döndürülen verilere erişim sağlar. Bu verileri isteyen uygulamaya göre bir akış olarak sağlandığından <xref:System.Net.WebResponse.GetResponseStream%2A> yöntemi, bir uygulamaya veri akışlarını kullanıldığı her yerde kullanılabilir.  
  
 **WebRequest** ve **WebResponse** sınıflardır takılabilir protokollerin temelini — olmadan Internet kaynakları kullanan uygulamalar geliştirmenize imkan sağlayan ağ hizmetleri uygulaması Her kaynak kullanan Protokolü belirli ayrıntılar hakkında endişelenmeden. Alt sınıfları **WebRequest** kayıtlı **WebRequest** Internet kaynaklarına gerçek bağlantı ayrıntılarını yönetmek için sınıf.  
  
 Örneğin, <xref:System.Net.HttpWebRequest> sınıfı HTTP kullanarak bir Internet kaynağına bağlanmayı ayrıntılarını yönetir. Varsayılan olarak, zaman **WebRequest.Create** yöntemi ile başlayan URI karşılaştığında "http:" veya "https:" (HTTP ve güvenli HTTP protokolü tanımlayıcılar), **WebRequest** olarak kullanılabilir döndürülür ise veya bu için türü atayarak **HttpWebRequest** protokole özgü özelliklere erişmek için. Çoğu durumda **WebRequest** isteği yapmak için gerekli tüm bilgileri sağlar.  
  
 İstek/yanıt işlem kullanılabilir olarak temsil edilebilir protokolü bir **WebRequest**. Protokole özgü sınıfları türetebilirsiniz **WebRequest** ve **WebResponse** ve sonra bunları kullanmak için statik uygulamayla kaydetmeniz <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> yöntemi.  
  
 Internet istekleri için istemci kimlik doğrulaması gerekli olduğunda <xref:System.Net.WebRequest.Credentials%2A> özelliği **WebRequest** gerekli kimlik bilgilerini sağlar. Bu kimlik bilgilerini temel HTTP veya Özet kimlik doğrulaması için bir basit adı/parola çifti olabilir veya bir adı/parola/etki alanı için NTLM veya Kerberos kimlik doğrulamasını ayarlayın. Bir dizi kimlik bilgisi depolanabilir bir <xref:System.Net.NetworkCredential> örneği veya birden fazla de aynı anda depolanabilir bir <xref:System.Net.CredentialCache> örneği. **CredentialCache** URI'si istek ve sunucuya göndermek için hangi kimlik bilgilerini belirlemek için sunucu destekleyen kimlik doğrulama şeması kullanır.  
  
## <a name="simple-requests-with-webclient"></a>WebClient ile basit istekler  
 Internet kaynaklarına yönelik basit isteğinde bulunmak için gereken uygulamalar <xref:System.Net.WebClient> sınıf verileri karşıya yükleme veya bir Internet sunucusundan verileri indirmek için ortak yöntemleri sağlar. **WebClient** dayanan **WebRequest** sınıfı; Internet kaynaklarına erişim sağlamak için bu nedenle, **WebClient** sınıfı, tüm kayıtlı takılabilir protokolleri kullanabilir.  
  
 İstek/yanıt modeli kullanamayan uygulamalar için veya yanı sıra ağda dinleme istekleri göndermek için gereken uygulamalar **System.Net.Sockets** ad alanı sağlar <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>ve <xref:System.Net.Sockets.UdpClient> sınıfları. Bu sınıflar farklı aktarım protokolünü kullanarak bağlantı ayrıntılarını işlemek ve uygulamaya bir akış olarak ağ bağlantısı üzerinden kullanıma sunacaksınız.  
  
 Tanıdık Windows Sockets arabirimini veya programlama yuva düzeyinde tarafından sağlanan denetime ihtiyacınız olanlar ile geliştiriciler, bulacaksınız **System.Net.Sockets** sınıfları ihtiyaçlarını karşılamak. **System.Net.Sockets** sınıflar içindeki yerel kod için yönetilen bir geçiş noktasından olan **System.Net** sınıfları. Çoğu durumda **System.Net.Sockets** sınıfları Windows 32-bit karşılıkları yanı sıra tüm gerekli güvenlik denetimleri işleme veri hazırlama.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Takılabilir Protokoller Programlama](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
- [.NET Framework'te Ağ Programlaması](../../../docs/framework/network-programming/index.md)
- [Ağ Programlama Örnekleri](../../../docs/framework/network-programming/network-programming-samples.md)
- [MSDN Kod Galerisi'nde .NET için ağ örnekleri](https://code.msdn.microsoft.com/Wiki/View.aspx?ProjectName=nclsamples)
