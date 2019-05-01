---
ms.openlocfilehash: 77d4978df76735d11f63c7118c1b4708b5b85502
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032518"
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
