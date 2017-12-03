---
title: "&lt;wsHttpBinding&gt; &lt;taşıma&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e1ea5fc60f4dc64fd895469b580b81379da26191
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="lttransportgt-of-ltwshttpbindinggt"></a>&lt;wsHttpBinding&gt; &lt;taşıma&gt;
HTTP taşıma için kimlik doğrulama ayarlarını tanımlar.  
  
 \<system.serviceModel >  
\<bağlamaları >  
\<wsHttpBinding >  
\<bağlama >  
\<Güvenlik >  
\<taşıma >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<wsHttpBinding>  
    <binding>  
        <security mode="None|Transport|TransportWithMessageCredential|TransportCredentialOnly">  
            <transport  
            clientCredentialType="Basic|Certificate|Digest|None|Ntlm|Windows"  
            proxyCredentialType="Basic|Digest|None|Ntlm|Windows"  
            realm="string" />  
                <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always" protectionScenario="TransportSelected|TrustedProxy">  
                    <customServiceNames></customServiceNames>  
                </extendedProtecutionPolicy>  
            </transport>  
        </security>  
    </binding>  
</wsHttpBinding>  
```  
  
## <a name="type"></a>Tür  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`clientCredentialType`|Hizmeti için istemci kimlik doğrulaması için kullanılan kimlik bilgilerini belirtir. Bu öznitelik türünde <xref:System.ServiceModel.HttpClientCredentialType>.|  
|`proxyCredentialType`|Bir etki alanı Ara sunucu için istemci kimlik doğrulaması için kullanılan kimlik bilgilerini belirtir. Bu öznitelik türünde <xref:System.ServiceModel.HttpProxyCredentialType>.|  
|`realm`|Özet veya temel kimlik doğrulaması için kimlik doğrulaması bölgesi belirten bir dize. Varsayılan boş bir dizedir.<br /><br /> Bir kimlik doğrulaması bölgesi, en az kimlik doğrulaması yapan ana bilgisayar adını belirtir. Ayrıca, erişimi olan bir kullanıcı koleksiyonu de belirtebilirsiniz. Bir kullanıcı hangisinin birkaç olası kullanıcı adları ve parolalar kullanılabilir olmadığından emin olmak için kimlik doğrulaması bölgesi sorgulayabilirsiniz.|  
|`policyEnforcement`|Bu numaralandırma ne zaman belirtir <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> zorunlu tutulmalıdır.<br /><br /> 1.  Hiçbir zaman – ilke hiçbir zaman zorlanır (genişletilmiş koruma devre dışı).<br />2.  Yalnızca istemci genişletilmiş koruma destekliyorsa WhenSupported – ilke uygulanır.<br />3.  Her zaman – ilke her zaman zorlanır. Genişletilmiş Koruma desteklemeyen istemcilerin kimliğini doğrulamak başarısız olur.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`None`|Güvenliği devre dışı bırakıldı.|  
|`Basic`|Temel kimlik doğrulaması kullanır.|  
|`Digest`|Özet kimlik doğrulaması kullanır.|  
|`Ntlm`|Bir Windows etki alanı ile bir geri dönüş olarak NTLM kimlik doğrulaması kullanır.|  
|`Windows`|Tümleşik Windows kimlik doğrulaması kullanır.|  
|`Certificate`|İstemci kimlik doğrulaması için X.509 sertifikaları kullanır.|  
  
## <a name="proxycredentialtype-attribute"></a>proxyCredentialType özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`None`|Güvenliği devre dışı bırakıldı.|  
|`Basic`|Temel kimlik doğrulaması kullanır.|  
|`Digest`|Özet kimlik doğrulaması kullanır.|  
|`Ntlm`|Bir Windows etki alanı ile bir geri dönüş olarak NTLM kullanır.|  
|`Windows`|Tümleşik Windows kimlik doğrulaması kullanır.|  
|`Certificate`|İstemci kimlik doğrulaması için X.509 sertifikaları kullanır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|Güvenlik özellikleri temsil eden [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>  
 [Hizmetler ve istemcileri güvenli hale getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Bağlamaları](../../../../../docs/framework/wcf/bindings.md)  
 [Sistem tarafından sağlanan bağlamaları yapılandırma](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<bağlama >](../../../../../docs/framework/misc/binding.md)
