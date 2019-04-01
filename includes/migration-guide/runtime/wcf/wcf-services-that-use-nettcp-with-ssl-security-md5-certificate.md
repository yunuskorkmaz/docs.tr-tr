---
ms.openlocfilehash: ae3766e2045b5834fbf6ea20415942413b1590c0
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58761437"
---
### <a name="wcf-services-that-use-nettcp-with-ssl-security-and-md5-certificate-authentication"></a>SSL güvenlik ve MD5 sertifika kimlik doğrulaması ile NETTCP kullanan WCF hizmetleri

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6, TLS 1.1 ve TLS 1.2 WCF SSL varsayılan protokol listesine ekler. İstemci ve sunucu makineler sahip .NET Framework 4.6 veya üzeri yüklü olduğunda, TLS 1.2 anlaşması için kullanılır. TLS 1.2 MD5 sertifika kimlik doğrulamasını desteklemez. Sonuç olarak, bir müşteri bir MD5 sertifikası kullanıyorsa, WCF hizmetine bağlanmak WCF istemcisini başarısız olur.|
|Öneri|Bir WCF istemcisi, aşağıdakilerden birini yaparak bir WCF sunucuya bağlanabilmesi için bu sorunu geçici olarak çalışabilir:<ul><li>MD5 algoritmasını kullanmayı sertifikayı güncelleştirin. Önerilen çözüm budur.</li><li>Bağlama dinamik olarak kaynak kodunda yapılandırılmamışsa, TLS 1.1 veya önceki bir sürümünün protokolü kullanmak için uygulama yapılandırma dosyasını güncelleştirin. Bu, bir sertifika MD5 karma algoritması ile kullanmaya devam etmek sağlar.</li></ul> <blockquote> [!WARNING] Bu geçici çözüm önerilmez, bu yana MD5 karma algoritması bir sertifikayla güvenli olarak kabul edilir.</blockquote> Şu yapılandırma dosyasını şunu yapar:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;system.serviceModel&gt;&#13;&#10;&lt;bindings&gt;&#13;&#10;&lt;netTcpBinding&gt;&#13;&#10;&lt;binding&gt;&#13;&#10;&lt;security mode= &quot;None/Transport/Message/TransportWithMessageCredential&quot; &gt;&#13;&#10;&lt;transport clientCredentialType=&quot;None/Windows/Certificate&quot;&#13;&#10;protectionLevel=&quot;None/Sign/EncryptAndSign&quot;&#13;&#10;sslProtocols=&quot;Ssl3/Tls1/Tls11&quot;&gt;&#13;&#10;&lt;/transport&gt;&#13;&#10;&lt;/security&gt;&#13;&#10;&lt;/binding&gt;&#13;&#10;&lt;/netTcpBinding&gt;&#13;&#10;&lt;/bindings&gt;&#13;&#10;&lt;/system.ServiceModel&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre><ul><li>Kaynak kodunda bağlama dinamik olarak yapılandırılmışsa, güncelleştirme <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType> özelliğinin TLS 1.1 kullanmak için (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType> veya önceki bir sürümünün kaynak kodundaki protokolü.</li></ul> <blockquote> [!WARNING] Bu geçici çözüm önerilmez, bu yana MD5 karma algoritması bir sertifikayla güvenli olarak kabul edilir.</blockquote> |
|Kapsam|İkincil|
|Sürüm|4.6|
|Tür|Çalışma zamanı|

