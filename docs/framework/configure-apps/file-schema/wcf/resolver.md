---
title: '&lt;Çözümleyici&gt;'
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: 2a3e0de2bb5d2ed022f53aa5e498f338eaf56ca8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54578607"
---
# <a name="ltresolvergt"></a><span data-ttu-id="599fb-102">&lt;Çözümleyici&gt;</span><span class="sxs-lookup"><span data-stu-id="599fb-102">&lt;resolver&gt;</span></span>
<span data-ttu-id="599fb-103">Ağ içinde katılan çeşitli düğümleri temsil eden bir eş düğüm adresleri kümesi bir eş çözümlemek için kullanılan bir eş çözümleyici ağ Kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="599fb-103">Specifies a peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>  
  
 <span data-ttu-id="599fb-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="599fb-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="599fb-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="599fb-105">\<bindings></span></span>  
<span data-ttu-id="599fb-106">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="599fb-106">\<netPeerBinding></span></span>  
<span data-ttu-id="599fb-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="599fb-107">\<binding></span></span>  
<span data-ttu-id="599fb-108">\<Çözümleyici ></span><span class="sxs-lookup"><span data-stu-id="599fb-108">\<resolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="599fb-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="599fb-109">Syntax</span></span>  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"
          referralPolicy="DoNotShare/Service/Share">
</resolver>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="599fb-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="599fb-110">Attributes and Elements</span></span>  
 <span data-ttu-id="599fb-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="599fb-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="599fb-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="599fb-112">Attributes</span></span>  
  
|<span data-ttu-id="599fb-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="599fb-113">Attribute</span></span>|<span data-ttu-id="599fb-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="599fb-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="599fb-115">Bu hizmetle ilişkili eş Çözücü örneğinin ya da PNRP belirli bir özel Çözücü olup olmadığını belirtir ya da otomatik olarak belirlenen bir dize.</span><span class="sxs-lookup"><span data-stu-id="599fb-115">A string that specifies whether the peer resolver instance associated with this service is either PNRP-specific, a custom resolver, or automatically determined.</span></span> <span data-ttu-id="599fb-116">Bu öznitelik türünde <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span><span class="sxs-lookup"><span data-stu-id="599fb-116">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span></span>|  
|`referralPolicy`|<span data-ttu-id="599fb-117">Eşler arasında paylaşılan yol başvurularını belirleyen bir dize.</span><span class="sxs-lookup"><span data-stu-id="599fb-117">A string that specifies the way referrals are shared among peers.</span></span> <span data-ttu-id="599fb-118">Bu öznitelik türünde <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span><span class="sxs-lookup"><span data-stu-id="599fb-118">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="599fb-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="599fb-119">Child Elements</span></span>  
  
|<span data-ttu-id="599fb-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="599fb-120">Element</span></span>|<span data-ttu-id="599fb-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="599fb-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="599fb-122">\<üstbilgiler ></span><span class="sxs-lookup"><span data-stu-id="599fb-122">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|<span data-ttu-id="599fb-123">Özel eş Çözücü hizmetinin ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="599fb-123">Specifies settings for a custom peer resolver service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="599fb-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="599fb-124">Parent Elements</span></span>  
  
|<span data-ttu-id="599fb-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="599fb-125">Element</span></span>|<span data-ttu-id="599fb-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="599fb-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="599fb-127">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="599fb-127">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="599fb-128">Tüm bağlama yeteneklerini tanımlar [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="599fb-128">Defines all binding capabilities of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="599fb-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="599fb-129">Remarks</span></span>  
 <span data-ttu-id="599fb-130">Bir eş ad çözümleyici eş bir eş ağ içinde katılan düğümleri bulmak için eş kanallar tarafından kullanılan bir bulma hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="599fb-130">A peer name resolver is a discovery service used by peer channels to find peer nodes that participate in a peer mesh.</span></span> <span data-ttu-id="599fb-131">Ayrıca, "bir düğüm olarak Eş düğüm eş kafes bilinen ve kullanılabilir hale gelir mekanizması bir eş kafes kaydetmek için" kullanılır.</span><span class="sxs-lookup"><span data-stu-id="599fb-131">It is also used to "register" a node with a peer mesh, the mechanism by which the peer node becomes known and available from the peer mesh.</span></span> <span data-ttu-id="599fb-132">Eş çözücüler hakkında daha fazla bilgi için bkz. [eş çözücüler](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).</span><span class="sxs-lookup"><span data-stu-id="599fb-132">For more information on peer resolvers, see [Peer Resolvers](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="599fb-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="599fb-133">See also</span></span>
- <xref:System.ServiceModel.PeerResolver>
- <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>
- <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>
- <xref:System.ServiceModel.Configuration.PeerResolverElement>
- [<span data-ttu-id="599fb-134">Eş Çözücüler</span><span class="sxs-lookup"><span data-stu-id="599fb-134">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
- [<span data-ttu-id="599fb-135">Bir özel Çözücü PeerChannel'a uygulamaya ekleme</span><span class="sxs-lookup"><span data-stu-id="599fb-135">Adding a Custom Resolver to a PeerChannel Application</span></span>](https://msdn.microsoft.com/library/12aa3787-2962-439c-ad27-46523c8b0419)
