---
title: <resolver>
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: 0dc667f392595d895bd4f2773ab69777d7369446
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738733"
---
# <a name="resolver"></a>\<çözümleyici >
Bir eş ağ KIMLIĞINI, kafeslere katılan çeşitli düğümleri temsil eden bir eş düğüm adresleri kümesine çözümlemek için kullanılan bir eş çözümleyici belirtir.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netPeerTcpBinding >** ](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<çözümleyici >**  
  
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
|`mode`|Bu hizmetle ilişkili eş çözümleyici örneğinin PNRP 'ye özgü mi, özel bir çözümleyici mi yoksa otomatik olarak mı belirlendiğini belirten bir dize. Bu öznitelik <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>türündedir.|  
|`referralPolicy`|Başvuruların eşler arasında paylaşılma yöntemini belirten bir dize. Bu öznitelik <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>türündedir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<üst bilgileri >](headers.md)|Özel bir eş çözümleyici hizmetinin ayarlarını belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\< bağlama >](bindings.md)|[\<netPeerTcpBinding >](netpeertcpbinding.md)bağlama yeteneklerini tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Eş adı çözümleyici, eş kanallar tarafından bir eş ağ içinde yer alan eş düğümleri bulmak için kullanılan bir bulma hizmetidir. Eş ağı olan bir düğüm olan bir düğümü "kaydettirmek" için de kullanılır. Bu bir düğüm, Eş ağ üzerinde bilinen ve kullanılabilir hale gelir. Eş çözümleyiciler hakkında daha fazla bilgi için bkz. [eşdüzey çözümleyiciler](../../../wcf/feature-details/peer-resolvers.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.PeerResolver>
- <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>
- <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>
- <xref:System.ServiceModel.Configuration.PeerResolverElement>
- [Eş Çözücüler](../../../wcf/feature-details/peer-resolvers.md)
- [Bir PeerChannel uygulamasına özel çözümleyici ekleme](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))
