---
title: < System.runtime.caching > öğesi (önbellek ayarları)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a68af0727e6f2fc92f9c6875ec6566dc969bd65d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55275801"
---
# <a name="systemruntimecaching-element-cache-settings"></a><span data-ttu-id="a0bf5-102">\<System.Runtime.Caching > öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="a0bf5-102">\<system.runtime.caching> Element (Cache Settings)</span></span>
<span data-ttu-id="a0bf5-103">Bellekteki varsayılan yapılandırmasını sağlar <xref:System.Runtime.Caching.ObjectCache> uygulaması aracılığıyla `memoryCache` yapılandırma dosyasında giriş.</span><span class="sxs-lookup"><span data-stu-id="a0bf5-103">Provides configuration for the default in-memory <xref:System.Runtime.Caching.ObjectCache> implementation through the `memoryCache` entry in the configuration file.</span></span>  
  
 <span data-ttu-id="a0bf5-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="a0bf5-104">\<configuration></span></span>  
<span data-ttu-id="a0bf5-105">\<System.Runtime.Caching ></span><span class="sxs-lookup"><span data-stu-id="a0bf5-105">\<system.runtime.caching></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0bf5-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a0bf5-106">Syntax</span></span>  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a0bf5-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a0bf5-107">Attributes and Elements</span></span>  
 <span data-ttu-id="a0bf5-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a0bf5-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a0bf5-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a0bf5-109">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="a0bf5-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a0bf5-110">Child Elements</span></span>  
  
|<span data-ttu-id="a0bf5-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="a0bf5-111">Element</span></span>|<span data-ttu-id="a0bf5-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0bf5-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a0bf5-113">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="a0bf5-113">\<memoryCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|<span data-ttu-id="a0bf5-114">Temel alan bir önbellek yapılandırmak için kullanılan bir öğe tanımlar <xref:System.Runtime.Caching.MemoryCache> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a0bf5-114">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a0bf5-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a0bf5-115">Parent Elements</span></span>  
  
|<span data-ttu-id="a0bf5-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="a0bf5-116">Element</span></span>|<span data-ttu-id="a0bf5-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0bf5-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a0bf5-118">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="a0bf5-118">\<configuration></span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="a0bf5-119">Her yapılandırma dosyasında ortak dil çalışma zamanı tarafından kullanılan kök öğesini belirtir ve [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="a0bf5-119">Specifies the root element in every configuration file that is used by the common language runtime and [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0bf5-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a0bf5-120">Remarks</span></span>  
 <span data-ttu-id="a0bf5-121">Bu ad alanındaki sınıflar üzerinde ASP.NET, ancak bir bağımlılık benzer önbelleğe alma özelliklerini kullanabilmeniz için bir yol sağlar `System.Web` derleme.</span><span class="sxs-lookup"><span data-stu-id="a0bf5-121">The classes in this namespace provide a way to use caching facilities like those in ASP.NET, but without a dependency on the `System.Web` assembly.</span></span> <span data-ttu-id="a0bf5-122">Daha fazla bilgi için [.NET Framework uygulamalarında önbelleğe alma](../../../../../docs/framework/performance/caching-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="a0bf5-122">For more information, see [Caching in .NET Framework Applications](../../../../../docs/framework/performance/caching-in-net-framework-applications.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a0bf5-123">Çıktı işlevleri ve türleri önbelleğe alma <xref:System.Runtime.Caching> ad alanı yeni [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a0bf5-123">The output caching functionality and types in the <xref:System.Runtime.Caching> namespace are new in [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0bf5-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="a0bf5-124">Example</span></span>  
 <span data-ttu-id="a0bf5-125">Aşağıdaki örnek, temel alan bir önbellek yapılandırma işlemi gösterilmektedir <xref:System.Runtime.Caching.MemoryCache> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a0bf5-125">The following example shows how to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="a0bf5-126">Örneğin, bir örneğini yapılandırma işlemi gösterilmektedir `namedCaches` önbellek girişi.</span><span class="sxs-lookup"><span data-stu-id="a0bf5-126">The example shows how to configure an instance of the `namedCaches` entry for memory cache.</span></span> <span data-ttu-id="a0bf5-127">Önbellek adı ayarlayarak varsayılan önbellek girişi adına ayarlanır `name` "varsayılan" özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a0bf5-127">The name of the cache is set to the default cache entry name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="a0bf5-128">`cacheMemoryLimitMegabytes` Özniteliği ve `physicalMemoryPercentage` öznitelik sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="a0bf5-128">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="a0bf5-129">Bu öznitelik sıfır olarak ayarlandığında <xref:System.Runtime.Caching.MemoryCache> otomatik boyutlandırma buluşsal yöntemler, varsayılan olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a0bf5-129">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="a0bf5-130">Önbellek uygulaması, iki dakikada mutlak ve yüzde tabanlı bellek sınırlarını karşı geçerli bellek yükü karşılaştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a0bf5-130">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a0bf5-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0bf5-131">See also</span></span>
- [<span data-ttu-id="a0bf5-132">\<memoryCache > öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="a0bf5-132">\<memoryCache> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)
