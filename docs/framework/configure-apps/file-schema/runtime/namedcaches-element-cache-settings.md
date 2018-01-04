---
title: "&lt;namedCaches&gt; öğesi (önbellek ayarları)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: f4c4bd9901b053c96a260435c34ffa3ddd2c7283
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltnamedcachesgt-element-cache-settings"></a><span data-ttu-id="09985-102">&lt;namedCaches&gt; öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="09985-102">&lt;namedCaches&gt; Element (Cache Settings)</span></span>
<span data-ttu-id="09985-103">Adlandırılmış için yapılandırma ayarlarını koleksiyonunu belirtir <xref:System.Runtime.Caching.MemoryCache> örnekleri.</span><span class="sxs-lookup"><span data-stu-id="09985-103">Specifies a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span> <span data-ttu-id="09985-104"><xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> Özelliği, bir veya daha fazla yapılandırma ayarları topluluğunu başvurur `namedCaches` yapılandırma dosyasının öğeleri.</span><span class="sxs-lookup"><span data-stu-id="09985-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> property references the collection of configuration settings from one or more `namedCaches` elements of the configuration file.</span></span>  
  
 <span data-ttu-id="09985-105">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="09985-105">\<configuration></span></span>  
<span data-ttu-id="09985-106">\<System.Runtime.Caching ></span><span class="sxs-lookup"><span data-stu-id="09985-106">\< system.runtime.caching></span></span>  
<span data-ttu-id="09985-107">\<memoryCache ></span><span class="sxs-lookup"><span data-stu-id="09985-107">\<memoryCache></span></span>  
<span data-ttu-id="09985-108">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="09985-108">\<namedCaches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09985-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="09985-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
  <add name="default"/>   
</namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="09985-110">Tür</span><span class="sxs-lookup"><span data-stu-id="09985-110">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="09985-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="09985-111">Attributes and Elements</span></span>  
 <span data-ttu-id="09985-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="09985-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="09985-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="09985-113">Attributes</span></span>  
  
|<span data-ttu-id="09985-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="09985-114">Attribute</span></span>|<span data-ttu-id="09985-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="09985-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|<span data-ttu-id="09985-116">En fazla izin verilen boyutu megabayt cinsinden belirten bir tamsayı değeri, örneği bir <xref:System.Runtime.Caching.MemoryCache> için büyüyebilir.</span><span class="sxs-lookup"><span data-stu-id="09985-116">An integer value that specifies the maximum allowable size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="09985-117">Varsayılan değer otomatik boyutlandırma buluşsal yöntemler, yani 0'dır <xref:System.Runtime.Caching.MemoryCache> sınıfı, varsayılan olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="09985-117">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`name`|<span data-ttu-id="09985-118">Önbellek adı.</span><span class="sxs-lookup"><span data-stu-id="09985-118">The name of the cache.</span></span>|  
|`physicalMemoryLimitPercentage`|<span data-ttu-id="09985-119">Önbellek tarafından kullanılabilecek yüklü olan fiziksel bilgisayar belleğini yüzdesinin üst sınırını belirtir 0 ile 100 arasında bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="09985-119">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="09985-120">Varsayılan değer otomatik boyutlandırma buluşsal yöntemler, yani 0'dır <xref:System.Runtime.Caching.MemoryCache> sınıfı, varsayılan olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="09985-120">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`pollingInterval`|<span data-ttu-id="09985-121">Daha sonra önbellek uygulaması için önbellek örneğini ayarlamak mutlak ve yüzde tabanlı bellek sınırları göre geçerli bellek yükü karşılaştırır zaman aralığını gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="09985-121">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="09985-122">Bu değer "Ss: dd:" biçiminde girilir.</span><span class="sxs-lookup"><span data-stu-id="09985-122">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="09985-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="09985-123">Child Elements</span></span>  
  
|<span data-ttu-id="09985-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="09985-124">Element</span></span>|<span data-ttu-id="09985-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="09985-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="09985-126">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="09985-126">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/add-element-for-namedcaches.md)|<span data-ttu-id="09985-127">Adlandırılmış bir önbelleğe ekler `namedCaches` bir önbellek için koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="09985-127">Adds a named cache to the `namedCaches` collection for a memory cache.</span></span>|  
|[<span data-ttu-id="09985-128">\<Clear ></span><span class="sxs-lookup"><span data-stu-id="09985-128">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md)|<span data-ttu-id="09985-129">Temizler `namedCaches` bir önbellek için koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="09985-129">Clears the `namedCaches` collection for a memory cache.</span></span>|  
|[<span data-ttu-id="09985-130">\<kaldırma ></span><span class="sxs-lookup"><span data-stu-id="09985-130">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/remove-element-for-namedcaches.md)|<span data-ttu-id="09985-131">Bir adlandırılmış önbellek girişi kaldırır `namedCaches` bir önbellek için koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="09985-131">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="09985-132">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="09985-132">Parent Elements</span></span>  
  
|<span data-ttu-id="09985-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="09985-133">Element</span></span>|<span data-ttu-id="09985-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="09985-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="09985-135">\<memoryCache ></span><span class="sxs-lookup"><span data-stu-id="09985-135">\<memoryCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|<span data-ttu-id="09985-136">Temel alan bir önbellek yapılandırmak için kullanılan bir öğe tanımlar <xref:System.Runtime.Caching.MemoryCache> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="09985-136">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="09985-137">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="09985-137">Remarks</span></span>  
 <span data-ttu-id="09985-138">Bellek önbelleği yapılandırma bölümü Web.config dosyasının içerebilir `add`, `remove`, ve `clear` için öznitelikler `namedCaches` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="09985-138">The memory cache configuration section of the Web.config file can contain `add`, `remove`, and `clear` attributes for the `namedCaches` collection.</span></span> <span data-ttu-id="09985-139">Her `namedCaches` girişi tarafından tanımlanan benzersiz olarak `name` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="09985-139">Each `namedCaches` entry is uniquely identified by the `name` attribute.</span></span>  
  
 <span data-ttu-id="09985-140">Uygulama yapılandırma dosyaları bilgilerinde başvurarak bellek önbellek girişlerinin örneklerini alabilir.</span><span class="sxs-lookup"><span data-stu-id="09985-140">You can retrieve instances of memory cache entries by referencing the information in the application configuration files.</span></span> <span data-ttu-id="09985-141">Varsayılan olarak, yalnızca varsayılan önbellek örneği yapılandırma dosyasında bir giriş içeriyor.</span><span class="sxs-lookup"><span data-stu-id="09985-141">By default, only the default cache instance has an entry in the configuration file.</span></span> <span data-ttu-id="09985-142">Varsayılan önbellek örneği sunucudan döndürülen örneğidir <xref:System.Runtime.Caching.MemoryCache.Default%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="09985-142">The default cache instance is the instance that is returned from the <xref:System.Runtime.Caching.MemoryCache.Default%2A> property.</span></span>  
  
 <span data-ttu-id="09985-143">"Varsayılan" name özniteliği ayarlarsanız, öğe varsayılan bellek önbellek örneği kullanır.</span><span class="sxs-lookup"><span data-stu-id="09985-143">If you set the name attribute to "default", the element uses the default memory cache instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="09985-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="09985-144">Example</span></span>  
 <span data-ttu-id="09985-145">Aşağıdaki örnek ayarlayarak varsayılan önbellek girişi adı önbellek adını ayarlayın gösterilmektedir `name` "varsayılan" özniteliği.</span><span class="sxs-lookup"><span data-stu-id="09985-145">The following example shows how to set the name of the cache to the default cache entry name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="09985-146">`cacheMemoryLimitMegabytes` Özniteliği ve `physicalMemoryPercentage` özniteliği sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="09985-146">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="09985-147">Bu öznitelikler sıfır olarak ayarlandığında anlamına otomatik boyutlandırma buluşsal yöntemler, <xref:System.Runtime.Caching.MemoryCache> sınıfı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="09985-147">Setting these attributes to zero means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used.</span></span> <span data-ttu-id="09985-148">Önbellek uygulaması mutlak ve yüzde tabanlı bellek sınırları her iki dakikada göre geçerli bellek yükü karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="09985-148">The cache implementation compares the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="09985-149">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="09985-149">See Also</span></span>  
 [<span data-ttu-id="09985-150">\<memoryCache > öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="09985-150">\<memoryCache> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)
