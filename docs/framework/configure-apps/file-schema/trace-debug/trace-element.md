---
title: "&lt;İzleme&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace
- http://schemas.microsoft.com/.NetConfiguration/v2.0#trace
helpviewer_keywords:
- <trace> element
- listeners
- trace element
- trace listener, <trace> element
ms.assetid: 7931c942-63c1-47c3-a045-9d9de3cacdbf
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 157adb6c7317aa047976cdb9e30711d20c9e543b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="lttracegt-element"></a><span data-ttu-id="d30de-102">&lt;İzleme&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="d30de-102">&lt;trace&gt; Element</span></span>
<span data-ttu-id="d30de-103">Toplamak, depolamak ve izleme iletilerini yönlendirmek dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="d30de-103">Contains listeners that collect, store, and route tracing messages.</span></span>  
  
 <span data-ttu-id="d30de-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="d30de-104">\<configuration></span></span>  
<span data-ttu-id="d30de-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="d30de-105">\<system.diagnostics></span></span>  
<span data-ttu-id="d30de-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="d30de-106">\<trace></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d30de-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d30de-107">Syntax</span></span>  
  
```xml  
<trace autoflush="true|false"   
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d30de-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d30de-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d30de-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d30de-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d30de-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d30de-110">Attributes</span></span>  
  
|<span data-ttu-id="d30de-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d30de-111">Attribute</span></span>|<span data-ttu-id="d30de-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d30de-112">Description</span></span>|  
|---------------|-----------------|  
|`autoflush`|<span data-ttu-id="d30de-113">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d30de-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="d30de-114">İzleme dinleyicileri çıkış arabelleği sonra her yazma işlemi otomatik olarak temizleme olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d30de-114">Specifies whether the trace listeners automatically flush the output buffer after every write operation.</span></span>|  
|`indentsize`|<span data-ttu-id="d30de-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d30de-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="d30de-116">Girinti alanları sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d30de-116">Specifies the number of spaces to indent.</span></span>|  
|`useGlobalLock`|<span data-ttu-id="d30de-117">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d30de-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="d30de-118">Genel kilit kullanılması gerekip gerekmediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d30de-118">Indicates whether the global lock should be used.</span></span>|  
  
## <a name="autoflush-attribute"></a><span data-ttu-id="d30de-119">AutoFlush özniteliği</span><span class="sxs-lookup"><span data-stu-id="d30de-119">autoflush Attribute</span></span>  
  
|<span data-ttu-id="d30de-120">Değer</span><span class="sxs-lookup"><span data-stu-id="d30de-120">Value</span></span>|<span data-ttu-id="d30de-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d30de-121">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="d30de-122">Otomatik olarak çıkış arabelleği temizleme değil.</span><span class="sxs-lookup"><span data-stu-id="d30de-122">Does not automatically flush the output buffer.</span></span> <span data-ttu-id="d30de-123">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="d30de-123">This is the default.</span></span>|  
|`true`|<span data-ttu-id="d30de-124">Çıkış arabelleği otomatik olarak boşaltır.</span><span class="sxs-lookup"><span data-stu-id="d30de-124">Automatically flushes the output buffer.</span></span>|  
  
## <a name="usegloballock-attribute"></a><span data-ttu-id="d30de-125">useGlobalLock özniteliği</span><span class="sxs-lookup"><span data-stu-id="d30de-125">useGlobalLock Attribute</span></span>  
  
|<span data-ttu-id="d30de-126">Değer</span><span class="sxs-lookup"><span data-stu-id="d30de-126">Value</span></span>|<span data-ttu-id="d30de-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d30de-127">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="d30de-128">Dinleyici iş parçacığı içinde korumalı ise genel kilit kullanmaz; Aksi takdirde, genel kilit kullanır.</span><span class="sxs-lookup"><span data-stu-id="d30de-128">Does not use the global lock if the listener is thread safe; otherwise, uses the global lock.</span></span>|  
|`true`|<span data-ttu-id="d30de-129">Dinleyici iş parçacığı güvenli olmasına bakılmaksızın genel kilit kullanır.</span><span class="sxs-lookup"><span data-stu-id="d30de-129">Uses the global lock regardless of whether the listener is thread safe.</span></span> <span data-ttu-id="d30de-130">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="d30de-130">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d30de-131">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d30de-131">Child Elements</span></span>  
  
|<span data-ttu-id="d30de-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="d30de-132">Element</span></span>|<span data-ttu-id="d30de-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d30de-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d30de-134">\<dinleyicileri ></span><span class="sxs-lookup"><span data-stu-id="d30de-134">\<listeners></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-trace.md)|<span data-ttu-id="d30de-135">Toplar, depolar, bir dinleyici belirtir ve iletileri yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="d30de-135">Specifies a listener that collects, stores, and routes messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d30de-136">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d30de-136">Parent Elements</span></span>  
  
|<span data-ttu-id="d30de-137">Öğe</span><span class="sxs-lookup"><span data-stu-id="d30de-137">Element</span></span>|<span data-ttu-id="d30de-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d30de-138">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d30de-139">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="d30de-139">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="d30de-140">Toplamak, depolamak ve iletileri ve izleme anahtarı ayarlandığı düzeyi rota izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d30de-140">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d30de-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="d30de-141">Example</span></span>  
 <span data-ttu-id="d30de-142">Aşağıdaki örnekte nasıl kullanılacağını gösterir `<trace>` dinleyicisi eklemek için öğesi `MyListener` için `Listeners` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d30de-142">The following example shows how to use the `<trace>` element to add the listener `MyListener` to the `Listeners` collection.</span></span> <span data-ttu-id="d30de-143">`MyListener`adlı bir dosya oluşturur `MyListener.log` ve çıkış dosyasına yazar.</span><span class="sxs-lookup"><span data-stu-id="d30de-143">`MyListener` creates a file that is named `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="d30de-144">`useGlobalLock` Özniteliği `false`, İzleme dinleyicisi iş parçacığı içinde korumalı ise kullanılmayacak genel kilit neden olur.</span><span class="sxs-lookup"><span data-stu-id="d30de-144">The `useGlobalLock` attribute is set to `false`, which causes the global lock not to be used if the trace listener is thread safe.</span></span> <span data-ttu-id="d30de-145">`autoflush` Özniteliği `true`, bağımsız olarak mı yoksa dosyaya yazmak İzleme dinleyicisi neden olan <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="d30de-145">The `autoflush` attribute is set to `true`, which causes the trace listener to write to the file regardless of whether the <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> method is called.</span></span> <span data-ttu-id="d30de-146">`indentsize` Özniteliği sıfır alanları girinti dinleyicisi neden olan 0 (sıfır) olarak ayarlanmış olduğunda <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="d30de-146">The `indentsize` attribute is set to 0 (zero), which causes the listener to indent zero spaces when the <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> method is called.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace useGlobalLock="false" autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d30de-147">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d30de-147">See Also</span></span>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 [<span data-ttu-id="d30de-148">İzleme ve hata ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="d30de-148">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
