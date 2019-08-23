---
title: <resolver>
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: e3a9ee00aab6ab48a1ba891565b63824e62b20fe
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934224"
---
# <a name="resolver"></a><span data-ttu-id="ab090-101">\<çözümleyici ></span><span class="sxs-lookup"><span data-stu-id="ab090-101">\<resolver></span></span>
<span data-ttu-id="ab090-102">Bir eş ağ KIMLIĞINI, kafeslere katılan çeşitli düğümleri temsil eden bir eş düğüm adresleri kümesine çözümlemek için kullanılan bir eş çözümleyici belirtir.</span><span class="sxs-lookup"><span data-stu-id="ab090-102">Specifies a peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>  
  
 <span data-ttu-id="ab090-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ab090-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="ab090-104">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="ab090-104">\<bindings></span></span>  
<span data-ttu-id="ab090-105">\<netPeerBinding ></span><span class="sxs-lookup"><span data-stu-id="ab090-105">\<netPeerBinding></span></span>  
<span data-ttu-id="ab090-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="ab090-106">\<binding></span></span>  
<span data-ttu-id="ab090-107">\<çözümleyici ></span><span class="sxs-lookup"><span data-stu-id="ab090-107">\<resolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab090-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ab090-108">Syntax</span></span>  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"
          referralPolicy="DoNotShare/Service/Share">
</resolver>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ab090-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ab090-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ab090-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ab090-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ab090-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ab090-111">Attributes</span></span>  
  
|<span data-ttu-id="ab090-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ab090-112">Attribute</span></span>|<span data-ttu-id="ab090-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ab090-113">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="ab090-114">Bu hizmetle ilişkili eş çözümleyici örneğinin PNRP 'ye özgü mi, özel bir çözümleyici mi yoksa otomatik olarak mı belirlendiğini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="ab090-114">A string that specifies whether the peer resolver instance associated with this service is either PNRP-specific, a custom resolver, or automatically determined.</span></span> <span data-ttu-id="ab090-115">Bu öznitelik türü <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span><span class="sxs-lookup"><span data-stu-id="ab090-115">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span></span>|  
|`referralPolicy`|<span data-ttu-id="ab090-116">Başvuruların eşler arasında paylaşılma yöntemini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="ab090-116">A string that specifies the way referrals are shared among peers.</span></span> <span data-ttu-id="ab090-117">Bu öznitelik türü <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span><span class="sxs-lookup"><span data-stu-id="ab090-117">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ab090-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ab090-118">Child Elements</span></span>  
  
|<span data-ttu-id="ab090-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="ab090-119">Element</span></span>|<span data-ttu-id="ab090-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ab090-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ab090-121">\<üst bilgiler ></span><span class="sxs-lookup"><span data-stu-id="ab090-121">\<headers></span></span>](headers.md)|<span data-ttu-id="ab090-122">Özel bir eş çözümleyici hizmetinin ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ab090-122">Specifies settings for a custom peer resolver service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ab090-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ab090-123">Parent Elements</span></span>  
  
|<span data-ttu-id="ab090-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="ab090-124">Element</span></span>|<span data-ttu-id="ab090-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ab090-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ab090-126">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="ab090-126">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="ab090-127">[ \<NetPeerTcpBinding >](netpeertcpbinding.md)'ın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ab090-127">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab090-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ab090-128">Remarks</span></span>  
 <span data-ttu-id="ab090-129">Eş adı çözümleyici, eş kanallar tarafından bir eş ağ içinde yer alan eş düğümleri bulmak için kullanılan bir bulma hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="ab090-129">A peer name resolver is a discovery service used by peer channels to find peer nodes that participate in a peer mesh.</span></span> <span data-ttu-id="ab090-130">Eş ağı olan bir düğüm olan bir düğümü "kaydettirmek" için de kullanılır. Bu bir düğüm, Eş ağ üzerinde bilinen ve kullanılabilir hale gelir.</span><span class="sxs-lookup"><span data-stu-id="ab090-130">It is also used to "register" a node with a peer mesh, the mechanism by which the peer node becomes known and available from the peer mesh.</span></span> <span data-ttu-id="ab090-131">Eş çözümleyiciler hakkında daha fazla bilgi için bkz. [eşdüzey çözümleyiciler](../../../wcf/feature-details/peer-resolvers.md).</span><span class="sxs-lookup"><span data-stu-id="ab090-131">For more information on peer resolvers, see [Peer Resolvers](../../../wcf/feature-details/peer-resolvers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab090-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab090-132">See also</span></span>

- <xref:System.ServiceModel.PeerResolver>
- <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>
- <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>
- <xref:System.ServiceModel.Configuration.PeerResolverElement>
- [<span data-ttu-id="ab090-133">Eş Çözücüler</span><span class="sxs-lookup"><span data-stu-id="ab090-133">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="ab090-134">[Bir PeerChannel uygulamasına özel çözümleyici ekleme](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="ab090-134">[Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span></span>
