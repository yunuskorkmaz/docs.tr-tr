---
title: <namedCaches> Öğesi (Önbellek Ayarları)
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: 4587234ad91fa3b1abbb376bd7ae517d5abea6c3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252457"
---
# <a name="namedcaches-element-cache-settings"></a><span data-ttu-id="7cdda-102">\<Namedönbellekler > öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="7cdda-102">\<namedCaches> Element (Cache Settings)</span></span>
<span data-ttu-id="7cdda-103">Adlandırılmış <xref:System.Runtime.Caching.MemoryCache> örnekler için yapılandırma ayarları koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="7cdda-103">Specifies a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span> <span data-ttu-id="7cdda-104">Özelliği yapılandırma dosyasının bir veya daha fazla `namedCaches` öğesinden yapılandırma ayarları koleksiyonuna başvurur. <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A></span><span class="sxs-lookup"><span data-stu-id="7cdda-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> property references the collection of configuration settings from one or more `namedCaches` elements of the configuration file.</span></span>  
  
<span data-ttu-id="7cdda-105">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7cdda-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7cdda-106">&nbsp;&nbsp;[ **\<System. Runtime. Caching >** ](system-runtime-caching-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="7cdda-106">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span></span>\
<span data-ttu-id="7cdda-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<memoryCache >** ](memorycache-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="7cdda-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)</span></span>\
<span data-ttu-id="7cdda-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Namedönbellekler >**</span><span class="sxs-lookup"><span data-stu-id="7cdda-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedCaches>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cdda-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7cdda-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
  <add name="default"/>   
</namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="7cdda-110">Tür</span><span class="sxs-lookup"><span data-stu-id="7cdda-110">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7cdda-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7cdda-111">Attributes and Elements</span></span>  
 <span data-ttu-id="7cdda-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7cdda-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7cdda-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7cdda-113">Attributes</span></span>  
  
|<span data-ttu-id="7cdda-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7cdda-114">Attribute</span></span>|<span data-ttu-id="7cdda-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7cdda-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|<span data-ttu-id="7cdda-116">Bir örneğinin bir <xref:System.Runtime.Caching.MemoryCache> örneğinin büyüyebileceği en fazla izin verilen boyutu megabayt cinsinden belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="7cdda-116">An integer value that specifies the maximum allowable size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="7cdda-117">Varsayılan değer 0 ' dır. Bu, <xref:System.Runtime.Caching.MemoryCache> sınıfının otomatik boyutlandırma buluşsal yöntemleri varsayılan olarak kullanıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="7cdda-117">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`name`|<span data-ttu-id="7cdda-118">Önbelleğin adı.</span><span class="sxs-lookup"><span data-stu-id="7cdda-118">The name of the cache.</span></span>|  
|`physicalMemoryLimitPercentage`|<span data-ttu-id="7cdda-119">0 ile 100 arasında, önbellek tarafından tüketilen fiziksel olarak yüklenen bilgisayar belleğinin maksimum yüzdesini belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="7cdda-119">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="7cdda-120">Varsayılan değer 0 ' dır. Bu, <xref:System.Runtime.Caching.MemoryCache> sınıfının otomatik boyutlandırma buluşsal yöntemleri varsayılan olarak kullanıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="7cdda-120">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`pollingInterval`|<span data-ttu-id="7cdda-121">Önbellek uygulamasının geçerli bellek yükünü, önbellek örneği için ayarlanan mutlak ve yüzde tabanlı bellek sınırlarına göre karşılaştıran zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="7cdda-121">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="7cdda-122">Bu değer "HH: MM: SS" biçiminde girilir.</span><span class="sxs-lookup"><span data-stu-id="7cdda-122">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7cdda-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7cdda-123">Child Elements</span></span>  
  
|<span data-ttu-id="7cdda-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="7cdda-124">Element</span></span>|<span data-ttu-id="7cdda-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7cdda-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7cdda-126">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="7cdda-126">\<add></span></span>](add-element-for-namedcaches.md)|<span data-ttu-id="7cdda-127">Bir bellek önbelleği için `namedCaches` koleksiyona adlandırılmış bir önbellek ekler.</span><span class="sxs-lookup"><span data-stu-id="7cdda-127">Adds a named cache to the `namedCaches` collection for a memory cache.</span></span>|  
|[<span data-ttu-id="7cdda-128">\<> Temizle</span><span class="sxs-lookup"><span data-stu-id="7cdda-128">\<clear></span></span>](clear-element-for-namedcaches.md)|<span data-ttu-id="7cdda-129">Bir bellek önbelleğinin koleksiyonunu temizler. `namedCaches`</span><span class="sxs-lookup"><span data-stu-id="7cdda-129">Clears the `namedCaches` collection for a memory cache.</span></span>|  
|[<span data-ttu-id="7cdda-130">\<> Kaldır</span><span class="sxs-lookup"><span data-stu-id="7cdda-130">\<remove></span></span>](remove-element-for-namedcaches.md)|<span data-ttu-id="7cdda-131">Bir bellek önbelleği için `namedCaches` koleksiyondan adlandırılmış bir önbellek girdisini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="7cdda-131">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7cdda-132">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7cdda-132">Parent Elements</span></span>  
  
|<span data-ttu-id="7cdda-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="7cdda-133">Element</span></span>|<span data-ttu-id="7cdda-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7cdda-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7cdda-135">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="7cdda-135">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="7cdda-136">Ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan her yapılandırma dosyasında kök öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7cdda-136">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="7cdda-137">\<memoryCache ></span><span class="sxs-lookup"><span data-stu-id="7cdda-137">\<memoryCache></span></span>](memorycache-element-cache-settings.md)|<span data-ttu-id="7cdda-138"><xref:System.Runtime.Caching.MemoryCache> Sınıfına dayalı bir önbelleği yapılandırmak için kullanılan bir öğesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7cdda-138">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
|[<span data-ttu-id="7cdda-139">\<System. Runtime. Caching ></span><span class="sxs-lookup"><span data-stu-id="7cdda-139">\<system.runtime.caching></span></span>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="7cdda-140">.NET Framework yerleşik uygulamalarda çıktı önbelleği uygulamanıza olanak sağlayan türler içerir.</span><span class="sxs-lookup"><span data-stu-id="7cdda-140">Contains types that let you implement output caching in applications that are built into the .NET Framework.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7cdda-141">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7cdda-141">Remarks</span></span>  
 <span data-ttu-id="7cdda-142">Web. config dosyasının bellek önbelleği `add`yapılandırması bölümü `namedCaches` koleksiyon için, `remove`ve `clear` özniteliklerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="7cdda-142">The memory cache configuration section of the Web.config file can contain `add`, `remove`, and `clear` attributes for the `namedCaches` collection.</span></span> <span data-ttu-id="7cdda-143">Her `namedCaches` giriş, `name` öznitelik tarafından benzersiz şekilde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="7cdda-143">Each `namedCaches` entry is uniquely identified by the `name` attribute.</span></span>  
  
 <span data-ttu-id="7cdda-144">Uygulama yapılandırma dosyalarındaki bilgilere başvurarak bellek önbelleği girdilerinin örneklerini alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7cdda-144">You can retrieve instances of memory cache entries by referencing the information in the application configuration files.</span></span> <span data-ttu-id="7cdda-145">Varsayılan olarak, yalnızca varsayılan önbellek örneğinin yapılandırma dosyasında bir girişi vardır.</span><span class="sxs-lookup"><span data-stu-id="7cdda-145">By default, only the default cache instance has an entry in the configuration file.</span></span> <span data-ttu-id="7cdda-146">Varsayılan önbellek örneği <xref:System.Runtime.Caching.MemoryCache.Default%2A> özelliğinden döndürülen örneğidir.</span><span class="sxs-lookup"><span data-stu-id="7cdda-146">The default cache instance is the instance that is returned from the <xref:System.Runtime.Caching.MemoryCache.Default%2A> property.</span></span>  
  
 <span data-ttu-id="7cdda-147">Name özniteliğini "default" olarak ayarlarsanız, öğesi varsayılan bellek önbelleği örneğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="7cdda-147">If you set the name attribute to "default", the element uses the default memory cache instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7cdda-148">Örnek</span><span class="sxs-lookup"><span data-stu-id="7cdda-148">Example</span></span>  
 <span data-ttu-id="7cdda-149">Aşağıdaki örnek, `name` özniteliğini "default" olarak ayarlayarak önbelleğin adının varsayılan önbellek girişi adına nasıl ayarlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7cdda-149">The following example shows how to set the name of the cache to the default cache entry name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="7cdda-150">`cacheMemoryLimitMegabytes` Özniteliği`physicalMemoryPercentage` ve özniteliği sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="7cdda-150">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="7cdda-151">Bu özniteliklerin sıfıra ayarlanması, <xref:System.Runtime.Caching.MemoryCache> sınıfının otomatik boyutlandırma buluşsal yöntemleri 'nin kullanıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="7cdda-151">Setting these attributes to zero means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used.</span></span> <span data-ttu-id="7cdda-152">Önbellek uygulamasının her iki dakikada bir mutlak ve yüzde tabanlı bellek sınırlarına göre geçerli bellek yükünü karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="7cdda-152">The cache implementation compares the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7cdda-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7cdda-153">See also</span></span>

- [<span data-ttu-id="7cdda-154">\<memoryCache > öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="7cdda-154">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
