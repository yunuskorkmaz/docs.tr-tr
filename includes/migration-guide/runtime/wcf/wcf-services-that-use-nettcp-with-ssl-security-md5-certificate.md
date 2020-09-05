---
ms.openlocfilehash: afcb9b950d4c47b4251dcc8ab0cf9cfc702005c8
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497948"
---
### <a name="wcf-services-that-use-nettcp-with-ssl-security-and-md5-certificate-authentication"></a>SSL güvenliği ve MD5 sertifikası kimlik doğrulamasıyla NETTCP kullanan WCF Hizmetleri

#### <a name="details"></a>Ayrıntılar

4,6 .NET Framework, WCF SSL varsayılan protokol listesine TLS 1,1 ve TLS 1,2 ekler. Hem istemci hem de sunucu makinelerinin .NET Framework 4,6 veya üzeri bir sürümü yüklüyse, anlaşma için TLS 1,2 kullanılır. TLS 1,2, MD5 sertifikası kimlik doğrulamasını desteklemez. Sonuç olarak, bir müşteri MD5 sertifikası kullanıyorsa, WCF istemcisi WCF hizmetine bağlanamaz.

#### <a name="suggestion"></a>Öneri

Bir WCF istemcisinin aşağıdakilerden birini yaparak bir WCF sunucusuna bağlanabilmesi için bu soruna geçici bir çözüm bulabilirsiniz:

- Bu sertifikayı, MD5 algoritmasını kullanacak şekilde güncelleştirin. Önerilen çözüm budur.
- Bağlama kaynak kodunda dinamik olarak yapılandırılmamışsa, uygulamanın yapılandırma dosyasını TLS 1,1 veya protokolün önceki bir sürümünü kullanacak şekilde güncelleştirin. Bu, MD5 karma algoritmasıyla bir sertifika kullanmaya devam etmenizi sağlar.

> [!WARNING]
> Bu geçici çözüm önerilmez, çünkü MD5 karma algoritması olan bir sertifika güvenli değil olarak kabul edilir.

Aşağıdaki yapılandırma dosyası bunu yapar:

```xml
<configuration>
  <system.serviceModel>
    <bindings>
      <netTcpBinding>
        <binding>
          <security mode= "None/Transport/Message/TransportWithMessageCredential" >
            <transport clientCredentialType="None/Windows/Certificate"
                       protectionLevel="None/Sign/EncryptAndSign"
                       sslProtocols="Ssl3/Tls1/Tls11">
            </transport>
          </security>
        </binding>
      </netTcpBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```

- Bağlama, kaynak kodunda dinamik olarak yapılandırılırsa, <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType> ÖZELLIĞI TLS 1,1 ( <xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType> veya kaynak kodundaki protokolün önceki bir sürümünü) kullanacak şekilde güncelleştirin.

> [!WARNING]
> Bu geçici çözüm önerilmez, çünkü MD5 karma algoritması olan bir sertifika güvenli değil olarak kabul edilir.

| Name    | Değer   |
|:--------|:--------|
| Kapsam   | İkincil   |
| Sürüm | 4.6     |
| Tür    | Çalışma Zamanı |

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
