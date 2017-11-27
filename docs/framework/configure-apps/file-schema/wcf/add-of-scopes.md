---
title: "&lt;kapsamların&gt; &lt;eklenmesi&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c720d99a5abee00eeb52f91586503e0a8a89027b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltaddgt-of-ltscopesgt"></a><span data-ttu-id="955bf-102">&lt;kapsamların&gt; &lt;eklenmesi&gt;</span><span class="sxs-lookup"><span data-stu-id="955bf-102">&lt;add&gt; of &lt;scopes&gt;</span></span>
<span data-ttu-id="955bf-103">Özel bir kapsam sorgusu sırasında hizmet uç noktaları filtrelemede kullanılan URI ekler.</span><span class="sxs-lookup"><span data-stu-id="955bf-103">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="955bf-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="955bf-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="955bf-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="955bf-105">\<behaviors></span></span>  
<span data-ttu-id="955bf-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="955bf-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="955bf-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="955bf-107">\<behavior></span></span>  
<span data-ttu-id="955bf-108">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="955bf-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="955bf-109">\<kapsamları ></span><span class="sxs-lookup"><span data-stu-id="955bf-109">\<scopes></span></span>  
<span data-ttu-id="955bf-110">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="955bf-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="955bf-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="955bf-111">Syntax</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enable="Boolean">
        <scopes>
          <add scope="URI"/>
        </scopes>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="955bf-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="955bf-112">Attributes and Elements</span></span>  
 <span data-ttu-id="955bf-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="955bf-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="955bf-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="955bf-114">Attributes</span></span>  
  
|<span data-ttu-id="955bf-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="955bf-115">Attribute</span></span>|<span data-ttu-id="955bf-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="955bf-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="955bf-117">kapsam</span><span class="sxs-lookup"><span data-stu-id="955bf-117">scope</span></span>|<span data-ttu-id="955bf-118">Hizmetleri bulmak için ölçütlerle eşleşen içinde kullanılabilir uç nokta için kapsam bilgileri içeren bir URI.</span><span class="sxs-lookup"><span data-stu-id="955bf-118">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="955bf-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="955bf-119">Child Elements</span></span>  
 <span data-ttu-id="955bf-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="955bf-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="955bf-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="955bf-121">Parent Elements</span></span>  
  
|<span data-ttu-id="955bf-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="955bf-122">Element</span></span>|<span data-ttu-id="955bf-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="955bf-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="955bf-124">\<kapsamları ></span><span class="sxs-lookup"><span data-stu-id="955bf-124">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="955bf-125">Özel kapsam sorgusu sırasında hizmet uç noktaları filtrelemede kullanılan URI belirtin yapılandırma öğelerinin koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="955bf-125">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="955bf-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="955bf-126">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
