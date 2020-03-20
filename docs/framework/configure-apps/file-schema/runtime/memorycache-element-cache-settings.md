---
title: <memoryCache> Öğesi (Önbellek Ayarları)
ms.date: 03/30/2017
helpviewer_keywords:
- <memoryCache> element
- caching [.NET Framework], configuration
- memoryCache element
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
ms.openlocfilehash: 94c21e0408b7616bf0c8a24267b72bfa7cc3aaa0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153990"
---
# <a name="memorycache-element-cache-settings"></a><span data-ttu-id="432a8-102">\<memoryÖnbellek> Öğesi (Önbellek Ayarları)</span><span class="sxs-lookup"><span data-stu-id="432a8-102">\<memoryCache> Element (Cache Settings)</span></span>
<span data-ttu-id="432a8-103">Sınıfı temel alan önbelleği yapılandırmak için kullanılan bir <xref:System.Runtime.Caching.MemoryCache> öğetanımlar.</span><span class="sxs-lookup"><span data-stu-id="432a8-103">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="432a8-104">Sınıf, <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> önbelleği yapılandırmak için kullanabileceğiniz bir [memoryCache](memorycache-element-cache-settings.md) öğesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="432a8-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> class defines a [memoryCache](memorycache-element-cache-settings.md) element that you can use to configure the cache.</span></span> <span data-ttu-id="432a8-105"><xref:System.Runtime.Caching.MemoryCache> Sınıfın birden çok örneği tek bir uygulamada kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="432a8-105">Multiple instances of the <xref:System.Runtime.Caching.MemoryCache> class can be used in a single application.</span></span> <span data-ttu-id="432a8-106">Yapılandırma `memoryCache` dosyasındaki her öğe, adlandırılmış <xref:System.Runtime.Caching.MemoryCache> bir örneğin ayarlarını içerebilir.</span><span class="sxs-lookup"><span data-stu-id="432a8-106">Each `memoryCache` element in the configuration file can contain settings for a named <xref:System.Runtime.Caching.MemoryCache> instance.</span></span>  
  
<span data-ttu-id="432a8-107">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="432a8-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="432a8-108">&nbsp;&nbsp;[**\<system.runtime.önbelleğe alma>**](system-runtime-caching-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="432a8-108">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span></span>\
<span data-ttu-id="432a8-109">&nbsp;&nbsp;&nbsp;&nbsp;**\<memoryÖnbellek>**</span><span class="sxs-lookup"><span data-stu-id="432a8-109">&nbsp;&nbsp;&nbsp;&nbsp;**\<memoryCache>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="432a8-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="432a8-110">Syntax</span></span>  
  
```xml  
<memoryCache>
    <namedCaches>  
        <!-- child elements -->  
    </namedCaches>
</memoryCache>  
```  
  
## <a name="type"></a><span data-ttu-id="432a8-111">Tür</span><span class="sxs-lookup"><span data-stu-id="432a8-111">Type</span></span>  
 <span data-ttu-id="432a8-112"><xref:System.Runtime.Caching.MemoryCache>Sınıfı.</span><span class="sxs-lookup"><span data-stu-id="432a8-112"><xref:System.Runtime.Caching.MemoryCache> class.</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="432a8-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="432a8-113">Attributes and Elements</span></span>  
 <span data-ttu-id="432a8-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="432a8-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="432a8-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="432a8-115">Attributes</span></span>  
  
|<span data-ttu-id="432a8-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="432a8-116">Attribute</span></span>|<span data-ttu-id="432a8-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="432a8-117">Description</span></span>|  
|---------------|-----------------|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="432a8-118">Megabaytlarda, bir <xref:System.Runtime.Caching.MemoryCache> nesnenin bir örneğinin büyüyebileceği maksimum bellek boyutu.</span><span class="sxs-lookup"><span data-stu-id="432a8-118">The maximum memory size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> object can grow to.</span></span> <span data-ttu-id="432a8-119">Varsayılan değer 0'dır, bu <xref:System.Runtime.Caching.MemoryCache> da sınıfın otomatik boyutlandırma buluşsal larının varsayılan olarak kullanıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="432a8-119">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="432a8-120">Önbellek yapılandırmasının adı.</span><span class="sxs-lookup"><span data-stu-id="432a8-120">The name of the cache configuration.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="432a8-121">Önbellek tarafından kullanılabilecek fiziksel bellek yüzdesi.</span><span class="sxs-lookup"><span data-stu-id="432a8-121">The percentage of physical memory that can be used by the cache.</span></span> <span data-ttu-id="432a8-122">Varsayılan değer 0'dır, bu <xref:System.Runtime.Caching.MemoryCache> da sınıfın otomatik boyutlandırma buluşsal larının varsayılan olarak kullanıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="432a8-122">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="432a8-123">Önbellek uygulamasının geçerli bellek yükünü önbellek örneği için ayarlanan mutlak ve yüzde tabanlı bellek sınırlarıyla karşılaştırdığı zaman aralığını gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="432a8-123">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="432a8-124">Değer "HH:MM:SS" biçiminde girilir.</span><span class="sxs-lookup"><span data-stu-id="432a8-124">The value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="432a8-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="432a8-125">Child Elements</span></span>  
  
|<span data-ttu-id="432a8-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="432a8-126">Element</span></span>|<span data-ttu-id="432a8-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="432a8-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="432a8-128">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="432a8-128">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="432a8-129">`namedCache` Örnek için yapılandırma ayarları koleksiyonu içerir.</span><span class="sxs-lookup"><span data-stu-id="432a8-129">Contains a collection of configuration settings for the `namedCache` instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="432a8-130">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="432a8-130">Parent Elements</span></span>  
  
|<span data-ttu-id="432a8-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="432a8-131">Element</span></span>|<span data-ttu-id="432a8-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="432a8-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="432a8-133">\<yapılandırma></span><span class="sxs-lookup"><span data-stu-id="432a8-133">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="432a8-134">Ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan her yapılandırma dosyasındaki kök öğeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="432a8-134">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="432a8-135">\<system.runtime.önbelleğe alma></span><span class="sxs-lookup"><span data-stu-id="432a8-135">\<system.runtime.caching></span></span>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="432a8-136">.NET Framework'de yerleşik olan uygulamalarda çıktı önbelleğe alma uygulamanızı sağlayan türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="432a8-136">Contains types that let you implement output caching in applications that are built into the .NET Framework.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="432a8-137">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="432a8-137">Remarks</span></span>  
 <span data-ttu-id="432a8-138">Sınıf <xref:System.Runtime.Caching.MemoryCache> soyut <xref:System.Runtime.Caching.ObjectCache> sınıfın somut bir uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="432a8-138">The <xref:System.Runtime.Caching.MemoryCache> class is a concrete implementation of the abstract <xref:System.Runtime.Caching.ObjectCache> class.</span></span> <span data-ttu-id="432a8-139"><xref:System.Runtime.Caching.MemoryCache> Sınıfın örnekleri, uygulama yapılandırma dosyalarından yapılandırma bilgileriyle birlikte sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="432a8-139">Instances of the <xref:System.Runtime.Caching.MemoryCache> class can be supplied with configuration information from application configuration files.</span></span> <span data-ttu-id="432a8-140">[memoryCache](memorycache-element-cache-settings.md) yapılandırma bölümü `namedCaches` bir yapılandırma koleksiyonu içerir.</span><span class="sxs-lookup"><span data-stu-id="432a8-140">The [memoryCache](memorycache-element-cache-settings.md) configuration section contains a `namedCaches` configuration collection.</span></span>  
  
 <span data-ttu-id="432a8-141">Bellek tabanlı önbellek nesnesi baş harfe döndüğünde, `namedCaches` önce bellek önbelleği oluşturucuya geçirilen parametredeki adla eşleşen bir giriş bulmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="432a8-141">When a memory-based cache object is initialized, it first tries to find a `namedCaches` entry that matches the name in the parameter that is passed to the memory cache constructor.</span></span> <span data-ttu-id="432a8-142">Bir `namedCaches` giriş bulunursa, yoklama ve bellek yönetimi bilgileri yapılandırma dosyasından alınır.</span><span class="sxs-lookup"><span data-stu-id="432a8-142">If a `namedCaches` entry is found, the polling and memory-management information are retrieved from the configuration file.</span></span>  
  
 <span data-ttu-id="432a8-143">Başlatma işlemi daha sonra, yapılandırma bilgilerinin isteğe bağlı topunu kullanarak yapılandırma girdilerinin geçersiz kılınıp geçersiz kılınmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="432a8-143">The initialization process then determines whether any configuration entries were overridden, by using the optional collection of name/value pairs of configuration information in the constructor.</span></span> <span data-ttu-id="432a8-144">Ad/değer çifti koleksiyonunda aşağıdaki değerlerden herhangi birini geçerseniz, bu değerler yapılandırma dosyasından elde edilen bilgileri geçersiz kılar:</span><span class="sxs-lookup"><span data-stu-id="432a8-144">If you pass any one of the following values in the name/value pair collection, these values override information obtained from the configuration file:</span></span>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
- <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## <a name="example"></a><span data-ttu-id="432a8-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="432a8-145">Example</span></span>  
 <span data-ttu-id="432a8-146">Aşağıdaki örnekte, <xref:System.Runtime.Caching.MemoryCache> `name` özniteliği "Varsayılan" olarak ayarlayarak nesnenin adının varsayılan önbellek nesnesi adına nasıl ayarlanılabildiği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="432a8-146">The following example shows how to set the name of the <xref:System.Runtime.Caching.MemoryCache> object to the default cache object name by setting the `name` attribute to "Default".</span></span>  
  
 <span data-ttu-id="432a8-147">Öznitelik `cacheMemoryLimitMegabytes` ve `physicalMemoryLimitPercentage` öznitelik sıfıra ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="432a8-147">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryLimitPercentage` attribute are set to zero.</span></span> <span data-ttu-id="432a8-148">Bu öznitelikleri sıfıra <xref:System.Runtime.Caching.MemoryCache> ayarlamak, otomatik boyutlandırma sezgisellerinin varsayılan olarak kullanıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="432a8-148">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="432a8-149">Önbellek uygulaması, geçerli bellek yükünü her iki dakikada bir mutlak ve yüzde tabanlı bellek sınırlarıyla karşılaştırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="432a8-149">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="432a8-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="432a8-150">See also</span></span>

- <xref:System.Runtime.Caching.MemoryCache>
- [<span data-ttu-id="432a8-151">\<system.runtime.cacching> Öğesi (Önbellek Ayarları)</span><span class="sxs-lookup"><span data-stu-id="432a8-151">\<system.runtime.caching> Element (Cache Settings)</span></span>](system-runtime-caching-element-cache-settings.md)
- [<span data-ttu-id="432a8-152">\<namedCaches> Öğesi (Önbellek Ayarları)</span><span class="sxs-lookup"><span data-stu-id="432a8-152">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
