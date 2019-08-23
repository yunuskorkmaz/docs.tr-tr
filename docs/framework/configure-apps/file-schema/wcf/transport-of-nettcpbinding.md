---
title: <transport> / <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
ms.openlocfilehash: 265b68e058919d1d5c5f1dbcfb1419b57be9aeab
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915557"
---
# <a name="transport-of-nettcpbinding"></a>\<\<NetTcpBinding > taşıma >
[ \<NetTcpBinding >](nettcpbinding.md)yapılandırılmış bir uç nokta için ileti düzeyi güvenlik gereksinimlerinin türünü tanımlar.  
  
 \<system.ServiceModel>  
\<bağlama >  
\<netTcpBinding>  
\<bağlama >  
\<Güvenlik >  
\<Taşıma >  
  
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
 Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|clientCredentialType|İsteğe bağlı. Aktarım güvenliği kullanılarak istemci kimlik doğrulaması gerçekleştirilirken kullanılacak kimlik bilgisinin türünü belirtir.<br /><br /> -Varsayılan değer `Windows`.<br />-Bu öznitelik türündedir <xref:System.ServiceModel.TcpClientCredentialType>.|  
|protectionLevel|İsteğe bağlı. TCP aktarımı düzeyinde güvenliği tanımlar. İmzalama iletileri, üçüncü bir tarafın aktarılırken ileti üzerinde izinsiz değişiklik yaptığı riski azaltır. Şifreleme, aktarım sırasında veri düzeyinde gizlilik sağlar.<br /><br /> Varsayılan değer `EncryptAndSign` şeklindedir.|  
|sslProtocols|Hangi SslProtocols desteklendiğini belirten bir SslProtocols numaralandırma bayrak değeri. Varsayılan değer TLS&#124;Tls11&#124;Tls12 ' dir.|  
|policyEnforcement|Bu numaralandırma, <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> ne zaman uygulanacağını belirtir.<br /><br /> 1.  Hiçbir süre – ilke hiçbir şekilde zorlanmaz (genişletilmiş koruma devre dışı bırakılır).<br />2.  WhenSupported – ilke yalnızca istemci genişletilmiş korumayı destekliyorsa zorlanır.<br />3.  Her zaman – ilke her zaman zorlanır. Genişletilmiş korumayı desteklemeyen istemciler kimlik doğrulaması yapamaz.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Yok.|İstemci anonimdir. Bu, hizmet için bir sertifika gerektirir.|  
|Windows|İstemcinin Windows kimlik doğrulamasını SP anlaşması (Kerberos anlaşması) kullanarak belirtir.|  
|Sertifika|İstemcinin kimliği bir sertifika kullanılarak doğrulanır. Bu, SSL anlaşmasını kullanır ve hizmet için bir sertifika gerektirir.|  
  
## <a name="protectionlevel-attribute"></a>protectionLevel özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Yok.|Koruma yok.|  
|İmzalayabilirsiniz|İletiler imzalanır.|  
|EncryptAndSign|-İletiler şifrelenir ve imzalanır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](security-of-nettcpbinding.md)|[ \<NetTcpBinding >](nettcpbinding.md)'nin güvenlik yeteneklerini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 SOAP iletisinin bütünlüğü ve gizliliği ve karşılıklı kimlik doğrulaması için aktarım güvenliği kullanın. Bu güvenlik modu bir bağlamada seçilirse, kanal yığını güvenli bir aktarım kullanılarak yapılandırılır ve SOAP iletileri Windows (Negotiate) veya TCP üzerinden SSL gibi aktarım güvenliği kullanılarak güvenli hale getirilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.TcpTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../wcf/feature-details/securing-services-and-clients.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<bağlama >](../../../misc/binding.md)
