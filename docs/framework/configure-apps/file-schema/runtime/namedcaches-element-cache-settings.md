---
title: <namedCaches> Öğesi (Önbellek Ayarları)
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: e0640ca18d386141f3c03135019eb4fe959b5bf8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153964"
---
# <a name="namedcaches-element-cache-settings"></a><span data-ttu-id="fb795-102">\<namedCaches> Öğesi (Önbellek Ayarları)</span><span class="sxs-lookup"><span data-stu-id="fb795-102">\<namedCaches> Element (Cache Settings)</span></span>
<span data-ttu-id="fb795-103">Adlandırılmış <xref:System.Runtime.Caching.MemoryCache> örnekler için yapılandırma ayarları koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="fb795-103">Specifies a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span> <span data-ttu-id="fb795-104">Özellik, <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> yapılandırma dosyasının bir veya `namedCaches` daha fazla öğesinden yapılandırma ayarlarının toplanmasına başvurur.</span><span class="sxs-lookup"><span data-stu-id="fb795-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> property references the collection of configuration settings from one or more `namedCaches` elements of the configuration file.</span></span>  
  
<span data-ttu-id="fb795-105">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="fb795-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="fb795-106">&nbsp;&nbsp;[**\<system.runtime.önbelleğe alma>**](system-runtime-caching-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="fb795-106">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span></span>\
<span data-ttu-id="fb795-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryÖnbellek>**](memorycache-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="fb795-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)</span></span>\
<span data-ttu-id="fb795-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedCaches>**</span><span class="sxs-lookup"><span data-stu-id="fb795-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedCaches>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb795-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fb795-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
  <add name="default"/>
</namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="fb795-110">Tür</span><span class="sxs-lookup"><span data-stu-id="fb795-110">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fb795-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fb795-111">Attributes and Elements</span></span>  
 <span data-ttu-id="fb795-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fb795-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fb795-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fb795-113">Attributes</span></span>  
  
|<span data-ttu-id="fb795-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fb795-114">Attribute</span></span>|<span data-ttu-id="fb795-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fb795-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|<span data-ttu-id="fb795-116">Megabaytlarda izin verilen maksimum boyutu belirten bir tamsayı değeri, bir <xref:System.Runtime.Caching.MemoryCache> örneğin büyüyebileceği.</span><span class="sxs-lookup"><span data-stu-id="fb795-116">An integer value that specifies the maximum allowable size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="fb795-117">Varsayılan değer 0'dır, bu da <xref:System.Runtime.Caching.MemoryCache> sınıfın otomatik boyutlandırma buluşclarının varsayılan olarak kullanıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="fb795-117">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`name`|<span data-ttu-id="fb795-118">Önbelleğin adı.</span><span class="sxs-lookup"><span data-stu-id="fb795-118">The name of the cache.</span></span>|  
|`physicalMemoryLimitPercentage`|<span data-ttu-id="fb795-119">Önbellek tarafından tüketilebilen fiziksel olarak yüklenmiş bilgisayar belleğinin maksimum yüzdesini belirten 0 ile 100 arasında bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="fb795-119">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="fb795-120">Varsayılan değer 0'dır, bu da <xref:System.Runtime.Caching.MemoryCache> sınıfın otomatik boyutlandırma buluşclarının varsayılan olarak kullanıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="fb795-120">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`pollingInterval`|<span data-ttu-id="fb795-121">Önbellek uygulamasının geçerli bellek yükünü önbellek örneği için ayarlanan mutlak ve yüzde tabanlı bellek sınırlarıyla karşılaştırdığı zaman aralığını gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="fb795-121">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="fb795-122">Bu değer "HH:MM:SS" biçiminde girilir.</span><span class="sxs-lookup"><span data-stu-id="fb795-122">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fb795-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fb795-123">Child Elements</span></span>  
  
|<span data-ttu-id="fb795-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="fb795-124">Element</span></span>|<span data-ttu-id="fb795-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fb795-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fb795-126">\<>ekleyin</span><span class="sxs-lookup"><span data-stu-id="fb795-126">\<add></span></span>](add-element-for-namedcaches.md)|<span data-ttu-id="fb795-127">Bellek önbelleği için `namedCaches` koleksiyona adlandırılmış bir önbellek ekler.</span><span class="sxs-lookup"><span data-stu-id="fb795-127">Adds a named cache to the `namedCaches` collection for a memory cache.</span></span>|  
|[<span data-ttu-id="fb795-128">\<açık></span><span class="sxs-lookup"><span data-stu-id="fb795-128">\<clear></span></span>](clear-element-for-namedcaches.md)|<span data-ttu-id="fb795-129">Bellek önbelleği `namedCaches` için koleksiyonu temizler.</span><span class="sxs-lookup"><span data-stu-id="fb795-129">Clears the `namedCaches` collection for a memory cache.</span></span>|  
|[<span data-ttu-id="fb795-130">\<>kaldırmak</span><span class="sxs-lookup"><span data-stu-id="fb795-130">\<remove></span></span>](remove-element-for-namedcaches.md)|<span data-ttu-id="fb795-131">Bellek önbelleği için `namedCaches` koleksiyondan adlandırılmış önbellek girişini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="fb795-131">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fb795-132">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fb795-132">Parent Elements</span></span>  
  
|<span data-ttu-id="fb795-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="fb795-133">Element</span></span>|<span data-ttu-id="fb795-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fb795-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fb795-135">\<yapılandırma></span><span class="sxs-lookup"><span data-stu-id="fb795-135">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="fb795-136">Ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan her yapılandırma dosyasındaki kök öğeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="fb795-136">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="fb795-137">\<memoryÖnbellek></span><span class="sxs-lookup"><span data-stu-id="fb795-137">\<memoryCache></span></span>](memorycache-element-cache-settings.md)|<span data-ttu-id="fb795-138">Sınıfı temel alan önbelleği yapılandırmak için kullanılan bir <xref:System.Runtime.Caching.MemoryCache> öğetanımlar.</span><span class="sxs-lookup"><span data-stu-id="fb795-138">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
|[<span data-ttu-id="fb795-139">\<system.runtime.önbelleğe alma></span><span class="sxs-lookup"><span data-stu-id="fb795-139">\<system.runtime.caching></span></span>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="fb795-140">.NET Framework'de yerleşik olan uygulamalarda çıktı önbelleğe alma uygulamanızı sağlayan türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="fb795-140">Contains types that let you implement output caching in applications that are built into the .NET Framework.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb795-141">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fb795-141">Remarks</span></span>  
 <span data-ttu-id="fb795-142">Web.config dosyasının bellek önbelleği yapılandırma `add` `remove` `namedCaches` bölümü, `clear` koleksiyon için öznitelikleri ve öznitelikleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="fb795-142">The memory cache configuration section of the Web.config file can contain `add`, `remove`, and `clear` attributes for the `namedCaches` collection.</span></span> <span data-ttu-id="fb795-143">Her `namedCaches` giriş öznitelik tarafından `name` benzersiz olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="fb795-143">Each `namedCaches` entry is uniquely identified by the `name` attribute.</span></span>  
  
 <span data-ttu-id="fb795-144">Uygulama yapılandırma dosyalarındaki bilgilere başvurarak bellek önbellek girişleri örneklerini alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fb795-144">You can retrieve instances of memory cache entries by referencing the information in the application configuration files.</span></span> <span data-ttu-id="fb795-145">Varsayılan olarak, yapılandırma dosyasında yalnızca varsayılan önbellek örneği bir girişi vardır.</span><span class="sxs-lookup"><span data-stu-id="fb795-145">By default, only the default cache instance has an entry in the configuration file.</span></span> <span data-ttu-id="fb795-146">Varsayılan önbellek <xref:System.Runtime.Caching.MemoryCache.Default%2A> örneği, özellikten döndürülen örnektir.</span><span class="sxs-lookup"><span data-stu-id="fb795-146">The default cache instance is the instance that is returned from the <xref:System.Runtime.Caching.MemoryCache.Default%2A> property.</span></span>  
  
 <span data-ttu-id="fb795-147">Ad özniteliğini "varsayılan" olarak ayarlarsanız, öğe varsayılan bellek önbellek örneğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="fb795-147">If you set the name attribute to "default", the element uses the default memory cache instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb795-148">Örnek</span><span class="sxs-lookup"><span data-stu-id="fb795-148">Example</span></span>  
 <span data-ttu-id="fb795-149">Aşağıdaki örnekte, `name` özniteliği "varsayılan" olarak ayarlayarak önbelleğin adının varsayılan önbellek giriş adı olarak nasıl ayarlanılabildiği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fb795-149">The following example shows how to set the name of the cache to the default cache entry name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="fb795-150">Öznitelik `cacheMemoryLimitMegabytes` ve `physicalMemoryPercentage` öznitelik sıfıra ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="fb795-150">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="fb795-151">Bu öznitelikleri sıfıra ayarlamak, <xref:System.Runtime.Caching.MemoryCache> sınıfın otomatik boyutlandırma sezgisellerinin kullanıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="fb795-151">Setting these attributes to zero means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used.</span></span> <span data-ttu-id="fb795-152">Önbellek uygulaması, geçerli bellek yükünü her iki dakikada bir mutlak ve yüzde tabanlı bellek sınırlarıyla karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="fb795-152">The cache implementation compares the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fb795-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb795-153">See also</span></span>

- [<span data-ttu-id="fb795-154">\<memoryÖnbellek> Öğesi (Önbellek Ayarları)</span><span class="sxs-lookup"><span data-stu-id="fb795-154">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
