---
title: <namedCaches> için <clear> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
ms.openlocfilehash: eb0a50919e163a795abc70d132bd45f1d05192ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674174"
---
# <a name="clear-element-for-namedcaches"></a><span data-ttu-id="44f13-102">\<Temizle > öğesi için \<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="44f13-102">\<clear> Element for \<namedCaches></span></span>
<span data-ttu-id="44f13-103">Tüm temizler `namedCache` girişleri `namedCaches` koleksiyonu için bir önbellek.</span><span class="sxs-lookup"><span data-stu-id="44f13-103">Clears all `namedCache` entries in the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="44f13-104">\<System.Runtime.Caching ></span><span class="sxs-lookup"><span data-stu-id="44f13-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="44f13-105">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="44f13-105">\<memoryCache></span></span>  
<span data-ttu-id="44f13-106">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="44f13-106">\<namedCaches></span></span>  
<span data-ttu-id="44f13-107">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="44f13-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44f13-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="44f13-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <clear name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="44f13-109">Tür</span><span class="sxs-lookup"><span data-stu-id="44f13-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44f13-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="44f13-110">Attributes and Elements</span></span>  
 <span data-ttu-id="44f13-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="44f13-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44f13-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="44f13-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="44f13-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="44f13-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="44f13-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="44f13-114">Parent Elements</span></span>  
  
|<span data-ttu-id="44f13-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="44f13-115">Element</span></span>|<span data-ttu-id="44f13-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="44f13-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="44f13-117">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="44f13-117">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="44f13-118">Yapılandırma ayarları için adlandırılmış bir koleksiyonunu içeren <xref:System.Runtime.Caching.MemoryCache> örnekleri.</span><span class="sxs-lookup"><span data-stu-id="44f13-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44f13-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="44f13-119">Remarks</span></span>  
 <span data-ttu-id="44f13-120">`clear` Öğesi tümünü temizler `namedCache` girişleri adlandırılmış önbelleği koleksiyondaki bir önbellek.</span><span class="sxs-lookup"><span data-stu-id="44f13-120">The `clear` element clears all `namedCache` entries in the named cache collection for a memory cache.</span></span> <span data-ttu-id="44f13-121">Kullanabileceğiniz `clear` kullanmadan önce öğesi `add` vardır başka hiçbir emin olmak için yeni bir adlandırılmış önbellek girdisi eklemek için öğesi adlı önbellekler koleksiyondaki.</span><span class="sxs-lookup"><span data-stu-id="44f13-121">You can use the `clear` element before you use the `add` element to add a new named cache entry in order to be certain there are no other named caches in the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44f13-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44f13-122">See also</span></span>

- [<span data-ttu-id="44f13-123">\<namedCaches > öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="44f13-123">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
