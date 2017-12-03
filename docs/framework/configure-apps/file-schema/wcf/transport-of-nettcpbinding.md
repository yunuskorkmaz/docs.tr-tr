---
title: "&lt;netTcpBinding&gt; &lt;taşıma&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5cf7a0aedc1fcd387b4b41233cd7c31b7ec64de4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="lttransportgt-of-ltnettcpbindinggt"></a>&lt;netTcpBinding&gt; &lt;taşıma&gt;
İleti düzeyi güvenlik gereksinimleri ile yapılandırılmış bir uç nokta türünü tanımlar [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).  
  
 \<Sistem. ServiceModel >  
\<bağlamaları >  
\<netTcpBinding >  
\<bağlama >  
\<Güvenlik >  
\<taşıma >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<netTcpBinding>  
    <binding>  
        <security  
         mode="None|Transport|Message|TransportWithMessageCredential">  
            <transport clientCredentialType="None|Windows|Certificate"  
             protectionLevel="None|Sign|EncryptAndSign"             sslProtocols="Tls|Tls11|Tls12">  
                <extendedProtectionPolicy  
                     policyEnforcement="Never|WhenSupported|Always"  
                     protectionScenario="TransportSelected|TrustedProxy">  
                    <customServiceNames></customServiceNames>  
                        </extendedProtectionPolicy>  
            </transport>  
        </security>  
    </binding>  
</netTcpBinding>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|clientCredentialType|İsteğe bağlı. Taşıma güvenliği kullanarak istemci kimlik doğrulaması yapılırken kullanılacak kimlik bilgileri türünü belirtir.<br /><br /> -Varsayılan değer `Windows`.<br />-Bu öznitelik türünde <xref:System.ServiceModel.TcpClientCredentialType>.|  
|ProtectionLevel|İsteğe bağlı. TCP Aktarım düzeyinde güvenlik tanımlar. İletileri imzalama bir üçüncü taraf onu aktarılırken iletiyle oynama riskini azaltır. Şifreleme, aktarım sırasında veri düzeyi gizliliği sağlar.<br /><br /> Varsayılan değer `EncryptAndSign` şeklindedir.|  
|sslProtocols|Hangi SslProtocols belirten bir SslProtocols enum bayrak değeri desteklenir. Varsayılan değer: Tls &#124; Tls11 &#124; Tls12.|  
|policyEnforcement|Bu numaralandırma ne zaman belirtir <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> zorunlu tutulmalıdır.<br /><br /> 1.  Hiçbir zaman – ilke hiçbir zaman zorlanır (genişletilmiş koruma devre dışı).<br />2.  Yalnızca istemci genişletilmiş koruma destekliyorsa WhenSupported – ilke uygulanır.<br />3.  Her zaman – ilke her zaman zorlanır. Genişletilmiş Koruma desteklemeyen istemcilerin kimliğini doğrulamak başarısız olur.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Yok.|İstemci anonimdir. Bu hizmet için bir sertifika gerektirir.|  
|Windows|Windows kimlik doğrulaması SP anlaşma (Kerberos anlaşması) kullanarak istemcinin belirtir.|  
|Sertifika|İstemci, bir sertifika kullanılarak doğrulanır. Bu, SSL anlaşması kullanır ve hizmet için bir sertifika gerektirir.|  
  
## <a name="protectionlevel-attribute"></a>protectionLevel özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Yok.|Koruma yok.|  
|Oturum|İmzalı iletiler.|  
|Da EncryptAndSign|-İletileri şifrelenir ve imzalanmış.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|Güvenlik özellikleri belirtir [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).|  
  
## <a name="remarks"></a>Açıklamalar  
 Taşıma güvenliği bütünlüğü ve gizliliği SOAP iletisi ve karşılıklı kimlik doğrulaması için kullanın. Bu güvenlik modunu bağlamada seçtiyseniz, kanal yığını güvenli bir taşıma kullanılarak yapılandırılır ve SOAP iletilerine, TCP üzerinden aktarım güvenliği gibi Windows (Negotiate) veya SSL kullanılarak güvenlik altına.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.TcpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>  
 [Hizmetler ve istemcileri güvenli hale getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Bağlamaları](../../../../../docs/framework/wcf/bindings.md)  
 [Sistem tarafından sağlanan bağlamaları yapılandırma](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<bağlama >](../../../../../docs/framework/misc/binding.md)
