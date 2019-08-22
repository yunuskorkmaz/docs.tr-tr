---
title: <namedCaches> için <add> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: fd6668a551663470a97b07ff131710dbe92a91f5
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659028"
---
# <a name="add-element-for-namedcaches"></a><span data-ttu-id="dd722-102">\<namedönbellekler için \<> öğesi ekleyin ></span><span class="sxs-lookup"><span data-stu-id="dd722-102">\<add> Element for \<namedCaches></span></span>
<span data-ttu-id="dd722-103">Bir bellek `namedCache` önbelleği için `namedCaches` koleksiyona bir giriş ekler.</span><span class="sxs-lookup"><span data-stu-id="dd722-103">Adds a `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="dd722-104">\<System. Runtime. Caching ></span><span class="sxs-lookup"><span data-stu-id="dd722-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="dd722-105">\<memoryCache ></span><span class="sxs-lookup"><span data-stu-id="dd722-105">\<memoryCache></span></span>  
<span data-ttu-id="dd722-106">\<Namedönbellekler ></span><span class="sxs-lookup"><span data-stu-id="dd722-106">\<namedCaches></span></span>  
<span data-ttu-id="dd722-107">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="dd722-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd722-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dd722-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <add name="Default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="dd722-109">Tür</span><span class="sxs-lookup"><span data-stu-id="dd722-109">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dd722-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="dd722-110">Attributes and Elements</span></span>  
 <span data-ttu-id="dd722-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dd722-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dd722-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="dd722-112">Attributes</span></span>  
  
|<span data-ttu-id="dd722-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="dd722-113">Attribute</span></span>|<span data-ttu-id="dd722-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dd722-114">Description</span></span>|  
|-|-|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="dd722-115">Bir örneğinin bir <xref:System.Runtime.Caching.MemoryCache> örneğinin büyüyebileceği en fazla izin verilen boyutu (megabayt cinsinden) belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="dd722-115">An integer value that specifies the maximum allowed size (in megabytes) that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="dd722-116">Varsayılan değer 0 ' dır. Bu, <xref:System.Runtime.Caching.MemoryCache> sınıfın otomatik boyutlandırma buluşsal yöntemleri varsayılan olarak kullanıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="dd722-116">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="dd722-117">Önbelleğin adı.</span><span class="sxs-lookup"><span data-stu-id="dd722-117">The name of the cache.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="dd722-118">0 ile 100 arasında, önbellek tarafından tüketilen fiziksel olarak yüklenen bilgisayar belleğinin maksimum yüzdesini belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="dd722-118">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="dd722-119">Varsayılan değer 0 ' dır. Bu, <xref:System.Runtime.Caching.MemoryCache> sınıfın otomatik boyutlandırma buluşsal yöntemleri varsayılan olarak kullanıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="dd722-119">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="dd722-120">Önbellek uygulamasının geçerli bellek yükünü, önbellek örneği için ayarlanan mutlak ve yüzde tabanlı bellek sınırlarına göre karşılaştıran zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="dd722-120">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="dd722-121">Bu değer "HH: MM: SS" biçiminde girilir.</span><span class="sxs-lookup"><span data-stu-id="dd722-121">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dd722-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="dd722-122">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="dd722-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="dd722-123">Parent Elements</span></span>  
  
|<span data-ttu-id="dd722-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="dd722-124">Element</span></span>|<span data-ttu-id="dd722-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dd722-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dd722-126">\<Namedönbellekler ></span><span class="sxs-lookup"><span data-stu-id="dd722-126">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="dd722-127">Adlandırılmış <xref:System.Runtime.Caching.MemoryCache> örnekler için yapılandırma ayarlarının bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="dd722-127">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd722-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dd722-128">Remarks</span></span>  
 <span data-ttu-id="dd722-129">Öğesi `add` , bir bellek önbelleği için `namedCaches` koleksiyona bir giriş ekler.</span><span class="sxs-lookup"><span data-stu-id="dd722-129">The `add` element adds an entry to the `namedCaches` collection for a memory cache.</span></span> <span data-ttu-id="dd722-130">Koleksiyonda başka bir adlandırılmış [](clear-element-for-namedcaches.md) önbellek bulunmadığından emin olmak için `add` öğesini kullanmadan önce Clear öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dd722-130">You can use the [clear](clear-element-for-namedcaches.md) element before you use the `add` element to be certain that there are no other named caches in the collection.</span></span> <span data-ttu-id="dd722-131">Bu öğe Machine. config dosyasında ve Web. config dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dd722-131">This element can be used in the machine.config file and in the Web.config file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd722-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="dd722-132">Example</span></span>  
 <span data-ttu-id="dd722-133">Aşağıdaki örnek, bir bellek önbelleğinin `namedCache` `namedCaches` koleksiyonuna varsayılan giriş için ayarların nasıl tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="dd722-133">The following example shows how to define settings for the default `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dd722-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd722-134">See also</span></span>

- [<span data-ttu-id="dd722-135">\<Namedönbellekler > öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="dd722-135">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
