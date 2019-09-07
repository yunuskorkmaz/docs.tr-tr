---
title: <resolver>
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: fb974492dee6b2a4244cedc06e3f5e40334dd02a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399977"
---
# <a name="resolver"></a><span data-ttu-id="991b9-101">\<çözümleyici ></span><span class="sxs-lookup"><span data-stu-id="991b9-101">\<resolver></span></span>
<span data-ttu-id="991b9-102">Bir eş ağ KIMLIĞINI, kafeslere katılan çeşitli düğümleri temsil eden bir eş düğüm adresleri kümesine çözümlemek için kullanılan bir eş çözümleyici belirtir.</span><span class="sxs-lookup"><span data-stu-id="991b9-102">Specifies a peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>  
  
<span data-ttu-id="991b9-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="991b9-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="991b9-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="991b9-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="991b9-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="991b9-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="991b9-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netPeerTcpBinding >** ](netpeertcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="991b9-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)</span></span>\
<span data-ttu-id="991b9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="991b9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="991b9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<çözümleyici >**</span><span class="sxs-lookup"><span data-stu-id="991b9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<resolver>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="991b9-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="991b9-109">Syntax</span></span>  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"
          referralPolicy="DoNotShare/Service/Share">
</resolver>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="991b9-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="991b9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="991b9-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="991b9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="991b9-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="991b9-112">Attributes</span></span>  
  
|<span data-ttu-id="991b9-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="991b9-113">Attribute</span></span>|<span data-ttu-id="991b9-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="991b9-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="991b9-115">Bu hizmetle ilişkili eş çözümleyici örneğinin PNRP 'ye özgü mi, özel bir çözümleyici mi yoksa otomatik olarak mı belirlendiğini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="991b9-115">A string that specifies whether the peer resolver instance associated with this service is either PNRP-specific, a custom resolver, or automatically determined.</span></span> <span data-ttu-id="991b9-116">Bu öznitelik türü <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span><span class="sxs-lookup"><span data-stu-id="991b9-116">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span></span>|  
|`referralPolicy`|<span data-ttu-id="991b9-117">Başvuruların eşler arasında paylaşılma yöntemini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="991b9-117">A string that specifies the way referrals are shared among peers.</span></span> <span data-ttu-id="991b9-118">Bu öznitelik türü <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span><span class="sxs-lookup"><span data-stu-id="991b9-118">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="991b9-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="991b9-119">Child Elements</span></span>  
  
|<span data-ttu-id="991b9-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="991b9-120">Element</span></span>|<span data-ttu-id="991b9-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="991b9-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="991b9-122">\<üst bilgiler ></span><span class="sxs-lookup"><span data-stu-id="991b9-122">\<headers></span></span>](headers.md)|<span data-ttu-id="991b9-123">Özel bir eş çözümleyici hizmetinin ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="991b9-123">Specifies settings for a custom peer resolver service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="991b9-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="991b9-124">Parent Elements</span></span>  
  
|<span data-ttu-id="991b9-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="991b9-125">Element</span></span>|<span data-ttu-id="991b9-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="991b9-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="991b9-127">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="991b9-127">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="991b9-128">[ \<NetPeerTcpBinding >](netpeertcpbinding.md)'ın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="991b9-128">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="991b9-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="991b9-129">Remarks</span></span>  
 <span data-ttu-id="991b9-130">Eş adı çözümleyici, eş kanallar tarafından bir eş ağ içinde yer alan eş düğümleri bulmak için kullanılan bir bulma hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="991b9-130">A peer name resolver is a discovery service used by peer channels to find peer nodes that participate in a peer mesh.</span></span> <span data-ttu-id="991b9-131">Eş ağı olan bir düğüm olan bir düğümü "kaydettirmek" için de kullanılır. Bu bir düğüm, Eş ağ üzerinde bilinen ve kullanılabilir hale gelir.</span><span class="sxs-lookup"><span data-stu-id="991b9-131">It is also used to "register" a node with a peer mesh, the mechanism by which the peer node becomes known and available from the peer mesh.</span></span> <span data-ttu-id="991b9-132">Eş çözümleyiciler hakkında daha fazla bilgi için bkz. [eşdüzey çözümleyiciler](../../../wcf/feature-details/peer-resolvers.md).</span><span class="sxs-lookup"><span data-stu-id="991b9-132">For more information on peer resolvers, see [Peer Resolvers](../../../wcf/feature-details/peer-resolvers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="991b9-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="991b9-133">See also</span></span>

- <xref:System.ServiceModel.PeerResolver>
- <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>
- <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>
- <xref:System.ServiceModel.Configuration.PeerResolverElement>
- [<span data-ttu-id="991b9-134">Eş Çözücüler</span><span class="sxs-lookup"><span data-stu-id="991b9-134">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="991b9-135">[Bir PeerChannel uygulamasına özel çözümleyici ekleme](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="991b9-135">[Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span></span>
