---
title: <namedCaches> için <clear> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
ms.openlocfilehash: a90970e468359714bbbb858f3f300c26b5757a4d
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658856"
---
# <a name="clear-element-for-namedcaches"></a><span data-ttu-id="8a50f-102">\<namedönbellekler için \<> öğesini Temizle ></span><span class="sxs-lookup"><span data-stu-id="8a50f-102">\<clear> Element for \<namedCaches></span></span>
<span data-ttu-id="8a50f-103">Bir bellek `namedCache` önbelleği için `namedCaches` koleksiyondaki tüm girişleri temizler.</span><span class="sxs-lookup"><span data-stu-id="8a50f-103">Clears all `namedCache` entries in the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="8a50f-104">\<System. Runtime. Caching ></span><span class="sxs-lookup"><span data-stu-id="8a50f-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="8a50f-105">\<memoryCache ></span><span class="sxs-lookup"><span data-stu-id="8a50f-105">\<memoryCache></span></span>  
<span data-ttu-id="8a50f-106">\<Namedönbellekler ></span><span class="sxs-lookup"><span data-stu-id="8a50f-106">\<namedCaches></span></span>  
<span data-ttu-id="8a50f-107">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="8a50f-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a50f-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8a50f-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <clear name="Default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="8a50f-109">Tür</span><span class="sxs-lookup"><span data-stu-id="8a50f-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8a50f-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8a50f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8a50f-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8a50f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8a50f-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8a50f-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="8a50f-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8a50f-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="8a50f-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8a50f-114">Parent Elements</span></span>  
  
|<span data-ttu-id="8a50f-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="8a50f-115">Element</span></span>|<span data-ttu-id="8a50f-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8a50f-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8a50f-117">\<Namedönbellekler ></span><span class="sxs-lookup"><span data-stu-id="8a50f-117">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="8a50f-118">Adlandırılmış <xref:System.Runtime.Caching.MemoryCache> örnekler için yapılandırma ayarlarının bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="8a50f-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a50f-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8a50f-119">Remarks</span></span>  
 <span data-ttu-id="8a50f-120">Öğesi `clear` , bir bellek `namedCache` önbelleği için adlandırılmış önbellek koleksiyonundaki tüm girişleri temizler.</span><span class="sxs-lookup"><span data-stu-id="8a50f-120">The `clear` element clears all `namedCache` entries in the named cache collection for a memory cache.</span></span> <span data-ttu-id="8a50f-121">Koleksiyonda başka bir adlandırılmış `clear` önbellek bulunmadığından emin olmak için `add` , öğesini kullanarak yeni bir adlandırılmış önbellek girişi ekleyebilmeniz için öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a50f-121">You can use the `clear` element before you use the `add` element to add a new named cache entry in order to be certain there are no other named caches in the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a50f-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a50f-122">See also</span></span>

- [<span data-ttu-id="8a50f-123">\<Namedönbellekler > öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="8a50f-123">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
