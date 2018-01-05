---
title: "İzleme ve Hata Ayıklama Ayarları Şeması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: e6d9e5ca97e4d5940dd9de3f3ffbd4db4183196c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="trace-and-debug-settings-schema"></a><span data-ttu-id="85b95-102">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="85b95-102">Trace and Debug Settings Schema</span></span>
<span data-ttu-id="85b95-103">İzleme ve hata ayıklama ayarları toplamak, depolamak ve iletileri ve izleme anahtarı ayarlandığı düzeyi rota izleme dinleyicileri belirtin.</span><span class="sxs-lookup"><span data-stu-id="85b95-103">Trace and debug settings specify trace listeners that collect, store, and route messages, and the level where a trace switch is set.</span></span>  
  
 <span data-ttu-id="85b95-104">Aşağıdaki tabloda her izleme ve hata ayıklama ayarları öğesi işlevi açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="85b95-104">The following table describes the function of each trace and debug settings element.</span></span>  
  
|<span data-ttu-id="85b95-105">Öğe</span><span class="sxs-lookup"><span data-stu-id="85b95-105">Element</span></span>|<span data-ttu-id="85b95-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="85b95-106">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="85b95-107">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="85b95-107">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-source.md)|<span data-ttu-id="85b95-108">Bir dinleyici ekler `Listeners` koleksiyonu için bir izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="85b95-108">Adds a listener to the `Listeners` collection for a trace source.</span></span>|  
|[<span data-ttu-id="85b95-109">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="85b95-109">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|<span data-ttu-id="85b95-110">Bir dinleyici ekler `Listeners` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="85b95-110">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="85b95-111">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="85b95-111">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-sharedlisteners.md)|<span data-ttu-id="85b95-112">Bir dinleyici ekler `sharedListeners` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="85b95-112">Adds a listener to the `sharedListeners` collection.</span></span>|  
|[<span data-ttu-id="85b95-113">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="85b95-113">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-switches.md)|<span data-ttu-id="85b95-114">İzleme anahtarı ayarlandığı düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="85b95-114">Specifies the level where a trace switch is set.</span></span>|  
|[<span data-ttu-id="85b95-115">\<Assert ></span><span class="sxs-lookup"><span data-stu-id="85b95-115">\<assert></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/assert-element.md)|<span data-ttu-id="85b95-116">Bir ileti kutusu çağırdığınızda görüntülenip görüntülenmeyeceğini belirtir <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> yöntemi; ayrıca iletileri yazmak için dosya adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="85b95-116">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>|  
|[<span data-ttu-id="85b95-117">\<Clear ></span><span class="sxs-lookup"><span data-stu-id="85b95-117">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)|<span data-ttu-id="85b95-118">Temizler `Listeners` koleksiyonu için bir izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="85b95-118">Clears the `Listeners` collection for a trace source.</span></span>|  
|[<span data-ttu-id="85b95-119">\<Clear ></span><span class="sxs-lookup"><span data-stu-id="85b95-119">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-trace.md)|<span data-ttu-id="85b95-120">Temizler `Listeners` izleme için koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="85b95-120">Clears the `Listeners` collection for trace.</span></span>|  
|[<span data-ttu-id="85b95-121">\<Filtre ></span><span class="sxs-lookup"><span data-stu-id="85b95-121">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-source.md)|<span data-ttu-id="85b95-122">Bir dinleyici için bir filtre ekler `Listeners` koleksiyonu için bir izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="85b95-122">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>|  
|[<span data-ttu-id="85b95-123">\<Filtre ></span><span class="sxs-lookup"><span data-stu-id="85b95-123">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-trace.md)|<span data-ttu-id="85b95-124">Bir dinleyici için bir filtre ekler `Listeners` izleme için koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="85b95-124">Adds a filter to a listener in the `Listeners` collection for trace.</span></span>|  
|[<span data-ttu-id="85b95-125">\<Filtre ></span><span class="sxs-lookup"><span data-stu-id="85b95-125">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-sharedlisteners.md)|<span data-ttu-id="85b95-126">Bir dinleyici için bir filtre ekler `sharedListeners` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="85b95-126">Adds a filter to a listener in the `sharedListeners` collection.</span></span>|  
|[<span data-ttu-id="85b95-127">\<dinleyicileri ></span><span class="sxs-lookup"><span data-stu-id="85b95-127">\<listeners></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-source.md)|<span data-ttu-id="85b95-128">Dinleyicileri için belirtir `Listeners` koleksiyonu için bir izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="85b95-128">Specifies listeners for the `Listeners` collection for a trace source.</span></span>|  
|[<span data-ttu-id="85b95-129">\<dinleyicileri ></span><span class="sxs-lookup"><span data-stu-id="85b95-129">\<listeners></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-trace.md)|<span data-ttu-id="85b95-130">Dinleyicileri için belirtir `Listeners` izleme için koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="85b95-130">Specifies listeners for the `Listeners` collection for trace.</span></span>|  
|[<span data-ttu-id="85b95-131">\<performans sayaçları ></span><span class="sxs-lookup"><span data-stu-id="85b95-131">\<performanceCounters></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/performancecounters-element.md)|<span data-ttu-id="85b95-132">Performans sayaçları tarafından paylaşılan genel bellek boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="85b95-132">Specifies the size of the global memory shared by performance counters.</span></span>|  
|[<span data-ttu-id="85b95-133">\<kaldırma ></span><span class="sxs-lookup"><span data-stu-id="85b95-133">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)|<span data-ttu-id="85b95-134">Gelen bir dinleyici kaldırır `Listeners` izleme için koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="85b95-134">Removes a listener from the `Listeners` collection for trace.</span></span>|  
|[<span data-ttu-id="85b95-135">\<kaldırma ></span><span class="sxs-lookup"><span data-stu-id="85b95-135">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-source.md)|<span data-ttu-id="85b95-136">Gelen bir dinleyici kaldırır `Listeners` koleksiyonu için bir izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="85b95-136">Removes a listener from the `Listeners` collection for a trace source.</span></span>|  
|[<span data-ttu-id="85b95-137">\<sharedListeners ></span><span class="sxs-lookup"><span data-stu-id="85b95-137">\<sharedListeners></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)|<span data-ttu-id="85b95-138">Herhangi bir kaynak veya trace ögesi başvurabilir dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="85b95-138">Contains listeners that any source or trace element can reference.</span></span>|  
|[<span data-ttu-id="85b95-139">\<Kaynakları ></span><span class="sxs-lookup"><span data-stu-id="85b95-139">\<sources></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sources-element.md)|<span data-ttu-id="85b95-140">İzleme iletileri başlatmak izleme kaynaklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="85b95-140">Contains trace sources that initiate tracing messages.</span></span>|  
|[<span data-ttu-id="85b95-141">\<Kaynak ></span><span class="sxs-lookup"><span data-stu-id="85b95-141">\<source></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)|<span data-ttu-id="85b95-142">İzleme iletileri başlatan bir izleme kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="85b95-142">Specifies a trace source that initiates tracing messages.</span></span>|  
|[<span data-ttu-id="85b95-143">\<anahtarları ></span><span class="sxs-lookup"><span data-stu-id="85b95-143">\<switches></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/switches-element.md)|<span data-ttu-id="85b95-144">İzleme anahtarları ve izleme anahtarları belirlendiği düzeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="85b95-144">Contains trace switches and the level where the trace switches are set.</span></span>|  
|[<span data-ttu-id="85b95-145">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="85b95-145">\<system.diagnostics></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/system-diagnostics-element.md)|<span data-ttu-id="85b95-146">Toplamak, depolamak ve iletileri ve izleme anahtarı ayarlandığı düzeyi rota izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="85b95-146">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|[<span data-ttu-id="85b95-147">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="85b95-147">\<trace></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)|<span data-ttu-id="85b95-148">Toplamak, depolamak ve izleme iletilerini yönlendirmek dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="85b95-148">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="85b95-149">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="85b95-149">See Also</span></span>  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.Debug>  
 [<span data-ttu-id="85b95-150">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="85b95-150">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
