---
title: <System. Diagnostics> öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
ms.openlocfilehash: aff324ac9952c95c78d7ca15572651dba23b79b7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195174"
---
# <a name="systemdiagnostics-element"></a><span data-ttu-id="821e9-102">\<system.diagnostics> Öğesi</span><span class="sxs-lookup"><span data-stu-id="821e9-102">\<system.diagnostics> Element</span></span>

<span data-ttu-id="821e9-103">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="821e9-103">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.diagnostics>**  
  
## <a name="syntax"></a><span data-ttu-id="821e9-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="821e9-104">Syntax</span></span>  
  
```xml  
<system.diagnostics>
</system.diagnostics>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="821e9-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="821e9-105">Attributes and Elements</span></span>  

 <span data-ttu-id="821e9-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="821e9-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="821e9-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="821e9-107">Attributes</span></span>  

 <span data-ttu-id="821e9-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="821e9-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="821e9-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="821e9-109">Child Elements</span></span>  
  
|<span data-ttu-id="821e9-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="821e9-110">Element</span></span>|<span data-ttu-id="821e9-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="821e9-111">Description</span></span>|  
|-------------|-----------------|  
|[\<assert>](assert-element.md)|<span data-ttu-id="821e9-112">Yöntemini çağırdığınızda bir ileti kutusunun görüntülenip görüntülenmeyeceğini belirtir <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> ; Ayrıca, iletilerin yazılacağı dosyanın adını da belirtir.</span><span class="sxs-lookup"><span data-stu-id="821e9-112">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>|  
|[\<performanceCounters>](performancecounters-element.md)|<span data-ttu-id="821e9-113">Performans sayaçları tarafından paylaşılan genel belleğin boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="821e9-113">Specifies the size of the global memory shared by performance counters.</span></span>|  
|[\<sharedListeners>](sharedlisteners-element.md)|<span data-ttu-id="821e9-114">Herhangi bir kaynak veya izleme öğesinin başvurmasına yönelik dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="821e9-114">Contains listeners that any source or trace element can reference.</span></span> <span data-ttu-id="821e9-115">Paylaşılan dinleyiciler ada göre kaynaklara veya izlemelere eklenebilir olarak tanımlanan dinleyiciler.</span><span class="sxs-lookup"><span data-stu-id="821e9-115">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>|  
|[\<sources>](sources-element.md)|<span data-ttu-id="821e9-116">İzleme iletilerini Başlatan izleme kaynaklarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="821e9-116">Specifies trace sources that initiate tracing messages.</span></span>|  
|[\<switches>](switches-element.md)|<span data-ttu-id="821e9-117">İzleme anahtarlarını ve izleme anahtarlarının ayarlandığı düzeyleri içerir.</span><span class="sxs-lookup"><span data-stu-id="821e9-117">Contains trace switches and the levels where the trace switches are set.</span></span>|  
|[\<trace>](trace-element.md)|<span data-ttu-id="821e9-118">İzleme iletilerini toplayıp depolayan, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="821e9-118">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="821e9-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="821e9-119">Parent Elements</span></span>  
  
|<span data-ttu-id="821e9-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="821e9-120">Element</span></span>|<span data-ttu-id="821e9-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="821e9-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="821e9-122">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="821e9-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="821e9-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="821e9-123">Example</span></span>  

 <span data-ttu-id="821e9-124">Aşağıdaki örnek, bir izleme anahtarı ve bir İzleme dinleyicisinin öğenin içine nasıl ekleneceğini gösterir **\<system.diagnostics>** .</span><span class="sxs-lookup"><span data-stu-id="821e9-124">The following example shows how to embed a trace switch and a trace listener inside the **\<system.diagnostics>** element.</span></span> <span data-ttu-id="821e9-125">`General`İzleme anahtarı düzeyi olarak ayarlanır <xref:System.Diagnostics.TraceLevel> .</span><span class="sxs-lookup"><span data-stu-id="821e9-125">The `General` trace switch is set to the <xref:System.Diagnostics.TraceLevel> level.</span></span> <span data-ttu-id="821e9-126">İzleme dinleyicisi `myListener` adlı bir dosya oluşturur `MyListener.log` ve çıktıyı dosyaya yazar.</span><span class="sxs-lookup"><span data-stu-id="821e9-126">The trace listener `myListener` creates a file called `MyListener.log` and writes the output to the file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="821e9-127">.NET Framework sürüm 2,0 ' de, bir anahtarın değerini belirtmek için metin kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="821e9-127">In the .NET Framework version 2.0, you can use text to specify the value for a switch.</span></span> <span data-ttu-id="821e9-128">Örneğin, `true` için bir <xref:System.Diagnostics.BooleanSwitch> veya gibi bir numaralandırma değerini temsil eden metni kullanabilirsiniz `Error` <xref:System.Diagnostics.TraceSwitch> .</span><span class="sxs-lookup"><span data-stu-id="821e9-128">For example, you can specify `true` for a <xref:System.Diagnostics.BooleanSwitch> or use the text representing an enumeration value such as `Error` for a <xref:System.Diagnostics.TraceSwitch>.</span></span> <span data-ttu-id="821e9-129">Satır `<add name="myTraceSwitch" value="Error" />` ile eşdeğerdir `<add name="myTraceSwitch" value="1" />` .</span><span class="sxs-lookup"><span data-stu-id="821e9-129">The line `<add name="myTraceSwitch" value="Error" />` is equivalent to `<add name="myTraceSwitch" value="1" />`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="821e9-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="821e9-130">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="821e9-131">İzleme ve hata ayıklama ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="821e9-131">Trace and Debug Settings Schema</span></span>](index.md)
