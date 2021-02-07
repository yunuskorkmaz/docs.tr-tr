---
description: 'İçin: öğesi hakkında daha fazla bilgi <clear><namedCaches>'
title: <namedCaches> için <clear> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
ms.openlocfilehash: 9d883c102fc76875ce155f353920f730bf9700c4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719103"
---
# <a name="clear-element-for-namedcaches"></a><span data-ttu-id="8fcca-103">\<namedCaches> için \<clear> Öğesi</span><span class="sxs-lookup"><span data-stu-id="8fcca-103">\<clear> Element for \<namedCaches></span></span>

<span data-ttu-id="8fcca-104">`namedCache` `namedCaches` Bir bellek önbelleği için koleksiyondaki tüm girişleri temizler.</span><span class="sxs-lookup"><span data-stu-id="8fcca-104">Clears all `namedCache` entries in the `namedCaches` collection for a memory cache.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**  
  
## <a name="syntax"></a><span data-ttu-id="8fcca-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="8fcca-105">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <clear name="Default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="8fcca-106">Tür</span><span class="sxs-lookup"><span data-stu-id="8fcca-106">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8fcca-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8fcca-107">Attributes and Elements</span></span>  

 <span data-ttu-id="8fcca-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8fcca-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8fcca-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8fcca-109">Attributes</span></span>  

 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="8fcca-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8fcca-110">Child Elements</span></span>  

 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="8fcca-111">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8fcca-111">Parent Elements</span></span>  
  
|<span data-ttu-id="8fcca-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="8fcca-112">Element</span></span>|<span data-ttu-id="8fcca-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8fcca-113">Description</span></span>|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="8fcca-114">Adlandırılmış örnekler için yapılandırma ayarlarının bir koleksiyonunu içerir <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="8fcca-114">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8fcca-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8fcca-115">Remarks</span></span>  

 <span data-ttu-id="8fcca-116">`clear`Öğesi, `namedCache` bir bellek önbelleği için adlandırılmış önbellek koleksiyonundaki tüm girişleri temizler.</span><span class="sxs-lookup"><span data-stu-id="8fcca-116">The `clear` element clears all `namedCache` entries in the named cache collection for a memory cache.</span></span> <span data-ttu-id="8fcca-117">`clear` `add` Koleksiyonda başka bir adlandırılmış önbellek bulunmadığından emin olmak için, öğesini kullanarak yeni bir adlandırılmış önbellek girişi ekleyebilmeniz için öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8fcca-117">You can use the `clear` element before you use the `add` element to add a new named cache entry in order to be certain there are no other named caches in the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fcca-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8fcca-118">See also</span></span>

- [<span data-ttu-id="8fcca-119">\<namedCaches> Öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="8fcca-119">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
