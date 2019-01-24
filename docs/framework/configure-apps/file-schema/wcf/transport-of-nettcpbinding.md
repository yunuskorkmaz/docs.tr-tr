---
title: '&lt;netTcpBinding&gt; &lt;taşıma&gt;'
ms.date: 03/30/2017
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
ms.openlocfilehash: 7372b94bde8325ec00116ee7022739f1b17a1ac9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555498"
---
# <a name="lttransportgt-of-ltnettcpbindinggt"></a>&lt;netTcpBinding&gt; &lt;taşıma&gt;
İleti düzeyi güvenliği gereksinimleri ile yapılandırılmış bir uç nokta türünü tanımlayan [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).  
  
 \<system.ServiceModel>  
\<bağlamaları >  
\<netTcpBinding>  
\<bağlama >  
\<Güvenlik >  
\<taşıma >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<netTcpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential">
      <transport clientCredentialType="None|Windows|Certificate"
                 protectionLevel="None|Sign|EncryptAndSign"
                 sslProtocols="Tls|Tls11|Tls12">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</netTcpBinding>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|clientCredentialType|İsteğe bağlı. Aktarım güvenliği kullanarak istemci kimlik doğrulaması yapılırken kullanılacak kimlik bilgisi türünü belirtir.<br /><br /> -Varsayılan değer `Windows`.<br />-Bu öznitelik türünde <xref:System.ServiceModel.TcpClientCredentialType>.|  
|protectionLevel|İsteğe bağlı. TCP taşıma düzeyinde güvenliği tanımlar. İleti imzalama, bir üçüncü taraf aktarılırken iletinin oynama riskini azaltır. Şifreleme, aktarım sırasında verileri düzeyinde gizlilik sağlar.<br /><br /> Varsayılan değer `EncryptAndSign` şeklindedir.|  
|sslProtocols|Hangi SslProtocols belirten bir SslProtocols enum bayrak değeri desteklenir. Tls varsayılandır&#124;Tls11&#124;Tls12.|  
|policyEnforcement|Bu sabit listesi ne zaman belirtir <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> zorlanmalıdır.<br /><br /> 1.  Hiçbir zaman – hiçbir zaman ilkenin uygulanıp (genişletilmiş koruma devre dışı).<br />2.  Yalnızca istemci genişletilmiş koruma destekliyorsa WhenSupported – ilke zorunlu tutulur.<br />3.  Her zaman – ilke her zaman uygulanmaz. Genişletilmiş Koruma desteklemeyen istemciler kimlik doğrulaması başarısız olur.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Hiçbiri|İstemci anonimdir. Bu hizmet için bir sertifika gerektirir.|  
|Windows|Windows kimlik doğrulaması SP anlaşma (Kerberos anlaşması) kullanarak istemciyi belirtir.|  
|Sertifika|İstemci, bir sertifika kullanılarak doğrulanır. Bu, SSL anlaşması kullanır ve hizmet için bir sertifika gerektirir.|  
  
## <a name="protectionlevel-attribute"></a>protectionLevel özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Hiçbiri|Koruma yok.|  
|oturum|İmzalı iletiler.|  
|EncryptAndSign|-Sıradaki iletiler şifrelenir ve imzalanmış.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Hiçbiri  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|Güvenlik yeteneklerini belirtir [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).|  
  
## <a name="remarks"></a>Açıklamalar  
 Aktarım güvenliği ve karşılıklı kimlik doğrulaması bütünlüğü ve gizliliği SOAP iletisi için kullanın. Üzerindeki bir bağlamaya bu güvenlik modunu seçtiyseniz, kanal yığının güvenli aktarım kullanarak yapılandırılır ve SOAP iletilerini TCP üzerinden gibi Windows (anlaş) ya da SSL Aktarım güvenliği kullanılarak güvenli hale getirilir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.TcpTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<bağlama >](../../../../../docs/framework/misc/binding.md)
