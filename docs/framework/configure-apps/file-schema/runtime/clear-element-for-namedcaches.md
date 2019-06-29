---
title: <namedCaches> için <clear> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
ms.openlocfilehash: e563f8f27538e70ba90465fc28d300754509f7a4
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423316"
---
# <a name="clear-element-for-namedcaches"></a><span data-ttu-id="fe59e-102">\<Temizle > öğesi için \<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="fe59e-102">\<clear> Element for \<namedCaches></span></span>
<span data-ttu-id="fe59e-103">Tüm temizler `namedCache` girişleri `namedCaches` koleksiyonu için bir önbellek.</span><span class="sxs-lookup"><span data-stu-id="fe59e-103">Clears all `namedCache` entries in the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="fe59e-104">\<System.Runtime.Caching ></span><span class="sxs-lookup"><span data-stu-id="fe59e-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="fe59e-105">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="fe59e-105">\<memoryCache></span></span>  
<span data-ttu-id="fe59e-106">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="fe59e-106">\<namedCaches></span></span>  
<span data-ttu-id="fe59e-107">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="fe59e-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe59e-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fe59e-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <clear name="Default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="fe59e-109">Tür</span><span class="sxs-lookup"><span data-stu-id="fe59e-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fe59e-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fe59e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="fe59e-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fe59e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fe59e-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fe59e-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="fe59e-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fe59e-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="fe59e-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fe59e-114">Parent Elements</span></span>  
  
|<span data-ttu-id="fe59e-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="fe59e-115">Element</span></span>|<span data-ttu-id="fe59e-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe59e-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fe59e-117">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="fe59e-117">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="fe59e-118">Yapılandırma ayarları için adlandırılmış bir koleksiyonunu içeren <xref:System.Runtime.Caching.MemoryCache> örnekleri.</span><span class="sxs-lookup"><span data-stu-id="fe59e-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe59e-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fe59e-119">Remarks</span></span>  
 <span data-ttu-id="fe59e-120">`clear` Öğesi tümünü temizler `namedCache` girişleri adlandırılmış önbelleği koleksiyondaki bir önbellek.</span><span class="sxs-lookup"><span data-stu-id="fe59e-120">The `clear` element clears all `namedCache` entries in the named cache collection for a memory cache.</span></span> <span data-ttu-id="fe59e-121">Kullanabileceğiniz `clear` kullanmadan önce öğesi `add` vardır başka hiçbir emin olmak için yeni bir adlandırılmış önbellek girdisi eklemek için öğesi adlı önbellekler koleksiyondaki.</span><span class="sxs-lookup"><span data-stu-id="fe59e-121">You can use the `clear` element before you use the `add` element to add a new named cache entry in order to be certain there are no other named caches in the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe59e-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe59e-122">See also</span></span>

- [<span data-ttu-id="fe59e-123">\<namedCaches > öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="fe59e-123">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
