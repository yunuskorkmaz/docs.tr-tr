---
title: '&lt;ekleme&gt; öğesi için &lt;namedCaches&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 695ee744bdf2226f0647c4cdf142a2dca4e97a4a
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48033460"
---
# <a name="ltaddgt-element-for-ltnamedcachesgt"></a><span data-ttu-id="c57cd-102">&lt;ekleme&gt; öğesi için &lt;namedCaches&gt;</span><span class="sxs-lookup"><span data-stu-id="c57cd-102">&lt;add&gt; Element for &lt;namedCaches&gt;</span></span>
<span data-ttu-id="c57cd-103">Ekler bir `namedCache` girişe `namedCaches` koleksiyonu için bir önbellek.</span><span class="sxs-lookup"><span data-stu-id="c57cd-103">Adds a `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="c57cd-104">\<System.Runtime.Caching ></span><span class="sxs-lookup"><span data-stu-id="c57cd-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="c57cd-105">\<memoryCache ></span><span class="sxs-lookup"><span data-stu-id="c57cd-105">\<memoryCache></span></span>  
<span data-ttu-id="c57cd-106">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="c57cd-106">\<namedCaches></span></span>  
<span data-ttu-id="c57cd-107">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="c57cd-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c57cd-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c57cd-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <add name="default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="c57cd-109">Tür</span><span class="sxs-lookup"><span data-stu-id="c57cd-109">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c57cd-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c57cd-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c57cd-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c57cd-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c57cd-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c57cd-112">Attributes</span></span>  
  
|<span data-ttu-id="c57cd-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c57cd-113">Attribute</span></span>|<span data-ttu-id="c57cd-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c57cd-114">Description</span></span>|  
|-|-|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="c57cd-115">(Megabayt olarak) boyutu izin verilen maksimum belirten bir tamsayı değeri, örneği bir <xref:System.Runtime.Caching.MemoryCache> kadar büyüyebilir.</span><span class="sxs-lookup"><span data-stu-id="c57cd-115">An integer value that specifies the maximum allowed size (in megabytes) that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="c57cd-116">Varsayılan değerdir, yani 0 <xref:System.Runtime.Caching.MemoryCache> sınıfın otomatik boyutlandırma buluşsal yöntemler, varsayılan olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c57cd-116">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="c57cd-117">Önbellek adı.</span><span class="sxs-lookup"><span data-stu-id="c57cd-117">The name of the cache.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="c57cd-118">Önbelleği tarafından tüketilebilecek yüklü olan fiziksel bilgisayar belleğini en yüksek yüzdesi belirten bir tamsayı değeri 0 ile 100 arasında.</span><span class="sxs-lookup"><span data-stu-id="c57cd-118">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="c57cd-119">Varsayılan değerdir, yani 0 <xref:System.Runtime.Caching.MemoryCache> sınıfın otomatik boyutlandırma buluşsal yöntemler, varsayılan olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c57cd-119">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="c57cd-120">Daha sonra önbellek uygulaması geçerli bellek yükü önbellek örneği için ayarlanan mutlak ve yüzde tabanlı bellek sınırlarını karşı karşılaştırır zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="c57cd-120">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="c57cd-121">Bu değer, "Ss" biçiminde girilir.</span><span class="sxs-lookup"><span data-stu-id="c57cd-121">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c57cd-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c57cd-122">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="c57cd-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c57cd-123">Parent Elements</span></span>  
  
|<span data-ttu-id="c57cd-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="c57cd-124">Element</span></span>|<span data-ttu-id="c57cd-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c57cd-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c57cd-126">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="c57cd-126">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="c57cd-127">Yapılandırma ayarları için adlandırılmış bir koleksiyonunu içeren <xref:System.Runtime.Caching.MemoryCache> örnekleri.</span><span class="sxs-lookup"><span data-stu-id="c57cd-127">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c57cd-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c57cd-128">Remarks</span></span>  
 <span data-ttu-id="c57cd-129">`add` Öğe için bir giriş ekler `namedCaches` koleksiyonu için bir önbellek.</span><span class="sxs-lookup"><span data-stu-id="c57cd-129">The `add` element adds an entry to the `namedCaches` collection for a memory cache.</span></span> <span data-ttu-id="c57cd-130">Kullanabileceğiniz [Temizle](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md) kullanmadan önce öğesi `add` olduğunu başka hiçbir emin olmak için öğesi adlı önbellekler koleksiyondaki.</span><span class="sxs-lookup"><span data-stu-id="c57cd-130">You can use the [clear](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md) element before you use the `add` element to be certain that there are no other named caches in the collection.</span></span> <span data-ttu-id="c57cd-131">Bu öğe, machine.config dosyasında ve Web.config dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c57cd-131">This element can be used in the machine.config file and in the Web.config file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c57cd-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="c57cd-132">Example</span></span>  
 <span data-ttu-id="c57cd-133">Aşağıdaki örnek, varsayılan ayarları belirlemek gösterilmektedir `namedCache` girişe `namedCaches` koleksiyonu için bir önbellek.</span><span class="sxs-lookup"><span data-stu-id="c57cd-133">The following example shows how to define settings for the default `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
```xml  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c57cd-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c57cd-134">See Also</span></span>  
 [<span data-ttu-id="c57cd-135">\<namedCaches > öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="c57cd-135">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
