---
title: <custom>
ms.date: 03/30/2017
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
ms.openlocfilehash: 18359e871feed17a11006d0b2998907faf25c158
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59106593"
---
# <a name="custom"></a><span data-ttu-id="e54a5-101">\<Özel ></span><span class="sxs-lookup"><span data-stu-id="e54a5-101">\<custom></span></span>
<span data-ttu-id="e54a5-102">Özel eş Çözücü hizmetinin ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e54a5-102">Specifies settings for a custom peer resolver service.</span></span>  
  
<span data-ttu-id="e54a5-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e54a5-103">\<system.serviceModel></span></span>  
<span data-ttu-id="e54a5-104">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="e54a5-104">\<bindings></span></span>  
<span data-ttu-id="e54a5-105">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="e54a5-105">\<netPeerBinding></span></span>  
<span data-ttu-id="e54a5-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="e54a5-106">\<binding></span></span>  
<span data-ttu-id="e54a5-107">\<Çözümleyici ></span><span class="sxs-lookup"><span data-stu-id="e54a5-107">\<resolver></span></span>  
<span data-ttu-id="e54a5-108">\<Özel ></span><span class="sxs-lookup"><span data-stu-id="e54a5-108">\<custom></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e54a5-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e54a5-109">Syntax</span></span>  
  
```xml  
<custom address="Uri"
        resolverType="String">
  <headers/>
  <identity/>
</custom>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e54a5-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e54a5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e54a5-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e54a5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e54a5-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e54a5-112">Attributes</span></span>  
  
|<span data-ttu-id="e54a5-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e54a5-113">Attribute</span></span>|<span data-ttu-id="e54a5-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e54a5-114">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="e54a5-115">Özel eş çözümleyici hizmetini barındıran eş düğümün uç nokta adresini belirten bir URI.</span><span class="sxs-lookup"><span data-stu-id="e54a5-115">A URI that specifies the endpoint address of the peer node that hosts the custom peer resolver service.</span></span>|  
|`resolverType`|<span data-ttu-id="e54a5-116">Özel eş Çözücü hizmetinin türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="e54a5-116">A string that specifies the type of the custom peer resolver service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e54a5-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e54a5-117">Child Elements</span></span>  
  
|<span data-ttu-id="e54a5-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="e54a5-118">Element</span></span>|<span data-ttu-id="e54a5-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e54a5-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e54a5-120">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="e54a5-120">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="e54a5-121">Bu öğe ile yapılandırılmış özel eş çözücüler kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e54a5-121">Specifies the identity for custom peer resolvers configured with this element.</span></span> <span data-ttu-id="e54a5-122">Bu öğe türünde <xref:System.ServiceModel.Configuration.IdentityElement>.</span><span class="sxs-lookup"><span data-stu-id="e54a5-122">This element is of type <xref:System.ServiceModel.Configuration.IdentityElement>.</span></span>|  
|[<span data-ttu-id="e54a5-123">\<üstbilgiler ></span><span class="sxs-lookup"><span data-stu-id="e54a5-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="e54a5-124">Özel eş çözümleyici tarafından işlenen SOAP iletileri için kullanılan adres üstbilgisi koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="e54a5-124">A collection of address header used for SOAP messages handled by the custom peer resolver.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e54a5-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e54a5-125">Parent Elements</span></span>  
  
|<span data-ttu-id="e54a5-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="e54a5-126">Element</span></span>|<span data-ttu-id="e54a5-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e54a5-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e54a5-128">\<Çözümleyici ></span><span class="sxs-lookup"><span data-stu-id="e54a5-128">\<resolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|<span data-ttu-id="e54a5-129">Bir eş çözümlemek için kullanılan bir eş çözümleyici ağ Kimliğini ağ içinde katılan çeşitli düğümleri temsil eden bir eş düğüm adresleri kümesi.</span><span class="sxs-lookup"><span data-stu-id="e54a5-129">A peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e54a5-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e54a5-130">Remarks</span></span>  
 <span data-ttu-id="e54a5-131">Bu öğe, hizmet ve herhangi bir özel bağlayıcı ayarları barındıran eş uç nokta adresini de dahil olmak üzere bir özel eş Çözücü hizmetinin temel ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e54a5-131">This element defines the basic settings for a custom peer resolver service, including the endpoint address of the peer hosting the service and any specific binding settings.</span></span> <span data-ttu-id="e54a5-132">Bir özel Çözücü oluşturma hakkında daha fazla bilgi için bkz. [PeerChannel'a uygulamaya özel Çözücü ekleme](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="e54a5-132">For more information on creating a custom resolver, see [Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e54a5-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e54a5-133">See also</span></span>

- <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>
- <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>
- <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>
- <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>
- [<span data-ttu-id="e54a5-134">Eş Çözücüler</span><span class="sxs-lookup"><span data-stu-id="e54a5-134">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
- [<span data-ttu-id="e54a5-135">Bir özel Çözücü PeerChannel'a uygulamaya ekleme</span><span class="sxs-lookup"><span data-stu-id="e54a5-135">Adding a Custom Resolver to a PeerChannel Application</span></span>](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))
