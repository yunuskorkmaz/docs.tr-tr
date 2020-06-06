---
title: <namedCaches> Öğesi (Önbellek Ayarları)
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: e0640ca18d386141f3c03135019eb4fe959b5bf8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153964"
---
# <a name="namedcaches-element-cache-settings"></a><span data-ttu-id="52a64-102">\<namedCaches> Öğesi (Önbellek Ayarları)</span><span class="sxs-lookup"><span data-stu-id="52a64-102">\<namedCaches> Element (Cache Settings)</span></span>
<span data-ttu-id="52a64-103">Adlandırılmış örnekler için yapılandırma ayarları koleksiyonunu belirtir <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="52a64-103">Specifies a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span> <span data-ttu-id="52a64-104"><xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A>Özelliği yapılandırma dosyasının bir veya daha fazla öğesinden yapılandırma ayarları koleksiyonuna başvurur `namedCaches` .</span><span class="sxs-lookup"><span data-stu-id="52a64-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> property references the collection of configuration settings from one or more `namedCaches` elements of the configuration file.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedCaches>**  
  
## <a name="syntax"></a><span data-ttu-id="52a64-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="52a64-105">Syntax</span></span>  
  
```xml  
<namedCaches>  
  <add name="default"/>
</namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="52a64-106">Tür</span><span class="sxs-lookup"><span data-stu-id="52a64-106">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="52a64-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="52a64-107">Attributes and Elements</span></span>  
 <span data-ttu-id="52a64-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="52a64-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="52a64-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="52a64-109">Attributes</span></span>  
  
|<span data-ttu-id="52a64-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="52a64-110">Attribute</span></span>|<span data-ttu-id="52a64-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="52a64-111">Description</span></span>|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|<span data-ttu-id="52a64-112">Bir örneğinin bir örneğinin büyüyebileceği en fazla izin verilen boyutu megabayt cinsinden belirten bir tamsayı değeri <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="52a64-112">An integer value that specifies the maximum allowable size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="52a64-113">Varsayılan değer 0 ' dır. Bu, sınıfının otomatik boyutlandırma buluşsal yöntemleri <xref:System.Runtime.Caching.MemoryCache> Varsayılan olarak kullanıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="52a64-113">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`name`|<span data-ttu-id="52a64-114">Önbelleğin adı.</span><span class="sxs-lookup"><span data-stu-id="52a64-114">The name of the cache.</span></span>|  
|`physicalMemoryLimitPercentage`|<span data-ttu-id="52a64-115">0 ile 100 arasında, önbellek tarafından tüketilen fiziksel olarak yüklenen bilgisayar belleğinin maksimum yüzdesini belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="52a64-115">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="52a64-116">Varsayılan değer 0 ' dır. Bu, sınıfının otomatik boyutlandırma buluşsal yöntemleri <xref:System.Runtime.Caching.MemoryCache> Varsayılan olarak kullanıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="52a64-116">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`pollingInterval`|<span data-ttu-id="52a64-117">Önbellek uygulamasının geçerli bellek yükünü, önbellek örneği için ayarlanan mutlak ve yüzde tabanlı bellek sınırlarına göre karşılaştıran zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="52a64-117">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="52a64-118">Bu değer "HH: MM: SS" biçiminde girilir.</span><span class="sxs-lookup"><span data-stu-id="52a64-118">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="52a64-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="52a64-119">Child Elements</span></span>  
  
|<span data-ttu-id="52a64-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="52a64-120">Element</span></span>|<span data-ttu-id="52a64-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="52a64-121">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-namedcaches.md)|<span data-ttu-id="52a64-122">`namedCaches`Bir bellek önbelleği için koleksiyona adlandırılmış bir önbellek ekler.</span><span class="sxs-lookup"><span data-stu-id="52a64-122">Adds a named cache to the `namedCaches` collection for a memory cache.</span></span>|  
|[\<clear>](clear-element-for-namedcaches.md)|<span data-ttu-id="52a64-123">`namedCaches`Bir bellek önbelleğinin koleksiyonunu temizler.</span><span class="sxs-lookup"><span data-stu-id="52a64-123">Clears the `namedCaches` collection for a memory cache.</span></span>|  
|[\<remove>](remove-element-for-namedcaches.md)|<span data-ttu-id="52a64-124">`namedCaches`Bir bellek önbelleği için koleksiyondan adlandırılmış bir önbellek girdisini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="52a64-124">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="52a64-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="52a64-125">Parent Elements</span></span>  
  
|<span data-ttu-id="52a64-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="52a64-126">Element</span></span>|<span data-ttu-id="52a64-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="52a64-127">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="52a64-128">Ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan her yapılandırma dosyasında kök öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="52a64-128">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[\<memoryCache>](memorycache-element-cache-settings.md)|<span data-ttu-id="52a64-129">Sınıfına dayalı bir önbelleği yapılandırmak için kullanılan bir öğesi tanımlar <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="52a64-129">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="52a64-130">.NET Framework yerleşik uygulamalarda çıktı önbelleği uygulamanıza olanak sağlayan türler içerir.</span><span class="sxs-lookup"><span data-stu-id="52a64-130">Contains types that let you implement output caching in applications that are built into the .NET Framework.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52a64-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="52a64-131">Remarks</span></span>  
 <span data-ttu-id="52a64-132">Web. config dosyasının bellek önbelleği yapılandırması bölümü `add` `remove` `clear` koleksiyon için, ve özniteliklerini içerebilir `namedCaches` .</span><span class="sxs-lookup"><span data-stu-id="52a64-132">The memory cache configuration section of the Web.config file can contain `add`, `remove`, and `clear` attributes for the `namedCaches` collection.</span></span> <span data-ttu-id="52a64-133">Her `namedCaches` giriş, öznitelik tarafından benzersiz şekilde tanımlanır `name` .</span><span class="sxs-lookup"><span data-stu-id="52a64-133">Each `namedCaches` entry is uniquely identified by the `name` attribute.</span></span>  
  
 <span data-ttu-id="52a64-134">Uygulama yapılandırma dosyalarındaki bilgilere başvurarak bellek önbelleği girdilerinin örneklerini alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52a64-134">You can retrieve instances of memory cache entries by referencing the information in the application configuration files.</span></span> <span data-ttu-id="52a64-135">Varsayılan olarak, yalnızca varsayılan önbellek örneğinin yapılandırma dosyasında bir girişi vardır.</span><span class="sxs-lookup"><span data-stu-id="52a64-135">By default, only the default cache instance has an entry in the configuration file.</span></span> <span data-ttu-id="52a64-136">Varsayılan önbellek örneği özelliğinden döndürülen örneğidir <xref:System.Runtime.Caching.MemoryCache.Default%2A> .</span><span class="sxs-lookup"><span data-stu-id="52a64-136">The default cache instance is the instance that is returned from the <xref:System.Runtime.Caching.MemoryCache.Default%2A> property.</span></span>  
  
 <span data-ttu-id="52a64-137">Name özniteliğini "default" olarak ayarlarsanız, öğesi varsayılan bellek önbelleği örneğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="52a64-137">If you set the name attribute to "default", the element uses the default memory cache instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52a64-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="52a64-138">Example</span></span>  
 <span data-ttu-id="52a64-139">Aşağıdaki örnek, `name` özniteliğini "default" olarak ayarlayarak önbelleğin adının varsayılan önbellek girişi adına nasıl ayarlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="52a64-139">The following example shows how to set the name of the cache to the default cache entry name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="52a64-140">`cacheMemoryLimitMegabytes`Özniteliği ve `physicalMemoryPercentage` özniteliği sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="52a64-140">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="52a64-141">Bu özniteliklerin sıfıra ayarlanması, sınıfının otomatik boyutlandırma buluşsal yöntemleri 'nin kullanıldığı anlamına gelir <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="52a64-141">Setting these attributes to zero means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used.</span></span> <span data-ttu-id="52a64-142">Önbellek uygulamasının her iki dakikada bir mutlak ve yüzde tabanlı bellek sınırlarına göre geçerli bellek yükünü karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="52a64-142">The cache implementation compares the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="52a64-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52a64-143">See also</span></span>

- [<span data-ttu-id="52a64-144">\<memoryCache>Öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="52a64-144">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
