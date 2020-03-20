---
title: <system.runtime.caching> Öğesi (Önbellek Ayarları)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
ms.openlocfilehash: df4887c8801dcf8af06b3826673a03cbc7dbc9b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153860"
---
# <a name="systemruntimecaching-element-cache-settings"></a><span data-ttu-id="c5df0-102">\<system.runtime.cacching> Öğesi (Önbellek Ayarları)</span><span class="sxs-lookup"><span data-stu-id="c5df0-102">\<system.runtime.caching> Element (Cache Settings)</span></span>

<span data-ttu-id="c5df0-103">Yapılandırma dosyasındaki <xref:System.Runtime.Caching.ObjectCache> `memoryCache` giriş aracılığıyla varsayılan bellek içi uygulama yapılandırmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5df0-103">Provides configuration for the default in-memory <xref:System.Runtime.Caching.ObjectCache> implementation through the `memoryCache` entry in the configuration file.</span></span>  
  
<span data-ttu-id="c5df0-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c5df0-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c5df0-105">&nbsp;&nbsp;**\<system.runtime.önbelleğe alma>**</span><span class="sxs-lookup"><span data-stu-id="c5df0-105">&nbsp;&nbsp;**\<system.runtime.caching>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5df0-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c5df0-106">Syntax</span></span>  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5df0-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c5df0-107">Attributes and Elements</span></span>

<span data-ttu-id="c5df0-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c5df0-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5df0-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c5df0-109">Attributes</span></span>

`None`  

### <a name="child-elements"></a><span data-ttu-id="c5df0-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c5df0-110">Child Elements</span></span>

|<span data-ttu-id="c5df0-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="c5df0-111">Element</span></span>|<span data-ttu-id="c5df0-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c5df0-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c5df0-113">\<memoryÖnbellek></span><span class="sxs-lookup"><span data-stu-id="c5df0-113">\<memoryCache></span></span>](memorycache-element-cache-settings.md)|<span data-ttu-id="c5df0-114">Sınıfı temel alan önbelleği yapılandırmak için kullanılan bir <xref:System.Runtime.Caching.MemoryCache> öğetanımlar.</span><span class="sxs-lookup"><span data-stu-id="c5df0-114">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c5df0-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c5df0-115">Parent Elements</span></span>  
  
|<span data-ttu-id="c5df0-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="c5df0-116">Element</span></span>|<span data-ttu-id="c5df0-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c5df0-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c5df0-118">\<yapılandırma></span><span class="sxs-lookup"><span data-stu-id="c5df0-118">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="c5df0-119">Ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan her yapılandırma dosyasındaki kök öğeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5df0-119">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5df0-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c5df0-120">Remarks</span></span>

<span data-ttu-id="c5df0-121">Bu ad alanındaki sınıflar, ASP.NET'daki gibi önbelleğe alma olanaklarını kullanmanın `System.Web` bir yolunu sağlar, ancak derlemeye bağımlılık olmadan.</span><span class="sxs-lookup"><span data-stu-id="c5df0-121">The classes in this namespace provide a way to use caching facilities like those in ASP.NET, but without a dependency on the `System.Web` assembly.</span></span> <span data-ttu-id="c5df0-122">Daha fazla bilgi için [.NET Framework Applications'da Önbelleğe Alma'ya](../../../performance/caching-in-net-framework-applications.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="c5df0-122">For more information, see [Caching in .NET Framework Applications](../../../performance/caching-in-net-framework-applications.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c5df0-123"><xref:System.Runtime.Caching> Ad alanındaki çıktı önbelleğe alma işlevi ve türleri .NET Framework 4'te yenidir.</span><span class="sxs-lookup"><span data-stu-id="c5df0-123">The output caching functionality and types in the <xref:System.Runtime.Caching> namespace are new in .NET Framework 4.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5df0-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="c5df0-124">Example</span></span>

<span data-ttu-id="c5df0-125">Aşağıdaki örnek, <xref:System.Runtime.Caching.MemoryCache> sınıfa dayalı bir önbelleğin nasıl yapılandırılabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c5df0-125">The following example shows how to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="c5df0-126">Örnek, bellek önbelleği için `namedCaches` giriş örneğinin nasıl yapılandırılabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c5df0-126">The example shows how to configure an instance of the `namedCaches` entry for memory cache.</span></span> <span data-ttu-id="c5df0-127">Önbelleğin adı, `name` özniteliği "Varsayılan" olarak ayarlayarak varsayılan önbellek giriş adı olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c5df0-127">The name of the cache is set to the default cache entry name by setting the `name` attribute to "Default".</span></span>  
  
<span data-ttu-id="c5df0-128">Öznitelik `cacheMemoryLimitMegabytes` ve `physicalMemoryPercentage` öznitelik sıfıra ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c5df0-128">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="c5df0-129">Bu öznitelikleri sıfıra <xref:System.Runtime.Caching.MemoryCache> ayarlamak, otomatik boyutlandırma sezgisellerinin varsayılan olarak kullanıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c5df0-129">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="c5df0-130">Önbellek uygulaması, geçerli bellek yükünü her iki dakikada bir mutlak ve yüzde tabanlı bellek sınırlarıyla karşılaştırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c5df0-130">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c5df0-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5df0-131">See also</span></span>

- [<span data-ttu-id="c5df0-132">\<memoryÖnbellek> Öğesi (Önbellek Ayarları)</span><span class="sxs-lookup"><span data-stu-id="c5df0-132">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
