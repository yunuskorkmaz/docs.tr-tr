---
title: <namedCaches> için <clear> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
ms.openlocfilehash: bcc0e23f0c47ad3a98430e36da31d39612caa3c9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252753"
---
# <a name="clear-element-for-namedcaches"></a><span data-ttu-id="cd8a7-102">\<namedCaches> için \<clear> Öğesi</span><span class="sxs-lookup"><span data-stu-id="cd8a7-102">\<clear> Element for \<namedCaches></span></span>
<span data-ttu-id="cd8a7-103">`namedCache` `namedCaches` Bir bellek önbelleği için koleksiyondaki tüm girişleri temizler.</span><span class="sxs-lookup"><span data-stu-id="cd8a7-103">Clears all `namedCache` entries in the `namedCaches` collection for a memory cache.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**  
  
## <a name="syntax"></a><span data-ttu-id="cd8a7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cd8a7-104">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <clear name="Default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="cd8a7-105">Tür</span><span class="sxs-lookup"><span data-stu-id="cd8a7-105">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cd8a7-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cd8a7-106">Attributes and Elements</span></span>  
 <span data-ttu-id="cd8a7-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cd8a7-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cd8a7-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cd8a7-108">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="cd8a7-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cd8a7-109">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="cd8a7-110">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cd8a7-110">Parent Elements</span></span>  
  
|<span data-ttu-id="cd8a7-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="cd8a7-111">Element</span></span>|<span data-ttu-id="cd8a7-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cd8a7-112">Description</span></span>|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="cd8a7-113">Adlandırılmış örnekler için yapılandırma ayarlarının bir koleksiyonunu içerir <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="cd8a7-113">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd8a7-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cd8a7-114">Remarks</span></span>  
 <span data-ttu-id="cd8a7-115">`clear`Öğesi, `namedCache` bir bellek önbelleği için adlandırılmış önbellek koleksiyonundaki tüm girişleri temizler.</span><span class="sxs-lookup"><span data-stu-id="cd8a7-115">The `clear` element clears all `namedCache` entries in the named cache collection for a memory cache.</span></span> <span data-ttu-id="cd8a7-116">`clear` `add` Koleksiyonda başka bir adlandırılmış önbellek bulunmadığından emin olmak için, öğesini kullanarak yeni bir adlandırılmış önbellek girişi ekleyebilmeniz için öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cd8a7-116">You can use the `clear` element before you use the `add` element to add a new named cache entry in order to be certain there are no other named caches in the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd8a7-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd8a7-117">See also</span></span>

- [<span data-ttu-id="cd8a7-118">\<namedCaches>Öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="cd8a7-118">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
