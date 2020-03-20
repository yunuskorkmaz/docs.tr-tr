---
ms.openlocfilehash: 9e8fdb54bddc32c08adbe114e2d46e2508585bc1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858409"
---
### <a name="wcf-services-that-use-nettcp-with-ssl-security-and-md5-certificate-authentication"></a>SSL güvenliği ve MD5 sertifika kimlik doğrulaması ile NETTCP kullanan WCF hizmetleri

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6, WCF SSL varsayılan protokol listesine 1,1 TLve TLS 1.2 ekler. Hem istemci hem de sunucu makineleri .NET Framework 4.6 veya daha sonra yüklü olduğunda, TLS 1.2 anlaşma için kullanılır. TLS 1.2, MD5 sertifika kimlik doğrulamasını desteklemez. Sonuç olarak, bir müşteri BIR MD5 sertifikası kullanırsa, WCF istemcisi WCF hizmetine bağlanmayı başaramaz.|
|Öneri|WCF istemcisinin aşağıdakilerden herhangi birini yaparak bir WCF sunucusuna bağlanabilmesi için bu sorunu çözebilirsiniz:<ul><li>MD5 algoritmasını kullanmamak için sertifikayı güncelleştirin. Bu önerilen çözümdür.</li><li>Bağlama kaynak kodunda dinamik olarak yapılandırılmamışsa, TLS 1.1 veya protokolün önceki bir sürümünü kullanacak şekilde uygulamanın yapılandırma dosyasını güncelleştirin. Bu, MD5 karma algoritması ile bir sertifika kullanmaya devam etmenizi sağlar.</li></ul> <blockquote> [!WARNING] MD5 karma algoritması olan bir sertifika güvenli olarak kabul edilir, bu geçici çözüm önerilmez.</blockquote> Aşağıdaki yapılandırma dosyası bunu yapar:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;system.serviceModel&gt;&#13;&#10;&lt;bindings&gt;&#13;&#10;&lt;netTcpBinding&gt;&#13;&#10;&lt;binding&gt;&#13;&#10;&lt;security mode= &quot;None/Transport/Message/TransportWithMessageCredential&quot; &gt;&#13;&#10;&lt;transport clientCredentialType=&quot;None/Windows/Certificate&quot;&#13;&#10;protectionLevel=&quot;None/Sign/EncryptAndSign&quot;&#13;&#10;sslProtocols=&quot;Ssl3/Tls1/Tls11&quot;&gt;&#13;&#10;&lt;/transport&gt;&#13;&#10;&lt;/security&gt;&#13;&#10;&lt;/binding&gt;&#13;&#10;&lt;/netTcpBinding&gt;&#13;&#10;&lt;/bindings&gt;&#13;&#10;&lt;/system.ServiceModel&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre><ul><li>Bağlama kaynak kodunda dinamik olarak yapılandırılırsa, <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType> tls 1.1<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType> (veya kaynak kodundaki protokolün önceki bir sürümünü) kullanacak şekilde özelliği güncelleştirin.</li></ul> <blockquote> [!WARNING] MD5 karma algoritması olan bir sertifika güvenli olarak kabul edilir, bu geçici çözüm önerilmez.</blockquote> |
|Kapsam|İkincil|
|Sürüm|4.6|
|Tür|Çalışma Zamanı|
