---
ms.openlocfilehash: a5f4047d70276a90c9d72918a2559fd795feb26e
ms.sourcegitcommit: 261e0c98a111357692b3b63c596edf0cacf72991
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2020
ms.locfileid: "90770812"
---
### <a name="remove-ssl3-from-the-wcf-transportdefaults"></a>WCF TransportDefaults Ssl3 kaldırma

#### <a name="details"></a>Ayrıntılar

Aktarım güvenliği ile NetTcp kullanılırken ve bir sertifika kimlik bilgisi türüyle, SSL 3 Protokolü artık güvenli bir bağlantı anlaşması için kullanılan varsayılan bir protokol değildir. Çoğu durumda, TLS 1,0, her zaman NetTcp protokol listesine eklendiğinden, var olan uygulamalara hiçbir etkisi olmaz. Tüm mevcut istemciler, en az TLS 1.0 kullanarak bir bağlantı anlaşması yapabilmelidir.

#### <a name="suggestion"></a>Öneri

Ssl3 gerekliyse, anlaşmalı protokoller listesine Ssl3 eklemek için aşağıdaki yapılandırma mekanizmalarından birini kullanın.

- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols>
- <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols>
- [\<transport> durumunu \<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)
- [\<sslStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)

| Name    | Değer   |
|:--------|:--------|
| Kapsam   | Edge    |
| Sürüm | 4.6.2   |
| Tür    | Çalışma Zamanı |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols?displayProperty=nameWithType>
- <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols`
- `P:System.ServiceModel.TcpTransportSecurity.SslProtocols`

-->
