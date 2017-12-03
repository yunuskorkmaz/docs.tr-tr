---
title: '&lt;localIssuer&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e8836d9e57dd7c4d9cfdc20c5e4856e384e6d67b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltlocalissuergt"></a>&lt;localIssuer&gt;
Bir güvenlik belirteci almak için kullanılacak yerel verenin bağlama ve adresini belirtir.  
  
 \<Sistem. ServiceModel >  
\<davranışları >  
endpointBehaviors bölümü  
\<davranışı >  
\<clientCredentials >  
\<IssuedToken >  
\<localIssuer >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<localIssuer address="string"  
      binding="string"  
      bindingConfiguration="string" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|adres|Gerekli dize. Yerel yayımlayan URI'sini belirtir.|  
|bağlama|İsteğe bağlı dize. Sistem tarafından sağlanan bağlamalar biri. Bir listesi için bkz: [System-Provided bağlamaları](../../../../../docs/framework/wcf/system-provided-bindings.md).|  
|bindingConfiguration|İsteğe bağlı dize. Yapılandırma dosyasında bulunan bir bağlama yapılandırması belirtir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Kimliği >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Yerel yayımlayan için kimlik bilgilerini belirtir.|  
|[\<üstbilgiler >](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|Doğru yerel yayımlayan değinmek için gerekli adres üstbilgileri koleksiyonu. Kullanabileceğiniz `add` üstbilgi bu koleksiyona eklemek için anahtar sözcüğü.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<IssuedToken >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|Bir hizmet için bir istemci kimlik doğrulaması için kullanılan özel bir belirteç belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir güvenlik belirteci hizmeti (STS) verilen bir belirteç elde ederken istemci uygulaması yapılandırılmalıdır adres ve STS ile iletişim kurmak için kullanılacak bağlama. Zaman <xref:System.ServiceModel.WSFederationHttpBinding> bir URL veya güvenlik belirteci hizmeti için Federasyon bağlaması veren adresi http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous olduğunda sağlamaz veya `null`, istemcinin [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Kanal tarafından belirtilen değerleri kullanan `address` ve `binding` verilen belirteç edinme STS ile iletişim kurmak için. Yerel yayımlayan yapılandırma hakkında daha fazla bilgi için bkz: [nasıl yapılır: yerel yayımlayan yapılandırma](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kümeleri `address`, `binding`, ve `bindingConfiguration` özniteliklerini bir `localIssuer` öğesi.  
  
```xml  
<system.serviceModel>  
 <behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <issuedToken cacheIssuedTokens="false"   
                 defaultKeyEntropyMode="ClientEntropy">  
     <localIssuer address="net.tcp://cohowinery/tokens"   
                  binding="netTcpBinding"  
                  bindingConfiguration="myTcpBindingConfig" />  
    </issuedToken>  
   </clientCredentials>  
  </behavior>  
  </endpointBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
 [Güvenlik davranışları](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Nasıl yapılır: yerel yayımlayan yapılandırma](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [Hizmet kimliği ve kimlik doğrulaması](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Güvenlik davranışları](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Federasyon ve verilen belirteçler](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [Hizmetler ve istemcileri güvenli hale getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [İstemcilerinin güvenliğini sağlama](../../../../../docs/framework/wcf/securing-clients.md)  
 [Nasıl yapılır: federe istemci oluşturma](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [Federasyon ve verilen belirteçler](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
