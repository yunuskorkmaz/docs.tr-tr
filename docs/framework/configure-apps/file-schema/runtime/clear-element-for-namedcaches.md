---
title: <namedCaches> için <clear> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
ms.openlocfilehash: d65712f091c5fb9212167b4759c70db7e5d744c1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149419"
---
# <a name="clear-element-for-namedcaches"></a><span data-ttu-id="ec823-102">\<namedCaches> için \<clear> Öğesi</span><span class="sxs-lookup"><span data-stu-id="ec823-102">\<clear> Element for \<namedCaches></span></span>

<span data-ttu-id="ec823-103">`namedCache` `namedCaches` Bir bellek önbelleği için koleksiyondaki tüm girişleri temizler.</span><span class="sxs-lookup"><span data-stu-id="ec823-103">Clears all `namedCache` entries in the `namedCaches` collection for a memory cache.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**  
  
## <a name="syntax"></a><span data-ttu-id="ec823-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="ec823-104">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <clear name="Default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="ec823-105">Tür</span><span class="sxs-lookup"><span data-stu-id="ec823-105">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ec823-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ec823-106">Attributes and Elements</span></span>  

 <span data-ttu-id="ec823-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ec823-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ec823-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ec823-108">Attributes</span></span>  

 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="ec823-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ec823-109">Child Elements</span></span>  

 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="ec823-110">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ec823-110">Parent Elements</span></span>  
  
|<span data-ttu-id="ec823-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="ec823-111">Element</span></span>|<span data-ttu-id="ec823-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ec823-112">Description</span></span>|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="ec823-113">Adlandırılmış örnekler için yapılandırma ayarlarının bir koleksiyonunu içerir <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="ec823-113">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec823-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ec823-114">Remarks</span></span>  

 <span data-ttu-id="ec823-115">`clear`Öğesi, `namedCache` bir bellek önbelleği için adlandırılmış önbellek koleksiyonundaki tüm girişleri temizler.</span><span class="sxs-lookup"><span data-stu-id="ec823-115">The `clear` element clears all `namedCache` entries in the named cache collection for a memory cache.</span></span> <span data-ttu-id="ec823-116">`clear` `add` Koleksiyonda başka bir adlandırılmış önbellek bulunmadığından emin olmak için, öğesini kullanarak yeni bir adlandırılmış önbellek girişi ekleyebilmeniz için öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec823-116">You can use the `clear` element before you use the `add` element to add a new named cache entry in order to be certain there are no other named caches in the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec823-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec823-117">See also</span></span>

- [<span data-ttu-id="ec823-118">\<namedCaches> Öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="ec823-118">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
