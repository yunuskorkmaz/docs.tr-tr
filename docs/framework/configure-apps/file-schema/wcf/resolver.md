---
title: '&lt;Çözümleyici&gt;'
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: f29c34f53a8bdaee4b30c72bb5d764ae3935fe7a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749029"
---
# <a name="ltresolvergt"></a><span data-ttu-id="bf69b-102">&lt;Çözümleyici&gt;</span><span class="sxs-lookup"><span data-stu-id="bf69b-102">&lt;resolver&gt;</span></span>
<span data-ttu-id="bf69b-103">Bir eş çözümlemek için kullanılan bir eş çözümleyici kafes katılmak birkaç düğüm temsil eden bir dizi Eş düğüm adresleri kimliği kafes belirtir.</span><span class="sxs-lookup"><span data-stu-id="bf69b-103">Specifies a peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>  
  
 <span data-ttu-id="bf69b-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="bf69b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="bf69b-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="bf69b-105">\<bindings></span></span>  
<span data-ttu-id="bf69b-106">\<netPeerBinding ></span><span class="sxs-lookup"><span data-stu-id="bf69b-106">\<netPeerBinding></span></span>  
<span data-ttu-id="bf69b-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="bf69b-107">\<binding></span></span>  
<span data-ttu-id="bf69b-108">\<Çözümleyici ></span><span class="sxs-lookup"><span data-stu-id="bf69b-108">\<resolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf69b-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bf69b-109">Syntax</span></span>  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"  
   referralPolicy="DoNotShare/Service/Share">  
</resolver>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bf69b-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bf69b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bf69b-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bf69b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bf69b-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bf69b-112">Attributes</span></span>  
  
|<span data-ttu-id="bf69b-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="bf69b-113">Attribute</span></span>|<span data-ttu-id="bf69b-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bf69b-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="bf69b-115">Bu hizmetle ilişkilendirilen eş Çözümleyicisi örneği ya da PNRP özgü özel bir çözümleyici olup olmadığını belirtir veya otomatik olarak belirlenen bir dize.</span><span class="sxs-lookup"><span data-stu-id="bf69b-115">A string that specifies whether the peer resolver instance associated with this service is either PNRP-specific, a custom resolver, or automatically determined.</span></span> <span data-ttu-id="bf69b-116">Bu öznitelik türünde <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span><span class="sxs-lookup"><span data-stu-id="bf69b-116">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span></span>|  
|`referralPolicy`|<span data-ttu-id="bf69b-117">Yol başvuruları eşler arasında paylaşılan belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="bf69b-117">A string that specifies the way referrals are shared among peers.</span></span> <span data-ttu-id="bf69b-118">Bu öznitelik türünde <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span><span class="sxs-lookup"><span data-stu-id="bf69b-118">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bf69b-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bf69b-119">Child Elements</span></span>  
  
|<span data-ttu-id="bf69b-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="bf69b-120">Element</span></span>|<span data-ttu-id="bf69b-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bf69b-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bf69b-122">\<üstbilgiler ></span><span class="sxs-lookup"><span data-stu-id="bf69b-122">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|<span data-ttu-id="bf69b-123">Özel eş Çözümleyici hizmeti ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bf69b-123">Specifies settings for a custom peer resolver service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bf69b-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bf69b-124">Parent Elements</span></span>  
  
|<span data-ttu-id="bf69b-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="bf69b-125">Element</span></span>|<span data-ttu-id="bf69b-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bf69b-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bf69b-127">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="bf69b-127">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="bf69b-128">Tüm bağlama özelliklerini tanımlayan [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="bf69b-128">Defines all binding capabilities of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf69b-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bf69b-129">Remarks</span></span>  
 <span data-ttu-id="bf69b-130">Eş adı çözümleyici eş bir eş kafes katılmak düğümleri bulmak için eş kanalları tarafından kullanılan bir bulma hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="bf69b-130">A peer name resolver is a discovery service used by peer channels to find peer nodes that participate in a peer mesh.</span></span> <span data-ttu-id="bf69b-131">Ayrıca, "olarak Eş düğüm eş kafes bilinir ve kullanılabilir hale mekanizması bir eş kafes sahip bir düğüm kaydetmek için" kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bf69b-131">It is also used to "register" a node with a peer mesh, the mechanism by which the peer node becomes known and available from the peer mesh.</span></span> <span data-ttu-id="bf69b-132">Eş çözücüler hakkında daha fazla bilgi için bkz: [eş çözücüler](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).</span><span class="sxs-lookup"><span data-stu-id="bf69b-132">For more information on peer resolvers, see [Peer Resolvers](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf69b-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bf69b-133">See Also</span></span>  
 <xref:System.ServiceModel.PeerResolver>  
 <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>  
 <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>  
 <xref:System.ServiceModel.Configuration.PeerResolverElement>  
 [<span data-ttu-id="bf69b-134">Eş Çözücüler</span><span class="sxs-lookup"><span data-stu-id="bf69b-134">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)  
 [<span data-ttu-id="bf69b-135">Özel Çözücü PeerChannel'a uygulamaya ekleme</span><span class="sxs-lookup"><span data-stu-id="bf69b-135">Adding a Custom Resolver to a PeerChannel Application</span></span>](http://msdn.microsoft.com/library/12aa3787-2962-439c-ad27-46523c8b0419)
