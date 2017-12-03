---
title: "&lt;ws2007HttpBinding&gt; &lt;taşıma&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 573b7fb5cf130d0a638326b87ae49f90db881df4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="lttransportgt-of-ltws2007httpbindinggt"></a>&lt;ws2007HttpBinding&gt; &lt;taşıma&gt;
HTTP taşıma için kimlik doğrulama ayarlarını tanımlar.  
  
 \<system.serviceModel >  
\<bağlamaları >  
\<ws2007HttpBinding >  
\<bağlama >  
\<Güvenlik >  
\<taşıma >  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
transport clientCredentialType =   
       "Basic/Certificate/Digest/None/Ntlm/Windows"  
       proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
       realm="string"   
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
|`realm`|Özet veya temel kimlik doğrulaması için kimlik doğrulaması bölgesi. Varsayılan boş bir dizedir.<br /><br /> Bir kimlik doğrulaması bölgesi, en az kimlik doğrulaması yapan ana bilgisayar adını belirtir. Ayrıca, erişimi olan kullanıcıların koleksiyonu de belirtebilirsiniz. Bir kullanıcı, birkaç olası kullanıcı adları ve parolalar hangisinin kullanılacağını belirlemek için kimlik doğrulaması bölgesi sorgulayabilirsiniz.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Yok.|Güvenliği devre dışı bırakıldı.|  
|Temel|Temel kimlik doğrulaması kullanır.|  
|Özet|Özet kimlik doğrulaması kullanır.|  
|NTLM|Bir Windows etki alanı ile bir geri dönüş olarak NTLM kimlik doğrulaması kullanır.|  
|Windows|Tümleşik Windows kimlik doğrulaması kullanır.|  
|Sertifika|İstemci kimlik doğrulaması için X.509 sertifikaları kullanır.|  
  
## <a name="proxycredentialtype-attribute"></a>proxyCredentialType özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Yok.|Güvenliği devre dışı bırakıldı.|  
|Temel|Temel kimlik doğrulaması kullanır.|  
|Özet|Özet kimlik doğrulaması kullanır.|  
|NTLM|Bir Windows etki alanı ile bir geri dönüş olarak NTLM kullanır.|  
|Windows|Tümleşik Windows kimlik doğrulaması kullanır.|  
|Sertifika|İstemci kimlik doğrulaması için X.509 sertifikaları kullanır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-ws2007httpbinding.md)|Güvenlik özellikleri temsil eden [ \<ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) öğesi.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>  
 [Hizmetler ve istemcileri güvenli hale getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Bağlamaları](../../../../../docs/framework/wcf/bindings.md)  
 [Sistem tarafından sağlanan bağlamaları yapılandırma](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<bağlama >](../../../../../docs/framework/misc/binding.md)
