---
title: <custom>
ms.date: 03/30/2017
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
ms.openlocfilehash: 4077aacab1c1c4594db76cc6663bfc0245d345d7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555503"
---
# \<custom>
Özel bir eş çözümleyici hizmetinin ayarlarını belirtir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<resolver>**](resolver.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<custom>**  
  
## <a name="syntax"></a>Syntax  
  
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
|`address`|Özel eş çözümleyici hizmetini barındıran eş düğümün uç nokta adresini belirten bir URI.|  
|`resolverType`|Özel eş çözücü hizmetinin türünü belirten bir dize.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<identity>](identity.md)|Bu öğeyle yapılandırılan özel eş çözümleyiciler için kimliği belirtir. Bu öğe türündedir <xref:System.ServiceModel.Configuration.IdentityElement> .|  
|[\<headers>](headers-element.md)|Özel eş çözümleyici tarafından işlenen SOAP iletileri için kullanılan adres üst bilgisi koleksiyonu.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<resolver>](resolver.md)|Eş ağ KIMLIĞINI, kafeslere katılan çeşitli düğümleri temsil eden bir eş düğüm adresleri kümesine çözümlemek için kullanılan bir eş çözümleyici.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu öğe, hizmeti barındıran eşin uç nokta adresi ve belirli bağlama ayarları dahil olmak üzere özel bir eşdüzey çözümleyici Hizmeti için temel ayarları tanımlar. Özel çözümleyici oluşturma hakkında daha fazla bilgi için bkz. [bir PeerChannel uygulamasına özel çözümleyici ekleme](/previous-versions/ms730105(v=vs.90)).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>
- <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>
- <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>
- <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>
- [Eş Çözücüler](../../../wcf/feature-details/peer-resolvers.md)
- [Bir PeerChannel uygulamasına özel çözümleyici ekleme](/previous-versions/ms730105(v=vs.90))
