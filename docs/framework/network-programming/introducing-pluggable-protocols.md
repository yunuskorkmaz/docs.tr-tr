---
title: "Takılabilir Protokol Tanıtımı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 3cc7ad6b6270b74e2eb6aa4a2cc3a540175d540b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="introducing-pluggable-protocols"></a>Takılabilir Protokol Tanıtımı
Microsoft .NET Framework uygulamalarınıza hızla ve kolayca tümleştirilebilir Internet Hizmetleri katmanlı, genişletilebilir ve yönetilen bir uygulamasını sağlar. Internet erişimi sınıfları <xref:System.Net> ve <xref:System.Net.Sockets> ad alanları, hem Web hem de Internet tabanlı uygulamalarını uygulamak için kullanılabilir.  
  
## <a name="internet-applications"></a>Internet uygulamaları  
 Internet uygulamaları sınıflandırılmış kapsamlı iki tür: istemcilerden bilgi isteklerine yanıt bilgileri ve sunucu uygulamaları istek istemci uygulamaları. Klasik Internet istemci-sunucu burada kişiler tarayıcılar erişim belgelere ve Web sunucularında dünya çapında depolanan diğer verileri kullanır. World Wide Web uygulamasıdır.  
  
 Uygulamalar, bu rolleri yalnızca biri için sınırlı değildir; Örneğin, istekte bulunan verileri başka bir sunucudan tarafından istemcilerden tanıdık orta katman uygulama sunucusu isteklerine yanıt bu durumda, hem sunucu hem de bir istemci olarak davranıyor.  
  
 İstemci uygulama, istenen Internet kaynağının ve istek ve yanıt için kullanılacak iletişim protokolü belirleyerek isteğinde bulunur. Gerekirse, istemci proxy konumu veya kimlik bilgilerini (kullanıcı adı, parola ve benzeri) gibi bir isteği tamamlamak için gereken herhangi bir ek veriyi de sağlar. İstek biçimlendirilmiş sonra istek sunucuya gönderilebilir.  
  
## <a name="identifying-resources"></a>Kaynakları tanımlama  
 .NET Framework Tekdüzen Kaynak Tanımlayıcısı (URI) istenen Internet kaynak ve iletişim kurallarını tanımlamak için kullanır. En az üç ve muhtemelen dört, parçalarını URI oluşur: istek ve yanıt; için iletişim protokolü tanımlayan düzen tanımlayıcısı bir etki alanı adı sistemi (DNS) ana bilgisayar adı veya sunucunun Internet üzerindeki benzersiz olarak tanıtan bir TCP adresi oluşan sunucu tanımlayıcısı; sunucuda istenen bilgileri bulur yolu tanımlayıcısı; ve bilgileri istemciden sunucuya geçirir bir isteğe bağlı sorgu dizesi. Örneğin, "http://www.contoso.com/whatsnew.aspx?date=today" URI oluşur düzeni tanımlayıcı "http", "www.contoso.com" Sunucu tanımlayıcısı, yol "/ whatsnew.aspx" ve sorgu dizesi "? tarihi bugün =".  
  
 Sunucu isteği aldı ve yanıt işlenen sonra istemci uygulaması yanıtı döndürür. Yanıt (ham metni veya örnek için XML verileri) içerik türü gibi ek bilgileri içerir.  
  
## <a name="requests-and-responses-in-the-net-framework"></a>İsteklerin ve yanıtların .NET Framework'teki  
 .NET Framework üç parça istek/yanıt modeli aracılığıyla Internet kaynaklarına erişmek için gerekli bilgiler sağlamak için belirli sınıfları kullanır: <xref:System.Uri> aramayı Internet kaynağının URI'sini içeren sınıf; <xref:System.Net.WebRequest>; kaynağı için bir istek içeren sınıfı ve <xref:System.Net.WebResponse> gelen yanıt için bir kapsayıcı sağlayan sınıf.  
  
 İstemci uygulamaları oluşturmak `WebRequest` ağ kaynağına URI'sini geçirerek örnekleri <xref:System.Net.WebRequest.Create%2A> yöntemi. Bu statik yöntem oluşturur bir `WebRequest` HTTP gibi belirli bir protokol için. `WebRequest` Hem sunucuya istek ve istek yapıldığında, gönderilen veri akışı erişimi denetleyen özellikler erişim sağlar döndürülür. <xref:System.Net.WebRequest.GetResponse%2A> Yöntemi `WebRequest` URI'de tanımlanan sunucuya istemci uygulamasından isteği gönderir. Zaman uyumsuz olarak kullanılarak istek, yanıt ertelenmesini durumlarda yapılabilir <xref:System.Net.WebRequest.BeginGetResponse%2A> yöntemi **WebRequest**, ve daha sonraki bir kullanarak zaman yanıt döndürülebilecek <xref:System.Net.WebRequest.EndGetResponse%2A> yöntemi.  
  
 **GetResponse** ve **EndGetResponse** yöntemleri döndürür bir **WebResponse** sunucu tarafından döndürülen veri erişim sağlar. Bu verileri isteyen uygulamaya göre bir akış olarak sağlandığından <xref:System.Net.WebResponse.GetResponseStream%2A> yöntemi, bir uygulamada veri akışlarını kullanılan herhangi bir yerde kullanılabilir.  
  
 **WebRequest** ve **WebResponse** sınıflardır Takılabilir Protokol temelini — Internet kaynakların olmadan kullanan uygulamalar geliştirmenize olanak tanıyan ağ hizmetleri uygulaması Her kaynak kullandığı protokol belirli ayrıntılar konusunda kaygı. Alt sınıfları **WebRequest** ile kayıtlı **WebRequest** Internet kaynaklarına gerçek bağlantı ayrıntılarını yönetmek için sınıf.  
  
 Örneğin, <xref:System.Net.HttpWebRequest> sınıfı HTTP kullanarak bir Internet kaynağına bağlanma ayrıntılarını yönetir. Varsayılan olarak, zaman **WebRequest.Create** yöntemi ile başlayan bir URI karşılaştığında "http:" veya "https:" (HTTP ve güvenli HTTP protokolü tanımlayıcılar), **WebRequest** olarak kullanılabilir döndürülür olan veya için typecast **HttpWebRequest** protokole özgü özelliklere erişmek için. Çoğu durumda, **WebRequest** bir isteği yapmak için gerekli tüm bilgileri sağlar.  
  
 Bir istek/yanıt işlem kullanılabilir olarak temsil edilebilir protokolü bir **WebRequest**. Protokole özgü sınıflardan türetilemeyeceğini **WebRequest** ve **WebResponse** ve sonra bunları kullanmak için statik uygulamayla tarafından kaydettirmeniz <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> yöntemi.  
  
 İstemci yetkilendirme Internet istekleri için gerektiğinde <xref:System.Net.WebRequest.Credentials%2A> özelliği **WebRequest** gerekli kimlik bilgilerini sağlar. Bu kimlik bilgileri temel HTTP veya Özet kimlik doğrulaması için bir basit adı/parola çifti olabilir veya NTLM veya Kerberos kimlik doğrulaması için bir ad/parola/etki alanı ayarlayın. Bir kimlik bilgileri kümesi depolanabilir bir <xref:System.Net.NetworkCredential> örneği veya birden çok kümeleri aynı anda depolanabilir bir <xref:System.Net.CredentialCache> örneği. **CredentialCache** istek ve sunucuya göndermek için hangi kimlik bilgilerinin belirlemek için sunucunun desteklediği kimlik doğrulama şeması URI'si kullanır.  
  
## <a name="simple-requests-with-webclient"></a>WebClient ile basit istekleri  
 Internet kaynaklarına yönelik basit isteği yapmak için gereken uygulamalar için <xref:System.Net.WebClient> sınıfı verileri yüklemeyi veya bir Internet sunucusundan veri indirme için sık kullanılan yöntemler sağlar. **WebClient** dayanan **WebRequest** sınıfı Internet kaynakların; erişmesini sağlamak için bu nedenle, **WebClient** sınıfı, herhangi bir kayıtlı takılabilir protokolünü kullanabilirsiniz.  
  
 İstek/yanıt modeli kullanamazsınız uygulamalar için veya yanı sıra ağ üzerinde dinleme istekleri göndermek için gereken uygulamalar için **System.Net.Sockets** ad alanı sağlar <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>ve <xref:System.Net.Sockets.UdpClient> sınıfları. Bu sınıfların farklı aktarım protokolünü kullanarak bağlantı ayrıntılarını işler ve ağ bağlantısı uygulamasına bir akış olarak kullanıma sunar.  
  
 Geliştiriciler Windows Sockets arabirimi ya da programlama yuva düzeyinde tarafından sağlanan denetime ihtiyaç duyan bilmiyorsanız, bulacaksınız **System.Net.Sockets** sınıfları ihtiyaçlarını karşılamak. **System.Net.Sockets** sınıfları içindeki yerel kod için yönetilen bir geçiş noktasından olan **System.Net** sınıfları. Çoğu durumda, **System.Net.Sockets** sınıfları sıralama veri Windows 32-bit dekiler yanı sıra tüm gerekli güvenlik denetimlerini işleme.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Takılabilir Protokoller Programlama](../../../docs/framework/network-programming/programming-pluggable-protocols.md)  
 [.NET Framework'te Ağ Programlaması](../../../docs/framework/network-programming/index.md)  
 [Ağ Programlama Örnekleri](../../../docs/framework/network-programming/network-programming-samples.md)  
 [MSDN kod Galerisi'nden .NET ağ örnekleri](http://code.msdn.microsoft.com/Wiki/View.aspx?ProjectName=nclsamples)
