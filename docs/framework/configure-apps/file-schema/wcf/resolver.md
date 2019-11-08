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
# <a name="resolver"></a><span data-ttu-id="4abc8-101">\<çözümleyici ></span><span class="sxs-lookup"><span data-stu-id="4abc8-101">\<resolver></span></span>
<span data-ttu-id="4abc8-102">Bir eş ağ KIMLIĞINI, kafeslere katılan çeşitli düğümleri temsil eden bir eş düğüm adresleri kümesine çözümlemek için kullanılan bir eş çözümleyici belirtir.</span><span class="sxs-lookup"><span data-stu-id="4abc8-102">Specifies a peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>  
  
<span data-ttu-id="4abc8-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="4abc8-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4abc8-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="4abc8-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="4abc8-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="4abc8-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="4abc8-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netPeerTcpBinding >** ](netpeertcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="4abc8-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)</span></span>\
<span data-ttu-id="4abc8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="4abc8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="4abc8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<çözümleyici >**</span><span class="sxs-lookup"><span data-stu-id="4abc8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<resolver>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4abc8-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4abc8-109">Syntax</span></span>  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"
          referralPolicy="DoNotShare/Service/Share">
</resolver>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4abc8-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4abc8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4abc8-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4abc8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4abc8-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4abc8-112">Attributes</span></span>  
  
|<span data-ttu-id="4abc8-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4abc8-113">Attribute</span></span>|<span data-ttu-id="4abc8-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4abc8-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="4abc8-115">Bu hizmetle ilişkili eş çözümleyici örneğinin PNRP 'ye özgü mi, özel bir çözümleyici mi yoksa otomatik olarak mı belirlendiğini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="4abc8-115">A string that specifies whether the peer resolver instance associated with this service is either PNRP-specific, a custom resolver, or automatically determined.</span></span> <span data-ttu-id="4abc8-116">Bu öznitelik <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>türündedir.</span><span class="sxs-lookup"><span data-stu-id="4abc8-116">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span></span>|  
|`referralPolicy`|<span data-ttu-id="4abc8-117">Başvuruların eşler arasında paylaşılma yöntemini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="4abc8-117">A string that specifies the way referrals are shared among peers.</span></span> <span data-ttu-id="4abc8-118">Bu öznitelik <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>türündedir.</span><span class="sxs-lookup"><span data-stu-id="4abc8-118">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4abc8-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4abc8-119">Child Elements</span></span>  
  
|<span data-ttu-id="4abc8-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="4abc8-120">Element</span></span>|<span data-ttu-id="4abc8-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4abc8-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4abc8-122">\<üst bilgileri ></span><span class="sxs-lookup"><span data-stu-id="4abc8-122">\<headers></span></span>](headers.md)|<span data-ttu-id="4abc8-123">Özel bir eş çözümleyici hizmetinin ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4abc8-123">Specifies settings for a custom peer resolver service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4abc8-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4abc8-124">Parent Elements</span></span>  
  
|<span data-ttu-id="4abc8-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="4abc8-125">Element</span></span>|<span data-ttu-id="4abc8-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4abc8-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4abc8-127">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="4abc8-127">\<binding></span></span>](bindings.md)|<span data-ttu-id="4abc8-128">[\<netPeerTcpBinding >](netpeertcpbinding.md)bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4abc8-128">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4abc8-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4abc8-129">Remarks</span></span>  
 <span data-ttu-id="4abc8-130">Eş adı çözümleyici, eş kanallar tarafından bir eş ağ içinde yer alan eş düğümleri bulmak için kullanılan bir bulma hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="4abc8-130">A peer name resolver is a discovery service used by peer channels to find peer nodes that participate in a peer mesh.</span></span> <span data-ttu-id="4abc8-131">Eş ağı olan bir düğüm olan bir düğümü "kaydettirmek" için de kullanılır. Bu bir düğüm, Eş ağ üzerinde bilinen ve kullanılabilir hale gelir.</span><span class="sxs-lookup"><span data-stu-id="4abc8-131">It is also used to "register" a node with a peer mesh, the mechanism by which the peer node becomes known and available from the peer mesh.</span></span> <span data-ttu-id="4abc8-132">Eş çözümleyiciler hakkında daha fazla bilgi için bkz. [eşdüzey çözümleyiciler](../../../wcf/feature-details/peer-resolvers.md).</span><span class="sxs-lookup"><span data-stu-id="4abc8-132">For more information on peer resolvers, see [Peer Resolvers](../../../wcf/feature-details/peer-resolvers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4abc8-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4abc8-133">See also</span></span>

- <xref:System.ServiceModel.PeerResolver>
- <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>
- <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>
- <xref:System.ServiceModel.Configuration.PeerResolverElement>
- [<span data-ttu-id="4abc8-134">Eş Çözücüler</span><span class="sxs-lookup"><span data-stu-id="4abc8-134">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="4abc8-135">[Bir PeerChannel uygulamasına özel çözümleyici ekleme](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="4abc8-135">[Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span></span>
