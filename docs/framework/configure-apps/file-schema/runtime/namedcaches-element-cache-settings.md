---
title: '&lt;namedCaches&gt; öğesi (önbellek ayarları)'
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
author: mcleblanc
ms.author: markl
ms.openlocfilehash: a824e958a2b75b28aa66a15212e0276d6c127739
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54536535"
---
# <a name="ltnamedcachesgt-element-cache-settings"></a><span data-ttu-id="48cbe-102">&lt;namedCaches&gt; öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="48cbe-102">&lt;namedCaches&gt; Element (Cache Settings)</span></span>
<span data-ttu-id="48cbe-103">Yapılandırma ayarları için adlandırılmış bir koleksiyonunu belirtir <xref:System.Runtime.Caching.MemoryCache> örnekleri.</span><span class="sxs-lookup"><span data-stu-id="48cbe-103">Specifies a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span> <span data-ttu-id="48cbe-104"><xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> Özelliği, bir veya daha fazla yapılandırma ayarları koleksiyonu başvurur `namedCaches` yapılandırma dosyasının öğeleri.</span><span class="sxs-lookup"><span data-stu-id="48cbe-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> property references the collection of configuration settings from one or more `namedCaches` elements of the configuration file.</span></span>  
  
 <span data-ttu-id="48cbe-105">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="48cbe-105">\<configuration></span></span>  
<span data-ttu-id="48cbe-106">\< System.Runtime.Caching ></span><span class="sxs-lookup"><span data-stu-id="48cbe-106">\< system.runtime.caching></span></span>  
<span data-ttu-id="48cbe-107">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="48cbe-107">\<memoryCache></span></span>  
<span data-ttu-id="48cbe-108">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="48cbe-108">\<namedCaches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48cbe-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="48cbe-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
  <add name="default"/>   
</namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="48cbe-110">Tür</span><span class="sxs-lookup"><span data-stu-id="48cbe-110">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="48cbe-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="48cbe-111">Attributes and Elements</span></span>  
 <span data-ttu-id="48cbe-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="48cbe-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="48cbe-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="48cbe-113">Attributes</span></span>  
  
|<span data-ttu-id="48cbe-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="48cbe-114">Attribute</span></span>|<span data-ttu-id="48cbe-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="48cbe-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|<span data-ttu-id="48cbe-116">Megabayt cinsinden izin verilen boyut sınırını belirten bir tamsayı değeri, örneği bir <xref:System.Runtime.Caching.MemoryCache> kadar büyüyebilir.</span><span class="sxs-lookup"><span data-stu-id="48cbe-116">An integer value that specifies the maximum allowable size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="48cbe-117">Varsayılan değer otomatik boyutlandırma buluşsal yöntemler, yani 0 ' dır <xref:System.Runtime.Caching.MemoryCache> sınıfı, varsayılan olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="48cbe-117">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`name`|<span data-ttu-id="48cbe-118">Önbellek adı.</span><span class="sxs-lookup"><span data-stu-id="48cbe-118">The name of the cache.</span></span>|  
|`physicalMemoryLimitPercentage`|<span data-ttu-id="48cbe-119">Önbelleği tarafından tüketilebilecek yüklü olan fiziksel bilgisayar belleğini en yüksek yüzdesi belirten bir tamsayı değeri 0 ile 100 arasında.</span><span class="sxs-lookup"><span data-stu-id="48cbe-119">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="48cbe-120">Varsayılan değer otomatik boyutlandırma buluşsal yöntemler, yani 0 ' dır <xref:System.Runtime.Caching.MemoryCache> sınıfı, varsayılan olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="48cbe-120">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`pollingInterval`|<span data-ttu-id="48cbe-121">Daha sonra önbellek uygulaması geçerli bellek yükü önbellek örneği için ayarlanan mutlak ve yüzde tabanlı bellek sınırlarını karşı karşılaştırır zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="48cbe-121">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="48cbe-122">Bu değer, "Ss" biçiminde girilir.</span><span class="sxs-lookup"><span data-stu-id="48cbe-122">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="48cbe-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="48cbe-123">Child Elements</span></span>  
  
|<span data-ttu-id="48cbe-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="48cbe-124">Element</span></span>|<span data-ttu-id="48cbe-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="48cbe-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="48cbe-126">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="48cbe-126">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/add-element-for-namedcaches.md)|<span data-ttu-id="48cbe-127">Adlandırılmış bir önbelleğe ekler `namedCaches` koleksiyonu için bir önbellek.</span><span class="sxs-lookup"><span data-stu-id="48cbe-127">Adds a named cache to the `namedCaches` collection for a memory cache.</span></span>|  
|[<span data-ttu-id="48cbe-128">\<Temizleme ></span><span class="sxs-lookup"><span data-stu-id="48cbe-128">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md)|<span data-ttu-id="48cbe-129">Temizler `namedCaches` koleksiyonu için bir önbellek.</span><span class="sxs-lookup"><span data-stu-id="48cbe-129">Clears the `namedCaches` collection for a memory cache.</span></span>|  
|[<span data-ttu-id="48cbe-130">\<kaldırma ></span><span class="sxs-lookup"><span data-stu-id="48cbe-130">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/remove-element-for-namedcaches.md)|<span data-ttu-id="48cbe-131">Bir adlandırılmış önbellek girişi kaldırır `namedCaches` koleksiyonu için bir önbellek.</span><span class="sxs-lookup"><span data-stu-id="48cbe-131">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="48cbe-132">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="48cbe-132">Parent Elements</span></span>  
  
|<span data-ttu-id="48cbe-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="48cbe-133">Element</span></span>|<span data-ttu-id="48cbe-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="48cbe-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="48cbe-135">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="48cbe-135">\<memoryCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|<span data-ttu-id="48cbe-136">Temel alan bir önbellek yapılandırmak için kullanılan bir öğe tanımlar <xref:System.Runtime.Caching.MemoryCache> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="48cbe-136">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48cbe-137">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="48cbe-137">Remarks</span></span>  
 <span data-ttu-id="48cbe-138">Bellek önbelleğini yapılandırma bölümü Web.config dosyasının içerebilir `add`, `remove`, ve `clear` özniteliklerini `namedCaches` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="48cbe-138">The memory cache configuration section of the Web.config file can contain `add`, `remove`, and `clear` attributes for the `namedCaches` collection.</span></span> <span data-ttu-id="48cbe-139">Her `namedCaches` giriş tarafından benzersiz şekilde tanımlanır `name` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="48cbe-139">Each `namedCaches` entry is uniquely identified by the `name` attribute.</span></span>  
  
 <span data-ttu-id="48cbe-140">Uygulama yapılandırma dosyaları bilgileri başvurarak bellek önbellek girişlerinin yinelenmesini örnekleri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48cbe-140">You can retrieve instances of memory cache entries by referencing the information in the application configuration files.</span></span> <span data-ttu-id="48cbe-141">Varsayılan olarak, yalnızca varsayılan önbellek örneği yapılandırma dosyasında bir girdi içeriyor.</span><span class="sxs-lookup"><span data-stu-id="48cbe-141">By default, only the default cache instance has an entry in the configuration file.</span></span> <span data-ttu-id="48cbe-142">Varsayılan önbellek örneği öğesinden döndürülen örneğidir <xref:System.Runtime.Caching.MemoryCache.Default%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="48cbe-142">The default cache instance is the instance that is returned from the <xref:System.Runtime.Caching.MemoryCache.Default%2A> property.</span></span>  
  
 <span data-ttu-id="48cbe-143">"Varsayılan" ad özniteliğini ayarlarsanız, öğe varsayılan bellek önbellek örneği kullanır.</span><span class="sxs-lookup"><span data-stu-id="48cbe-143">If you set the name attribute to "default", the element uses the default memory cache instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48cbe-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="48cbe-144">Example</span></span>  
 <span data-ttu-id="48cbe-145">Aşağıdaki örnek, önbelleğin adını varsayılan önbellek girişi adına ayarlayarak ayarlamak gösterilmektedir `name` "varsayılan" özniteliği.</span><span class="sxs-lookup"><span data-stu-id="48cbe-145">The following example shows how to set the name of the cache to the default cache entry name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="48cbe-146">`cacheMemoryLimitMegabytes` Özniteliği ve `physicalMemoryPercentage` öznitelik sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="48cbe-146">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="48cbe-147">Bu öznitelik sıfır olarak ayarlandığında anlamına otomatik boyutlandırma buluşsal yöntemler, <xref:System.Runtime.Caching.MemoryCache> sınıfı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="48cbe-147">Setting these attributes to zero means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used.</span></span> <span data-ttu-id="48cbe-148">Önbellek uygulaması geçerli bellek yükü mutlak ve yüzde tabanlı bellek sınırlarını her iki dakikada karşı karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="48cbe-148">The cache implementation compares the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
```xml  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryLimitPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="48cbe-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48cbe-149">See also</span></span>
- [<span data-ttu-id="48cbe-150">\<memoryCache > öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="48cbe-150">\<memoryCache> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)
