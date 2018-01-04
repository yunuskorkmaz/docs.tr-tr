---
title: "&lt;Özel&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9bcab1e8361448abfe14db8ac38a924c656b9065
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcustomgt"></a><span data-ttu-id="65b92-102">&lt;Özel&gt;</span><span class="sxs-lookup"><span data-stu-id="65b92-102">&lt;custom&gt;</span></span>
<span data-ttu-id="65b92-103">Özel eş Çözümleyici hizmeti ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="65b92-103">Specifies settings for a custom peer resolver service.</span></span>  
  
<span data-ttu-id="65b92-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="65b92-104">\<system.serviceModel></span></span>  
<span data-ttu-id="65b92-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="65b92-105">\<bindings></span></span>  
<span data-ttu-id="65b92-106">\<netPeerBinding ></span><span class="sxs-lookup"><span data-stu-id="65b92-106">\<netPeerBinding></span></span>  
<span data-ttu-id="65b92-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="65b92-107">\<binding></span></span>  
<span data-ttu-id="65b92-108">\<Çözümleyici ></span><span class="sxs-lookup"><span data-stu-id="65b92-108">\<resolver></span></span>  
<span data-ttu-id="65b92-109">\<Özel ></span><span class="sxs-lookup"><span data-stu-id="65b92-109">\<custom></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65b92-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="65b92-110">Syntax</span></span>  
  
```xml
<custom address="Uri" 
        resolverType="String">  
  <headers/>  
  <identity/>  
</custom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="65b92-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="65b92-111">Attributes and Elements</span></span>  
 <span data-ttu-id="65b92-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="65b92-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="65b92-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="65b92-113">Attributes</span></span>  
  
|<span data-ttu-id="65b92-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="65b92-114">Attribute</span></span>|<span data-ttu-id="65b92-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="65b92-115">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="65b92-116">Özel eş çözümleyicisini barındıran Eş düğüm bitiş adresini belirtir URI.</span><span class="sxs-lookup"><span data-stu-id="65b92-116">A URI that specifies the endpoint address of the peer node that hosts the custom peer resolver service.</span></span>|  
|`resolverType`|<span data-ttu-id="65b92-117">Özel eş çözümleyicisini türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="65b92-117">A string that specifies the type of the custom peer resolver service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="65b92-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="65b92-118">Child Elements</span></span>  
  
|<span data-ttu-id="65b92-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="65b92-119">Element</span></span>|<span data-ttu-id="65b92-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="65b92-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="65b92-121">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="65b92-121">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="65b92-122">Bu öğeyle yapılandırılmış özel eş çözücüler kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="65b92-122">Specifies the identity for custom peer resolvers configured with this element.</span></span> <span data-ttu-id="65b92-123">Bu öğe türünde <xref:System.ServiceModel.Configuration.IdentityElement>.</span><span class="sxs-lookup"><span data-stu-id="65b92-123">This element is of type <xref:System.ServiceModel.Configuration.IdentityElement>.</span></span>|  
|[<span data-ttu-id="65b92-124">\<üstbilgiler ></span><span class="sxs-lookup"><span data-stu-id="65b92-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="65b92-125">SOAP iletilerine özel eş çözümleyici tarafından işlenen için kullanılan adres üstbilgisi koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="65b92-125">A collection of address header used for SOAP messages handled by the custom peer resolver.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="65b92-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="65b92-126">Parent Elements</span></span>  
  
|<span data-ttu-id="65b92-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="65b92-127">Element</span></span>|<span data-ttu-id="65b92-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="65b92-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="65b92-129">\<Çözümleyici ></span><span class="sxs-lookup"><span data-stu-id="65b92-129">\<resolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|<span data-ttu-id="65b92-130">Bir eş çözümlemek için kullanılan bir eş çözümleyici kafes katılmak birkaç düğüm temsil eden bir dizi Eş düğüm adresleri kimliği kafes.</span><span class="sxs-lookup"><span data-stu-id="65b92-130">A peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="65b92-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="65b92-131">Remarks</span></span>  
 <span data-ttu-id="65b92-132">Bu öğe barındırma hizmeti ve herhangi bir özel bağlama ayarı eş uç nokta adresi de dahil olmak üzere bir özel eş çözümleyici hizmetinin temel ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="65b92-132">This element defines the basic settings for a custom peer resolver service, including the endpoint address of the peer hosting the service and any specific binding settings.</span></span> <span data-ttu-id="65b92-133">Özel Çözücü oluşturma hakkında daha fazla bilgi için bkz: [PeerChannel'a uygulamaya özel Çözücü ekleme](http://msdn.microsoft.com/en-us/12aa3787-2962-439c-ad27-46523c8b0419).</span><span class="sxs-lookup"><span data-stu-id="65b92-133">For more information on creating a custom resolver, see [Adding a Custom Resolver to a PeerChannel Application](http://msdn.microsoft.com/en-us/12aa3787-2962-439c-ad27-46523c8b0419).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65b92-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="65b92-134">See Also</span></span>  
 <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>  
 <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>  
 <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>  
 <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>  
 [<span data-ttu-id="65b92-135">Eş Çözücüler</span><span class="sxs-lookup"><span data-stu-id="65b92-135">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)  
 [<span data-ttu-id="65b92-136">Özel Çözücü PeerChannel'a uygulamaya ekleme</span><span class="sxs-lookup"><span data-stu-id="65b92-136">Adding a Custom Resolver to a PeerChannel Application</span></span>](http://msdn.microsoft.com/en-us/12aa3787-2962-439c-ad27-46523c8b0419)
