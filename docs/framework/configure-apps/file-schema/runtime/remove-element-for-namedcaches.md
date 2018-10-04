---
title: '&lt;kaldırma&gt; öğesi için &lt;namedCaches&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
author: mcleblanc
ms.author: markl
ms.openlocfilehash: f885416629ae58949cc688f4e6fbd41e77e872aa
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48781680"
---
# <a name="ltremovegt-element-for-ltnamedcachesgt"></a><span data-ttu-id="0c1e7-102">&lt;kaldırma&gt; öğesi için &lt;namedCaches&gt;</span><span class="sxs-lookup"><span data-stu-id="0c1e7-102">&lt;remove&gt; Element for &lt;namedCaches&gt;</span></span>
<span data-ttu-id="0c1e7-103">Bir adlandırılmış önbellek girişi kaldırır `namedCaches` koleksiyonu için bir önbellek.</span><span class="sxs-lookup"><span data-stu-id="0c1e7-103">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="0c1e7-104">\<System.Runtime.Caching ></span><span class="sxs-lookup"><span data-stu-id="0c1e7-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="0c1e7-105">\<memoryCache ></span><span class="sxs-lookup"><span data-stu-id="0c1e7-105">\<memoryCache></span></span>  
<span data-ttu-id="0c1e7-106">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="0c1e7-106">\<namedCaches></span></span>  
<span data-ttu-id="0c1e7-107">\<kaldırma ></span><span class="sxs-lookup"><span data-stu-id="0c1e7-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c1e7-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0c1e7-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="0c1e7-109">Tür</span><span class="sxs-lookup"><span data-stu-id="0c1e7-109">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c1e7-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0c1e7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0c1e7-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0c1e7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c1e7-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0c1e7-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="0c1e7-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0c1e7-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="0c1e7-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0c1e7-114">Parent Elements</span></span>  
  
|<span data-ttu-id="0c1e7-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="0c1e7-115">Element</span></span>|<span data-ttu-id="0c1e7-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0c1e7-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0c1e7-117">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="0c1e7-117">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="0c1e7-118">Yapılandırma ayarları için adlandırılmış bir koleksiyonunu içeren <xref:System.Runtime.Caching.MemoryCache> örnekleri.</span><span class="sxs-lookup"><span data-stu-id="0c1e7-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c1e7-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0c1e7-119">Remarks</span></span>  
 <span data-ttu-id="0c1e7-120">`remove` Öğeyi kaldırır bir `namedCache` adlandırılmış önbelleği koleksiyon için bir önbellek girişi.</span><span class="sxs-lookup"><span data-stu-id="0c1e7-120">The `remove` element removes a `namedCache` entry from the named cache collection for a memory cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c1e7-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0c1e7-121">See Also</span></span>  
 [<span data-ttu-id="0c1e7-122">\<namedCaches > öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="0c1e7-122">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
