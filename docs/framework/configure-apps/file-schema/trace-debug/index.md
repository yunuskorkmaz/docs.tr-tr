---
description: 'Daha fazla bilgi edinin: Izleme ve hata ayıklama ayarları şeması'
title: İzleme ve Hata Ayıklama Ayarları Şeması
ms.date: 03/30/2017
helpviewer_keywords:
- tracing [.NET Framework], trace and debug settings schema
- configuration schema [.NET Framework], trace and debug settings
- configuration settings [.NET Framework], tracing
- schema configuration settings
- configuration settings [.NET Framework], debugging
- trace listeners, trace and debug settings schema
- configuration sections [.NET Framework]
- elements [.NET Framework], trace and debug settings
ms.assetid: 277ca5f6-e1c4-41b6-a47f-3a67ce5b94ac
ms.openlocfilehash: 2429585c44952d2ee12547dab8f51662295bf02f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639659"
---
# <a name="trace-and-debug-settings-schema"></a><span data-ttu-id="303b9-103">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="303b9-103">Trace and Debug Settings Schema</span></span>

<span data-ttu-id="303b9-104">İzleme ve hata ayıklama ayarları, iletileri toplama, depolama ve yönlendiren izleme dinleyicilerini ve bir izleme anahtarının ayarlandığı düzeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="303b9-104">Trace and debug settings specify trace listeners that collect, store, and route messages, and the level where a trace switch is set.</span></span>  
  
 <span data-ttu-id="303b9-105">Aşağıdaki tabloda, her bir izleme ve hata ayıklama ayarları öğesinin işlevi açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="303b9-105">The following table describes the function of each trace and debug settings element.</span></span>  
  
|<span data-ttu-id="303b9-106">Öğe</span><span class="sxs-lookup"><span data-stu-id="303b9-106">Element</span></span>|<span data-ttu-id="303b9-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="303b9-107">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-source.md)|<span data-ttu-id="303b9-108">`Listeners`İzleme kaynağı için koleksiyona bir dinleyici ekler.</span><span class="sxs-lookup"><span data-stu-id="303b9-108">Adds a listener to the `Listeners` collection for a trace source.</span></span>|  
|[\<add>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="303b9-109">Koleksiyona bir dinleyici ekler `Listeners` .</span><span class="sxs-lookup"><span data-stu-id="303b9-109">Adds a listener to the `Listeners` collection.</span></span>|  
|[\<add>](add-element-for-sharedlisteners.md)|<span data-ttu-id="303b9-110">Koleksiyona bir dinleyici ekler `sharedListeners` .</span><span class="sxs-lookup"><span data-stu-id="303b9-110">Adds a listener to the `sharedListeners` collection.</span></span>|  
|[\<add>](add-element-for-switches.md)|<span data-ttu-id="303b9-111">Bir izleme anahtarının ayarlandığı düzeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="303b9-111">Specifies the level where a trace switch is set.</span></span>|  
|[\<assert>](assert-element.md)|<span data-ttu-id="303b9-112">Yöntemini çağırdığınızda bir ileti kutusunun görüntülenip görüntülenmeyeceğini belirtir <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> ; Ayrıca, iletilerin yazılacağı dosyanın adını da belirtir.</span><span class="sxs-lookup"><span data-stu-id="303b9-112">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>|  
|[\<clear>](clear-element-for-listeners-for-source.md)|<span data-ttu-id="303b9-113">`Listeners`İzleme kaynağı için koleksiyonu temizler.</span><span class="sxs-lookup"><span data-stu-id="303b9-113">Clears the `Listeners` collection for a trace source.</span></span>|  
|[\<clear>](clear-element-for-listeners-for-trace.md)|<span data-ttu-id="303b9-114">`Listeners`İzleme için koleksiyonu temizler.</span><span class="sxs-lookup"><span data-stu-id="303b9-114">Clears the `Listeners` collection for trace.</span></span>|  
|[\<filter>](filter-element-for-add-for-listeners-for-source.md)|<span data-ttu-id="303b9-115">İzleme kaynağı için koleksiyondaki bir dinleyiciye bir filtre ekler `Listeners` .</span><span class="sxs-lookup"><span data-stu-id="303b9-115">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>|  
|[\<filter>](filter-element-for-add-for-listeners-for-trace.md)|<span data-ttu-id="303b9-116">İzleme için koleksiyondaki bir dinleyiciye bir filtre ekler `Listeners` .</span><span class="sxs-lookup"><span data-stu-id="303b9-116">Adds a filter to a listener in the `Listeners` collection for trace.</span></span>|  
|[\<filter>](filter-element-for-add-for-sharedlisteners.md)|<span data-ttu-id="303b9-117">Koleksiyondaki bir dinleyiciye bir filtre ekler `sharedListeners` .</span><span class="sxs-lookup"><span data-stu-id="303b9-117">Adds a filter to a listener in the `sharedListeners` collection.</span></span>|  
|[\<listeners>](listeners-element-for-source.md)|<span data-ttu-id="303b9-118">`Listeners`İzleme kaynağı için koleksiyon dinleyicileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="303b9-118">Specifies listeners for the `Listeners` collection for a trace source.</span></span>|  
|[\<listeners>](listeners-element-for-trace.md)|<span data-ttu-id="303b9-119">İzleme koleksiyonu için dinleyicileri belirtir `Listeners` .</span><span class="sxs-lookup"><span data-stu-id="303b9-119">Specifies listeners for the `Listeners` collection for trace.</span></span>|  
|[\<performanceCounters>](performancecounters-element.md)|<span data-ttu-id="303b9-120">Performans sayaçları tarafından paylaşılan genel belleğin boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="303b9-120">Specifies the size of the global memory shared by performance counters.</span></span>|  
|[\<remove>](remove-element-for-listeners-for-trace.md)|<span data-ttu-id="303b9-121">`Listeners`İzleme için koleksiyondan bir dinleyici kaldırır.</span><span class="sxs-lookup"><span data-stu-id="303b9-121">Removes a listener from the `Listeners` collection for trace.</span></span>|  
|[\<remove>](remove-element-for-listeners-for-source.md)|<span data-ttu-id="303b9-122">`Listeners`İzleme kaynağı için koleksiyondan bir dinleyiciyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="303b9-122">Removes a listener from the `Listeners` collection for a trace source.</span></span>|  
|[\<sharedListeners>](sharedlisteners-element.md)|<span data-ttu-id="303b9-123">Herhangi bir kaynak veya izleme öğesinin başvurmasına yönelik dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="303b9-123">Contains listeners that any source or trace element can reference.</span></span>|  
|[\<sources>](sources-element.md)|<span data-ttu-id="303b9-124">İzleme iletilerini Başlatan izleme kaynaklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="303b9-124">Contains trace sources that initiate tracing messages.</span></span>|  
|[\<source>](source-element.md)|<span data-ttu-id="303b9-125">İzleme iletilerini Başlatan bir izleme kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="303b9-125">Specifies a trace source that initiates tracing messages.</span></span>|  
|[\<switches>](switches-element.md)|<span data-ttu-id="303b9-126">İzleme anahtarlarını ve izleme anahtarlarının ayarlandığı düzeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="303b9-126">Contains trace switches and the level where the trace switches are set.</span></span>|  
|[\<system.diagnostics>](system-diagnostics-element.md)|<span data-ttu-id="303b9-127">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="303b9-127">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|[\<trace>](trace-element.md)|<span data-ttu-id="303b9-128">İzleme iletilerini toplayıp depolayan, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="303b9-128">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="303b9-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="303b9-129">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="303b9-130">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="303b9-130">Configuration File Schema</span></span>](../index.md)
