---
title: <custom>
ms.date: 03/30/2017
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
ms.openlocfilehash: 598b341e8b09acd11ba215e6add3adf9e44b2b81
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400461"
---
# <a name="custom"></a><span data-ttu-id="229d7-101">\<Özel ></span><span class="sxs-lookup"><span data-stu-id="229d7-101">\<custom></span></span>
<span data-ttu-id="229d7-102">Özel bir eş çözümleyici hizmetinin ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="229d7-102">Specifies settings for a custom peer resolver service.</span></span>  
  
<span data-ttu-id="229d7-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="229d7-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="229d7-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="229d7-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="229d7-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="229d7-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="229d7-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netPeerTcpBinding >** ](netpeertcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="229d7-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)</span></span>\
<span data-ttu-id="229d7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="229d7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="229d7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<çözümleyici >** ](resolver.md)</span><span class="sxs-lookup"><span data-stu-id="229d7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<resolver>**](resolver.md)</span></span>\
<span data-ttu-id="229d7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Özel >**</span><span class="sxs-lookup"><span data-stu-id="229d7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<custom>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="229d7-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="229d7-110">Syntax</span></span>  
  
```xml  
<custom address="Uri"
        resolverType="String">
  <headers/>
  <identity/>
</custom>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="229d7-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="229d7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="229d7-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="229d7-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="229d7-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="229d7-113">Attributes</span></span>  
  
|<span data-ttu-id="229d7-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="229d7-114">Attribute</span></span>|<span data-ttu-id="229d7-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="229d7-115">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="229d7-116">Özel eş çözümleyici hizmetini barındıran eş düğümün uç nokta adresini belirten bir URI.</span><span class="sxs-lookup"><span data-stu-id="229d7-116">A URI that specifies the endpoint address of the peer node that hosts the custom peer resolver service.</span></span>|  
|`resolverType`|<span data-ttu-id="229d7-117">Özel eş çözücü hizmetinin türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="229d7-117">A string that specifies the type of the custom peer resolver service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="229d7-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="229d7-118">Child Elements</span></span>  
  
|<span data-ttu-id="229d7-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="229d7-119">Element</span></span>|<span data-ttu-id="229d7-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="229d7-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="229d7-121">\<kimlik ></span><span class="sxs-lookup"><span data-stu-id="229d7-121">\<identity></span></span>](identity.md)|<span data-ttu-id="229d7-122">Bu öğeyle yapılandırılan özel eş çözümleyiciler için kimliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="229d7-122">Specifies the identity for custom peer resolvers configured with this element.</span></span> <span data-ttu-id="229d7-123">Bu öğe türündedir <xref:System.ServiceModel.Configuration.IdentityElement>.</span><span class="sxs-lookup"><span data-stu-id="229d7-123">This element is of type <xref:System.ServiceModel.Configuration.IdentityElement>.</span></span>|  
|[<span data-ttu-id="229d7-124">\<üst bilgiler ></span><span class="sxs-lookup"><span data-stu-id="229d7-124">\<headers></span></span>](headers-element.md)|<span data-ttu-id="229d7-125">Özel eş çözümleyici tarafından işlenen SOAP iletileri için kullanılan adres üst bilgisi koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="229d7-125">A collection of address header used for SOAP messages handled by the custom peer resolver.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="229d7-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="229d7-126">Parent Elements</span></span>  
  
|<span data-ttu-id="229d7-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="229d7-127">Element</span></span>|<span data-ttu-id="229d7-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="229d7-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="229d7-129">\<çözümleyici ></span><span class="sxs-lookup"><span data-stu-id="229d7-129">\<resolver></span></span>](resolver.md)|<span data-ttu-id="229d7-130">Eş ağ KIMLIĞINI, kafeslere katılan çeşitli düğümleri temsil eden bir eş düğüm adresleri kümesine çözümlemek için kullanılan bir eş çözümleyici.</span><span class="sxs-lookup"><span data-stu-id="229d7-130">A peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="229d7-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="229d7-131">Remarks</span></span>  
 <span data-ttu-id="229d7-132">Bu öğe, hizmeti barındıran eşin uç nokta adresi ve belirli bağlama ayarları dahil olmak üzere özel bir eşdüzey çözümleyici Hizmeti için temel ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="229d7-132">This element defines the basic settings for a custom peer resolver service, including the endpoint address of the peer hosting the service and any specific binding settings.</span></span> <span data-ttu-id="229d7-133">Özel çözümleyici oluşturma hakkında daha fazla bilgi için bkz. [bir PeerChannel uygulamasına özel çözümleyici ekleme](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="229d7-133">For more information on creating a custom resolver, see [Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="229d7-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="229d7-134">See also</span></span>

- <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>
- <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>
- <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>
- <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>
- [<span data-ttu-id="229d7-135">Eş Çözücüler</span><span class="sxs-lookup"><span data-stu-id="229d7-135">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="229d7-136">[Bir PeerChannel uygulamasına özel çözümleyici ekleme](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="229d7-136">[Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span></span>
