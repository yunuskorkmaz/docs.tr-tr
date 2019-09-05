---
title: <namedCaches> için <add> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: 076d940e0c15cf48013480fef68b8fac42cf76e9
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252885"
---
# <a name="add-element-for-namedcaches"></a><span data-ttu-id="97be6-102">\<namedönbellekler için \<> öğesi ekleyin ></span><span class="sxs-lookup"><span data-stu-id="97be6-102">\<add> Element for \<namedCaches></span></span>
<span data-ttu-id="97be6-103">Bir bellek `namedCache` önbelleği için `namedCaches` koleksiyona bir giriş ekler.</span><span class="sxs-lookup"><span data-stu-id="97be6-103">Adds a `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
<span data-ttu-id="97be6-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="97be6-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="97be6-105">&nbsp;&nbsp;[ **\<System. Runtime. Caching >** ](system-runtime-caching-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="97be6-105">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span></span>\
<span data-ttu-id="97be6-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<memoryCache >** ](memorycache-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="97be6-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)</span></span>\
<span data-ttu-id="97be6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Namedönbellekler >** ](namedcaches-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="97be6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)</span></span>\
<span data-ttu-id="97be6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> Ekle**</span><span class="sxs-lookup"><span data-stu-id="97be6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97be6-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="97be6-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <add name="Default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="97be6-110">Tür</span><span class="sxs-lookup"><span data-stu-id="97be6-110">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="97be6-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="97be6-111">Attributes and Elements</span></span>  
 <span data-ttu-id="97be6-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="97be6-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="97be6-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="97be6-113">Attributes</span></span>  
  
|<span data-ttu-id="97be6-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="97be6-114">Attribute</span></span>|<span data-ttu-id="97be6-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="97be6-115">Description</span></span>|  
|-|-|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="97be6-116">Bir örneğinin bir <xref:System.Runtime.Caching.MemoryCache> örneğinin büyüyebileceği en fazla izin verilen boyutu (megabayt cinsinden) belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="97be6-116">An integer value that specifies the maximum allowed size (in megabytes) that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="97be6-117">Varsayılan değer 0 ' dır. Bu, <xref:System.Runtime.Caching.MemoryCache> sınıfın otomatik boyutlandırma buluşsal yöntemleri varsayılan olarak kullanıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="97be6-117">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="97be6-118">Önbelleğin adı.</span><span class="sxs-lookup"><span data-stu-id="97be6-118">The name of the cache.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="97be6-119">0 ile 100 arasında, önbellek tarafından tüketilen fiziksel olarak yüklenen bilgisayar belleğinin maksimum yüzdesini belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="97be6-119">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="97be6-120">Varsayılan değer 0 ' dır. Bu, <xref:System.Runtime.Caching.MemoryCache> sınıfın otomatik boyutlandırma buluşsal yöntemleri varsayılan olarak kullanıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="97be6-120">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="97be6-121">Önbellek uygulamasının geçerli bellek yükünü, önbellek örneği için ayarlanan mutlak ve yüzde tabanlı bellek sınırlarına göre karşılaştıran zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="97be6-121">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="97be6-122">Bu değer "HH: MM: SS" biçiminde girilir.</span><span class="sxs-lookup"><span data-stu-id="97be6-122">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="97be6-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="97be6-123">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="97be6-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="97be6-124">Parent Elements</span></span>  
  
|<span data-ttu-id="97be6-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="97be6-125">Element</span></span>|<span data-ttu-id="97be6-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="97be6-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="97be6-127">\<Namedönbellekler ></span><span class="sxs-lookup"><span data-stu-id="97be6-127">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="97be6-128">Adlandırılmış <xref:System.Runtime.Caching.MemoryCache> örnekler için yapılandırma ayarlarının bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="97be6-128">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97be6-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="97be6-129">Remarks</span></span>  
 <span data-ttu-id="97be6-130">Öğesi `add` , bir bellek önbelleği için `namedCaches` koleksiyona bir giriş ekler.</span><span class="sxs-lookup"><span data-stu-id="97be6-130">The `add` element adds an entry to the `namedCaches` collection for a memory cache.</span></span> <span data-ttu-id="97be6-131">Koleksiyonda başka bir adlandırılmış [](clear-element-for-namedcaches.md) önbellek bulunmadığından emin olmak için `add` öğesini kullanmadan önce Clear öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97be6-131">You can use the [clear](clear-element-for-namedcaches.md) element before you use the `add` element to be certain that there are no other named caches in the collection.</span></span> <span data-ttu-id="97be6-132">Bu öğe Machine. config dosyasında ve Web. config dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="97be6-132">This element can be used in the machine.config file and in the Web.config file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97be6-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="97be6-133">Example</span></span>  
 <span data-ttu-id="97be6-134">Aşağıdaki örnek, bir bellek önbelleğinin `namedCache` `namedCaches` koleksiyonuna varsayılan giriş için ayarların nasıl tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="97be6-134">The following example shows how to define settings for the default `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
```xml  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="Default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="97be6-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97be6-135">See also</span></span>

- [<span data-ttu-id="97be6-136">\<Namedönbellekler > öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="97be6-136">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
