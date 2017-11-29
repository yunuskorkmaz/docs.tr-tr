---
title: "&lt;Çözümleyici&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5734a985c4941a12be5032c254a75987f2074da6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltresolvergt"></a>&lt;Çözümleyici&gt;
Bir eş çözümlemek için kullanılan bir eş çözümleyici kafes katılmak birkaç düğüm temsil eden bir dizi Eş düğüm adresleri kimliği kafes belirtir.  
  
 \<Sistem. ServiceModel >  
\<bağlamaları >  
\<netPeerBinding >  
\<bağlama >  
\<Çözümleyici >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"  
   referralPolicy="DoNotShare/Service/Share">  
</resolver>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`mode`|Bu hizmetle ilişkilendirilen eş Çözümleyicisi örneği ya da PNRP özgü özel bir çözümleyici olup olmadığını belirtir veya otomatik olarak belirlenen bir dize. Bu öznitelik türünde <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.|  
|`referralPolicy`|Yol başvuruları eşler arasında paylaşılan belirten bir dize. Bu öznitelik türünde <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<üstbilgiler >](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|Özel eş Çözümleyici hizmeti ayarlarını belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlama >](../../../../../docs/framework/misc/binding.md)|Tüm bağlama özelliklerini tanımlayan [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).|  
  
## <a name="remarks"></a>Açıklamalar  
 Eş adı çözümleyici eş bir eş kafes katılmak düğümleri bulmak için eş kanalları tarafından kullanılan bir bulma hizmetidir. Ayrıca, "olarak Eş düğüm eş kafes bilinir ve kullanılabilir hale mekanizması bir eş kafes sahip bir düğüm kaydetmek için" kullanılır. Eş çözücüler hakkında daha fazla bilgi için bkz: [eş çözücüler](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.PeerResolver>  
 <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>  
 <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>  
 <xref:System.ServiceModel.Configuration.PeerResolverElement>  
 [Eş çözücüler](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)  
 [Özel Çözücü PeerChannel'a uygulamaya ekleme](http://msdn.microsoft.com/en-us/12aa3787-2962-439c-ad27-46523c8b0419)
