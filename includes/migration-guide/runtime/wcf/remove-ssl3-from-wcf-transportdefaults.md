---
ms.openlocfilehash: 37d771305bb0a4a38eeac9713e8667d158962174
ms.sourcegitcommit: 5d9f4b805787f890ca6e0dc7ea30a43018bc9cbb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57788952"
---
### <a name="remove-ssl3-from-the-wcf-transportdefaults"></a>WCF TransportDefaults Ssl3 Kaldır

|   |   |
|---|---|
|Ayrıntılar|Aktarım güvenliği ile NetTcp ve sertifika kimlik bilgisi türü kullanırken, SSL 3 artık güvenli bağlantı anlaşması için kullanılan bir varsayılan protokoldür. Çoğu durumda olması gerekir mevcut uygulamalara herhangi bir etkisi olarak TLS 1.0 her zaman protokol listesinde NetTcp için eklenmiştir. Var olan tüm istemciler bir bağlantı kullanarak en az TLS1.0.|
|Öneri|Ssl3 gerekiyorsa, aşağıdaki yapılandırma mekanizmalardan biri Ssl3 anlaşma protokolleri listesine eklemek için kullanın.<ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols></li><li>[\<Aktarım >, \<netTcpBinding >](~/docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)</li><li>[&lt;sslStreamSecurity&gt; bölümünü &lt;customBinding&gt;](~/docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)</li></ul>|
|Kapsam|Kenar|
|Sürüm|4.6.2|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols?displayProperty=nameWithType></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType></li></ul>|

