---
title: '&lt;issuerChannelBehaviors&gt; &lt;ekleme&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bf66b3d3b531ae41329aade6a416c330957d83c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltissuerchannelbehaviorsgt"></a>&lt;issuerChannelBehaviors&gt; &lt;ekleme&gt;
Bir STS ile iletişim kurarken kullanılacak bir uç noktası davranışı ekler.  
  
> [!NOTE]
>  Uç noktası davranışı içeriyorsa bir [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) öğesi, bir özel durum.  
  
 \<Sistem. ServiceModel >  
\<davranışları >  
endpointBehaviors bölümü  
\<davranışı >  
\<clientCredentials >  
\<IssuedToken >  
\<issuerChannelBehaviors > öğesi  
\<ekleme >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<add issuerAddress="string"  
     behaviorConfiguraton="string" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|issuerAddress|İle iletişim kurmak için güvenlik belirteci verenin URI'si.|  
|behaviorConfiguration|Aynı yapılandırma dosyasında tanımlanan bir uç noktası davranışı adı.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<issuerChannelBehaviors >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|Bir koleksiyonu içerir [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] istemci uç nokta davranışları belirtilen hizmet belirteci Hizmetleri ile iletişim kurarken kullanılacak.|  
  
## <a name="remarks"></a>Açıklamalar  
 `issuerAddress`istemci ile iletişim kurmak istediği güvenlik belirteci hizmeti URI içeriyor. `behaviorConfiguration`uygulama tarafından oluşturulan kanaldaki kullanan bir uç noktası davranışı işaret [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] verilen belirteçler güvenlik belirteci hizmetlerinden almak için.  
  
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
 [\<issuerChannelBehaviors >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)
