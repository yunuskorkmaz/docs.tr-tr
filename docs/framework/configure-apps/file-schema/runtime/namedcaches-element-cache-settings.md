---
title: <namedCaches> Öğesi (Önbellek Ayarları)
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: ad76c01bba859934be399d73262bd974309efe98
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192405"
---
# <a name="namedcaches-element-cache-settings"></a><span data-ttu-id="fca04-102">\<namedCaches> Öğesi (Önbellek Ayarları)</span><span class="sxs-lookup"><span data-stu-id="fca04-102">\<namedCaches> Element (Cache Settings)</span></span>

<span data-ttu-id="fca04-103">Adlandırılmış örnekler için yapılandırma ayarları koleksiyonunu belirtir <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="fca04-103">Specifies a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span> <span data-ttu-id="fca04-104"><xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A>Özelliği yapılandırma dosyasının bir veya daha fazla öğesinden yapılandırma ayarları koleksiyonuna başvurur `namedCaches` .</span><span class="sxs-lookup"><span data-stu-id="fca04-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> property references the collection of configuration settings from one or more `namedCaches` elements of the configuration file.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedCaches>**  
  
## <a name="syntax"></a><span data-ttu-id="fca04-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="fca04-105">Syntax</span></span>  
  
```xml  
<namedCaches>  
  <add name="default"/>
</namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="fca04-106">Tür</span><span class="sxs-lookup"><span data-stu-id="fca04-106">Type</span></span>  

 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fca04-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fca04-107">Attributes and Elements</span></span>  

 <span data-ttu-id="fca04-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fca04-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fca04-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fca04-109">Attributes</span></span>  
  
|<span data-ttu-id="fca04-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fca04-110">Attribute</span></span>|<span data-ttu-id="fca04-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fca04-111">Description</span></span>|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|<span data-ttu-id="fca04-112">Bir örneğinin bir örneğinin büyüyebileceği en fazla izin verilen boyutu megabayt cinsinden belirten bir tamsayı değeri <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="fca04-112">An integer value that specifies the maximum allowable size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="fca04-113">Varsayılan değer 0 ' dır. Bu, sınıfının otomatik boyutlandırma buluşsal yöntemleri <xref:System.Runtime.Caching.MemoryCache> Varsayılan olarak kullanıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="fca04-113">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`name`|<span data-ttu-id="fca04-114">Önbelleğin adı.</span><span class="sxs-lookup"><span data-stu-id="fca04-114">The name of the cache.</span></span>|  
|`physicalMemoryLimitPercentage`|<span data-ttu-id="fca04-115">0 ile 100 arasında, önbellek tarafından tüketilen fiziksel olarak yüklenen bilgisayar belleğinin maksimum yüzdesini belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="fca04-115">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="fca04-116">Varsayılan değer 0 ' dır. Bu, sınıfının otomatik boyutlandırma buluşsal yöntemleri <xref:System.Runtime.Caching.MemoryCache> Varsayılan olarak kullanıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="fca04-116">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`pollingInterval`|<span data-ttu-id="fca04-117">Önbellek uygulamasının geçerli bellek yükünü, önbellek örneği için ayarlanan mutlak ve yüzde tabanlı bellek sınırlarına göre karşılaştıran zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="fca04-117">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="fca04-118">Bu değer "HH: MM: SS" biçiminde girilir.</span><span class="sxs-lookup"><span data-stu-id="fca04-118">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fca04-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fca04-119">Child Elements</span></span>  
  
|<span data-ttu-id="fca04-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="fca04-120">Element</span></span>|<span data-ttu-id="fca04-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fca04-121">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-namedcaches.md)|<span data-ttu-id="fca04-122">`namedCaches`Bir bellek önbelleği için koleksiyona adlandırılmış bir önbellek ekler.</span><span class="sxs-lookup"><span data-stu-id="fca04-122">Adds a named cache to the `namedCaches` collection for a memory cache.</span></span>|  
|[\<clear>](clear-element-for-namedcaches.md)|<span data-ttu-id="fca04-123">`namedCaches`Bir bellek önbelleğinin koleksiyonunu temizler.</span><span class="sxs-lookup"><span data-stu-id="fca04-123">Clears the `namedCaches` collection for a memory cache.</span></span>|  
|[\<remove>](remove-element-for-namedcaches.md)|<span data-ttu-id="fca04-124">`namedCaches`Bir bellek önbelleği için koleksiyondan adlandırılmış bir önbellek girdisini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="fca04-124">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fca04-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fca04-125">Parent Elements</span></span>  
  
|<span data-ttu-id="fca04-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="fca04-126">Element</span></span>|<span data-ttu-id="fca04-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fca04-127">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="fca04-128">Ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan her yapılandırma dosyasında kök öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fca04-128">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[\<memoryCache>](memorycache-element-cache-settings.md)|<span data-ttu-id="fca04-129">Sınıfına dayalı bir önbelleği yapılandırmak için kullanılan bir öğesi tanımlar <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="fca04-129">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="fca04-130">.NET Framework yerleşik uygulamalarda çıktı önbelleği uygulamanıza olanak sağlayan türler içerir.</span><span class="sxs-lookup"><span data-stu-id="fca04-130">Contains types that let you implement output caching in applications that are built into the .NET Framework.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fca04-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fca04-131">Remarks</span></span>  

 <span data-ttu-id="fca04-132">Web.config dosyanın bellek önbelleği yapılandırması bölümü `add` `remove` `clear` koleksiyon için, ve özniteliklerini içerebilir `namedCaches` .</span><span class="sxs-lookup"><span data-stu-id="fca04-132">The memory cache configuration section of the Web.config file can contain `add`, `remove`, and `clear` attributes for the `namedCaches` collection.</span></span> <span data-ttu-id="fca04-133">Her `namedCaches` giriş, öznitelik tarafından benzersiz şekilde tanımlanır `name` .</span><span class="sxs-lookup"><span data-stu-id="fca04-133">Each `namedCaches` entry is uniquely identified by the `name` attribute.</span></span>  
  
 <span data-ttu-id="fca04-134">Uygulama yapılandırma dosyalarındaki bilgilere başvurarak bellek önbelleği girdilerinin örneklerini alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fca04-134">You can retrieve instances of memory cache entries by referencing the information in the application configuration files.</span></span> <span data-ttu-id="fca04-135">Varsayılan olarak, yalnızca varsayılan önbellek örneğinin yapılandırma dosyasında bir girişi vardır.</span><span class="sxs-lookup"><span data-stu-id="fca04-135">By default, only the default cache instance has an entry in the configuration file.</span></span> <span data-ttu-id="fca04-136">Varsayılan önbellek örneği özelliğinden döndürülen örneğidir <xref:System.Runtime.Caching.MemoryCache.Default%2A> .</span><span class="sxs-lookup"><span data-stu-id="fca04-136">The default cache instance is the instance that is returned from the <xref:System.Runtime.Caching.MemoryCache.Default%2A> property.</span></span>  
  
 <span data-ttu-id="fca04-137">Name özniteliğini "default" olarak ayarlarsanız, öğesi varsayılan bellek önbelleği örneğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="fca04-137">If you set the name attribute to "default", the element uses the default memory cache instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fca04-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="fca04-138">Example</span></span>  

 <span data-ttu-id="fca04-139">Aşağıdaki örnek, `name` özniteliğini "default" olarak ayarlayarak önbelleğin adının varsayılan önbellek girişi adına nasıl ayarlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fca04-139">The following example shows how to set the name of the cache to the default cache entry name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="fca04-140">`cacheMemoryLimitMegabytes`Özniteliği ve `physicalMemoryPercentage` özniteliği sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="fca04-140">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="fca04-141">Bu özniteliklerin sıfıra ayarlanması, sınıfının otomatik boyutlandırma buluşsal yöntemleri 'nin kullanıldığı anlamına gelir <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="fca04-141">Setting these attributes to zero means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used.</span></span> <span data-ttu-id="fca04-142">Önbellek uygulamasının her iki dakikada bir mutlak ve yüzde tabanlı bellek sınırlarına göre geçerli bellek yükünü karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="fca04-142">The cache implementation compares the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fca04-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fca04-143">See also</span></span>

- [<span data-ttu-id="fca04-144">\<memoryCache> Öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="fca04-144">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
