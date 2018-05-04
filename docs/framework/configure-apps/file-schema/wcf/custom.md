---
title: '&lt;Özel&gt;'
ms.date: 03/30/2017
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
ms.openlocfilehash: 19f960c14b6171557ec0f353dae34f26d7a7686c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltcustomgt"></a>&lt;Özel&gt;
Özel eş Çözümleyici hizmeti ayarlarını belirtir.  
  
\<system.serviceModel>  
\<bağlamaları >  
\<netPeerBinding >  
\<bağlama >  
\<Çözümleyici >  
\<Özel >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml
<custom address="Uri" 
        resolverType="String">  
  <headers/>  
  <identity/>  
</custom>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`address`|Özel eş çözümleyicisini barındıran Eş düğüm bitiş adresini belirtir URI.|  
|`resolverType`|Özel eş çözümleyicisini türünü belirten bir dize.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Kimliği >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Bu öğeyle yapılandırılmış özel eş çözücüler kimliğini belirtir. Bu öğe türünde <xref:System.ServiceModel.Configuration.IdentityElement>.|  
|[\<üstbilgiler >](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|SOAP iletilerine özel eş çözümleyici tarafından işlenen için kullanılan adres üstbilgisi koleksiyonu.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Çözümleyici >](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|Bir eş çözümlemek için kullanılan bir eş çözümleyici kafes katılmak birkaç düğüm temsil eden bir dizi Eş düğüm adresleri kimliği kafes.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu öğe barındırma hizmeti ve herhangi bir özel bağlama ayarı eş uç nokta adresi de dahil olmak üzere bir özel eş çözümleyici hizmetinin temel ayarlarını tanımlar. Özel Çözücü oluşturma hakkında daha fazla bilgi için bkz: [PeerChannel'a uygulamaya özel Çözücü ekleme](http://msdn.microsoft.com/library/12aa3787-2962-439c-ad27-46523c8b0419).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>  
 <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>  
 <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>  
 <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>  
 [Eş Çözücüler](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)  
 [Özel Çözücü PeerChannel'a uygulamaya ekleme](http://msdn.microsoft.com/library/12aa3787-2962-439c-ad27-46523c8b0419)
