---
title: <namedCaches> için <remove> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
ms.openlocfilehash: 991ad0eb9c04c27ded4d566115107ac7b47a71e1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252346"
---
# <a name="remove-element-for-namedcaches"></a><span data-ttu-id="ca9f5-102">\<namedCaches> için \<remove> Öğesi</span><span class="sxs-lookup"><span data-stu-id="ca9f5-102">\<remove> Element for \<namedCaches></span></span>
<span data-ttu-id="ca9f5-103">`namedCaches`Bir bellek önbelleği için koleksiyondan adlandırılmış bir önbellek girdisini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ca9f5-103">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  
  
## <a name="syntax"></a><span data-ttu-id="ca9f5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ca9f5-104">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="ca9f5-105">Tür</span><span class="sxs-lookup"><span data-stu-id="ca9f5-105">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ca9f5-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ca9f5-106">Attributes and Elements</span></span>  
 <span data-ttu-id="ca9f5-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ca9f5-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ca9f5-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ca9f5-108">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="ca9f5-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ca9f5-109">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="ca9f5-110">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ca9f5-110">Parent Elements</span></span>  
  
|<span data-ttu-id="ca9f5-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="ca9f5-111">Element</span></span>|<span data-ttu-id="ca9f5-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ca9f5-112">Description</span></span>|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="ca9f5-113">Adlandırılmış örnekler için yapılandırma ayarlarının bir koleksiyonunu içerir <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="ca9f5-113">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca9f5-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ca9f5-114">Remarks</span></span>  
 <span data-ttu-id="ca9f5-115">`remove`Öğesi, `namedCache` bir bellek önbelleğinin adlandırılmış önbellek koleksiyonundan bir girişi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ca9f5-115">The `remove` element removes a `namedCache` entry from the named cache collection for a memory cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca9f5-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca9f5-116">See also</span></span>

- [<span data-ttu-id="ca9f5-117">\<namedCaches>Öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="ca9f5-117">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
