---
title: <namedCaches> için <remove> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
ms.openlocfilehash: c8ad5a0ce6d7a3059943b3962b9255385cea6e15
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183994"
---
# <a name="remove-element-for-namedcaches"></a><span data-ttu-id="8e712-102">\<namedCaches> için \<remove> Öğesi</span><span class="sxs-lookup"><span data-stu-id="8e712-102">\<remove> Element for \<namedCaches></span></span>

<span data-ttu-id="8e712-103">`namedCaches`Bir bellek önbelleği için koleksiyondan adlandırılmış bir önbellek girdisini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="8e712-103">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  
  
## <a name="syntax"></a><span data-ttu-id="8e712-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="8e712-104">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="8e712-105">Tür</span><span class="sxs-lookup"><span data-stu-id="8e712-105">Type</span></span>  

 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8e712-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8e712-106">Attributes and Elements</span></span>  

 <span data-ttu-id="8e712-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8e712-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8e712-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8e712-108">Attributes</span></span>  

 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="8e712-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8e712-109">Child Elements</span></span>  

 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="8e712-110">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8e712-110">Parent Elements</span></span>  
  
|<span data-ttu-id="8e712-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="8e712-111">Element</span></span>|<span data-ttu-id="8e712-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8e712-112">Description</span></span>|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="8e712-113">Adlandırılmış örnekler için yapılandırma ayarlarının bir koleksiyonunu içerir <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="8e712-113">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e712-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8e712-114">Remarks</span></span>  

 <span data-ttu-id="8e712-115">`remove`Öğesi, `namedCache` bir bellek önbelleğinin adlandırılmış önbellek koleksiyonundan bir girişi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="8e712-115">The `remove` element removes a `namedCache` entry from the named cache collection for a memory cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e712-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e712-116">See also</span></span>

- [<span data-ttu-id="8e712-117">\<namedCaches> Öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="8e712-117">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
