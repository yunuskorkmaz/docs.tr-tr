---
title: '&lt;ekleme&gt; öğesi için &lt;namedCaches&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d65dfd9a1560f2657f48b327277b64ab77014b47
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743829"
---
# <a name="ltaddgt-element-for-ltnamedcachesgt"></a><span data-ttu-id="afe30-102">&lt;ekleme&gt; öğesi için &lt;namedCaches&gt;</span><span class="sxs-lookup"><span data-stu-id="afe30-102">&lt;add&gt; Element for &lt;namedCaches&gt;</span></span>
<span data-ttu-id="afe30-103">Ekler bir `namedCache` girişe `namedCaches` bir önbellek için koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="afe30-103">Adds a `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="afe30-104">\<System.Runtime.Caching ></span><span class="sxs-lookup"><span data-stu-id="afe30-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="afe30-105">\<memoryCache ></span><span class="sxs-lookup"><span data-stu-id="afe30-105">\<memoryCache></span></span>  
<span data-ttu-id="afe30-106">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="afe30-106">\<namedCaches></span></span>  
<span data-ttu-id="afe30-107">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="afe30-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afe30-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="afe30-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <add name="default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="afe30-109">Tür</span><span class="sxs-lookup"><span data-stu-id="afe30-109">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="afe30-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="afe30-110">Attributes and Elements</span></span>  
 <span data-ttu-id="afe30-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="afe30-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="afe30-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="afe30-112">Attributes</span></span>  
  
|<span data-ttu-id="afe30-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="afe30-113">Attribute</span></span>|<span data-ttu-id="afe30-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="afe30-114">Description</span></span>|  
|-|-|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="afe30-115">(Megabayt cinsinden) izin verilen maksimum boyut belirten bir tamsayı değeri, örneği bir <xref:System.Runtime.Caching.MemoryCache> için büyüyebilir.</span><span class="sxs-lookup"><span data-stu-id="afe30-115">An integer value that specifies the maximum allowed size (in megabytes) that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="afe30-116">Varsayılan değer anlamına 0'dır <xref:System.Runtime.Caching.MemoryCache> sınıfın otomatik boyutlandırma buluşsal yöntemler, varsayılan olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="afe30-116">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="afe30-117">Önbellek adı.</span><span class="sxs-lookup"><span data-stu-id="afe30-117">The name of the cache.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="afe30-118">Önbellek tarafından kullanılabilecek yüklü olan fiziksel bilgisayar belleğini yüzdesinin üst sınırını belirtir 0 ile 100 arasında bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="afe30-118">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="afe30-119">Varsayılan değer anlamına 0'dır <xref:System.Runtime.Caching.MemoryCache> sınıfın otomatik boyutlandırma buluşsal yöntemler, varsayılan olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="afe30-119">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="afe30-120">Daha sonra önbellek uygulaması için önbellek örneğini ayarlamak mutlak ve yüzde tabanlı bellek sınırları göre geçerli bellek yükü karşılaştırır zaman aralığını gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="afe30-120">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="afe30-121">Bu değer "Ss: dd:" biçiminde girilir.</span><span class="sxs-lookup"><span data-stu-id="afe30-121">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="afe30-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="afe30-122">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="afe30-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="afe30-123">Parent Elements</span></span>  
  
|<span data-ttu-id="afe30-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="afe30-124">Element</span></span>|<span data-ttu-id="afe30-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="afe30-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="afe30-126">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="afe30-126">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="afe30-127">Yapılandırma ayarları adlandırılmış bir koleksiyonu içerir <xref:System.Runtime.Caching.MemoryCache> örnekleri.</span><span class="sxs-lookup"><span data-stu-id="afe30-127">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="afe30-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="afe30-128">Remarks</span></span>  
 <span data-ttu-id="afe30-129">`add` Öğesi ekler bir girişe `namedCaches` bir önbellek için koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="afe30-129">The `add` element adds an entry to the `namedCaches` collection for a memory cache.</span></span> <span data-ttu-id="afe30-130">Kullanabileceğiniz [temizleyin](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md) kullanmadan önce öğesi `add` olduğunu başka emin olmak için öğe koleksiyonda önbellekleri adlı.</span><span class="sxs-lookup"><span data-stu-id="afe30-130">You can use the [clear](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md) element before you use the `add` element to be certain that there are no other named caches in the collection.</span></span> <span data-ttu-id="afe30-131">Bu öğe machine.config dosyasındaki ve Web.config dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="afe30-131">This element can be used in the machine.config file and in the Web.config file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="afe30-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="afe30-132">Example</span></span>  
 <span data-ttu-id="afe30-133">Aşağıdaki örnek, varsayılan ayarları belirlemek gösterilmiştir `namedCache` girişe `namedCaches` bir önbellek için koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="afe30-133">The following example shows how to define settings for the default `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="afe30-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="afe30-134">See Also</span></span>  
 [<span data-ttu-id="afe30-135">\<namedCaches > öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="afe30-135">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
