---
title: < System.diagnostics > öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
ms.openlocfilehash: 026805ffb9b89aa55e84cf9a5c4afb8ed63cec09
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142720"
---
# <a name="systemdiagnostics-element"></a><span data-ttu-id="ca49a-102">\<System.Diagnostics > öğesi</span><span class="sxs-lookup"><span data-stu-id="ca49a-102">\<system.diagnostics> Element</span></span>
<span data-ttu-id="ca49a-103">Toplamak, depolamak ve iletileri ve bir izleme anahtarı ayarlandığı düzeyi izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ca49a-103">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>  
  
 <span data-ttu-id="ca49a-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="ca49a-104">\<configuration></span></span>  
<span data-ttu-id="ca49a-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="ca49a-105">\<system.diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca49a-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ca49a-106">Syntax</span></span>  
  
```xml  
<system.diagnostics>   
</system.diagnostics>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ca49a-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ca49a-107">Attributes and Elements</span></span>  
 <span data-ttu-id="ca49a-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ca49a-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ca49a-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ca49a-109">Attributes</span></span>  
 <span data-ttu-id="ca49a-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="ca49a-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ca49a-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ca49a-111">Child Elements</span></span>  
  
|<span data-ttu-id="ca49a-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="ca49a-112">Element</span></span>|<span data-ttu-id="ca49a-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ca49a-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ca49a-114">\<Assert ></span><span class="sxs-lookup"><span data-stu-id="ca49a-114">\<assert></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/assert-element.md)|<span data-ttu-id="ca49a-115">Bir ileti kutusu çağırdığınızda görüntülenip görüntülenmeyeceğini belirtir <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> yöntemi de ileti yazmak için dosya adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ca49a-115">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>|  
|[<span data-ttu-id="ca49a-116">\<performanceCounters ></span><span class="sxs-lookup"><span data-stu-id="ca49a-116">\<performanceCounters></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/performancecounters-element.md)|<span data-ttu-id="ca49a-117">Performans sayaçlarını birer paylaşılan genel bellek boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="ca49a-117">Specifies the size of the global memory shared by performance counters.</span></span>|  
|[<span data-ttu-id="ca49a-118">\<sharedListeners ></span><span class="sxs-lookup"><span data-stu-id="ca49a-118">\<sharedListeners></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)|<span data-ttu-id="ca49a-119">Herhangi bir kaynak veya trace ögesi başvurabilirsiniz dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="ca49a-119">Contains listeners that any source or trace element can reference.</span></span> <span data-ttu-id="ca49a-120">Paylaşılan dinleyiciler tanımlanan dinleyicileri adına göre kaynakları veya izlemeleri eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="ca49a-120">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>|  
|[<span data-ttu-id="ca49a-121">\<Kaynakları ></span><span class="sxs-lookup"><span data-stu-id="ca49a-121">\<sources></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sources-element.md)|<span data-ttu-id="ca49a-122">İzleme iletileri başlatmak iz kaynakları belirtir.</span><span class="sxs-lookup"><span data-stu-id="ca49a-122">Specifies trace sources that initiate tracing messages.</span></span>|  
|[<span data-ttu-id="ca49a-123">\<anahtarlar ></span><span class="sxs-lookup"><span data-stu-id="ca49a-123">\<switches></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/switches-element.md)|<span data-ttu-id="ca49a-124">İzleme anahtarları ve izleme anahtarları ayarlandığı düzeyleri içerir.</span><span class="sxs-lookup"><span data-stu-id="ca49a-124">Contains trace switches and the levels where the trace switches are set.</span></span>|  
|[<span data-ttu-id="ca49a-125">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="ca49a-125">\<trace></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)|<span data-ttu-id="ca49a-126">Toplamak, depolamak ve izleme iletilerini yönlendirmek dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="ca49a-126">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ca49a-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ca49a-127">Parent Elements</span></span>  
  
|<span data-ttu-id="ca49a-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="ca49a-128">Element</span></span>|<span data-ttu-id="ca49a-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ca49a-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ca49a-130">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="ca49a-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ca49a-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="ca49a-131">Example</span></span>  
 <span data-ttu-id="ca49a-132">Aşağıdaki örnek bir izleme anahtarı ve içinde bir izleme dinleyicisi ekleme gösterir  **\<system.diagnostics >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="ca49a-132">The following example shows how to embed a trace switch and a trace listener inside the **\<system.diagnostics>** element.</span></span> <span data-ttu-id="ca49a-133">`General` İzleme anahtarını ayarlayın <xref:System.Diagnostics.TraceLevel> düzeyi.</span><span class="sxs-lookup"><span data-stu-id="ca49a-133">The `General` trace switch is set to the <xref:System.Diagnostics.TraceLevel> level.</span></span> <span data-ttu-id="ca49a-134">İzleme dinleyicisi `myListener` adlı bir dosya oluşturur `MyListener.log` ve çıkış dosyasına yazar.</span><span class="sxs-lookup"><span data-stu-id="ca49a-134">The trace listener `myListener` creates a file called `MyListener.log` and writes the output to the file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ca49a-135">.NET Framework sürüm 2. 0'da, metin anahtar değeri belirtmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca49a-135">In the .NET Framework version 2.0, you can use text to specify the value for a switch.</span></span> <span data-ttu-id="ca49a-136">Örneğin, belirtebilirsiniz `true` için bir <xref:System.Diagnostics.BooleanSwitch> veya bir sabit listesi değeri gibi temsil eden metin `Error` için bir <xref:System.Diagnostics.TraceSwitch>.</span><span class="sxs-lookup"><span data-stu-id="ca49a-136">For example, you can specify `true` for a <xref:System.Diagnostics.BooleanSwitch> or use the text representing an enumeration value such as `Error` for a <xref:System.Diagnostics.TraceSwitch>.</span></span> <span data-ttu-id="ca49a-137">Satır `<add name="myTraceSwitch" value="Error" />` eşdeğerdir `<add name="myTraceSwitch" value="1" />`.</span><span class="sxs-lookup"><span data-stu-id="ca49a-137">The line `<add name="myTraceSwitch" value="Error" />` is equivalent to `<add name="myTraceSwitch" value="1" />`.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
      </switches>  
      <trace autoflush="true" indentsize="2">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="MyListener.log" traceOutputOptions="ProcessId, LogicalOperationStack, Timestamp, ThreadId, Callstack, DateTime" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ca49a-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca49a-138">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="ca49a-139">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="ca49a-139">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
