---
title: "&lt;System.Runtime.Caching&gt; öğesi (önbellek ayarları)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 83964d3a6e07267eaa946fa306301bc6d0d16e8f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsystemruntimecachinggt-element-cache-settings"></a><span data-ttu-id="45fa2-102">&lt;System.Runtime.Caching&gt; öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="45fa2-102">&lt;system.runtime.caching&gt; Element (Cache Settings)</span></span>
<span data-ttu-id="45fa2-103">Varsayılan bellek içi için yapılandırma sağlar <xref:System.Runtime.Caching.ObjectCache> uygulaması aracılığıyla `memoryCache` yapılandırma dosyasındaki girişi.</span><span class="sxs-lookup"><span data-stu-id="45fa2-103">Provides configuration for the default in-memory <xref:System.Runtime.Caching.ObjectCache> implementation through the `memoryCache` entry in the configuration file.</span></span>  
  
 <span data-ttu-id="45fa2-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="45fa2-104">\<configuration></span></span>  
<span data-ttu-id="45fa2-105">\<System.Runtime.Caching ></span><span class="sxs-lookup"><span data-stu-id="45fa2-105">\<system.runtime.caching></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45fa2-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="45fa2-106">Syntax</span></span>  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="45fa2-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="45fa2-107">Attributes and Elements</span></span>  
 <span data-ttu-id="45fa2-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="45fa2-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="45fa2-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="45fa2-109">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="45fa2-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="45fa2-110">Child Elements</span></span>  
  
|<span data-ttu-id="45fa2-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="45fa2-111">Element</span></span>|<span data-ttu-id="45fa2-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="45fa2-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="45fa2-113">\<memoryCache ></span><span class="sxs-lookup"><span data-stu-id="45fa2-113">\<memoryCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|<span data-ttu-id="45fa2-114">Temel alan bir önbellek yapılandırmak için kullanılan bir öğe tanımlar <xref:System.Runtime.Caching.MemoryCache> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="45fa2-114">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="45fa2-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="45fa2-115">Parent Elements</span></span>  
  
|<span data-ttu-id="45fa2-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="45fa2-116">Element</span></span>|<span data-ttu-id="45fa2-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="45fa2-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="45fa2-118">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="45fa2-118">\<configuration></span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="45fa2-119">Ortak dil çalışma zamanı tarafından kullanılan her yapılandırma dosyası kök öğesi belirtir ve [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="45fa2-119">Specifies the root element in every configuration file that is used by the common language runtime and [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45fa2-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="45fa2-120">Remarks</span></span>  
 <span data-ttu-id="45fa2-121">Bu ad alanındaki sınıflar üzerinde gelenler ASP.NET, ancak bir bağımlılık önbelleğe alma özelliklerini kullanabilmeniz için bir yol sağlama `System.Web` derleme.</span><span class="sxs-lookup"><span data-stu-id="45fa2-121">The classes in this namespace provide a way to use caching facilities like those in ASP.NET, but without a dependency on the `System.Web` assembly.</span></span> <span data-ttu-id="45fa2-122">Daha fazla bilgi için bkz: [.NET Framework uygulamalarında önbelleğe alma](../../../../../docs/framework/performance/caching-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="45fa2-122">For more information, see [Caching in .NET Framework Applications](../../../../../docs/framework/performance/caching-in-net-framework-applications.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="45fa2-123">Çıktı önbelleği işlevselliği ve türlerinde <xref:System.Runtime.Caching> ad yeni [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="45fa2-123">The output caching functionality and types in the <xref:System.Runtime.Caching> namespace are new in [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="45fa2-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="45fa2-124">Example</span></span>  
 <span data-ttu-id="45fa2-125">Aşağıdaki örnek temel alan bir önbellek yapılandırma gösterir <xref:System.Runtime.Caching.MemoryCache> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="45fa2-125">The following example shows how to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="45fa2-126">Örnek bir örneğini yapılandırın gösterilmektedir `namedCaches` önbellek girişi.</span><span class="sxs-lookup"><span data-stu-id="45fa2-126">The example shows how to configure an instance of the `namedCaches` entry for memory cache.</span></span> <span data-ttu-id="45fa2-127">Önbellek adı ayarlayarak varsayılan önbellek girişi adına ayarlanır `name` "varsayılan" özniteliği.</span><span class="sxs-lookup"><span data-stu-id="45fa2-127">The name of the cache is set to the default cache entry name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="45fa2-128">`cacheMemoryLimitMegabytes` Özniteliği ve `physicalMemoryPercentage` özniteliği sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="45fa2-128">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="45fa2-129">Bu öznitelikler sıfır olarak ayarlandığında <xref:System.Runtime.Caching.MemoryCache> otomatik boyutlandırma buluşsal yöntemler, varsayılan olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="45fa2-129">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="45fa2-130">Önbellek uygulaması mutlak ve yüzde tabanlı bellek sınırları her iki dakikada göre geçerli bellek yükü karşılaştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="45fa2-130">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
```xml  
<configuration>  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="45fa2-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="45fa2-131">See Also</span></span>  
 [<span data-ttu-id="45fa2-132">\<memoryCache > öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="45fa2-132">\<memoryCache> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)
