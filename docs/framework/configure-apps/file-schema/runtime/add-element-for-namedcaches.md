---
description: 'İçin: öğesi hakkında daha fazla bilgi <add><namedCaches>'
title: <namedCaches> için <add> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: 1485b80fa84268f68759bfb50744133744142d72
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802437"
---
# <a name="add-element-for-namedcaches"></a><span data-ttu-id="bc5cc-103">\<namedCaches> için \<add> Öğesi</span><span class="sxs-lookup"><span data-stu-id="bc5cc-103">\<add> Element for \<namedCaches></span></span>

<span data-ttu-id="bc5cc-104">`namedCache` `namedCaches` Bir bellek önbelleği için koleksiyona bir giriş ekler.</span><span class="sxs-lookup"><span data-stu-id="bc5cc-104">Adds a `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="bc5cc-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="bc5cc-105">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <add name="Default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="bc5cc-106">Tür</span><span class="sxs-lookup"><span data-stu-id="bc5cc-106">Type</span></span>  

 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bc5cc-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bc5cc-107">Attributes and Elements</span></span>  

 <span data-ttu-id="bc5cc-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bc5cc-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bc5cc-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bc5cc-109">Attributes</span></span>  
  
|<span data-ttu-id="bc5cc-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="bc5cc-110">Attribute</span></span>|<span data-ttu-id="bc5cc-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bc5cc-111">Description</span></span>|  
|-|-|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="bc5cc-112">Bir örneğinin bir örneğinin büyüyebileceği en fazla izin verilen boyutu (megabayt cinsinden) belirten bir tamsayı değeri <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="bc5cc-112">An integer value that specifies the maximum allowed size (in megabytes) that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="bc5cc-113">Varsayılan değer 0 ' dır. Bu, <xref:System.Runtime.Caching.MemoryCache> sınıfın otomatik boyutlandırma buluşsal yöntemleri varsayılan olarak kullanıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="bc5cc-113">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="bc5cc-114">Önbelleğin adı.</span><span class="sxs-lookup"><span data-stu-id="bc5cc-114">The name of the cache.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="bc5cc-115">0 ile 100 arasında, önbellek tarafından tüketilen fiziksel olarak yüklenen bilgisayar belleğinin maksimum yüzdesini belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="bc5cc-115">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="bc5cc-116">Varsayılan değer 0 ' dır. Bu, <xref:System.Runtime.Caching.MemoryCache> sınıfın otomatik boyutlandırma buluşsal yöntemleri varsayılan olarak kullanıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="bc5cc-116">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="bc5cc-117">Önbellek uygulamasının geçerli bellek yükünü, önbellek örneği için ayarlanan mutlak ve yüzde tabanlı bellek sınırlarına göre karşılaştıran zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="bc5cc-117">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="bc5cc-118">Bu değer "HH: MM: SS" biçiminde girilir.</span><span class="sxs-lookup"><span data-stu-id="bc5cc-118">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bc5cc-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bc5cc-119">Child Elements</span></span>  

 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="bc5cc-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bc5cc-120">Parent Elements</span></span>  
  
|<span data-ttu-id="bc5cc-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="bc5cc-121">Element</span></span>|<span data-ttu-id="bc5cc-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bc5cc-122">Description</span></span>|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="bc5cc-123">Adlandırılmış örnekler için yapılandırma ayarlarının bir koleksiyonunu içerir <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="bc5cc-123">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc5cc-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bc5cc-124">Remarks</span></span>  

 <span data-ttu-id="bc5cc-125">`add`Öğesi, `namedCaches` bir bellek önbelleği için koleksiyona bir giriş ekler.</span><span class="sxs-lookup"><span data-stu-id="bc5cc-125">The `add` element adds an entry to the `namedCaches` collection for a memory cache.</span></span> <span data-ttu-id="bc5cc-126">[](clear-element-for-namedcaches.md) `add` Koleksiyonda başka bir adlandırılmış önbellek bulunmadığından emin olmak için öğesini kullanmadan önce Clear öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc5cc-126">You can use the [clear](clear-element-for-namedcaches.md) element before you use the `add` element to be certain that there are no other named caches in the collection.</span></span> <span data-ttu-id="bc5cc-127">Bu öğe machine.config dosyasında ve Web.config dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bc5cc-127">This element can be used in the machine.config file and in the Web.config file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc5cc-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="bc5cc-128">Example</span></span>  

 <span data-ttu-id="bc5cc-129">Aşağıdaki örnek, `namedCache` `namedCaches` bir bellek önbelleğinin koleksiyonuna varsayılan giriş için ayarların nasıl tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bc5cc-129">The following example shows how to define settings for the default `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
```xml  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="Default"
               cacheMemoryLimitMegabytes="0"
               physicalMemoryPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bc5cc-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc5cc-130">See also</span></span>

- [<span data-ttu-id="bc5cc-131">\<namedCaches> Öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="bc5cc-131">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
