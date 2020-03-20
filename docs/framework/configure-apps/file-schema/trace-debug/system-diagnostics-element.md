---
title: <sistemi.tanılama> Elemanı
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
ms.openlocfilehash: 4f831592d7d178276b1625e1ef7d8512085342af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153213"
---
# <a name="systemdiagnostics-element"></a><span data-ttu-id="1adf5-102">\<system.diagnostics> Element</span><span class="sxs-lookup"><span data-stu-id="1adf5-102">\<system.diagnostics> Element</span></span>
<span data-ttu-id="1adf5-103">İletileri toplayan, depolayan ve yönlendiren izleme dinleyicilerini ve izleme anahtarının ayarlandığı düzeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="1adf5-103">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>  
  
[<span data-ttu-id="1adf5-104">**\<yapılandırma>**</span><span class="sxs-lookup"><span data-stu-id="1adf5-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="1adf5-105">&nbsp;&nbsp;**\<system.diagnostics>**</span><span class="sxs-lookup"><span data-stu-id="1adf5-105">&nbsp;&nbsp;**\<system.diagnostics>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1adf5-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1adf5-106">Syntax</span></span>  
  
```xml  
<system.diagnostics>
</system.diagnostics>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1adf5-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1adf5-107">Attributes and Elements</span></span>  
 <span data-ttu-id="1adf5-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1adf5-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1adf5-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1adf5-109">Attributes</span></span>  
 <span data-ttu-id="1adf5-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="1adf5-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1adf5-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1adf5-111">Child Elements</span></span>  
  
|<span data-ttu-id="1adf5-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="1adf5-112">Element</span></span>|<span data-ttu-id="1adf5-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1adf5-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1adf5-114">\<>iddia</span><span class="sxs-lookup"><span data-stu-id="1adf5-114">\<assert></span></span>](assert-element.md)|<span data-ttu-id="1adf5-115">Yöntemi aradiğinizde ileti kutusunun görüntülenip <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> görüntülenip görüntülenmeyeceğini belirtir; ayrıca ileti yazacak dosyanın adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1adf5-115">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>|  
|[<span data-ttu-id="1adf5-116">\<performansSayaçları></span><span class="sxs-lookup"><span data-stu-id="1adf5-116">\<performanceCounters></span></span>](performancecounters-element.md)|<span data-ttu-id="1adf5-117">Performans sayaçları tarafından paylaşılan genel belleğin boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1adf5-117">Specifies the size of the global memory shared by performance counters.</span></span>|  
|[<span data-ttu-id="1adf5-118">\<paylaşılanDinleyiciler></span><span class="sxs-lookup"><span data-stu-id="1adf5-118">\<sharedListeners></span></span>](sharedlisteners-element.md)|<span data-ttu-id="1adf5-119">Herhangi bir kaynak veya izleme öğesinin başvuruedebileceği dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="1adf5-119">Contains listeners that any source or trace element can reference.</span></span> <span data-ttu-id="1adf5-120">Paylaşılan dinleyici olarak tanımlanan dinleyiciler kaynaklara veya izadile eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="1adf5-120">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>|  
|[<span data-ttu-id="1adf5-121">\<kaynaklar></span><span class="sxs-lookup"><span data-stu-id="1adf5-121">\<sources></span></span>](sources-element.md)|<span data-ttu-id="1adf5-122">İletileri izlemeyi başlatan izleme kaynaklarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1adf5-122">Specifies trace sources that initiate tracing messages.</span></span>|  
|[<span data-ttu-id="1adf5-123">\<anahtarları></span><span class="sxs-lookup"><span data-stu-id="1adf5-123">\<switches></span></span>](switches-element.md)|<span data-ttu-id="1adf5-124">İzleme anahtarları ve izleme anahtarlarının ayarlandığı düzeyleri içerir.</span><span class="sxs-lookup"><span data-stu-id="1adf5-124">Contains trace switches and the levels where the trace switches are set.</span></span>|  
|[<span data-ttu-id="1adf5-125">\<izleme></span><span class="sxs-lookup"><span data-stu-id="1adf5-125">\<trace></span></span>](trace-element.md)|<span data-ttu-id="1adf5-126">İletileri toplayan, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="1adf5-126">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1adf5-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1adf5-127">Parent Elements</span></span>  
  
|<span data-ttu-id="1adf5-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="1adf5-128">Element</span></span>|<span data-ttu-id="1adf5-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1adf5-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1adf5-130">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="1adf5-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1adf5-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="1adf5-131">Example</span></span>  
 <span data-ttu-id="1adf5-132">Aşağıdaki örnek, \*\* \<sistemin\*\* içine izleme anahtarı ve izleme dinleyicisi nasıl yerleştirilir gösterilmektedir.tanılama>öğesi.</span><span class="sxs-lookup"><span data-stu-id="1adf5-132">The following example shows how to embed a trace switch and a trace listener inside the **\<system.diagnostics>** element.</span></span> <span data-ttu-id="1adf5-133">`General` İzleme anahtarı düzeye <xref:System.Diagnostics.TraceLevel> ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="1adf5-133">The `General` trace switch is set to the <xref:System.Diagnostics.TraceLevel> level.</span></span> <span data-ttu-id="1adf5-134">İzleme dinleyicisi `myListener` adlı `MyListener.log` bir dosya oluşturur ve çıktıyı dosyaya yazar.</span><span class="sxs-lookup"><span data-stu-id="1adf5-134">The trace listener `myListener` creates a file called `MyListener.log` and writes the output to the file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1adf5-135">.NET Framework sürüm 2.0'da, bir anahtarın değerini belirtmek için metni kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1adf5-135">In the .NET Framework version 2.0, you can use text to specify the value for a switch.</span></span> <span data-ttu-id="1adf5-136">Örneğin, `true` bir <xref:System.Diagnostics.BooleanSwitch> için belirtebilir veya bir `Error` <xref:System.Diagnostics.TraceSwitch>. gibi numaralandırma değerini temsil eden metni kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1adf5-136">For example, you can specify `true` for a <xref:System.Diagnostics.BooleanSwitch> or use the text representing an enumeration value such as `Error` for a <xref:System.Diagnostics.TraceSwitch>.</span></span> <span data-ttu-id="1adf5-137">Satır `<add name="myTraceSwitch" value="Error" />` ' a `<add name="myTraceSwitch" value="1" />`eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="1adf5-137">The line `<add name="myTraceSwitch" value="Error" />` is equivalent to `<add name="myTraceSwitch" value="1" />`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1adf5-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1adf5-138">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="1adf5-139">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="1adf5-139">Trace and Debug Settings Schema</span></span>](index.md)
