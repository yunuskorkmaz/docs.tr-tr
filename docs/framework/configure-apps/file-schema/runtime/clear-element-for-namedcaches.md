---
title: '&lt;Clear&gt; öğesi için &lt;namedCaches&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: cdd6e4a4849a031dc6bcad909509498406fcb129
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745519"
---
# <a name="ltcleargt-element-for-ltnamedcachesgt"></a><span data-ttu-id="1a3ad-102">&lt;Clear&gt; öğesi için &lt;namedCaches&gt;</span><span class="sxs-lookup"><span data-stu-id="1a3ad-102">&lt;clear&gt; Element for &lt;namedCaches&gt;</span></span>
<span data-ttu-id="1a3ad-103">Tüm temizler `namedCache` girişleri `namedCaches` bir önbellek için koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="1a3ad-103">Clears all `namedCache` entries in the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="1a3ad-104">\<System.Runtime.Caching ></span><span class="sxs-lookup"><span data-stu-id="1a3ad-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="1a3ad-105">\<memoryCache ></span><span class="sxs-lookup"><span data-stu-id="1a3ad-105">\<memoryCache></span></span>  
<span data-ttu-id="1a3ad-106">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="1a3ad-106">\<namedCaches></span></span>  
<span data-ttu-id="1a3ad-107">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="1a3ad-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a3ad-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1a3ad-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <clear name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="1a3ad-109">Tür</span><span class="sxs-lookup"><span data-stu-id="1a3ad-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1a3ad-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1a3ad-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1a3ad-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1a3ad-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1a3ad-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1a3ad-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="1a3ad-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1a3ad-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="1a3ad-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1a3ad-114">Parent Elements</span></span>  
  
|<span data-ttu-id="1a3ad-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="1a3ad-115">Element</span></span>|<span data-ttu-id="1a3ad-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1a3ad-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1a3ad-117">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="1a3ad-117">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="1a3ad-118">Yapılandırma ayarları adlandırılmış bir koleksiyonu içerir <xref:System.Runtime.Caching.MemoryCache> örnekleri.</span><span class="sxs-lookup"><span data-stu-id="1a3ad-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a3ad-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1a3ad-119">Remarks</span></span>  
 <span data-ttu-id="1a3ad-120">`clear` Öğesi temizler tüm `namedCache` adlandırılmış önbellek koleksiyonu için bir önbellek girdileri.</span><span class="sxs-lookup"><span data-stu-id="1a3ad-120">The `clear` element clears all `namedCache` entries in the named cache collection for a memory cache.</span></span> <span data-ttu-id="1a3ad-121">Kullanabileceğiniz `clear` kullanmadan önce öğesi `add` vardır başka emin olmak için yeni bir adlandırılmış önbellek girdisi eklemek için öğe koleksiyonda önbellekleri adlı.</span><span class="sxs-lookup"><span data-stu-id="1a3ad-121">You can use the `clear` element before you use the `add` element to add a new named cache entry in order to be certain there are no other named caches in the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a3ad-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1a3ad-122">See Also</span></span>  
 [<span data-ttu-id="1a3ad-123">\<namedCaches > öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="1a3ad-123">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
