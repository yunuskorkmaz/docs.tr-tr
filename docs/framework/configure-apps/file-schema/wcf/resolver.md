---
description: 'Hakkında daha fazla bilgi edinin: <resolver>'
title: <resolver>
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: 338f9342d1ef14f3d96dada17fb9f6d893c86bee
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683365"
---
# \<resolver>

<span data-ttu-id="e793a-102">Bir eş ağ KIMLIĞINI, kafeslere katılan çeşitli düğümleri temsil eden bir eş düğüm adresleri kümesine çözümlemek için kullanılan bir eş çözümleyici belirtir.</span><span class="sxs-lookup"><span data-stu-id="e793a-102">Specifies a peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<resolver>**  
  
## <a name="syntax"></a><span data-ttu-id="e793a-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="e793a-103">Syntax</span></span>  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"
          referralPolicy="DoNotShare/Service/Share">
</resolver>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e793a-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e793a-104">Attributes and Elements</span></span>  

 <span data-ttu-id="e793a-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e793a-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e793a-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e793a-106">Attributes</span></span>  
  
|<span data-ttu-id="e793a-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e793a-107">Attribute</span></span>|<span data-ttu-id="e793a-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e793a-108">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="e793a-109">Bu hizmetle ilişkili eş çözümleyici örneğinin PNRP 'ye özgü mi, özel bir çözümleyici mi yoksa otomatik olarak mı belirlendiğini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="e793a-109">A string that specifies whether the peer resolver instance associated with this service is either PNRP-specific, a custom resolver, or automatically determined.</span></span> <span data-ttu-id="e793a-110">Bu öznitelik türü <xref:System.ServiceModel.PeerResolvers.PeerResolverMode> .</span><span class="sxs-lookup"><span data-stu-id="e793a-110">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span></span>|  
|`referralPolicy`|<span data-ttu-id="e793a-111">Başvuruların eşler arasında paylaşılma yöntemini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="e793a-111">A string that specifies the way referrals are shared among peers.</span></span> <span data-ttu-id="e793a-112">Bu öznitelik türü <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy> .</span><span class="sxs-lookup"><span data-stu-id="e793a-112">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e793a-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e793a-113">Child Elements</span></span>  
  
|<span data-ttu-id="e793a-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="e793a-114">Element</span></span>|<span data-ttu-id="e793a-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e793a-115">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers.md)|<span data-ttu-id="e793a-116">Özel bir eş çözümleyici hizmetinin ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e793a-116">Specifies settings for a custom peer resolver service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e793a-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e793a-117">Parent Elements</span></span>  
  
|<span data-ttu-id="e793a-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="e793a-118">Element</span></span>|<span data-ttu-id="e793a-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e793a-119">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="e793a-120">Öğesinin tüm bağlama yeteneklerini tanımlar [\<netPeerTcpBinding>](netpeertcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="e793a-120">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e793a-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e793a-121">Remarks</span></span>  

 <span data-ttu-id="e793a-122">Eş adı çözümleyici, eş kanallar tarafından bir eş ağ içinde yer alan eş düğümleri bulmak için kullanılan bir bulma hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="e793a-122">A peer name resolver is a discovery service used by peer channels to find peer nodes that participate in a peer mesh.</span></span> <span data-ttu-id="e793a-123">Eş ağı olan bir düğüm olan bir düğümü "kaydettirmek" için de kullanılır. Bu bir düğüm, Eş ağ üzerinde bilinen ve kullanılabilir hale gelir.</span><span class="sxs-lookup"><span data-stu-id="e793a-123">It is also used to "register" a node with a peer mesh, the mechanism by which the peer node becomes known and available from the peer mesh.</span></span> <span data-ttu-id="e793a-124">Eş çözümleyiciler hakkında daha fazla bilgi için bkz. [eşdüzey çözümleyiciler](../../../wcf/feature-details/peer-resolvers.md).</span><span class="sxs-lookup"><span data-stu-id="e793a-124">For more information on peer resolvers, see [Peer Resolvers](../../../wcf/feature-details/peer-resolvers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e793a-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e793a-125">See also</span></span>

- <xref:System.ServiceModel.PeerResolver>
- <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>
- <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>
- <xref:System.ServiceModel.Configuration.PeerResolverElement>
- [<span data-ttu-id="e793a-126">Eş Çözücüler</span><span class="sxs-lookup"><span data-stu-id="e793a-126">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="e793a-127">[Bir PeerChannel uygulamasına özel çözümleyici ekleme](/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="e793a-127">[Adding a Custom Resolver to a PeerChannel Application](/previous-versions/ms730105(v=vs.90))</span></span>
