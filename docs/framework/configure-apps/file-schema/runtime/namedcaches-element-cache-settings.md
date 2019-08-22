---
title: <namedCaches> Öğesi (Önbellek Ayarları)
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: 9cedd462aa539745ddab844dff158912914cb024
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663574"
---
# <a name="namedcaches-element-cache-settings"></a><span data-ttu-id="fb72a-102">\<Namedönbellekler > öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="fb72a-102">\<namedCaches> Element (Cache Settings)</span></span>
<span data-ttu-id="fb72a-103">Adlandırılmış <xref:System.Runtime.Caching.MemoryCache> örnekler için yapılandırma ayarları koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="fb72a-103">Specifies a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span> <span data-ttu-id="fb72a-104">Özelliği yapılandırma dosyasının bir veya daha fazla `namedCaches` öğesinden yapılandırma ayarları koleksiyonuna başvurur. <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A></span><span class="sxs-lookup"><span data-stu-id="fb72a-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> property references the collection of configuration settings from one or more `namedCaches` elements of the configuration file.</span></span>  
  
 <span data-ttu-id="fb72a-105">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="fb72a-105">\<configuration></span></span>  
<span data-ttu-id="fb72a-106">\<System. Runtime. Caching ></span><span class="sxs-lookup"><span data-stu-id="fb72a-106">\< system.runtime.caching></span></span>  
<span data-ttu-id="fb72a-107">\<memoryCache ></span><span class="sxs-lookup"><span data-stu-id="fb72a-107">\<memoryCache></span></span>  
<span data-ttu-id="fb72a-108">\<Namedönbellekler ></span><span class="sxs-lookup"><span data-stu-id="fb72a-108">\<namedCaches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb72a-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fb72a-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
  <add name="default"/>   
</namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="fb72a-110">Tür</span><span class="sxs-lookup"><span data-stu-id="fb72a-110">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fb72a-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fb72a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="fb72a-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fb72a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fb72a-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fb72a-113">Attributes</span></span>  
  
|<span data-ttu-id="fb72a-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fb72a-114">Attribute</span></span>|<span data-ttu-id="fb72a-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fb72a-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|<span data-ttu-id="fb72a-116">Bir örneğinin bir <xref:System.Runtime.Caching.MemoryCache> örneğinin büyüyebileceği en fazla izin verilen boyutu megabayt cinsinden belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="fb72a-116">An integer value that specifies the maximum allowable size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="fb72a-117">Varsayılan değer 0 ' dır. Bu, <xref:System.Runtime.Caching.MemoryCache> sınıfının otomatik boyutlandırma buluşsal yöntemleri varsayılan olarak kullanıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="fb72a-117">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`name`|<span data-ttu-id="fb72a-118">Önbelleğin adı.</span><span class="sxs-lookup"><span data-stu-id="fb72a-118">The name of the cache.</span></span>|  
|`physicalMemoryLimitPercentage`|<span data-ttu-id="fb72a-119">0 ile 100 arasında, önbellek tarafından tüketilen fiziksel olarak yüklenen bilgisayar belleğinin maksimum yüzdesini belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="fb72a-119">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="fb72a-120">Varsayılan değer 0 ' dır. Bu, <xref:System.Runtime.Caching.MemoryCache> sınıfının otomatik boyutlandırma buluşsal yöntemleri varsayılan olarak kullanıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="fb72a-120">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`pollingInterval`|<span data-ttu-id="fb72a-121">Önbellek uygulamasının geçerli bellek yükünü, önbellek örneği için ayarlanan mutlak ve yüzde tabanlı bellek sınırlarına göre karşılaştıran zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="fb72a-121">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="fb72a-122">Bu değer "HH: MM: SS" biçiminde girilir.</span><span class="sxs-lookup"><span data-stu-id="fb72a-122">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fb72a-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fb72a-123">Child Elements</span></span>  
  
|<span data-ttu-id="fb72a-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="fb72a-124">Element</span></span>|<span data-ttu-id="fb72a-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fb72a-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fb72a-126">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="fb72a-126">\<add></span></span>](add-element-for-namedcaches.md)|<span data-ttu-id="fb72a-127">Bir bellek önbelleği için `namedCaches` koleksiyona adlandırılmış bir önbellek ekler.</span><span class="sxs-lookup"><span data-stu-id="fb72a-127">Adds a named cache to the `namedCaches` collection for a memory cache.</span></span>|  
|[<span data-ttu-id="fb72a-128">\<> Temizle</span><span class="sxs-lookup"><span data-stu-id="fb72a-128">\<clear></span></span>](clear-element-for-namedcaches.md)|<span data-ttu-id="fb72a-129">Bir bellek önbelleğinin koleksiyonunu temizler. `namedCaches`</span><span class="sxs-lookup"><span data-stu-id="fb72a-129">Clears the `namedCaches` collection for a memory cache.</span></span>|  
|[<span data-ttu-id="fb72a-130">\<> Kaldır</span><span class="sxs-lookup"><span data-stu-id="fb72a-130">\<remove></span></span>](remove-element-for-namedcaches.md)|<span data-ttu-id="fb72a-131">Bir bellek önbelleği için `namedCaches` koleksiyondan adlandırılmış bir önbellek girdisini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="fb72a-131">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fb72a-132">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fb72a-132">Parent Elements</span></span>  
  
|<span data-ttu-id="fb72a-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="fb72a-133">Element</span></span>|<span data-ttu-id="fb72a-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fb72a-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fb72a-135">\<memoryCache ></span><span class="sxs-lookup"><span data-stu-id="fb72a-135">\<memoryCache></span></span>](memorycache-element-cache-settings.md)|<span data-ttu-id="fb72a-136"><xref:System.Runtime.Caching.MemoryCache> Sınıfına dayalı bir önbelleği yapılandırmak için kullanılan bir öğesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fb72a-136">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb72a-137">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fb72a-137">Remarks</span></span>  
 <span data-ttu-id="fb72a-138">Web. config dosyasının bellek önbelleği `add`yapılandırması bölümü `namedCaches` koleksiyon için, `remove`ve `clear` özniteliklerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="fb72a-138">The memory cache configuration section of the Web.config file can contain `add`, `remove`, and `clear` attributes for the `namedCaches` collection.</span></span> <span data-ttu-id="fb72a-139">Her `namedCaches` giriş, `name` öznitelik tarafından benzersiz şekilde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="fb72a-139">Each `namedCaches` entry is uniquely identified by the `name` attribute.</span></span>  
  
 <span data-ttu-id="fb72a-140">Uygulama yapılandırma dosyalarındaki bilgilere başvurarak bellek önbelleği girdilerinin örneklerini alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fb72a-140">You can retrieve instances of memory cache entries by referencing the information in the application configuration files.</span></span> <span data-ttu-id="fb72a-141">Varsayılan olarak, yalnızca varsayılan önbellek örneğinin yapılandırma dosyasında bir girişi vardır.</span><span class="sxs-lookup"><span data-stu-id="fb72a-141">By default, only the default cache instance has an entry in the configuration file.</span></span> <span data-ttu-id="fb72a-142">Varsayılan önbellek örneği <xref:System.Runtime.Caching.MemoryCache.Default%2A> özelliğinden döndürülen örneğidir.</span><span class="sxs-lookup"><span data-stu-id="fb72a-142">The default cache instance is the instance that is returned from the <xref:System.Runtime.Caching.MemoryCache.Default%2A> property.</span></span>  
  
 <span data-ttu-id="fb72a-143">Name özniteliğini "default" olarak ayarlarsanız, öğesi varsayılan bellek önbelleği örneğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="fb72a-143">If you set the name attribute to "default", the element uses the default memory cache instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb72a-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="fb72a-144">Example</span></span>  
 <span data-ttu-id="fb72a-145">Aşağıdaki örnek, `name` özniteliğini "default" olarak ayarlayarak önbelleğin adının varsayılan önbellek girişi adına nasıl ayarlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fb72a-145">The following example shows how to set the name of the cache to the default cache entry name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="fb72a-146">`cacheMemoryLimitMegabytes` Özniteliği`physicalMemoryPercentage` ve özniteliği sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="fb72a-146">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="fb72a-147">Bu özniteliklerin sıfıra ayarlanması, <xref:System.Runtime.Caching.MemoryCache> sınıfının otomatik boyutlandırma buluşsal yöntemleri 'nin kullanıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="fb72a-147">Setting these attributes to zero means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used.</span></span> <span data-ttu-id="fb72a-148">Önbellek uygulamasının her iki dakikada bir mutlak ve yüzde tabanlı bellek sınırlarına göre geçerli bellek yükünü karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="fb72a-148">The cache implementation compares the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fb72a-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb72a-149">See also</span></span>

- [<span data-ttu-id="fb72a-150">\<memoryCache > öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="fb72a-150">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
