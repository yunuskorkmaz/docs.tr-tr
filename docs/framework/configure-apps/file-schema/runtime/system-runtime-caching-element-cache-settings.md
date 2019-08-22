---
title: <system.runtime.caching> Öğesi (Önbellek Ayarları)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 91a97807d45d3cafdac0c0608dc9590533b185dc
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663440"
---
# <a name="systemruntimecaching-element-cache-settings"></a><span data-ttu-id="92e34-102">\<System. Runtime. Caching > öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="92e34-102">\<system.runtime.caching> Element (Cache Settings)</span></span>

<span data-ttu-id="92e34-103">Yapılandırma dosyasındaki <xref:System.Runtime.Caching.ObjectCache> `memoryCache` giriş aracılığıyla varsayılan bellek içi uygulama için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="92e34-103">Provides configuration for the default in-memory <xref:System.Runtime.Caching.ObjectCache> implementation through the `memoryCache` entry in the configuration file.</span></span>  
  
 <span data-ttu-id="92e34-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="92e34-104">\<configuration></span></span>  
<span data-ttu-id="92e34-105">\<System. Runtime. Caching ></span><span class="sxs-lookup"><span data-stu-id="92e34-105">\<system.runtime.caching></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92e34-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="92e34-106">Syntax</span></span>  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="92e34-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="92e34-107">Attributes and Elements</span></span>

<span data-ttu-id="92e34-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="92e34-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="92e34-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="92e34-109">Attributes</span></span>

`None`  

### <a name="child-elements"></a><span data-ttu-id="92e34-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="92e34-110">Child Elements</span></span>

|<span data-ttu-id="92e34-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="92e34-111">Element</span></span>|<span data-ttu-id="92e34-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92e34-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="92e34-113">\<memoryCache ></span><span class="sxs-lookup"><span data-stu-id="92e34-113">\<memoryCache></span></span>](memorycache-element-cache-settings.md)|<span data-ttu-id="92e34-114"><xref:System.Runtime.Caching.MemoryCache> Sınıfına dayalı bir önbelleği yapılandırmak için kullanılan bir öğesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="92e34-114">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="92e34-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="92e34-115">Parent Elements</span></span>  
  
|<span data-ttu-id="92e34-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="92e34-116">Element</span></span>|<span data-ttu-id="92e34-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92e34-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="92e34-118">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="92e34-118">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="92e34-119">Ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan her yapılandırma dosyasında kök öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="92e34-119">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92e34-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="92e34-120">Remarks</span></span>

<span data-ttu-id="92e34-121">Bu ad alanındaki sınıflar, ASP.net ' deki, ancak `System.Web` derlemeye bağımlılık olmadan önbelleğe alma olanaklarını kullanmanın bir yolunu sunar.</span><span class="sxs-lookup"><span data-stu-id="92e34-121">The classes in this namespace provide a way to use caching facilities like those in ASP.NET, but without a dependency on the `System.Web` assembly.</span></span> <span data-ttu-id="92e34-122">Daha fazla bilgi için bkz. [.NET Framework uygulamalarında önbelleğe alma](../../../performance/caching-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="92e34-122">For more information, see [Caching in .NET Framework Applications](../../../performance/caching-in-net-framework-applications.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="92e34-123">Çıktı önbelleği işlevselliği ve <xref:System.Runtime.Caching> ad alanındaki türler .NET Framework 4 ' te yenidir.</span><span class="sxs-lookup"><span data-stu-id="92e34-123">The output caching functionality and types in the <xref:System.Runtime.Caching> namespace are new in .NET Framework 4.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92e34-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="92e34-124">Example</span></span>

<span data-ttu-id="92e34-125">Aşağıdaki örnek, <xref:System.Runtime.Caching.MemoryCache> sınıfına dayalı bir önbelleğin nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="92e34-125">The following example shows how to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="92e34-126">Örnek, bellek önbelleği için `namedCaches` girdinin bir örneğinin nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="92e34-126">The example shows how to configure an instance of the `namedCaches` entry for memory cache.</span></span> <span data-ttu-id="92e34-127">Önbellek adı `name` özniteliği "varsayılan" olarak ayarlanarak varsayılan önbellek girişi adına ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="92e34-127">The name of the cache is set to the default cache entry name by setting the `name` attribute to "Default".</span></span>  
  
<span data-ttu-id="92e34-128">`cacheMemoryLimitMegabytes` Özniteliği`physicalMemoryPercentage` ve özniteliği sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="92e34-128">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="92e34-129">Bu özniteliklerin sıfıra ayarlanması, <xref:System.Runtime.Caching.MemoryCache> otomatik boyutlandırma buluşsal yöntemleri varsayılan olarak kullanıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="92e34-129">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="92e34-130">Önbellek uygulamasının her iki dakikada bir, geçerli bellek yükünü mutlak ve yüzde tabanlı bellek sınırlarına göre karşılaştırması gerekir.</span><span class="sxs-lookup"><span data-stu-id="92e34-130">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="92e34-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92e34-131">See also</span></span>

- [<span data-ttu-id="92e34-132">\<memoryCache > öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="92e34-132">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
