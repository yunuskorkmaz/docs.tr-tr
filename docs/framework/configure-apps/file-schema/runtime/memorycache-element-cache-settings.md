---
title: <memoryCache> Öğesi (Önbellek Ayarları)
ms.date: 03/30/2017
helpviewer_keywords:
- <memoryCache> element
- caching [.NET Framework], configuration
- memoryCache element
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
ms.openlocfilehash: 46f430f7cf112da40aa3b25bfb280c5014612eae
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663613"
---
# <a name="memorycache-element-cache-settings"></a><span data-ttu-id="78728-102">\<memoryCache > öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="78728-102">\<memoryCache> Element (Cache Settings)</span></span>
<span data-ttu-id="78728-103"><xref:System.Runtime.Caching.MemoryCache> Sınıfına dayalı bir önbelleği yapılandırmak için kullanılan bir öğesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="78728-103">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="78728-104">Sınıfı, önbelleği yapılandırmak için kullanabileceğiniz bir memoryCache öğesi tanımlar. [](memorycache-element-cache-settings.md) <xref:System.Runtime.Caching.Configuration.MemoryCacheElement></span><span class="sxs-lookup"><span data-stu-id="78728-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> class defines a [memoryCache](memorycache-element-cache-settings.md) element that you can use to configure the cache.</span></span> <span data-ttu-id="78728-105"><xref:System.Runtime.Caching.MemoryCache> Sınıfın birden çok örneği tek bir uygulamada kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="78728-105">Multiple instances of the <xref:System.Runtime.Caching.MemoryCache> class can be used in a single application.</span></span> <span data-ttu-id="78728-106">Yapılandırma `memoryCache` dosyasındaki her öğe, adlandırılmış <xref:System.Runtime.Caching.MemoryCache> bir örnek için ayarları içerebilir.</span><span class="sxs-lookup"><span data-stu-id="78728-106">Each `memoryCache` element in the configuration file can contain settings for a named <xref:System.Runtime.Caching.MemoryCache> instance.</span></span>  
  
 <span data-ttu-id="78728-107">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="78728-107">\<configuration></span></span>  
<span data-ttu-id="78728-108">\<System. Runtime. Caching ></span><span class="sxs-lookup"><span data-stu-id="78728-108">\<system.runtime.caching></span></span>  
<span data-ttu-id="78728-109">\<memoryCache ></span><span class="sxs-lookup"><span data-stu-id="78728-109">\<memoryCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78728-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="78728-110">Syntax</span></span>  
  
```xml  
<memoryCache>   
    <namedCaches>  
        <!-- child elements -->  
    </namedCaches>   
</memoryCache>  
```  
  
## <a name="type"></a><span data-ttu-id="78728-111">Tür</span><span class="sxs-lookup"><span data-stu-id="78728-111">Type</span></span>  
 <span data-ttu-id="78728-112"><xref:System.Runtime.Caching.MemoryCache>sınıfı.</span><span class="sxs-lookup"><span data-stu-id="78728-112"><xref:System.Runtime.Caching.MemoryCache> class.</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="78728-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="78728-113">Attributes and Elements</span></span>  
 <span data-ttu-id="78728-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="78728-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="78728-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="78728-115">Attributes</span></span>  
  
|<span data-ttu-id="78728-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="78728-116">Attribute</span></span>|<span data-ttu-id="78728-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="78728-117">Description</span></span>|  
|---------------|-----------------|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="78728-118">Bir <xref:System.Runtime.Caching.MemoryCache> nesne örneğinin büyüyebileceği maksimum bellek boyutu (megabayt cinsinden).</span><span class="sxs-lookup"><span data-stu-id="78728-118">The maximum memory size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> object can grow to.</span></span> <span data-ttu-id="78728-119">Varsayılan değer 0 ' dır. Bu, <xref:System.Runtime.Caching.MemoryCache> sınıfın AutoSize buluşsal yöntemleri varsayılan olarak kullanıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="78728-119">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="78728-120">Önbellek yapılandırmasının adı.</span><span class="sxs-lookup"><span data-stu-id="78728-120">The name of the cache configuration.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="78728-121">Önbellek tarafından kullanılabilen fiziksel bellek yüzdesi.</span><span class="sxs-lookup"><span data-stu-id="78728-121">The percentage of physical memory that can be used by the cache.</span></span> <span data-ttu-id="78728-122">Varsayılan değer 0 ' dır. Bu, <xref:System.Runtime.Caching.MemoryCache> sınıfın AutoSize buluşsal yöntemleri varsayılan olarak kullanıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="78728-122">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="78728-123">Önbellek uygulamasının geçerli bellek yükünü, önbellek örneği için ayarlanan mutlak ve yüzde tabanlı bellek sınırlarına göre karşılaştıran zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="78728-123">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="78728-124">Değer "HH: MM: SS" biçiminde girilir.</span><span class="sxs-lookup"><span data-stu-id="78728-124">The value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="78728-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="78728-125">Child Elements</span></span>  
  
|<span data-ttu-id="78728-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="78728-126">Element</span></span>|<span data-ttu-id="78728-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="78728-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="78728-128">\<Namedönbellekler ></span><span class="sxs-lookup"><span data-stu-id="78728-128">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="78728-129">`namedCache` Örnek için yapılandırma ayarlarının bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="78728-129">Contains a collection of configuration settings for the `namedCache` instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="78728-130">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="78728-130">Parent Elements</span></span>  
  
|<span data-ttu-id="78728-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="78728-131">Element</span></span>|<span data-ttu-id="78728-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="78728-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="78728-133">\<System. Runtime. Caching ></span><span class="sxs-lookup"><span data-stu-id="78728-133">\<system.runtime.caching></span></span>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="78728-134">.NET Framework yerleşik uygulamalarda çıktı önbelleği uygulamanıza olanak sağlayan türler içerir.</span><span class="sxs-lookup"><span data-stu-id="78728-134">Contains types that let you implement output caching in applications that are built into the .NET Framework.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78728-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="78728-135">Remarks</span></span>  
 <span data-ttu-id="78728-136">Sınıf, soyut <xref:System.Runtime.Caching.ObjectCache> sınıfın somut bir uygulamasıdır. <xref:System.Runtime.Caching.MemoryCache></span><span class="sxs-lookup"><span data-stu-id="78728-136">The <xref:System.Runtime.Caching.MemoryCache> class is a concrete implementation of the abstract <xref:System.Runtime.Caching.ObjectCache> class.</span></span> <span data-ttu-id="78728-137">Sınıf örnekleri, <xref:System.Runtime.Caching.MemoryCache> uygulama yapılandırma dosyalarından yapılandırma bilgileriyle sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="78728-137">Instances of the <xref:System.Runtime.Caching.MemoryCache> class can be supplied with configuration information from application configuration files.</span></span> <span data-ttu-id="78728-138">[MemoryCache](memorycache-element-cache-settings.md) yapılandırma bölümü bir `namedCaches` yapılandırma koleksiyonu içerir.</span><span class="sxs-lookup"><span data-stu-id="78728-138">The [memoryCache](memorycache-element-cache-settings.md) configuration section contains a `namedCaches` configuration collection.</span></span>  
  
 <span data-ttu-id="78728-139">Bellek tabanlı önbellek nesnesi başlatıldığında, önce bellek önbelleği oluşturucusuna geçirilen parametresindeki adla eşleşen bir `namedCaches` giriş bulmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="78728-139">When a memory-based cache object is initialized, it first tries to find a `namedCaches` entry that matches the name in the parameter that is passed to the memory cache constructor.</span></span> <span data-ttu-id="78728-140">Bir `namedCaches` giriş bulunursa, yoklama ve bellek yönetimi bilgileri yapılandırma dosyasından alınır.</span><span class="sxs-lookup"><span data-stu-id="78728-140">If a `namedCaches` entry is found, the polling and memory-management information are retrieved from the configuration file.</span></span>  
  
 <span data-ttu-id="78728-141">Başlatma işlemi daha sonra, kurucudaki yapılandırma bilgileri için isteğe bağlı ad/değer çiftleri koleksiyonu kullanılarak herhangi bir yapılandırma girişinin geçersiz kılınıp kılınmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="78728-141">The initialization process then determines whether any configuration entries were overridden, by using the optional collection of name/value pairs of configuration information in the constructor.</span></span> <span data-ttu-id="78728-142">Ad/değer çifti koleksiyonunda aşağıdaki değerlerden birini geçirirseniz, bu değerler yapılandırma dosyasından elde edilen bilgileri geçersiz kılar:</span><span class="sxs-lookup"><span data-stu-id="78728-142">If you pass any one of the following values in the name/value pair collection, these values override information obtained from the configuration file:</span></span>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
- <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## <a name="example"></a><span data-ttu-id="78728-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="78728-143">Example</span></span>  
 <span data-ttu-id="78728-144">Aşağıdaki örnek, <xref:System.Runtime.Caching.MemoryCache> `name` özniteliğini "default" olarak ayarlayarak nesnenin adının varsayılan önbellek nesnesi adına nasıl ayarlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="78728-144">The following example shows how to set the name of the <xref:System.Runtime.Caching.MemoryCache> object to the default cache object name by setting the `name` attribute to "Default".</span></span>  
  
 <span data-ttu-id="78728-145">`cacheMemoryLimitMegabytes` Özniteliği`physicalMemoryLimitPercentage` ve özniteliği sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="78728-145">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryLimitPercentage` attribute are set to zero.</span></span> <span data-ttu-id="78728-146">Bu özniteliklerin sıfıra ayarlanması, <xref:System.Runtime.Caching.MemoryCache> otomatik boyutlandırma buluşsal yöntemleri varsayılan olarak kullanıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="78728-146">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="78728-147">Önbellek uygulamasının her iki dakikada bir, geçerli bellek yükünü mutlak ve yüzde tabanlı bellek sınırlarına göre karşılaştırması gerekir.</span><span class="sxs-lookup"><span data-stu-id="78728-147">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
```xml  
<configuration>  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="Default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryLimitPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="78728-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78728-148">See also</span></span>

- <xref:System.Runtime.Caching.MemoryCache>
- [<span data-ttu-id="78728-149">\<System. Runtime. Caching > öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="78728-149">\<system.runtime.caching> Element (Cache Settings)</span></span>](system-runtime-caching-element-cache-settings.md)
- [<span data-ttu-id="78728-150">\<Namedönbellekler > öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="78728-150">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
