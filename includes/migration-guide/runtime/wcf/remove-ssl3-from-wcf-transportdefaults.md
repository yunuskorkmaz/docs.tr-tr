---
ms.openlocfilehash: 492138ffc6af6bd98d0d45eea4ddfdf54c86988c
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857553"
---
### <a name="remove-ssl3-from-the-wcf-transportdefaults"></a>WCF TransportDefaults Ssl3 Kaldır

|   |   |
|---|---|
|Ayrıntılar|Aktarım güvenliği ile NetTcp ve sertifika kimlik bilgisi türü kullanırken, SSL 3 artık güvenli bağlantı anlaşması için kullanılan bir varsayılan protokoldür. Çoğu durumda olması gerekir mevcut uygulamalara herhangi bir etkisi olarak TLS 1.0 her zaman protokol listesinde NetTcp için eklenmiştir. Var olan tüm istemciler bir bağlantı kullanarak en az TLS1.0.|
|Öneri|Ssl3 gerekiyorsa, aşağıdaki yapılandırma mekanizmalardan biri Ssl3 anlaşma protokolleri listesine eklemek için kullanın.<ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols></li><li>[<](~/docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)</li><li>[&lt;sslStreamSecurity&gt; bölümünü &lt;customBinding&gt;] ~ / docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)</li></ul>|
|`Scope`|Kenar|
|Version|4.6.2|
|Type|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols?displayProperty=nameWithType></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType></li></ul>|

