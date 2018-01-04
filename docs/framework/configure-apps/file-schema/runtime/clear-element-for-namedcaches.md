---
title: "&lt;Clear&gt; öğesi için &lt;namedCaches&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 501371346b3c1496122d93a98eb89dd4afc6bcd1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcleargt-element-for-ltnamedcachesgt"></a><span data-ttu-id="43c06-102">&lt;Clear&gt; öğesi için &lt;namedCaches&gt;</span><span class="sxs-lookup"><span data-stu-id="43c06-102">&lt;clear&gt; Element for &lt;namedCaches&gt;</span></span>
<span data-ttu-id="43c06-103">Tüm temizler `namedCache` girişleri `namedCaches` bir önbellek için koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="43c06-103">Clears all `namedCache` entries in the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="43c06-104">\<System.Runtime.Caching ></span><span class="sxs-lookup"><span data-stu-id="43c06-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="43c06-105">\<memoryCache ></span><span class="sxs-lookup"><span data-stu-id="43c06-105">\<memoryCache></span></span>  
<span data-ttu-id="43c06-106">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="43c06-106">\<namedCaches></span></span>  
<span data-ttu-id="43c06-107">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="43c06-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43c06-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="43c06-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <clear name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="43c06-109">Tür</span><span class="sxs-lookup"><span data-stu-id="43c06-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43c06-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="43c06-110">Attributes and Elements</span></span>  
 <span data-ttu-id="43c06-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="43c06-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43c06-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="43c06-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="43c06-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="43c06-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="43c06-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="43c06-114">Parent Elements</span></span>  
  
|<span data-ttu-id="43c06-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="43c06-115">Element</span></span>|<span data-ttu-id="43c06-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43c06-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="43c06-117">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="43c06-117">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="43c06-118">Yapılandırma ayarları adlandırılmış bir koleksiyonu içerir <xref:System.Runtime.Caching.MemoryCache> örnekleri.</span><span class="sxs-lookup"><span data-stu-id="43c06-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43c06-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="43c06-119">Remarks</span></span>  
 <span data-ttu-id="43c06-120">`clear` Öğesi temizler tüm `namedCache` adlandırılmış önbellek koleksiyonu için bir önbellek girdileri.</span><span class="sxs-lookup"><span data-stu-id="43c06-120">The `clear` element clears all `namedCache` entries in the named cache collection for a memory cache.</span></span> <span data-ttu-id="43c06-121">Kullanabileceğiniz `clear` kullanmadan önce öğesi `add` vardır başka emin olmak için yeni bir adlandırılmış önbellek girdisi eklemek için öğe koleksiyonda önbellekleri adlı.</span><span class="sxs-lookup"><span data-stu-id="43c06-121">You can use the `clear` element before you use the `add` element to add a new named cache entry in order to be certain there are no other named caches in the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43c06-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="43c06-122">See Also</span></span>  
 [<span data-ttu-id="43c06-123">\<namedCaches > öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="43c06-123">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
