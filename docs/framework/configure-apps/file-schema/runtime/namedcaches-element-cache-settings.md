---
description: 'Daha fazla bilgi edinin: <namedCaches> öğesi (önbellek ayarları)'
title: <namedCaches> Öğesi (Önbellek Ayarları)
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: 543650513270c0cee24d965b8efe98a75d7b8f9a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782331"
---
# <a name="namedcaches-element-cache-settings"></a><span data-ttu-id="667de-103">\<namedCaches> Öğesi (Önbellek Ayarları)</span><span class="sxs-lookup"><span data-stu-id="667de-103">\<namedCaches> Element (Cache Settings)</span></span>

<span data-ttu-id="667de-104">Adlandırılmış örnekler için yapılandırma ayarları koleksiyonunu belirtir <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="667de-104">Specifies a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span> <span data-ttu-id="667de-105"><xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A>Özelliği yapılandırma dosyasının bir veya daha fazla öğesinden yapılandırma ayarları koleksiyonuna başvurur `namedCaches` .</span><span class="sxs-lookup"><span data-stu-id="667de-105">The <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> property references the collection of configuration settings from one or more `namedCaches` elements of the configuration file.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedCaches>**  
  
## <a name="syntax"></a><span data-ttu-id="667de-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="667de-106">Syntax</span></span>  
  
```xml  
<namedCaches>  
  <add name="default"/>
</namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="667de-107">Tür</span><span class="sxs-lookup"><span data-stu-id="667de-107">Type</span></span>  

 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="667de-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="667de-108">Attributes and Elements</span></span>  

 <span data-ttu-id="667de-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="667de-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="667de-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="667de-110">Attributes</span></span>  
  
|<span data-ttu-id="667de-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="667de-111">Attribute</span></span>|<span data-ttu-id="667de-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="667de-112">Description</span></span>|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|<span data-ttu-id="667de-113">Bir örneğinin bir örneğinin büyüyebileceği en fazla izin verilen boyutu megabayt cinsinden belirten bir tamsayı değeri <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="667de-113">An integer value that specifies the maximum allowable size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="667de-114">Varsayılan değer 0 ' dır. Bu, sınıfının otomatik boyutlandırma buluşsal yöntemleri <xref:System.Runtime.Caching.MemoryCache> Varsayılan olarak kullanıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="667de-114">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`name`|<span data-ttu-id="667de-115">Önbelleğin adı.</span><span class="sxs-lookup"><span data-stu-id="667de-115">The name of the cache.</span></span>|  
|`physicalMemoryLimitPercentage`|<span data-ttu-id="667de-116">0 ile 100 arasında, önbellek tarafından tüketilen fiziksel olarak yüklenen bilgisayar belleğinin maksimum yüzdesini belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="667de-116">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="667de-117">Varsayılan değer 0 ' dır. Bu, sınıfının otomatik boyutlandırma buluşsal yöntemleri <xref:System.Runtime.Caching.MemoryCache> Varsayılan olarak kullanıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="667de-117">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`pollingInterval`|<span data-ttu-id="667de-118">Önbellek uygulamasının geçerli bellek yükünü, önbellek örneği için ayarlanan mutlak ve yüzde tabanlı bellek sınırlarına göre karşılaştıran zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="667de-118">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="667de-119">Bu değer "HH: MM: SS" biçiminde girilir.</span><span class="sxs-lookup"><span data-stu-id="667de-119">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="667de-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="667de-120">Child Elements</span></span>  
  
|<span data-ttu-id="667de-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="667de-121">Element</span></span>|<span data-ttu-id="667de-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="667de-122">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-namedcaches.md)|<span data-ttu-id="667de-123">`namedCaches`Bir bellek önbelleği için koleksiyona adlandırılmış bir önbellek ekler.</span><span class="sxs-lookup"><span data-stu-id="667de-123">Adds a named cache to the `namedCaches` collection for a memory cache.</span></span>|  
|[\<clear>](clear-element-for-namedcaches.md)|<span data-ttu-id="667de-124">`namedCaches`Bir bellek önbelleğinin koleksiyonunu temizler.</span><span class="sxs-lookup"><span data-stu-id="667de-124">Clears the `namedCaches` collection for a memory cache.</span></span>|  
|[\<remove>](remove-element-for-namedcaches.md)|<span data-ttu-id="667de-125">`namedCaches`Bir bellek önbelleği için koleksiyondan adlandırılmış bir önbellek girdisini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="667de-125">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="667de-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="667de-126">Parent Elements</span></span>  
  
|<span data-ttu-id="667de-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="667de-127">Element</span></span>|<span data-ttu-id="667de-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="667de-128">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="667de-129">Ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan her yapılandırma dosyasında kök öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="667de-129">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[\<memoryCache>](memorycache-element-cache-settings.md)|<span data-ttu-id="667de-130">Sınıfına dayalı bir önbelleği yapılandırmak için kullanılan bir öğesi tanımlar <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="667de-130">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="667de-131">.NET Framework yerleşik uygulamalarda çıktı önbelleği uygulamanıza olanak sağlayan türler içerir.</span><span class="sxs-lookup"><span data-stu-id="667de-131">Contains types that let you implement output caching in applications that are built into the .NET Framework.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="667de-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="667de-132">Remarks</span></span>  

 <span data-ttu-id="667de-133">Web.config dosyanın bellek önbelleği yapılandırması bölümü `add` `remove` `clear` koleksiyon için, ve özniteliklerini içerebilir `namedCaches` .</span><span class="sxs-lookup"><span data-stu-id="667de-133">The memory cache configuration section of the Web.config file can contain `add`, `remove`, and `clear` attributes for the `namedCaches` collection.</span></span> <span data-ttu-id="667de-134">Her `namedCaches` giriş, öznitelik tarafından benzersiz şekilde tanımlanır `name` .</span><span class="sxs-lookup"><span data-stu-id="667de-134">Each `namedCaches` entry is uniquely identified by the `name` attribute.</span></span>  
  
 <span data-ttu-id="667de-135">Uygulama yapılandırma dosyalarındaki bilgilere başvurarak bellek önbelleği girdilerinin örneklerini alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="667de-135">You can retrieve instances of memory cache entries by referencing the information in the application configuration files.</span></span> <span data-ttu-id="667de-136">Varsayılan olarak, yalnızca varsayılan önbellek örneğinin yapılandırma dosyasında bir girişi vardır.</span><span class="sxs-lookup"><span data-stu-id="667de-136">By default, only the default cache instance has an entry in the configuration file.</span></span> <span data-ttu-id="667de-137">Varsayılan önbellek örneği özelliğinden döndürülen örneğidir <xref:System.Runtime.Caching.MemoryCache.Default%2A> .</span><span class="sxs-lookup"><span data-stu-id="667de-137">The default cache instance is the instance that is returned from the <xref:System.Runtime.Caching.MemoryCache.Default%2A> property.</span></span>  
  
 <span data-ttu-id="667de-138">Name özniteliğini "default" olarak ayarlarsanız, öğesi varsayılan bellek önbelleği örneğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="667de-138">If you set the name attribute to "default", the element uses the default memory cache instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="667de-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="667de-139">Example</span></span>  

 <span data-ttu-id="667de-140">Aşağıdaki örnek, `name` özniteliğini "default" olarak ayarlayarak önbelleğin adının varsayılan önbellek girişi adına nasıl ayarlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="667de-140">The following example shows how to set the name of the cache to the default cache entry name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="667de-141">`cacheMemoryLimitMegabytes`Özniteliği ve `physicalMemoryPercentage` özniteliği sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="667de-141">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="667de-142">Bu özniteliklerin sıfıra ayarlanması, sınıfının otomatik boyutlandırma buluşsal yöntemleri 'nin kullanıldığı anlamına gelir <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="667de-142">Setting these attributes to zero means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used.</span></span> <span data-ttu-id="667de-143">Önbellek uygulamasının her iki dakikada bir mutlak ve yüzde tabanlı bellek sınırlarına göre geçerli bellek yükünü karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="667de-143">The cache implementation compares the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="667de-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="667de-144">See also</span></span>

- [<span data-ttu-id="667de-145">\<memoryCache> Öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="667de-145">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
