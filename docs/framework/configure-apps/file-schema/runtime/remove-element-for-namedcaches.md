---
description: 'İçin: öğesi hakkında daha fazla bilgi <remove><namedCaches>'
title: <namedCaches> için <remove> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
ms.openlocfilehash: 5b39fc596735d746c52cdb5623962f5b9952fa3e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802469"
---
# <a name="remove-element-for-namedcaches"></a><span data-ttu-id="a4fb0-103">\<namedCaches> için \<remove> Öğesi</span><span class="sxs-lookup"><span data-stu-id="a4fb0-103">\<remove> Element for \<namedCaches></span></span>

<span data-ttu-id="a4fb0-104">`namedCaches`Bir bellek önbelleği için koleksiyondan adlandırılmış bir önbellek girdisini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="a4fb0-104">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  
  
## <a name="syntax"></a><span data-ttu-id="a4fb0-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a4fb0-105">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="a4fb0-106">Tür</span><span class="sxs-lookup"><span data-stu-id="a4fb0-106">Type</span></span>  

 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a4fb0-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a4fb0-107">Attributes and Elements</span></span>  

 <span data-ttu-id="a4fb0-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a4fb0-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a4fb0-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a4fb0-109">Attributes</span></span>  

 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="a4fb0-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a4fb0-110">Child Elements</span></span>  

 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="a4fb0-111">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a4fb0-111">Parent Elements</span></span>  
  
|<span data-ttu-id="a4fb0-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="a4fb0-112">Element</span></span>|<span data-ttu-id="a4fb0-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4fb0-113">Description</span></span>|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="a4fb0-114">Adlandırılmış örnekler için yapılandırma ayarlarının bir koleksiyonunu içerir <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="a4fb0-114">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4fb0-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a4fb0-115">Remarks</span></span>  

 <span data-ttu-id="a4fb0-116">`remove`Öğesi, `namedCache` bir bellek önbelleğinin adlandırılmış önbellek koleksiyonundan bir girişi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="a4fb0-116">The `remove` element removes a `namedCache` entry from the named cache collection for a memory cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4fb0-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4fb0-117">See also</span></span>

- [<span data-ttu-id="a4fb0-118">\<namedCaches> Öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="a4fb0-118">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
