---
title: "&lt;kaldırma&gt; öğesi için &lt;namedCaches&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 4b360b206586b263627ab6f6b7e0309f3055f38a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltremovegt-element-for-ltnamedcachesgt"></a><span data-ttu-id="13813-102">&lt;kaldırma&gt; öğesi için &lt;namedCaches&gt;</span><span class="sxs-lookup"><span data-stu-id="13813-102">&lt;remove&gt; Element for &lt;namedCaches&gt;</span></span>
<span data-ttu-id="13813-103">Bir adlandırılmış önbellek girişi kaldırır `namedCaches` bir önbellek için koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="13813-103">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="13813-104">\<System.Runtime.Caching ></span><span class="sxs-lookup"><span data-stu-id="13813-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="13813-105">\<memoryCache ></span><span class="sxs-lookup"><span data-stu-id="13813-105">\<memoryCache></span></span>  
<span data-ttu-id="13813-106">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="13813-106">\<namedCaches></span></span>  
<span data-ttu-id="13813-107">\<kaldırma ></span><span class="sxs-lookup"><span data-stu-id="13813-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13813-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="13813-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="13813-109">Tür</span><span class="sxs-lookup"><span data-stu-id="13813-109">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13813-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="13813-110">Attributes and Elements</span></span>  
 <span data-ttu-id="13813-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="13813-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13813-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="13813-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="13813-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="13813-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="13813-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="13813-114">Parent Elements</span></span>  
  
|<span data-ttu-id="13813-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="13813-115">Element</span></span>|<span data-ttu-id="13813-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="13813-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="13813-117">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="13813-117">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="13813-118">Yapılandırma ayarları adlandırılmış bir koleksiyonu içerir <xref:System.Runtime.Caching.MemoryCache> örnekleri.</span><span class="sxs-lookup"><span data-stu-id="13813-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13813-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="13813-119">Remarks</span></span>  
 <span data-ttu-id="13813-120">`remove` Öğeyi kaldırır bir `namedCache` adlandırılmış önbellek koleksiyonu için bir önbellek girişi.</span><span class="sxs-lookup"><span data-stu-id="13813-120">The `remove` element removes a `namedCache` entry from the named cache collection for a memory cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13813-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="13813-121">See Also</span></span>  
 [<span data-ttu-id="13813-122">\<namedCaches > öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="13813-122">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
