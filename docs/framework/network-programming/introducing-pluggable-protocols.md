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
ms.openlocfilehash: 72b47b8159f9f6f0dc3a19c5cbf94335507d9e7d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047869"
---
# <a name="introducing-pluggable-protocols"></a>Takılabilir Protokollere Giriş
Microsoft .NET Framework, uygulamalarınız için hızlı ve kolay bir şekilde entegre edilebilen, katmanlı, genişletilebilir ve yönetilen bir Internet hizmeti uygulaması sağlar. Hem Web tabanlı <xref:System.Net> hem <xref:System.Net.Sockets> de Internet tabanlı uygulamaları uygulamak için ad ve ad alanlarındaki Internet erişim sınıfları kullanılabilir.  
  
## <a name="internet-applications"></a>İnternet Uygulamaları  
 Internet uygulamaları genel olarak iki türe sınıflandırılabilir: bilgi isteyen istemci uygulamaları ve istemcilerden gelen bilgi isteklerine yanıt veren sunucu uygulamaları. Klasik Internet istemci-sunucu uygulaması, insanların dünya çapında Web sunucularında depolanan belgelere ve diğer verilere erişmek için tarayıcıları kullandığı World Wide Web'dir.  
  
 Uygulamalar bu rollerden sadece biriyle sınırlı değildir; örneğin, tanıdık orta katman uygulama sunucusu istemcilerden gelen isteklere başka bir sunucudan veri isteyerek yanıt verir ve bu durumda hem sunucu hem de istemci olarak hareket eder.  
  
 İstemci uygulaması, istenen Internet kaynağını ve istek ve yanıt için kullanılacak iletişim protokolünü tanımlayarak bir istekte bulunarak bir istekte bulunarak. Gerekirse, istemci ayrıca proxy konumu veya kimlik doğrulama bilgileri (kullanıcı adı, parola vb.) gibi isteği tamamlamak için gereken ek verileri de sağlar. İstek oluşturulduktan sonra, istek sunucuya gönderilebilir.  
  
## <a name="identifying-resources"></a>Kaynakların Tanımlanması  
 .NET Framework, istenen Internet kaynağı ve iletişim protokolünü tanımlamak için Tek düzen Kaynak Tanımlayıcısı (URI) kullanır. URI en az üç ve muhtemelen dört parçadan oluşur: istek ve yanıt için iletişim protokolünü tanımlayan şema tanımlayıcısı; Alan Adı Sistemi (DNS) ana bilgisayar adı veya Internet'teki sunucuyu benzersiz olarak tanımlayan bir TCP adresinden oluşan sunucu tanımlayıcısı; sunucuda istenen bilgileri bulunan yol tanımlayıcısı; ve istemciden sunucuya bilgi aktaran isteğe bağlı bir sorgu dizesi. Örneğin, `http://www.contoso.com/whatsnew.aspx?date=today` URI şema `http`tanımlayıcısı, sunucu `www.contoso.com`tanımlayıcısı, yol `/whatsnew.aspx`ve sorgu dizeoluşur. `?date=today`  
  
 Sunucu isteği aldıktan ve yanıtı işledikten sonra, yanıtı istemci uygulamasına döndürür. Yanıt, içeriğin türü (örneğin ham metin veya XML verileri) gibi ek bilgiler içerir.  
  
## <a name="requests-and-responses-in-the-net-framework"></a>.NET Çerçevesindeki İstek ve Yanıtlar  
 .NET Framework, bir istek/yanıt modeli aracılığıyla Internet kaynaklarına erişmek için gereken <xref:System.Uri> üç bilgi parçasını sağlamak için belirli sınıfları kullanır: aradığınız Internet kaynağının URI'sini içeren sınıf; kaynak <xref:System.Net.WebRequest> için bir istek içeren sınıf; ve <xref:System.Net.WebResponse> gelen yanıt için bir kapsayıcı sağlayan sınıf.  
  
 İstemci `WebRequest` uygulamaları, ağ kaynağının URI'sini <xref:System.Net.WebRequest.Create%2A> yönteme geçirerek örnekler oluşturur. Bu statik yöntem, `WebRequest` HTTP gibi belirli bir protokol için bir yöntem oluşturur. Döndürülen `WebRequest` ler, hem sunucuya gelen isteği hem de istek yapıldığında gönderilen veri akışına erişimi denetleyen özelliklere erişim sağlar. İstemci <xref:System.Net.WebRequest.GetResponse%2A> `WebRequest` uygulamasından uri'de tanımlanan sunucuya istek gönderir yöntemi. Yanıtın gecikebileceği durumlarda, istek <xref:System.Net.WebRequest.BeginGetResponse%2A> **Webİstek'teki**yöntem kullanılarak eş zamanlı olarak yapılabilir ve yanıt <xref:System.Net.WebRequest.EndGetResponse%2A> daha sonra yöntem kullanılarak döndürülebilir.  
  
 **GetResponse** ve **EndGetResponse** yöntemleri, sunucu tarafından döndürülen verilere erişim sağlayan bir **WebResponse** döndürür. Bu veriler <xref:System.Net.WebResponse.GetResponseStream%2A> yöntemle bir akış olarak isteyen uygulamaya sağlandığı için, veri akışlarının kullanıldığı her yerde bir uygulamada kullanılabilir.  
  
 **Webİstek** ve **WebResponse** sınıfları takılabilir protokollerin temelini oluşturur — her kaynağın kullandığı protokolün belirli ayrıntıları hakkında endişelenmeden Internet kaynaklarını kullanan uygulamalar geliştirmenize olanak tanıyan ağ hizmetlerinin bir uygulamasıdır. **WebRequest'in** soyundan gelen sınıfları, Internet kaynaklarına gerçek bağlantılar kurmanın ayrıntılarını yönetmek için **WebRequest** sınıfına kaydedilir.  
  
 Örnek olarak, <xref:System.Net.HttpWebRequest> sınıf HTTP'yi kullanarak bir Internet kaynağına bağlanma ayrıntılarını yönetir. Varsayılan olarak, **WebRequest.Create** yöntemi "http:" veya "https:" (HTTP ve güvenli HTTP için protokol tanımlayıcıları) ile başlayan bir URI ile karşılaştığında, döndürülen **Webİstek** olduğu gibi kullanılabilir veya protokole özgü özelliklere erişmek için **HttpWebRequest'e** daktino yazılabilir. Çoğu durumda, **Web İstek** bir istekte bulunmak için gerekli tüm bilgileri sağlar.  
  
 İstek/yanıt hareketi olarak temsil edilebilen herhangi bir protokol **Bir Webİsteği'nde**kullanılabilir. **WebRequest** ve **WebResponse'dan** protokole özgü sınıfları türetebilir ve ardından <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> bunları statik yöntemle uygulama tarafından kullanılmak üzere kaydedebilirsiniz.  
  
 Internet istekleri için istemci yetkilendirmesi gerektiğinde, <xref:System.Net.WebRequest.Credentials%2A> **WebRequest** özelliği gerekli kimlik bilgilerini sağlar. Bu kimlik bilgileri, temel HTTP veya özet kimlik doğrulaması için basit bir ad/parola çifti veya NTLM veya Kerberos kimlik doğrulaması için bir ad/parola/etki alanı kümesi olabilir. Bir kimlik bilgileri kümesi bir <xref:System.Net.NetworkCredential> örnekte depolanabilir veya birden çok küme <xref:System.Net.CredentialCache> aynı anda bir örnekte depolanabilir. **Kimlik Bilgisi Önbellek,** isteğin URI'sini ve sunucunun sunucuya hangi kimlik bilgilerini göndereceğini belirlemek için desteklediği kimlik doğrulama düzenini kullanır.  
  
## <a name="simple-requests-with-webclient"></a>WebClient ile Basit İstekler  
 Internet kaynakları için basit isteklerde bulunmak zorunda <xref:System.Net.WebClient> olan uygulamalar için sınıf, bir Internet sunucusuna veri yüklemek veya verileri indirmek için yaygın yöntemler sağlar. **WebClient,** Internet kaynaklarına erişim sağlamak için **WebRequest** sınıfına güvenir; bu nedenle, **WebClient** sınıfı herhangi bir kayıtlı takılabilir protokolü kullanabilirsiniz.  
  
 İstek/yanıt modelini kullanamayan uygulamalar veya ağda dinlemesi ve istek göndermesi gereken uygulamalar için **System.Net.Sockets** <xref:System.Net.Sockets.TcpListener>ad <xref:System.Net.Sockets.UdpClient> alanı <xref:System.Net.Sockets.TcpClient>, ve sınıflar sağlar. Bu sınıflar, farklı aktarım protokolleri kullanarak bağlantı kurma ayrıntılarını işler ve ağ bağlantısını uygulamaya akış olarak ortaya çıkarır.  
  
 Windows Soketleri arabirimini bilen veya soket düzeyinde programlama tarafından sağlanan denetime ihtiyaç duyan **geliştiriciler, System.Net.Sockets** sınıflarının gereksinimlerini karşıladığını göreceksiniz. **System.Net.Sockets sınıfları,** **System.Net** sınıfları içinde yönetilen koddan yerel koda bir geçiş noktasıdır. Çoğu durumda, **System.Net.Sockets sınıfları,** gerekli güvenlik denetimlerini yürütmenin yanı sıra verileri Windows 32 bit'lik karşılıklarına göre işlemeye dönüştürür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Takılabilir Protokoller Programlama](programming-pluggable-protocols.md)
- [.NET Framework'te Ağ Programlaması](index.md)
- [Ağ Programlama Örnekleri](network-programming-samples.md)
