---
ms.openlocfilehash: 9b734fe960165b6d4b97b861cb3e8f31979f25c5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621383"
---
### <a name="remove-ssl3-from-the-wcf-transportdefaults"></a>WCF TransportDefaults Ssl3 kaldırma

#### <a name="details"></a>Ayrıntılar

Aktarım güvenliği ile NetTcp kullanılırken ve bir sertifika kimlik bilgisi türüyle, SSL 3 Protokolü artık güvenli bir bağlantı anlaşması için kullanılan varsayılan bir protokol değildir. Çoğu durumda, TLS 1,0, her zaman NetTcp protokol listesine eklendiğinden, var olan uygulamalara hiçbir etkisi olmaz. Tüm mevcut istemciler, en az TLS 1.0 kullanarak bir bağlantı anlaşması yapabilmelidir.

#### <a name="suggestion"></a>Öneri

Ssl3 gerekliyse, anlaşmalı protokoller listesine Ssl3 eklemek için aşağıdaki yapılandırma mekanizmalarından birini kullanın.<ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols></li><li>[<](~/docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)</li><li>[ &lt; CustomBinding] için [sslStreamSecurity &gt; bölümü &lt; &gt; ] ~/FI/Framework/configure-Apps/File-Schema/WCF/sslStreamSecurity.exe)</li></ul>

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4.6.2|
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols?displayProperty=nameWithType></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType></li></ul>|
