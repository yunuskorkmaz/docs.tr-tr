---
title: "&lt;kapsamları&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9f198811483edb8a7be882588c38b1f3942f8bb4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltscopesgt"></a><span data-ttu-id="70c6a-102">&lt;kapsamları&gt;</span><span class="sxs-lookup"><span data-stu-id="70c6a-102">&lt;scopes&gt;</span></span>
<span data-ttu-id="70c6a-103">Özel kapsam sorgusu sırasında hizmet uç noktaları filtrelemede kullanılan URI belirtin yapılandırma öğelerinin koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="70c6a-103">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="70c6a-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="70c6a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="70c6a-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="70c6a-105">\<behaviors></span></span>  
<span data-ttu-id="70c6a-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="70c6a-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="70c6a-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="70c6a-107">\<behavior></span></span>  
<span data-ttu-id="70c6a-108">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="70c6a-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="70c6a-109">\<kapsamları ></span><span class="sxs-lookup"><span data-stu-id="70c6a-109">\<scopes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70c6a-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="70c6a-110">Syntax</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enable="Boolean">
        <scopes>
          <add scope="URI" />
        </scopes>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="70c6a-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="70c6a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="70c6a-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="70c6a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="70c6a-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="70c6a-113">Attributes</span></span>  
 <span data-ttu-id="70c6a-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="70c6a-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="70c6a-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="70c6a-115">Child Elements</span></span>  
  
|<span data-ttu-id="70c6a-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="70c6a-116">Attribute</span></span>|<span data-ttu-id="70c6a-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="70c6a-117">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="70c6a-118">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="70c6a-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopes.md)|<span data-ttu-id="70c6a-119">Kullanılabilir uç nokta için kapsam bilgileri Hizmetleri bulma ölçütlerini eşleştirmelerinde ekler.</span><span class="sxs-lookup"><span data-stu-id="70c6a-119">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="70c6a-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="70c6a-120">Parent Elements</span></span>  
  
|<span data-ttu-id="70c6a-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="70c6a-121">Element</span></span>|<span data-ttu-id="70c6a-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="70c6a-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="70c6a-123">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="70c6a-123">\<endpointDiscovery></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointdiscovery.md)|<span data-ttu-id="70c6a-124">Kendi bulunabilirlik, kapsamları ve kendi meta verileri için özel uzantılar gibi bir uç nokta için çeşitli bulma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="70c6a-124">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="70c6a-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="70c6a-125">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
