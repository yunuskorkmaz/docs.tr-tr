---
title: <memoryCache> Öğesi (Önbellek Ayarları)
ms.date: 03/30/2017
helpviewer_keywords:
- <memoryCache> element
- caching [.NET Framework], configuration
- memoryCache element
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
ms.openlocfilehash: 25e87aa9fa4e56c5042eb25c41f6cfe1b65aea24
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266383"
---
# <a name="memorycache-element-cache-settings"></a><span data-ttu-id="d55fc-102">\<memoryCache > öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="d55fc-102">\<memoryCache> Element (Cache Settings)</span></span>
<span data-ttu-id="d55fc-103">Temel alan bir önbellek yapılandırmak için kullanılan bir öğe tanımlar <xref:System.Runtime.Caching.MemoryCache> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d55fc-103">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="d55fc-104"><xref:System.Runtime.Caching.Configuration.MemoryCacheElement> Sınıfı tanımlayan bir [memoryCache](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md) önbelleğini yapılandırmak için kullanabileceğiniz bir öğesi.</span><span class="sxs-lookup"><span data-stu-id="d55fc-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> class defines a [memoryCache](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md) element that you can use to configure the cache.</span></span> <span data-ttu-id="d55fc-105">Birden çok örneğini <xref:System.Runtime.Caching.MemoryCache> sınıfı tek bir uygulama içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d55fc-105">Multiple instances of the <xref:System.Runtime.Caching.MemoryCache> class can be used in a single application.</span></span> <span data-ttu-id="d55fc-106">Her `memoryCache` öğesi yapılandırma dosyasında bir adlandırılmış için ayarları içerebilir <xref:System.Runtime.Caching.MemoryCache> örneği.</span><span class="sxs-lookup"><span data-stu-id="d55fc-106">Each `memoryCache` element in the configuration file can contain settings for a named <xref:System.Runtime.Caching.MemoryCache> instance.</span></span>  
  
 <span data-ttu-id="d55fc-107">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="d55fc-107">\<configuration></span></span>  
<span data-ttu-id="d55fc-108">\<System.Runtime.Caching ></span><span class="sxs-lookup"><span data-stu-id="d55fc-108">\<system.runtime.caching></span></span>  
<span data-ttu-id="d55fc-109">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="d55fc-109">\<memoryCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d55fc-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d55fc-110">Syntax</span></span>  
  
```xml  
<memoryCache>   
    <namedCaches>  
        <!-- child elements -->  
    </namedCaches>   
</memoryCache>  
```  
  
## <a name="type"></a><span data-ttu-id="d55fc-111">Tür</span><span class="sxs-lookup"><span data-stu-id="d55fc-111">Type</span></span>  
 <span data-ttu-id="d55fc-112"><xref:System.Runtime.Caching.MemoryCache> sınıf.</span><span class="sxs-lookup"><span data-stu-id="d55fc-112"><xref:System.Runtime.Caching.MemoryCache> class.</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d55fc-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d55fc-113">Attributes and Elements</span></span>  
 <span data-ttu-id="d55fc-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d55fc-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d55fc-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d55fc-115">Attributes</span></span>  
  
|<span data-ttu-id="d55fc-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d55fc-116">Attribute</span></span>|<span data-ttu-id="d55fc-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d55fc-117">Description</span></span>|  
|---------------|-----------------|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="d55fc-118">Megabayt cinsinden en yüksek bellek boyutu, örneği bir <xref:System.Runtime.Caching.MemoryCache> nesne büyüyebileceği.</span><span class="sxs-lookup"><span data-stu-id="d55fc-118">The maximum memory size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> object can grow to.</span></span> <span data-ttu-id="d55fc-119">Varsayılan değerdir, yani 0 <xref:System.Runtime.Caching.MemoryCache> sınıfın autosize buluşsal yöntemler, varsayılan olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d55fc-119">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="d55fc-120">Önbellek yapılandırmasının adı.</span><span class="sxs-lookup"><span data-stu-id="d55fc-120">The name of the cache configuration.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="d55fc-121">Önbelleği tarafından kullanılan fiziksel bellek yüzdesi.</span><span class="sxs-lookup"><span data-stu-id="d55fc-121">The percentage of physical memory that can be used by the cache.</span></span> <span data-ttu-id="d55fc-122">Varsayılan değerdir, yani 0 <xref:System.Runtime.Caching.MemoryCache> sınıfın autosize buluşsal yöntemler, varsayılan olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d55fc-122">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="d55fc-123">Daha sonra önbellek uygulaması geçerli bellek yükü önbellek örneği için ayarlanan mutlak ve yüzde tabanlı bellek sınırlarını karşı karşılaştırır zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="d55fc-123">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="d55fc-124">"Ss" biçiminde girilen değer.</span><span class="sxs-lookup"><span data-stu-id="d55fc-124">The value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d55fc-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d55fc-125">Child Elements</span></span>  
  
|<span data-ttu-id="d55fc-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="d55fc-126">Element</span></span>|<span data-ttu-id="d55fc-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d55fc-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d55fc-128">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="d55fc-128">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="d55fc-129">Yapılandırma ayarları koleksiyonu içeren `namedCache` örneği.</span><span class="sxs-lookup"><span data-stu-id="d55fc-129">Contains a collection of configuration settings for the `namedCache` instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d55fc-130">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d55fc-130">Parent Elements</span></span>  
  
|<span data-ttu-id="d55fc-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="d55fc-131">Element</span></span>|<span data-ttu-id="d55fc-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d55fc-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d55fc-133">\<System.Runtime.Caching ></span><span class="sxs-lookup"><span data-stu-id="d55fc-133">\<system.runtime.caching></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="d55fc-134">Çıktı önbelleği içinde yerleşik olan uygulamalarda uygulama sağlayan türler içerir [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d55fc-134">Contains types that let you implement output caching in applications that are built into the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d55fc-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d55fc-135">Remarks</span></span>  
 <span data-ttu-id="d55fc-136"><xref:System.Runtime.Caching.MemoryCache> Sınıf, soyut bir somut uygulaması <xref:System.Runtime.Caching.ObjectCache> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d55fc-136">The <xref:System.Runtime.Caching.MemoryCache> class is a concrete implementation of the abstract <xref:System.Runtime.Caching.ObjectCache> class.</span></span> <span data-ttu-id="d55fc-137">Örneklerini <xref:System.Runtime.Caching.MemoryCache> sınıfı, uygulama yapılandırma dosyaları yapılandırma bilgileriyle sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="d55fc-137">Instances of the <xref:System.Runtime.Caching.MemoryCache> class can be supplied with configuration information from application configuration files.</span></span> <span data-ttu-id="d55fc-138">[MemoryCache](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md) yapılandırma bölümü içeren bir `namedCaches` yapılandırma koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d55fc-138">The [memoryCache](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md) configuration section contains a `namedCaches` configuration collection.</span></span>  
  
 <span data-ttu-id="d55fc-139">Bir bellek tabanlı önbellek nesnesi başlatılırken, ilk bulmaya çalışır bir `namedCaches` bellek önbellek oluşturucuya geçirilen parametre adıyla eşleşen girişi.</span><span class="sxs-lookup"><span data-stu-id="d55fc-139">When a memory-based cache object is initialized, it first tries to find a `namedCaches` entry that matches the name in the parameter that is passed to the memory cache constructor.</span></span> <span data-ttu-id="d55fc-140">Varsa bir `namedCaches` girişi bulundu, yoklama ve bellek yönetimi bilgileri yapılandırma dosyasından alınır.</span><span class="sxs-lookup"><span data-stu-id="d55fc-140">If a `namedCaches` entry is found, the polling and memory-management information are retrieved from the configuration file.</span></span>  
  
 <span data-ttu-id="d55fc-141">Başlatma işlemi, ardından herhangi bir yapılandırma girdileri, oluşturucuda isteğe bağlı yapılandırma bilgilerini ad/değer çiftleri koleksiyonu kullanarak geçersiz kılınmış olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="d55fc-141">The initialization process then determines whether any configuration entries were overridden, by using the optional collection of name/value pairs of configuration information in the constructor.</span></span> <span data-ttu-id="d55fc-142">Aşağıdaki değerlerden herhangi bir ad/değer çifti koleksiyonu geçirirseniz, bu değerler yapılandırma dosyasından alınan bilgilerle geçersiz kıl:</span><span class="sxs-lookup"><span data-stu-id="d55fc-142">If you pass any one of the following values in the name/value pair collection, these values override information obtained from the configuration file:</span></span>  
  
-   <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
-   <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
-   <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## <a name="example"></a><span data-ttu-id="d55fc-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="d55fc-143">Example</span></span>  
 <span data-ttu-id="d55fc-144">Aşağıdaki örnek adını ayarlama işlemi gösterilmektedir <xref:System.Runtime.Caching.MemoryCache> ayarlayarak varsayılan önbellek nesnesi adı nesnesine `name` "varsayılan" özniteliği.</span><span class="sxs-lookup"><span data-stu-id="d55fc-144">The following example shows how to set the name of the <xref:System.Runtime.Caching.MemoryCache> object to the default cache object name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="d55fc-145">`cacheMemoryLimitMegabytes` Özniteliği ve `physicalMemoryLimitPercentage` öznitelik sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="d55fc-145">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryLimitPercentage` attribute are set to zero.</span></span> <span data-ttu-id="d55fc-146">Bu öznitelik sıfır olarak ayarlandığında <xref:System.Runtime.Caching.MemoryCache> otomatik boyutlandırma buluşsal yöntemler, varsayılan olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d55fc-146">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="d55fc-147">Önbellek uygulaması, iki dakikada mutlak ve yüzde tabanlı bellek sınırlarını karşı geçerli bellek yükü karşılaştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d55fc-147">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d55fc-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d55fc-148">See also</span></span>
- <xref:System.Runtime.Caching.MemoryCache>
- [<span data-ttu-id="d55fc-149">\<System.Runtime.Caching > öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="d55fc-149">\<system.runtime.caching> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)
- [<span data-ttu-id="d55fc-150">\<namedCaches > öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="d55fc-150">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
