---
title: <namedCaches> için <remove> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
ms.openlocfilehash: 991ad0eb9c04c27ded4d566115107ac7b47a71e1
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252346"
---
# <a name="remove-element-for-namedcaches"></a><span data-ttu-id="bfc87-102">\<namedönbellekler için \<> öğesini kaldırın ></span><span class="sxs-lookup"><span data-stu-id="bfc87-102">\<remove> Element for \<namedCaches></span></span>
<span data-ttu-id="bfc87-103">Bir bellek önbelleği için `namedCaches` koleksiyondan adlandırılmış bir önbellek girdisini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="bfc87-103">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>  
  
<span data-ttu-id="bfc87-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bfc87-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bfc87-105">&nbsp;&nbsp;[ **\<System. Runtime. Caching >** ](system-runtime-caching-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="bfc87-105">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span></span>\
<span data-ttu-id="bfc87-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<memoryCache >** ](memorycache-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="bfc87-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)</span></span>\
<span data-ttu-id="bfc87-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Namedönbellekler >** ](namedcaches-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="bfc87-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)</span></span>\
<span data-ttu-id="bfc87-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> Kaldır**</span><span class="sxs-lookup"><span data-stu-id="bfc87-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfc87-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bfc87-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="bfc87-110">Tür</span><span class="sxs-lookup"><span data-stu-id="bfc87-110">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bfc87-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bfc87-111">Attributes and Elements</span></span>  
 <span data-ttu-id="bfc87-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bfc87-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bfc87-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bfc87-113">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="bfc87-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bfc87-114">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="bfc87-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bfc87-115">Parent Elements</span></span>  
  
|<span data-ttu-id="bfc87-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="bfc87-116">Element</span></span>|<span data-ttu-id="bfc87-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bfc87-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bfc87-118">\<Namedönbellekler ></span><span class="sxs-lookup"><span data-stu-id="bfc87-118">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="bfc87-119">Adlandırılmış <xref:System.Runtime.Caching.MemoryCache> örnekler için yapılandırma ayarlarının bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="bfc87-119">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bfc87-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bfc87-120">Remarks</span></span>  
 <span data-ttu-id="bfc87-121">Öğesi `remove` , bir bellek `namedCache` önbelleğinin adlandırılmış önbellek koleksiyonundan bir girişi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="bfc87-121">The `remove` element removes a `namedCache` entry from the named cache collection for a memory cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfc87-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bfc87-122">See also</span></span>

- [<span data-ttu-id="bfc87-123">\<Namedönbellekler > öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="bfc87-123">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
