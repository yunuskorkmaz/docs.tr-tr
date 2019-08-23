---
title: <custom>
ms.date: 03/30/2017
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
ms.openlocfilehash: b5cc522604fa7aca8ca6eae787520265b36fef6f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925950"
---
# <a name="custom"></a><span data-ttu-id="57594-101">\<Özel ></span><span class="sxs-lookup"><span data-stu-id="57594-101">\<custom></span></span>
<span data-ttu-id="57594-102">Özel bir eş çözümleyici hizmetinin ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="57594-102">Specifies settings for a custom peer resolver service.</span></span>  
  
<span data-ttu-id="57594-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="57594-103">\<system.serviceModel></span></span>  
<span data-ttu-id="57594-104">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="57594-104">\<bindings></span></span>  
<span data-ttu-id="57594-105">\<netPeerBinding ></span><span class="sxs-lookup"><span data-stu-id="57594-105">\<netPeerBinding></span></span>  
<span data-ttu-id="57594-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="57594-106">\<binding></span></span>  
<span data-ttu-id="57594-107">\<çözümleyici ></span><span class="sxs-lookup"><span data-stu-id="57594-107">\<resolver></span></span>  
<span data-ttu-id="57594-108">\<Özel ></span><span class="sxs-lookup"><span data-stu-id="57594-108">\<custom></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57594-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="57594-109">Syntax</span></span>  
  
```xml  
<custom address="Uri"
        resolverType="String">
  <headers/>
  <identity/>
</custom>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="57594-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="57594-110">Attributes and Elements</span></span>  
 <span data-ttu-id="57594-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="57594-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="57594-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="57594-112">Attributes</span></span>  
  
|<span data-ttu-id="57594-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="57594-113">Attribute</span></span>|<span data-ttu-id="57594-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57594-114">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="57594-115">Özel eş çözümleyici hizmetini barındıran eş düğümün uç nokta adresini belirten bir URI.</span><span class="sxs-lookup"><span data-stu-id="57594-115">A URI that specifies the endpoint address of the peer node that hosts the custom peer resolver service.</span></span>|  
|`resolverType`|<span data-ttu-id="57594-116">Özel eş çözücü hizmetinin türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="57594-116">A string that specifies the type of the custom peer resolver service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="57594-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="57594-117">Child Elements</span></span>  
  
|<span data-ttu-id="57594-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="57594-118">Element</span></span>|<span data-ttu-id="57594-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57594-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57594-120">\<kimlik ></span><span class="sxs-lookup"><span data-stu-id="57594-120">\<identity></span></span>](identity.md)|<span data-ttu-id="57594-121">Bu öğeyle yapılandırılan özel eş çözümleyiciler için kimliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="57594-121">Specifies the identity for custom peer resolvers configured with this element.</span></span> <span data-ttu-id="57594-122">Bu öğe türündedir <xref:System.ServiceModel.Configuration.IdentityElement>.</span><span class="sxs-lookup"><span data-stu-id="57594-122">This element is of type <xref:System.ServiceModel.Configuration.IdentityElement>.</span></span>|  
|[<span data-ttu-id="57594-123">\<üst bilgiler ></span><span class="sxs-lookup"><span data-stu-id="57594-123">\<headers></span></span>](headers-element.md)|<span data-ttu-id="57594-124">Özel eş çözümleyici tarafından işlenen SOAP iletileri için kullanılan adres üst bilgisi koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="57594-124">A collection of address header used for SOAP messages handled by the custom peer resolver.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="57594-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="57594-125">Parent Elements</span></span>  
  
|<span data-ttu-id="57594-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="57594-126">Element</span></span>|<span data-ttu-id="57594-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57594-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57594-128">\<çözümleyici ></span><span class="sxs-lookup"><span data-stu-id="57594-128">\<resolver></span></span>](resolver.md)|<span data-ttu-id="57594-129">Eş ağ KIMLIĞINI, kafeslere katılan çeşitli düğümleri temsil eden bir eş düğüm adresleri kümesine çözümlemek için kullanılan bir eş çözümleyici.</span><span class="sxs-lookup"><span data-stu-id="57594-129">A peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57594-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="57594-130">Remarks</span></span>  
 <span data-ttu-id="57594-131">Bu öğe, hizmeti barındıran eşin uç nokta adresi ve belirli bağlama ayarları dahil olmak üzere özel bir eşdüzey çözümleyici Hizmeti için temel ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="57594-131">This element defines the basic settings for a custom peer resolver service, including the endpoint address of the peer hosting the service and any specific binding settings.</span></span> <span data-ttu-id="57594-132">Özel çözümleyici oluşturma hakkında daha fazla bilgi için bkz. [bir PeerChannel uygulamasına özel çözümleyici ekleme](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="57594-132">For more information on creating a custom resolver, see [Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57594-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="57594-133">See also</span></span>

- <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>
- <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>
- <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>
- <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>
- [<span data-ttu-id="57594-134">Eş Çözücüler</span><span class="sxs-lookup"><span data-stu-id="57594-134">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="57594-135">[Bir PeerChannel uygulamasına özel çözümleyici ekleme](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="57594-135">[Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span></span>
