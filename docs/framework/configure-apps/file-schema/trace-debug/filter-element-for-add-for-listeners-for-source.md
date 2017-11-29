---
title: "&lt;Filtre&gt; öğesi için &lt;ekleme&gt; için &lt;dinleyicileri&gt; için &lt;kaynağı&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 3b02f97caeef2a560682e5746c6c24986d5a3ad2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltfiltergt-element-for-ltaddgt-for-ltlistenersgt-for-ltsourcegt"></a><span data-ttu-id="8ada1-102">&lt;Filtre&gt; öğesi için &lt;ekleme&gt; için &lt;dinleyicileri&gt; için &lt;kaynağı&gt;</span><span class="sxs-lookup"><span data-stu-id="8ada1-102">&lt;filter&gt; Element for &lt;add&gt; for &lt;listeners&gt; for &lt;source&gt;</span></span>
<span data-ttu-id="8ada1-103">Bir dinleyici için bir filtre ekler `Listeners` koleksiyonu için bir izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="8ada1-103">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="8ada1-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="8ada1-104">\<configuration></span></span>  
<span data-ttu-id="8ada1-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="8ada1-105">\<system.diagnostics></span></span>  
<span data-ttu-id="8ada1-106">\<Kaynakları ></span><span class="sxs-lookup"><span data-stu-id="8ada1-106">\<sources></span></span>  
<span data-ttu-id="8ada1-107">\<Kaynak ></span><span class="sxs-lookup"><span data-stu-id="8ada1-107">\<source></span></span>  
<span data-ttu-id="8ada1-108">\<dinleyicileri ></span><span class="sxs-lookup"><span data-stu-id="8ada1-108">\<listeners></span></span>  
<span data-ttu-id="8ada1-109">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="8ada1-109">\<add></span></span>  
<span data-ttu-id="8ada1-110">\<Filtre ></span><span class="sxs-lookup"><span data-stu-id="8ada1-110">\<filter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ada1-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8ada1-111">Syntax</span></span>  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8ada1-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8ada1-112">Attributes and Elements</span></span>  
 <span data-ttu-id="8ada1-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8ada1-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8ada1-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8ada1-114">Attributes</span></span>  
  
|<span data-ttu-id="8ada1-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8ada1-115">Attribute</span></span>|<span data-ttu-id="8ada1-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8ada1-116">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="8ada1-117">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="8ada1-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="8ada1-118">Devralınan filtre türünü belirtir <xref:System.Diagnostics.TraceFilter> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8ada1-118">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="8ada1-119">Tür için karşılık gelen türü ad alanı tam adını kullanabilirsiniz <xref:System.Type.FullName%2A> özelliği veya karşılık gelen derleme bilgileri dahil tam olarak nitelenmiş tür adını kullanabilir <xref:System.Type.AssemblyQualifiedName%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="8ada1-119">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="8ada1-120">Tam olarak nitelenmiş tür adları hakkında daha fazla bilgi için bkz: [belirtme tam olarak nitelenmiş tür adları](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="8ada1-120">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="8ada1-121">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="8ada1-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="8ada1-122">Dize belirtilen filtre sınıfı oluşturucuya geçirilen.</span><span class="sxs-lookup"><span data-stu-id="8ada1-122">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8ada1-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8ada1-123">Child Elements</span></span>  
 <span data-ttu-id="8ada1-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="8ada1-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8ada1-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8ada1-125">Parent Elements</span></span>  
  
|<span data-ttu-id="8ada1-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="8ada1-126">Element</span></span>|<span data-ttu-id="8ada1-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8ada1-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="8ada1-128">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="8ada1-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="8ada1-129">Toplamak, depolamak ve iletileri ve izleme anahtarı ayarlandığı düzeyi rota izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8ada1-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="8ada1-130">İzleme iletileri başlatmak izleme kaynaklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="8ada1-130">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="8ada1-131">İzleme iletileri başlatan bir izleme kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8ada1-131">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="8ada1-132">Toplamak, depolamak ve iletileri yönlendirmek dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="8ada1-132">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="8ada1-133">Dinleyicileri uygun hedef İzleme çıkışı yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="8ada1-133">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="8ada1-134">Bir dinleyici ekler `Listeners` koleksiyonu için bir izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="8ada1-134">Adds a listener to the `Listeners` collection for a trace source.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ada1-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8ada1-135">Remarks</span></span>  
 <span data-ttu-id="8ada1-136">`<filter>` Öğesi içeriyordu, içinde bir `<add>` yalnızca bir dinleyici adını öğesi dinleyicisi türünü belirtir. bir izleme kaynağı dinleyicisi için tanımlanmış bir [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md).</span><span class="sxs-lookup"><span data-stu-id="8ada1-136">The `<filter>` element must be contained in an `<add>` element for a trace source listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md).</span></span> <span data-ttu-id="8ada1-137">Dinleyici tanımlanmış olması durumunda bir [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), filtre bu dinleyici için bu öğe tanımlanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8ada1-137">If the listener is defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="8ada1-138">Bu öğe makine yapılandırma dosyası (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8ada1-138">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ada1-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="8ada1-139">Example</span></span>  
 <span data-ttu-id="8ada1-140">Aşağıdaki örnekte nasıl kullanılacağını gösterir `<filter>` dinleyiciye filtre eklemek için öğesi `console` içinde `Listeners` izleme kaynağı toplamalarında `myTraceSource`, filtre olay düzeyi olarak belirterek `Error`.</span><span class="sxs-lookup"><span data-stu-id="8ada1-140">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for the trace source `myTraceSource`, specifying the filter event level as `Error`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" switchName="SourceSwitch"   
        switchType="System.Diagnostics.SourceSwitch"  >  
        <listeners>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener" >  
            <filter type="System.Diagnostics.EventTypeFilter"   
              initializeData="Error" />  
          </add>  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="SourceSwitch" value="Warning" />  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8ada1-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8ada1-141">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>  
 <xref:System.Diagnostics.TraceFilter>  
 [<span data-ttu-id="8ada1-142">İzleme ve hata ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="8ada1-142">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
