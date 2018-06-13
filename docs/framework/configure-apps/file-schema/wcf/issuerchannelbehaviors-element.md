---
title: '&lt;issuerChannelBehaviors&gt; Öğesi'
ms.date: 03/30/2017
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
ms.openlocfilehash: 7e5b8ace06a224db3abcc6b9d0ec87ccbc1a6a77
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747063"
---
# <a name="ltissuerchannelbehaviorsgt-element"></a>&lt;issuerChannelBehaviors&gt; Öğesi
Belirtilen hizmet belirteci Hizmetleri ile iletişim kurarken kullanılacak (yapılandırmasında tanımlanmış) Windows Communication Foundation (WCF) istemci uç nokta davranışları koleksiyonunu içerir. Tanımlı davranışları herhangi içeremez [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) öğeleri.  
  
 \<system.ServiceModel>  
\<davranışları >  
endpointBehaviors bölümü  
\<davranışı >  
\<clientCredentials >  
\<IssuedToken >  
\<issuerChannelBehaviors >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<issuerChannelBehaviors>  
      <add behaviorConfiguraton="string"  
                issuerAddress="string" />  
</issuerChannelBehaviors>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<ekleme >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-issuerchannelbehaviors.md)|Bir davranış koleksiyona ekler.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<IssuedToken >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|Bir hizmet için bir istemci kimlik doğrulaması için kullanılan özel bir belirteç belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Herhangi bir zaman bu öğeyi kullanın davranışları (dahil davranışları dışında `<clientCredentials>` öğeleri) hizmet ile iletişim kurmak için kullanılan gerekir. Örneğin, bir [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) davranışı öğesi dahil edilmesi gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>  
 [Kimlik Doğrulama ile Hizmet Kimliği](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Güvenlik Davranışları](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Federasyon ve Verilen Belirteçler](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [İstemcileri Güvenli Hale Getirme](../../../../../docs/framework/wcf/securing-clients.md)  
 [Nasıl yapılır: Federe İstemci Oluşturma](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [Nasıl yapılır: Yerel Yayımlayan Yapılandırma](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [Federasyon ve Verilen Belirteçler](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
