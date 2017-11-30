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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6b35696cbecb0badf397d6d48e7c97aae3d0232e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltscopesgt"></a><span data-ttu-id="ca1f5-102">&lt;kapsamları&gt;</span><span class="sxs-lookup"><span data-stu-id="ca1f5-102">&lt;scopes&gt;</span></span>
<span data-ttu-id="ca1f5-103">Özel kapsam sorgusu sırasında hizmet uç noktaları filtrelemede kullanılan URI belirtin yapılandırma öğelerinin koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="ca1f5-103">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="ca1f5-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="ca1f5-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ca1f5-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="ca1f5-105">\<behaviors></span></span>  
<span data-ttu-id="ca1f5-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="ca1f5-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="ca1f5-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="ca1f5-107">\<behavior></span></span>  
<span data-ttu-id="ca1f5-108">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="ca1f5-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="ca1f5-109">\<kapsamları ></span><span class="sxs-lookup"><span data-stu-id="ca1f5-109">\<scopes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca1f5-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ca1f5-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ca1f5-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ca1f5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ca1f5-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ca1f5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ca1f5-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ca1f5-113">Attributes</span></span>  
 <span data-ttu-id="ca1f5-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="ca1f5-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ca1f5-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ca1f5-115">Child Elements</span></span>  
  
|<span data-ttu-id="ca1f5-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ca1f5-116">Attribute</span></span>|<span data-ttu-id="ca1f5-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ca1f5-117">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="ca1f5-118">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="ca1f5-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopes.md)|<span data-ttu-id="ca1f5-119">Kullanılabilir uç nokta için kapsam bilgileri Hizmetleri bulma ölçütlerini eşleştirmelerinde ekler.</span><span class="sxs-lookup"><span data-stu-id="ca1f5-119">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ca1f5-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ca1f5-120">Parent Elements</span></span>  
  
|<span data-ttu-id="ca1f5-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="ca1f5-121">Element</span></span>|<span data-ttu-id="ca1f5-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ca1f5-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ca1f5-123">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="ca1f5-123">\<endpointDiscovery></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointdiscovery.md)|<span data-ttu-id="ca1f5-124">Kendi bulunabilirlik, kapsamları ve kendi meta verileri için özel uzantılar gibi bir uç nokta için çeşitli bulma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ca1f5-124">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ca1f5-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ca1f5-125">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
