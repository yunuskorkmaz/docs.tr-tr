---
title: <system.runtime.caching> Öğesi (Önbellek Ayarları)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
ms.openlocfilehash: df4887c8801dcf8af06b3826673a03cbc7dbc9b5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153860"
---
# <a name="systemruntimecaching-element-cache-settings"></a><span data-ttu-id="78db2-102">\<system.runtime.caching> Öğesi (Önbellek Ayarları)</span><span class="sxs-lookup"><span data-stu-id="78db2-102">\<system.runtime.caching> Element (Cache Settings)</span></span>

<span data-ttu-id="78db2-103"><xref:System.Runtime.Caching.ObjectCache>Yapılandırma dosyasındaki giriş aracılığıyla varsayılan bellek içi uygulama için yapılandırma sağlar `memoryCache` .</span><span class="sxs-lookup"><span data-stu-id="78db2-103">Provides configuration for the default in-memory <xref:System.Runtime.Caching.ObjectCache> implementation through the `memoryCache` entry in the configuration file.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.runtime.caching>**  
  
## <a name="syntax"></a><span data-ttu-id="78db2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="78db2-104">Syntax</span></span>  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="78db2-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="78db2-105">Attributes and Elements</span></span>

<span data-ttu-id="78db2-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="78db2-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="78db2-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="78db2-107">Attributes</span></span>

`None`  

### <a name="child-elements"></a><span data-ttu-id="78db2-108">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="78db2-108">Child Elements</span></span>

|<span data-ttu-id="78db2-109">Öğe</span><span class="sxs-lookup"><span data-stu-id="78db2-109">Element</span></span>|<span data-ttu-id="78db2-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="78db2-110">Description</span></span>|  
|-------------|-----------------|  
|[\<memoryCache>](memorycache-element-cache-settings.md)|<span data-ttu-id="78db2-111">Sınıfına dayalı bir önbelleği yapılandırmak için kullanılan bir öğesi tanımlar <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="78db2-111">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="78db2-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="78db2-112">Parent Elements</span></span>  
  
|<span data-ttu-id="78db2-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="78db2-113">Element</span></span>|<span data-ttu-id="78db2-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="78db2-114">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="78db2-115">Ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan her yapılandırma dosyasında kök öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="78db2-115">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78db2-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="78db2-116">Remarks</span></span>

<span data-ttu-id="78db2-117">Bu ad alanındaki sınıflar, ASP.NET ' deki, ancak derlemeye bağımlılık olmadan önbelleğe alma olanaklarını kullanmanın bir yolunu sunar `System.Web` .</span><span class="sxs-lookup"><span data-stu-id="78db2-117">The classes in this namespace provide a way to use caching facilities like those in ASP.NET, but without a dependency on the `System.Web` assembly.</span></span> <span data-ttu-id="78db2-118">Daha fazla bilgi için bkz. [.NET Framework uygulamalarında önbelleğe alma](../../../performance/caching-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="78db2-118">For more information, see [Caching in .NET Framework Applications](../../../performance/caching-in-net-framework-applications.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="78db2-119">Çıktı önbelleği işlevselliği ve <xref:System.Runtime.Caching> ad alanındaki türler .NET Framework 4 ' te yenidir.</span><span class="sxs-lookup"><span data-stu-id="78db2-119">The output caching functionality and types in the <xref:System.Runtime.Caching> namespace are new in .NET Framework 4.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78db2-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="78db2-120">Example</span></span>

<span data-ttu-id="78db2-121">Aşağıdaki örnek, sınıfına dayalı bir önbelleğin nasıl yapılandırılacağını gösterir <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="78db2-121">The following example shows how to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="78db2-122">Örnek, `namedCaches` bellek önbelleği için girdinin bir örneğinin nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="78db2-122">The example shows how to configure an instance of the `namedCaches` entry for memory cache.</span></span> <span data-ttu-id="78db2-123">Önbellek adı `name` özniteliği "varsayılan" olarak ayarlanarak varsayılan önbellek girişi adına ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="78db2-123">The name of the cache is set to the default cache entry name by setting the `name` attribute to "Default".</span></span>  
  
<span data-ttu-id="78db2-124">`cacheMemoryLimitMegabytes`Özniteliği ve `physicalMemoryPercentage` özniteliği sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="78db2-124">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="78db2-125">Bu özniteliklerin sıfıra ayarlanması, <xref:System.Runtime.Caching.MemoryCache> otomatik boyutlandırma buluşsal yöntemleri varsayılan olarak kullanıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="78db2-125">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="78db2-126">Önbellek uygulamasının her iki dakikada bir, geçerli bellek yükünü mutlak ve yüzde tabanlı bellek sınırlarına göre karşılaştırması gerekir.</span><span class="sxs-lookup"><span data-stu-id="78db2-126">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="78db2-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78db2-127">See also</span></span>

- [<span data-ttu-id="78db2-128">\<memoryCache>Öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="78db2-128">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
