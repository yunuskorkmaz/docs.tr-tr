### <a name="remove-ssl3-from-the-wcf-transportdefaults"></a>WCF TransportDefaults Ssl3 Kaldır

|   |   |
|---|---|
|Ayrıntılar|Taşıma güvenliği ile NetTcp ve sertifika kimlik bilgisi türünü kullanırken SSL 3 artık güvenli bağlantı anlaşması için kullanılan bir varsayılan protokoldür. Çoğu durumda olması gerekir etkisi olan mevcut uygulamalar için TLS 1.0 her zaman protokol listesinde NetTcp için eklenen gibi. Tüm mevcut istemcilerin kullanarak bir bağlantı anlaşması gerekir en az TLS1.0.|
|Öneri|Ssl3 gerekiyorsa, aşağıdaki yapılandırma mekanizmalardan biri Ssl3 üzerinde anlaşılan protokolleri listesine eklemek için kullanın.<ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols></li><li>[<](~/docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)</li><li>[&lt;sslStreamSecurity&gt; bölümünü &lt;customBinding&gt;] ~ / docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)</li></ul>|
|Kapsam|Kenar|
|Sürüm|4.6.2|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols?displayProperty=nameWithType></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType></li></ul>|

