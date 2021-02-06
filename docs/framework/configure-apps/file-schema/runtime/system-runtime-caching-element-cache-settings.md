---
description: 'Hakkında daha fazla bilgi edinin: <System. Runtime. Caching> öğesi (önbellek ayarları)'
title: <system.runtime.caching> Öğesi (Önbellek Ayarları)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
ms.openlocfilehash: 602d863caedef5c1334948b25b0caa2b0e35f685
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652737"
---
# <a name="systemruntimecaching-element-cache-settings"></a><span data-ttu-id="c803d-103">\<system.runtime.caching> Öğesi (Önbellek Ayarları)</span><span class="sxs-lookup"><span data-stu-id="c803d-103">\<system.runtime.caching> Element (Cache Settings)</span></span>

<span data-ttu-id="c803d-104"><xref:System.Runtime.Caching.ObjectCache>Yapılandırma dosyasındaki giriş aracılığıyla varsayılan bellek içi uygulama için yapılandırma sağlar `memoryCache` .</span><span class="sxs-lookup"><span data-stu-id="c803d-104">Provides configuration for the default in-memory <xref:System.Runtime.Caching.ObjectCache> implementation through the `memoryCache` entry in the configuration file.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.runtime.caching>**  
  
## <a name="syntax"></a><span data-ttu-id="c803d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c803d-105">Syntax</span></span>  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c803d-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c803d-106">Attributes and Elements</span></span>

<span data-ttu-id="c803d-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c803d-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c803d-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c803d-108">Attributes</span></span>

`None`  

### <a name="child-elements"></a><span data-ttu-id="c803d-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c803d-109">Child Elements</span></span>

|<span data-ttu-id="c803d-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="c803d-110">Element</span></span>|<span data-ttu-id="c803d-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c803d-111">Description</span></span>|  
|-------------|-----------------|  
|[\<memoryCache>](memorycache-element-cache-settings.md)|<span data-ttu-id="c803d-112">Sınıfına dayalı bir önbelleği yapılandırmak için kullanılan bir öğesi tanımlar <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="c803d-112">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c803d-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c803d-113">Parent Elements</span></span>  
  
|<span data-ttu-id="c803d-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="c803d-114">Element</span></span>|<span data-ttu-id="c803d-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c803d-115">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="c803d-116">Ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan her yapılandırma dosyasında kök öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c803d-116">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c803d-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c803d-117">Remarks</span></span>

<span data-ttu-id="c803d-118">Bu ad alanındaki sınıflar, ASP.NET ' deki, ancak derlemeye bağımlılık olmadan önbelleğe alma olanaklarını kullanmanın bir yolunu sunar `System.Web` .</span><span class="sxs-lookup"><span data-stu-id="c803d-118">The classes in this namespace provide a way to use caching facilities like those in ASP.NET, but without a dependency on the `System.Web` assembly.</span></span> <span data-ttu-id="c803d-119">Daha fazla bilgi için bkz. [.NET Framework uygulamalarında önbelleğe alma](../../../performance/caching-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="c803d-119">For more information, see [Caching in .NET Framework Applications](../../../performance/caching-in-net-framework-applications.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c803d-120">Çıktı önbelleği işlevselliği ve <xref:System.Runtime.Caching> ad alanındaki türler .NET Framework 4 ' te yenidir.</span><span class="sxs-lookup"><span data-stu-id="c803d-120">The output caching functionality and types in the <xref:System.Runtime.Caching> namespace are new in .NET Framework 4.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c803d-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="c803d-121">Example</span></span>

<span data-ttu-id="c803d-122">Aşağıdaki örnek, sınıfına dayalı bir önbelleğin nasıl yapılandırılacağını gösterir <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="c803d-122">The following example shows how to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="c803d-123">Örnek, `namedCaches` bellek önbelleği için girdinin bir örneğinin nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c803d-123">The example shows how to configure an instance of the `namedCaches` entry for memory cache.</span></span> <span data-ttu-id="c803d-124">Önbellek adı `name` özniteliği "varsayılan" olarak ayarlanarak varsayılan önbellek girişi adına ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c803d-124">The name of the cache is set to the default cache entry name by setting the `name` attribute to "Default".</span></span>  
  
<span data-ttu-id="c803d-125">`cacheMemoryLimitMegabytes`Özniteliği ve `physicalMemoryPercentage` özniteliği sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c803d-125">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="c803d-126">Bu özniteliklerin sıfıra ayarlanması, <xref:System.Runtime.Caching.MemoryCache> otomatik boyutlandırma buluşsal yöntemleri varsayılan olarak kullanıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c803d-126">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="c803d-127">Önbellek uygulamasının her iki dakikada bir, geçerli bellek yükünü mutlak ve yüzde tabanlı bellek sınırlarına göre karşılaştırması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c803d-127">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c803d-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c803d-128">See also</span></span>

- [<span data-ttu-id="c803d-129">\<memoryCache> Öğesi (önbellek ayarları)</span><span class="sxs-lookup"><span data-stu-id="c803d-129">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
