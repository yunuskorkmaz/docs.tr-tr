---
title: <namedCaches> için <add> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: cd920b58290050fcc30ea5d0a1ac113a333902fa
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195369"
---
# <a name="add-element-for-namedcaches"></a><span data-ttu-id="f18ae-102">\<namedCaches> için \<add> Öğesi</span><span class="sxs-lookup"><span data-stu-id="f18ae-102">\<add> Element for \<namedCaches></span></span>

<span data-ttu-id="f18ae-103">`namedCache` `namedCaches` Bir bellek önbelleği için koleksiyona bir giriş ekler.</span><span class="sxs-lookup"><span data-stu-id="f18ae-103">Adds a `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="f18ae-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="f18ae-104">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <add name="Default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="f18ae-105">Tür</span><span class="sxs-lookup"><span data-stu-id="f18ae-105">Type</span></span>  

 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f18ae-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f18ae-106">Attributes and Elements</span></span>  

 <span data-ttu-id="f18ae-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f18ae-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f18ae-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f18ae-108">Attributes</span></span>  
  
|<span data-ttu-id="f18ae-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f18ae-109">Attribute</span></span>|<span data-ttu-id="f18ae-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f18ae-110">Description</span></span>|  
|-|-|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="f18ae-111">Bir örneğinin bir örneğinin büyüyebileceği en fazla izin verilen boyutu (megabayt cinsinden) belirten bir tamsayı değeri <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="f18ae-111">An integer value that specifies the maximum allowed size (in megabytes) that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="f18ae-112">Varsayılan değer 0 ' dır. Bu, <xref:System.Runtime.Caching.MemoryCache> sınıfın otomatik boyutlandırma buluşsal yöntemleri varsayılan olarak kullanıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f18ae-112">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="f18ae-113">Önbelleğin adı.</span><span class="sxs-lookup"><span data-stu-id="f18ae-113">The name of the cache.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="f18ae-114">0 ile 100 arasında, önbellek tarafından tüketilen fiziksel olarak yüklenen bilgisayar belleğinin maksimum yüzdesini belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="f18ae-114">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="f18ae-115">Varsayılan değer 0 ' dır. Bu, <xref:System.Runtime.Caching.MemoryCache> sınıfın otomatik boyutlandırma buluşsal yöntemleri varsayılan olarak kullanıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f18ae-115">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="f18ae-116">Önbellek uygulamasının geçerli bellek yükünü, önbellek örneği için ayarlanan mutlak ve yüzde tabanlı bellek sınırlarına göre karşılaştıran zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="f18ae-116">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="f18ae-117">Bu değer "HH: MM: SS" biçiminde girilir.</span><span class="sxs-lookup"><span data-stu-id="f18ae-117">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f18ae-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f18ae-118">Child Elements</span></span>  

 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="f18ae-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f18ae-119">Parent Elements</span></span>  
  
|<span data-ttu-id="f18ae-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="f18ae-120">Element</span></span>|<span data-ttu-id="f18ae-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f18ae-121">Description</span></span>|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="f18ae-122">Adlandırılmış örnekler için yapılandırma ayarlarının bir koleksiyonunu içerir <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="f18ae-122">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f18ae-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f18ae-123">Remarks</span></span>  

 <span data-ttu-id="f18ae-124">`add`Öğesi, `namedCaches` bir bellek önbelleği için koleksiyona bir giriş ekler.</span><span class="sxs-lookup"><span data-stu-id="f18ae-124">The `add` element adds an entry to the `namedCaches` collection for a memory cache.</span></span> <span data-ttu-id="f18ae-125">[clear](clear-element-for-namedcaches.md) `add` Koleksiyonda başka bir adlandırılmış önbellek bulunmadığından emin olmak için öğesini kullanmadan önce Clear öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f18ae-125">You can use the [clear](clear-element-for-namedcaches.md) element before you use the `add` element to be certain that there are no other named caches in the collection.</span></span> <span data-ttu-id="f18ae-126">Bu öğe machine.config dosyasında ve Web.config dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f18ae-126">This element can be used in the machine.config file and in the Web.config file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f18ae-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="f18ae-127">Example</span></span>  

 <span data-ttu-id="f18ae-128">Aşağıdaki örnek, `namedCache` `namedCaches` bir bellek önbelleğinin koleksiyonuna varsayılan giriş için ayarların nasıl tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f18ae-128">The following example shows how to define settings for the default `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f18ae-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f18ae-129">See also</span></span>

- [<span data-ttu-id="f18ae-130">\<namedCaches> Öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="f18ae-130">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
