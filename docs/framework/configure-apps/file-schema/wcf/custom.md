---
title: <custom>
ms.date: 03/30/2017
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
ms.openlocfilehash: 4077aacab1c1c4594db76cc6663bfc0245d345d7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555503"
---
# \<custom>
<span data-ttu-id="059ff-101">Özel bir eş çözümleyici hizmetinin ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="059ff-101">Specifies settings for a custom peer resolver service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<resolver>**](resolver.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<custom>**  
  
## <a name="syntax"></a><span data-ttu-id="059ff-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="059ff-102">Syntax</span></span>  
  
```xml  
<custom address="Uri"
        resolverType="String">
  <headers/>
  <identity/>
</custom>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="059ff-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="059ff-103">Attributes and Elements</span></span>  
 <span data-ttu-id="059ff-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="059ff-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="059ff-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="059ff-105">Attributes</span></span>  
  
|<span data-ttu-id="059ff-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="059ff-106">Attribute</span></span>|<span data-ttu-id="059ff-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="059ff-107">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="059ff-108">Özel eş çözümleyici hizmetini barındıran eş düğümün uç nokta adresini belirten bir URI.</span><span class="sxs-lookup"><span data-stu-id="059ff-108">A URI that specifies the endpoint address of the peer node that hosts the custom peer resolver service.</span></span>|  
|`resolverType`|<span data-ttu-id="059ff-109">Özel eş çözücü hizmetinin türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="059ff-109">A string that specifies the type of the custom peer resolver service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="059ff-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="059ff-110">Child Elements</span></span>  
  
|<span data-ttu-id="059ff-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="059ff-111">Element</span></span>|<span data-ttu-id="059ff-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="059ff-112">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="059ff-113">Bu öğeyle yapılandırılan özel eş çözümleyiciler için kimliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="059ff-113">Specifies the identity for custom peer resolvers configured with this element.</span></span> <span data-ttu-id="059ff-114">Bu öğe türündedir <xref:System.ServiceModel.Configuration.IdentityElement> .</span><span class="sxs-lookup"><span data-stu-id="059ff-114">This element is of type <xref:System.ServiceModel.Configuration.IdentityElement>.</span></span>|  
|[\<headers>](headers-element.md)|<span data-ttu-id="059ff-115">Özel eş çözümleyici tarafından işlenen SOAP iletileri için kullanılan adres üst bilgisi koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="059ff-115">A collection of address header used for SOAP messages handled by the custom peer resolver.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="059ff-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="059ff-116">Parent Elements</span></span>  
  
|<span data-ttu-id="059ff-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="059ff-117">Element</span></span>|<span data-ttu-id="059ff-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="059ff-118">Description</span></span>|  
|-------------|-----------------|  
|[\<resolver>](resolver.md)|<span data-ttu-id="059ff-119">Eş ağ KIMLIĞINI, kafeslere katılan çeşitli düğümleri temsil eden bir eş düğüm adresleri kümesine çözümlemek için kullanılan bir eş çözümleyici.</span><span class="sxs-lookup"><span data-stu-id="059ff-119">A peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="059ff-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="059ff-120">Remarks</span></span>  
 <span data-ttu-id="059ff-121">Bu öğe, hizmeti barındıran eşin uç nokta adresi ve belirli bağlama ayarları dahil olmak üzere özel bir eşdüzey çözümleyici Hizmeti için temel ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="059ff-121">This element defines the basic settings for a custom peer resolver service, including the endpoint address of the peer hosting the service and any specific binding settings.</span></span> <span data-ttu-id="059ff-122">Özel çözümleyici oluşturma hakkında daha fazla bilgi için bkz. [bir PeerChannel uygulamasına özel çözümleyici ekleme](/previous-versions/ms730105(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="059ff-122">For more information on creating a custom resolver, see [Adding a Custom Resolver to a PeerChannel Application](/previous-versions/ms730105(v=vs.90)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="059ff-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="059ff-123">See also</span></span>

- <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>
- <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>
- <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>
- <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>
- [<span data-ttu-id="059ff-124">Eş Çözücüler</span><span class="sxs-lookup"><span data-stu-id="059ff-124">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="059ff-125">[Bir PeerChannel uygulamasına özel çözümleyici ekleme](/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="059ff-125">[Adding a Custom Resolver to a PeerChannel Application](/previous-versions/ms730105(v=vs.90))</span></span>
