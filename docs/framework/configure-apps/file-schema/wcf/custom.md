---
description: 'Hakkında daha fazla bilgi edinin: <custom>'
title: <custom>
ms.date: 03/30/2017
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
ms.openlocfilehash: 327a5d7ff1bab88a1633d7a10095e708e6b1a533
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725915"
---
# \<custom>

<span data-ttu-id="933fe-102">Özel bir eş çözümleyici hizmetinin ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="933fe-102">Specifies settings for a custom peer resolver service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<resolver>**](resolver.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<custom>**  
  
## <a name="syntax"></a><span data-ttu-id="933fe-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="933fe-103">Syntax</span></span>  
  
```xml  
<custom address="Uri"
        resolverType="String">
  <headers/>
  <identity/>
</custom>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="933fe-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="933fe-104">Attributes and Elements</span></span>  

 <span data-ttu-id="933fe-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="933fe-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="933fe-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="933fe-106">Attributes</span></span>  
  
|<span data-ttu-id="933fe-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="933fe-107">Attribute</span></span>|<span data-ttu-id="933fe-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="933fe-108">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="933fe-109">Özel eş çözümleyici hizmetini barındıran eş düğümün uç nokta adresini belirten bir URI.</span><span class="sxs-lookup"><span data-stu-id="933fe-109">A URI that specifies the endpoint address of the peer node that hosts the custom peer resolver service.</span></span>|  
|`resolverType`|<span data-ttu-id="933fe-110">Özel eş çözücü hizmetinin türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="933fe-110">A string that specifies the type of the custom peer resolver service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="933fe-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="933fe-111">Child Elements</span></span>  
  
|<span data-ttu-id="933fe-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="933fe-112">Element</span></span>|<span data-ttu-id="933fe-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="933fe-113">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="933fe-114">Bu öğeyle yapılandırılan özel eş çözümleyiciler için kimliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="933fe-114">Specifies the identity for custom peer resolvers configured with this element.</span></span> <span data-ttu-id="933fe-115">Bu öğe türündedir <xref:System.ServiceModel.Configuration.IdentityElement> .</span><span class="sxs-lookup"><span data-stu-id="933fe-115">This element is of type <xref:System.ServiceModel.Configuration.IdentityElement>.</span></span>|  
|[\<headers>](headers-element.md)|<span data-ttu-id="933fe-116">Özel eş çözümleyici tarafından işlenen SOAP iletileri için kullanılan adres üst bilgisi koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="933fe-116">A collection of address header used for SOAP messages handled by the custom peer resolver.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="933fe-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="933fe-117">Parent Elements</span></span>  
  
|<span data-ttu-id="933fe-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="933fe-118">Element</span></span>|<span data-ttu-id="933fe-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="933fe-119">Description</span></span>|  
|-------------|-----------------|  
|[\<resolver>](resolver.md)|<span data-ttu-id="933fe-120">Eş ağ KIMLIĞINI, kafeslere katılan çeşitli düğümleri temsil eden bir eş düğüm adresleri kümesine çözümlemek için kullanılan bir eş çözümleyici.</span><span class="sxs-lookup"><span data-stu-id="933fe-120">A peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="933fe-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="933fe-121">Remarks</span></span>  

 <span data-ttu-id="933fe-122">Bu öğe, hizmeti barındıran eşin uç nokta adresi ve belirli bağlama ayarları dahil olmak üzere özel bir eşdüzey çözümleyici Hizmeti için temel ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="933fe-122">This element defines the basic settings for a custom peer resolver service, including the endpoint address of the peer hosting the service and any specific binding settings.</span></span> <span data-ttu-id="933fe-123">Özel çözümleyici oluşturma hakkında daha fazla bilgi için bkz. [bir PeerChannel uygulamasına özel çözümleyici ekleme](/previous-versions/ms730105(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="933fe-123">For more information on creating a custom resolver, see [Adding a Custom Resolver to a PeerChannel Application](/previous-versions/ms730105(v=vs.90)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="933fe-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="933fe-124">See also</span></span>

- <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>
- <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>
- <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>
- <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>
- [<span data-ttu-id="933fe-125">Eş Çözücüler</span><span class="sxs-lookup"><span data-stu-id="933fe-125">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="933fe-126">[Bir PeerChannel uygulamasına özel çözümleyici ekleme](/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="933fe-126">[Adding a Custom Resolver to a PeerChannel Application](/previous-versions/ms730105(v=vs.90))</span></span>
