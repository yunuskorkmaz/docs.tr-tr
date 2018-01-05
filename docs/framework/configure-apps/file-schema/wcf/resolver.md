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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc6e919600fbea15937a61eaa65299b3a372caaf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltresolvergt"></a><span data-ttu-id="a4a64-102">&lt;Çözümleyici&gt;</span><span class="sxs-lookup"><span data-stu-id="a4a64-102">&lt;resolver&gt;</span></span>
<span data-ttu-id="a4a64-103">Bir eş çözümlemek için kullanılan bir eş çözümleyici kafes katılmak birkaç düğüm temsil eden bir dizi Eş düğüm adresleri kimliği kafes belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4a64-103">Specifies a peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>  
  
 <span data-ttu-id="a4a64-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="a4a64-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a4a64-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="a4a64-105">\<bindings></span></span>  
<span data-ttu-id="a4a64-106">\<netPeerBinding ></span><span class="sxs-lookup"><span data-stu-id="a4a64-106">\<netPeerBinding></span></span>  
<span data-ttu-id="a4a64-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="a4a64-107">\<binding></span></span>  
<span data-ttu-id="a4a64-108">\<Çözümleyici ></span><span class="sxs-lookup"><span data-stu-id="a4a64-108">\<resolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4a64-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a4a64-109">Syntax</span></span>  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"  
   referralPolicy="DoNotShare/Service/Share">  
</resolver>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a4a64-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a4a64-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a4a64-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a4a64-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a4a64-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a4a64-112">Attributes</span></span>  
  
|<span data-ttu-id="a4a64-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a4a64-113">Attribute</span></span>|<span data-ttu-id="a4a64-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4a64-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="a4a64-115">Bu hizmetle ilişkilendirilen eş Çözümleyicisi örneği ya da PNRP özgü özel bir çözümleyici olup olmadığını belirtir veya otomatik olarak belirlenen bir dize.</span><span class="sxs-lookup"><span data-stu-id="a4a64-115">A string that specifies whether the peer resolver instance associated with this service is either PNRP-specific, a custom resolver, or automatically determined.</span></span> <span data-ttu-id="a4a64-116">Bu öznitelik türünde <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span><span class="sxs-lookup"><span data-stu-id="a4a64-116">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span></span>|  
|`referralPolicy`|<span data-ttu-id="a4a64-117">Yol başvuruları eşler arasında paylaşılan belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="a4a64-117">A string that specifies the way referrals are shared among peers.</span></span> <span data-ttu-id="a4a64-118">Bu öznitelik türünde <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span><span class="sxs-lookup"><span data-stu-id="a4a64-118">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a4a64-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a4a64-119">Child Elements</span></span>  
  
|<span data-ttu-id="a4a64-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="a4a64-120">Element</span></span>|<span data-ttu-id="a4a64-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4a64-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a4a64-122">\<üstbilgiler ></span><span class="sxs-lookup"><span data-stu-id="a4a64-122">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|<span data-ttu-id="a4a64-123">Özel eş Çözümleyici hizmeti ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4a64-123">Specifies settings for a custom peer resolver service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a4a64-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a4a64-124">Parent Elements</span></span>  
  
|<span data-ttu-id="a4a64-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="a4a64-125">Element</span></span>|<span data-ttu-id="a4a64-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4a64-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a4a64-127">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="a4a64-127">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="a4a64-128">Tüm bağlama özelliklerini tanımlayan [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="a4a64-128">Defines all binding capabilities of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4a64-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a4a64-129">Remarks</span></span>  
 <span data-ttu-id="a4a64-130">Eş adı çözümleyici eş bir eş kafes katılmak düğümleri bulmak için eş kanalları tarafından kullanılan bir bulma hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="a4a64-130">A peer name resolver is a discovery service used by peer channels to find peer nodes that participate in a peer mesh.</span></span> <span data-ttu-id="a4a64-131">Ayrıca, "olarak Eş düğüm eş kafes bilinir ve kullanılabilir hale mekanizması bir eş kafes sahip bir düğüm kaydetmek için" kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a4a64-131">It is also used to "register" a node with a peer mesh, the mechanism by which the peer node becomes known and available from the peer mesh.</span></span> <span data-ttu-id="a4a64-132">Eş çözücüler hakkında daha fazla bilgi için bkz: [eş çözücüler](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).</span><span class="sxs-lookup"><span data-stu-id="a4a64-132">For more information on peer resolvers, see [Peer Resolvers](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4a64-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a4a64-133">See Also</span></span>  
 <xref:System.ServiceModel.PeerResolver>  
 <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>  
 <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>  
 <xref:System.ServiceModel.Configuration.PeerResolverElement>  
 [<span data-ttu-id="a4a64-134">Eş Çözücüler</span><span class="sxs-lookup"><span data-stu-id="a4a64-134">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)  
 [<span data-ttu-id="a4a64-135">Özel Çözücü PeerChannel'a uygulamaya ekleme</span><span class="sxs-lookup"><span data-stu-id="a4a64-135">Adding a Custom Resolver to a PeerChannel Application</span></span>](http://msdn.microsoft.com/en-us/12aa3787-2962-439c-ad27-46523c8b0419)
