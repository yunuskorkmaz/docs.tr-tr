---
title: <namedCaches> için <add> öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: c1345022b79df371ad9c89a39a0a8b625e26608c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154511"
---
# <a name="add-element-for-namedcaches"></a><span data-ttu-id="c1f03-102">\<adCaches \<> için> Öğesi ekleyin</span><span class="sxs-lookup"><span data-stu-id="c1f03-102">\<add> Element for \<namedCaches></span></span>
<span data-ttu-id="c1f03-103">Bellek `namedCache` önbelleği `namedCaches` için koleksiyona bir giriş ekler.</span><span class="sxs-lookup"><span data-stu-id="c1f03-103">Adds a `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
<span data-ttu-id="c1f03-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c1f03-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c1f03-105">&nbsp;&nbsp;[**\<system.runtime.önbelleğe alma>**](system-runtime-caching-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="c1f03-105">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span></span>\
<span data-ttu-id="c1f03-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryÖnbellek>**](memorycache-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="c1f03-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)</span></span>\
<span data-ttu-id="c1f03-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="c1f03-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)</span></span>\
<span data-ttu-id="c1f03-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>ekleyin**</span><span class="sxs-lookup"><span data-stu-id="c1f03-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1f03-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c1f03-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <add name="Default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="c1f03-110">Tür</span><span class="sxs-lookup"><span data-stu-id="c1f03-110">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c1f03-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c1f03-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c1f03-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c1f03-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c1f03-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c1f03-113">Attributes</span></span>  
  
|<span data-ttu-id="c1f03-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c1f03-114">Attribute</span></span>|<span data-ttu-id="c1f03-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c1f03-115">Description</span></span>|  
|-|-|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="c1f03-116">İzin verilen en büyük boyutu (megabaytlarda) belirten bir <xref:System.Runtime.Caching.MemoryCache> tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="c1f03-116">An integer value that specifies the maximum allowed size (in megabytes) that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="c1f03-117">Varsayılan değer 0'dır, bu <xref:System.Runtime.Caching.MemoryCache> da sınıfın otomatik boyutlandırma sezgiselinin varsayılan olarak kullanıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c1f03-117">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="c1f03-118">Önbelleğin adı.</span><span class="sxs-lookup"><span data-stu-id="c1f03-118">The name of the cache.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="c1f03-119">Önbellek tarafından tüketilebilen fiziksel olarak yüklenmiş bilgisayar belleğinin maksimum yüzdesini belirten 0 ile 100 arasında bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="c1f03-119">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="c1f03-120">Varsayılan değer 0'dır, bu <xref:System.Runtime.Caching.MemoryCache> da sınıfın otomatik boyutlandırma sezgiselinin varsayılan olarak kullanıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c1f03-120">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="c1f03-121">Önbellek uygulamasının geçerli bellek yükünü önbellek örneği için ayarlanan mutlak ve yüzde tabanlı bellek sınırlarıyla karşılaştırdığı zaman aralığını gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="c1f03-121">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="c1f03-122">Bu değer "HH:MM:SS" biçiminde girilir.</span><span class="sxs-lookup"><span data-stu-id="c1f03-122">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c1f03-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c1f03-123">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="c1f03-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c1f03-124">Parent Elements</span></span>  
  
|<span data-ttu-id="c1f03-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="c1f03-125">Element</span></span>|<span data-ttu-id="c1f03-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c1f03-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c1f03-127">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="c1f03-127">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="c1f03-128">Adlandırılmış <xref:System.Runtime.Caching.MemoryCache> örnekler için yapılandırma ayarları koleksiyonu içerir.</span><span class="sxs-lookup"><span data-stu-id="c1f03-128">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1f03-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c1f03-129">Remarks</span></span>  
 <span data-ttu-id="c1f03-130">Öğe, `add` bellek önbelleği için `namedCaches` koleksiyona bir giriş ekler.</span><span class="sxs-lookup"><span data-stu-id="c1f03-130">The `add` element adds an entry to the `namedCaches` collection for a memory cache.</span></span> <span data-ttu-id="c1f03-131">Koleksiyonda başka [clear](clear-element-for-namedcaches.md) adlandırılmış önbellek `add` olmadığından emin olmak için öğeyi kullanmadan önce açık öğeyi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c1f03-131">You can use the [clear](clear-element-for-namedcaches.md) element before you use the `add` element to be certain that there are no other named caches in the collection.</span></span> <span data-ttu-id="c1f03-132">Bu öğe machine.config dosyasında ve Web.config dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c1f03-132">This element can be used in the machine.config file and in the Web.config file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1f03-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="c1f03-133">Example</span></span>  
 <span data-ttu-id="c1f03-134">Aşağıdaki örnekte, bir bellek önbelleği `namedCaches` için koleksiyona varsayılan `namedCache` giriş ayarlarının nasıl tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c1f03-134">The following example shows how to define settings for the default `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c1f03-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1f03-135">See also</span></span>

- [<span data-ttu-id="c1f03-136">\<namedCaches> Öğesi (Önbellek Ayarları)</span><span class="sxs-lookup"><span data-stu-id="c1f03-136">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
