---
title: '&lt;Temizle&gt; öğesi için &lt;namedCaches&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
ms.openlocfilehash: d71c5de42104961bc096b786dfe50bb4097bc4fc
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083567"
---
# <a name="ltcleargt-element-for-ltnamedcachesgt"></a><span data-ttu-id="25cf2-102">&lt;Temizle&gt; öğesi için &lt;namedCaches&gt;</span><span class="sxs-lookup"><span data-stu-id="25cf2-102">&lt;clear&gt; Element for &lt;namedCaches&gt;</span></span>
<span data-ttu-id="25cf2-103">Tüm temizler `namedCache` girişleri `namedCaches` koleksiyonu için bir önbellek.</span><span class="sxs-lookup"><span data-stu-id="25cf2-103">Clears all `namedCache` entries in the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="25cf2-104">\<System.Runtime.Caching ></span><span class="sxs-lookup"><span data-stu-id="25cf2-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="25cf2-105">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="25cf2-105">\<memoryCache></span></span>  
<span data-ttu-id="25cf2-106">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="25cf2-106">\<namedCaches></span></span>  
<span data-ttu-id="25cf2-107">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="25cf2-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25cf2-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="25cf2-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <clear name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="25cf2-109">Tür</span><span class="sxs-lookup"><span data-stu-id="25cf2-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="25cf2-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="25cf2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="25cf2-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="25cf2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="25cf2-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="25cf2-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="25cf2-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="25cf2-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="25cf2-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="25cf2-114">Parent Elements</span></span>  
  
|<span data-ttu-id="25cf2-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="25cf2-115">Element</span></span>|<span data-ttu-id="25cf2-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="25cf2-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="25cf2-117">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="25cf2-117">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="25cf2-118">Yapılandırma ayarları için adlandırılmış bir koleksiyonunu içeren <xref:System.Runtime.Caching.MemoryCache> örnekleri.</span><span class="sxs-lookup"><span data-stu-id="25cf2-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25cf2-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="25cf2-119">Remarks</span></span>  
 <span data-ttu-id="25cf2-120">`clear` Öğesi tümünü temizler `namedCache` girişleri adlandırılmış önbelleği koleksiyondaki bir önbellek.</span><span class="sxs-lookup"><span data-stu-id="25cf2-120">The `clear` element clears all `namedCache` entries in the named cache collection for a memory cache.</span></span> <span data-ttu-id="25cf2-121">Kullanabileceğiniz `clear` kullanmadan önce öğesi `add` vardır başka hiçbir emin olmak için yeni bir adlandırılmış önbellek girdisi eklemek için öğesi adlı önbellekler koleksiyondaki.</span><span class="sxs-lookup"><span data-stu-id="25cf2-121">You can use the `clear` element before you use the `add` element to add a new named cache entry in order to be certain there are no other named caches in the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25cf2-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25cf2-122">See also</span></span>
- [<span data-ttu-id="25cf2-123">\<namedCaches > öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="25cf2-123">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
