---
title: <resolver>
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: 0dc667f392595d895bd4f2773ab69777d7369446
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738733"
---
# \<resolver>
<span data-ttu-id="c5bc9-101">Bir eş ağ KIMLIĞINI, kafeslere katılan çeşitli düğümleri temsil eden bir eş düğüm adresleri kümesine çözümlemek için kullanılan bir eş çözümleyici belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5bc9-101">Specifies a peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<resolver>**  
  
## <a name="syntax"></a><span data-ttu-id="c5bc9-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c5bc9-102">Syntax</span></span>  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"
          referralPolicy="DoNotShare/Service/Share">
</resolver>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5bc9-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c5bc9-103">Attributes and Elements</span></span>  
 <span data-ttu-id="c5bc9-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c5bc9-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5bc9-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c5bc9-105">Attributes</span></span>  
  
|<span data-ttu-id="c5bc9-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c5bc9-106">Attribute</span></span>|<span data-ttu-id="c5bc9-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c5bc9-107">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="c5bc9-108">Bu hizmetle ilişkili eş çözümleyici örneğinin PNRP 'ye özgü mi, özel bir çözümleyici mi yoksa otomatik olarak mı belirlendiğini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="c5bc9-108">A string that specifies whether the peer resolver instance associated with this service is either PNRP-specific, a custom resolver, or automatically determined.</span></span> <span data-ttu-id="c5bc9-109">Bu öznitelik türü <xref:System.ServiceModel.PeerResolvers.PeerResolverMode> .</span><span class="sxs-lookup"><span data-stu-id="c5bc9-109">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span></span>|  
|`referralPolicy`|<span data-ttu-id="c5bc9-110">Başvuruların eşler arasında paylaşılma yöntemini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="c5bc9-110">A string that specifies the way referrals are shared among peers.</span></span> <span data-ttu-id="c5bc9-111">Bu öznitelik türü <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy> .</span><span class="sxs-lookup"><span data-stu-id="c5bc9-111">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c5bc9-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c5bc9-112">Child Elements</span></span>  
  
|<span data-ttu-id="c5bc9-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="c5bc9-113">Element</span></span>|<span data-ttu-id="c5bc9-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c5bc9-114">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers.md)|<span data-ttu-id="c5bc9-115">Özel bir eş çözümleyici hizmetinin ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5bc9-115">Specifies settings for a custom peer resolver service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c5bc9-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c5bc9-116">Parent Elements</span></span>  
  
|<span data-ttu-id="c5bc9-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="c5bc9-117">Element</span></span>|<span data-ttu-id="c5bc9-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c5bc9-118">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="c5bc9-119">Öğesinin tüm bağlama yeteneklerini tanımlar [\<netPeerTcpBinding>](netpeertcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="c5bc9-119">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5bc9-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c5bc9-120">Remarks</span></span>  
 <span data-ttu-id="c5bc9-121">Eş adı çözümleyici, eş kanallar tarafından bir eş ağ içinde yer alan eş düğümleri bulmak için kullanılan bir bulma hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="c5bc9-121">A peer name resolver is a discovery service used by peer channels to find peer nodes that participate in a peer mesh.</span></span> <span data-ttu-id="c5bc9-122">Eş ağı olan bir düğüm olan bir düğümü "kaydettirmek" için de kullanılır. Bu bir düğüm, Eş ağ üzerinde bilinen ve kullanılabilir hale gelir.</span><span class="sxs-lookup"><span data-stu-id="c5bc9-122">It is also used to "register" a node with a peer mesh, the mechanism by which the peer node becomes known and available from the peer mesh.</span></span> <span data-ttu-id="c5bc9-123">Eş çözümleyiciler hakkında daha fazla bilgi için bkz. [eşdüzey çözümleyiciler](../../../wcf/feature-details/peer-resolvers.md).</span><span class="sxs-lookup"><span data-stu-id="c5bc9-123">For more information on peer resolvers, see [Peer Resolvers](../../../wcf/feature-details/peer-resolvers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5bc9-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5bc9-124">See also</span></span>

- <xref:System.ServiceModel.PeerResolver>
- <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>
- <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>
- <xref:System.ServiceModel.Configuration.PeerResolverElement>
- [<span data-ttu-id="c5bc9-125">Eş Çözücüler</span><span class="sxs-lookup"><span data-stu-id="c5bc9-125">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="c5bc9-126">[Bir PeerChannel uygulamasına özel çözümleyici ekleme](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="c5bc9-126">[Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span></span>
