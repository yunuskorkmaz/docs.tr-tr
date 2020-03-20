---
ms.openlocfilehash: d75eff2d2a43ab4488577014ec43a9826b2b2924
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "68237844"
---
### <a name="remove-ssl3-from-the-wcf-transportdefaults"></a>Ssl3'u WCF TransportDefaults'tan kaldırın

|   |   |
|---|---|
|Ayrıntılar|Aktarım güvenliği ve kimlik bilgisi sertifikası türü yle NetTcp kullanılırken, SSL 3 protokolü artık güvenli bir bağlantı için kullanılan varsayılan bir protokol değildir. Çoğu durumda, TLS 1.0 her zaman NetTcp için protokol listesine dahil edildiğinden, mevcut uygulamalara hiçbir etkisi olmamalıdır. Mevcut tüm istemciler en az TLS1.0 kullanarak bir bağlantı üzerinde anlaşma yapabilmelidir.|
|Öneri|Ssl3 gerekiyorsa, ssl3'ü anlaşmalı protokoller listesine eklemek için aşağıdaki yapılandırma mekanizmalarından birini kullanın.<ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols></li><li>[<](~/docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)</li><li>[&lt;&gt; &lt;sslStreamSecurity bölümü&gt;özelBinding ]~/docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)</li></ul>|
|Kapsam|Edge|
|Sürüm|4.6.2|
|Tür|Çalışma Zamanı|
|Etkilenen API’ler|<ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols?displayProperty=nameWithType></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType></li></ul>|
