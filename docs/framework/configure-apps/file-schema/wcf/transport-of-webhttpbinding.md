---
title: <transport> / <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
ms.openlocfilehash: f78add5397644dc40bfd22f10bd84aa5c5eb29e6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923207"
---
# <a name="transport-of-webhttpbinding"></a>\<\<WebHttpBinding > taşıma >
HTTP isteklerini alacak şekilde yapılandırılmış bir hizmet uç noktası için aktarım düzeyi güvenlik ayarlarını tanımlar.  
  
 \<system.ServiceModel>  
\<bağlama >  
\<webHttpBinding>  
\<bağlama >  
\<Güvenlik >  
\<Taşıma >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<webHttpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows"
                 realm="string">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</webHttpBinding>
```  
  
## <a name="type"></a>Tür  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`clientCredentialType`|Hizmetin istemcinin kimliğini doğrulamak için kullanılan kimlik bilgisini belirtir. Bu öznitelik türü <xref:System.ServiceModel.HttpClientCredentialType>.|  
|`proxyCredentialType`|Bir etki alanı ara sunucusu için istemcinin kimliğini doğrulamak için kullanılan kimlik bilgisini belirtir. Bu öznitelik türü <xref:System.ServiceModel.HttpProxyCredentialType>.|  
|`realm`|Özet veya temel kimlik doğrulaması için kimlik doğrulama bölgesini belirten bir dize. Varsayılan değer boş bir dizedir.<br /><br /> Kimlik doğrulama bölgesi, kimlik doğrulamasını gerçekleştiren konağın en azından adını belirtir. Ayrıca, erişimi olan bir kullanıcı koleksiyonu da belirtebilir. Kullanıcı, birkaç olası Kullanıcı adı ve parolanın kullanılabileceğini belirlemek için kimlik doğrulama bölgesini sorgulayabilir.|  
|`policyEnforcement`|Bu numaralandırma, <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> ne zaman uygulanacağını belirtir.<br /><br /> 1.  Hiçbir süre – ilke hiçbir şekilde zorlanmaz (genişletilmiş koruma devre dışı bırakılır).<br />2.  WhenSupported – ilke yalnızca istemci genişletilmiş korumayı destekliyorsa zorlanır.<br />3.  Her zaman – ilke her zaman zorlanır. Genişletilmiş korumayı desteklemeyen istemciler kimlik doğrulaması yapamaz.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`None`|Güvenlik devre dışı bırakıldı.|  
|`Basic`|Temel kimlik doğrulamasını kullanır.|  
|`Certificate`|İstemcinin kimliğini doğrulamak için X. 509.440 sertifikalarını kullanır.|  
|`Digest`|Özet kimlik doğrulaması kullanır.|  
|`Ntlm`|Windows etki alanı ile geri dönüş olarak NTLM kimlik doğrulamasını kullanır.|  
|`Windows`|Tümleşik Windows kimlik doğrulamasını kullanır.|  
  
## <a name="proxycredentialtype-attribute"></a>proxyCredentialType özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`None`|Güvenlik devre dışı bırakıldı.|  
|`Basic`|Temel kimlik doğrulamasını kullanır.|  
|`Digest`|Özet kimlik doğrulaması kullanır.|  
|`Ntlm`|Windows etki alanı ile geri dönüş olarak NTLM kullanır.|  
|`Windows`|Tümleşik Windows kimlik doğrulamasını kullanır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](security-of-webhttpbinding.md)|WSHttpBinding > öğesinin güvenlik yeteneklerini [ \<](wshttpbinding.md) temsil eder.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../wcf/feature-details/securing-services-and-clients.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<bağlama >](../../../misc/binding.md)
- [WCF Web HTTP Programlama Modeli](../../../wcf/feature-details/wcf-web-http-programming-model.md)
