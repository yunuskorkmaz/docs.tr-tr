---
title: <namedCaches> için <clear> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
ms.openlocfilehash: bcc0e23f0c47ad3a98430e36da31d39612caa3c9
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252753"
---
# <a name="clear-element-for-namedcaches"></a><span data-ttu-id="c78ad-102">\<namedönbellekler için \<> öğesini Temizle ></span><span class="sxs-lookup"><span data-stu-id="c78ad-102">\<clear> Element for \<namedCaches></span></span>
<span data-ttu-id="c78ad-103">Bir bellek `namedCache` önbelleği için `namedCaches` koleksiyondaki tüm girişleri temizler.</span><span class="sxs-lookup"><span data-stu-id="c78ad-103">Clears all `namedCache` entries in the `namedCaches` collection for a memory cache.</span></span>  
  
<span data-ttu-id="c78ad-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c78ad-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c78ad-105">&nbsp;&nbsp;[ **\<System. Runtime. Caching >** ](system-runtime-caching-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="c78ad-105">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span></span>\
<span data-ttu-id="c78ad-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<memoryCache >** ](memorycache-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="c78ad-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)</span></span>\
<span data-ttu-id="c78ad-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Namedönbellekler >** ](namedcaches-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="c78ad-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)</span></span>\
<span data-ttu-id="c78ad-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> Temizle**</span><span class="sxs-lookup"><span data-stu-id="c78ad-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c78ad-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c78ad-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <clear name="Default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="c78ad-110">Tür</span><span class="sxs-lookup"><span data-stu-id="c78ad-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c78ad-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c78ad-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c78ad-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c78ad-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c78ad-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c78ad-113">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="c78ad-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c78ad-114">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="c78ad-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c78ad-115">Parent Elements</span></span>  
  
|<span data-ttu-id="c78ad-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="c78ad-116">Element</span></span>|<span data-ttu-id="c78ad-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c78ad-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c78ad-118">\<Namedönbellekler ></span><span class="sxs-lookup"><span data-stu-id="c78ad-118">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="c78ad-119">Adlandırılmış <xref:System.Runtime.Caching.MemoryCache> örnekler için yapılandırma ayarlarının bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="c78ad-119">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c78ad-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c78ad-120">Remarks</span></span>  
 <span data-ttu-id="c78ad-121">Öğesi `clear` , bir bellek `namedCache` önbelleği için adlandırılmış önbellek koleksiyonundaki tüm girişleri temizler.</span><span class="sxs-lookup"><span data-stu-id="c78ad-121">The `clear` element clears all `namedCache` entries in the named cache collection for a memory cache.</span></span> <span data-ttu-id="c78ad-122">Koleksiyonda başka bir adlandırılmış `clear` önbellek bulunmadığından emin olmak için `add` , öğesini kullanarak yeni bir adlandırılmış önbellek girişi ekleyebilmeniz için öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c78ad-122">You can use the `clear` element before you use the `add` element to add a new named cache entry in order to be certain there are no other named caches in the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c78ad-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c78ad-123">See also</span></span>

- [<span data-ttu-id="c78ad-124">\<Namedönbellekler > öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="c78ad-124">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
