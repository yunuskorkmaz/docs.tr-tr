---
title: <memoryCache> Öğesi (Önbellek Ayarları)
ms.date: 03/30/2017
helpviewer_keywords:
- <memoryCache> element
- caching [.NET Framework], configuration
- memoryCache element
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
ms.openlocfilehash: 14480682c5d221216df5da3844897855d1d92a0d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192431"
---
# <a name="memorycache-element-cache-settings"></a><span data-ttu-id="5aa1b-102">\<memoryCache> Öğesi (Önbellek Ayarları)</span><span class="sxs-lookup"><span data-stu-id="5aa1b-102">\<memoryCache> Element (Cache Settings)</span></span>

<span data-ttu-id="5aa1b-103">Sınıfına dayalı bir önbelleği yapılandırmak için kullanılan bir öğesi tanımlar <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="5aa1b-103">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="5aa1b-104"><xref:System.Runtime.Caching.Configuration.MemoryCacheElement>Sınıfı, önbelleği yapılandırmak için kullanabileceğiniz bir [MemoryCache](memorycache-element-cache-settings.md) öğesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5aa1b-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> class defines a [memoryCache](memorycache-element-cache-settings.md) element that you can use to configure the cache.</span></span> <span data-ttu-id="5aa1b-105">Sınıfın birden çok örneği <xref:System.Runtime.Caching.MemoryCache> tek bir uygulamada kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5aa1b-105">Multiple instances of the <xref:System.Runtime.Caching.MemoryCache> class can be used in a single application.</span></span> <span data-ttu-id="5aa1b-106">`memoryCache`Yapılandırma dosyasındaki her öğe, adlandırılmış bir örnek için ayarları içerebilir <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="5aa1b-106">Each `memoryCache` element in the configuration file can contain settings for a named <xref:System.Runtime.Caching.MemoryCache> instance.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<memoryCache>**  
  
## <a name="syntax"></a><span data-ttu-id="5aa1b-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="5aa1b-107">Syntax</span></span>  
  
```xml  
<memoryCache>
    <namedCaches>  
        <!-- child elements -->  
    </namedCaches>
</memoryCache>  
```  
  
## <a name="type"></a><span data-ttu-id="5aa1b-108">Tür</span><span class="sxs-lookup"><span data-stu-id="5aa1b-108">Type</span></span>  

 <span data-ttu-id="5aa1b-109"><xref:System.Runtime.Caching.MemoryCache> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5aa1b-109"><xref:System.Runtime.Caching.MemoryCache> class.</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5aa1b-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5aa1b-110">Attributes and Elements</span></span>  

 <span data-ttu-id="5aa1b-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5aa1b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5aa1b-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5aa1b-112">Attributes</span></span>  
  
|<span data-ttu-id="5aa1b-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5aa1b-113">Attribute</span></span>|<span data-ttu-id="5aa1b-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5aa1b-114">Description</span></span>|  
|---------------|-----------------|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="5aa1b-115">Bir nesne örneğinin büyüyebileceği maksimum bellek boyutu (megabayt cinsinden) <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="5aa1b-115">The maximum memory size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> object can grow to.</span></span> <span data-ttu-id="5aa1b-116">Varsayılan değer 0 ' dır. Bu, <xref:System.Runtime.Caching.MemoryCache> sınıfın AutoSize buluşsal yöntemleri varsayılan olarak kullanıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5aa1b-116">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="5aa1b-117">Önbellek yapılandırmasının adı.</span><span class="sxs-lookup"><span data-stu-id="5aa1b-117">The name of the cache configuration.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="5aa1b-118">Önbellek tarafından kullanılabilen fiziksel bellek yüzdesi.</span><span class="sxs-lookup"><span data-stu-id="5aa1b-118">The percentage of physical memory that can be used by the cache.</span></span> <span data-ttu-id="5aa1b-119">Varsayılan değer 0 ' dır. Bu, <xref:System.Runtime.Caching.MemoryCache> sınıfın AutoSize buluşsal yöntemleri varsayılan olarak kullanıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5aa1b-119">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="5aa1b-120">Önbellek uygulamasının geçerli bellek yükünü, önbellek örneği için ayarlanan mutlak ve yüzde tabanlı bellek sınırlarına göre karşılaştıran zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="5aa1b-120">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="5aa1b-121">Değer "HH: MM: SS" biçiminde girilir.</span><span class="sxs-lookup"><span data-stu-id="5aa1b-121">The value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5aa1b-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5aa1b-122">Child Elements</span></span>  
  
|<span data-ttu-id="5aa1b-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="5aa1b-123">Element</span></span>|<span data-ttu-id="5aa1b-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5aa1b-124">Description</span></span>|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="5aa1b-125">Örnek için yapılandırma ayarlarının bir koleksiyonunu içerir `namedCache` .</span><span class="sxs-lookup"><span data-stu-id="5aa1b-125">Contains a collection of configuration settings for the `namedCache` instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5aa1b-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5aa1b-126">Parent Elements</span></span>  
  
|<span data-ttu-id="5aa1b-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="5aa1b-127">Element</span></span>|<span data-ttu-id="5aa1b-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5aa1b-128">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="5aa1b-129">Ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan her yapılandırma dosyasında kök öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5aa1b-129">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="5aa1b-130">.NET Framework yerleşik uygulamalarda çıktı önbelleği uygulamanıza olanak sağlayan türler içerir.</span><span class="sxs-lookup"><span data-stu-id="5aa1b-130">Contains types that let you implement output caching in applications that are built into the .NET Framework.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5aa1b-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5aa1b-131">Remarks</span></span>  

 <span data-ttu-id="5aa1b-132"><xref:System.Runtime.Caching.MemoryCache>Sınıf, soyut sınıfın somut bir uygulamasıdır <xref:System.Runtime.Caching.ObjectCache> .</span><span class="sxs-lookup"><span data-stu-id="5aa1b-132">The <xref:System.Runtime.Caching.MemoryCache> class is a concrete implementation of the abstract <xref:System.Runtime.Caching.ObjectCache> class.</span></span> <span data-ttu-id="5aa1b-133">Sınıf örnekleri, <xref:System.Runtime.Caching.MemoryCache> uygulama yapılandırma dosyalarından yapılandırma bilgileriyle sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="5aa1b-133">Instances of the <xref:System.Runtime.Caching.MemoryCache> class can be supplied with configuration information from application configuration files.</span></span> <span data-ttu-id="5aa1b-134">[MemoryCache](memorycache-element-cache-settings.md) yapılandırma bölümü bir `namedCaches` yapılandırma koleksiyonu içerir.</span><span class="sxs-lookup"><span data-stu-id="5aa1b-134">The [memoryCache](memorycache-element-cache-settings.md) configuration section contains a `namedCaches` configuration collection.</span></span>  
  
 <span data-ttu-id="5aa1b-135">Bellek tabanlı önbellek nesnesi başlatıldığında, önce `namedCaches` bellek önbelleği oluşturucusuna geçirilen parametresindeki adla eşleşen bir giriş bulmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="5aa1b-135">When a memory-based cache object is initialized, it first tries to find a `namedCaches` entry that matches the name in the parameter that is passed to the memory cache constructor.</span></span> <span data-ttu-id="5aa1b-136">Bir `namedCaches` giriş bulunursa, yoklama ve bellek yönetimi bilgileri yapılandırma dosyasından alınır.</span><span class="sxs-lookup"><span data-stu-id="5aa1b-136">If a `namedCaches` entry is found, the polling and memory-management information are retrieved from the configuration file.</span></span>  
  
 <span data-ttu-id="5aa1b-137">Başlatma işlemi daha sonra, kurucudaki yapılandırma bilgileri için isteğe bağlı ad/değer çiftleri koleksiyonu kullanılarak herhangi bir yapılandırma girişinin geçersiz kılınıp kılınmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="5aa1b-137">The initialization process then determines whether any configuration entries were overridden, by using the optional collection of name/value pairs of configuration information in the constructor.</span></span> <span data-ttu-id="5aa1b-138">Ad/değer çifti koleksiyonunda aşağıdaki değerlerden birini geçirirseniz, bu değerler yapılandırma dosyasından elde edilen bilgileri geçersiz kılar:</span><span class="sxs-lookup"><span data-stu-id="5aa1b-138">If you pass any one of the following values in the name/value pair collection, these values override information obtained from the configuration file:</span></span>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
- <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## <a name="example"></a><span data-ttu-id="5aa1b-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="5aa1b-139">Example</span></span>  

 <span data-ttu-id="5aa1b-140">Aşağıdaki örnek, <xref:System.Runtime.Caching.MemoryCache> `name` özniteliğini "default" olarak ayarlayarak nesnenin adının varsayılan önbellek nesnesi adına nasıl ayarlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5aa1b-140">The following example shows how to set the name of the <xref:System.Runtime.Caching.MemoryCache> object to the default cache object name by setting the `name` attribute to "Default".</span></span>  
  
 <span data-ttu-id="5aa1b-141">`cacheMemoryLimitMegabytes`Özniteliği ve `physicalMemoryLimitPercentage` özniteliği sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="5aa1b-141">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryLimitPercentage` attribute are set to zero.</span></span> <span data-ttu-id="5aa1b-142">Bu özniteliklerin sıfıra ayarlanması, <xref:System.Runtime.Caching.MemoryCache> otomatik boyutlandırma buluşsal yöntemleri varsayılan olarak kullanıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5aa1b-142">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="5aa1b-143">Önbellek uygulamasının her iki dakikada bir, geçerli bellek yükünü mutlak ve yüzde tabanlı bellek sınırlarına göre karşılaştırması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5aa1b-143">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5aa1b-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5aa1b-144">See also</span></span>

- <xref:System.Runtime.Caching.MemoryCache>
- [<span data-ttu-id="5aa1b-145">\<system.runtime.caching> Öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="5aa1b-145">\<system.runtime.caching> Element (Cache Settings)</span></span>](system-runtime-caching-element-cache-settings.md)
- [<span data-ttu-id="5aa1b-146">\<namedCaches> Öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="5aa1b-146">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
