---
title: '&lt;Filtre&gt; öğesi için &lt;ekleme&gt; için &lt;dinleyicileri&gt; için &lt;izleme&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
author: mcleblanc
ms.author: markl
ms.openlocfilehash: be4f3dcce1a746b287e75e0e6d3ba6eaa1d9b57b
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48032562"
---
# <a name="ltfiltergt-element-for-ltaddgt-for-ltlistenersgt-for-lttracegt"></a><span data-ttu-id="860d5-102">&lt;Filtre&gt; öğesi için &lt;ekleme&gt; için &lt;dinleyicileri&gt; için &lt;izleme&gt;</span><span class="sxs-lookup"><span data-stu-id="860d5-102">&lt;filter&gt; Element for &lt;add&gt; for &lt;listeners&gt; for &lt;trace&gt;</span></span>
<span data-ttu-id="860d5-103">Bir dinleyicisi için bir filtre ekler `Listeners` koleksiyonu için bir izleme.</span><span class="sxs-lookup"><span data-stu-id="860d5-103">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>  
  
 <span data-ttu-id="860d5-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="860d5-104">\<configuration></span></span>  
<span data-ttu-id="860d5-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="860d5-105">\<system.diagnostics></span></span>  
<span data-ttu-id="860d5-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="860d5-106">\<trace></span></span>  
<span data-ttu-id="860d5-107">\<dinleyicileri ></span><span class="sxs-lookup"><span data-stu-id="860d5-107">\<listeners></span></span>  
<span data-ttu-id="860d5-108">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="860d5-108">\<add></span></span>  
<span data-ttu-id="860d5-109">\<Filtre ></span><span class="sxs-lookup"><span data-stu-id="860d5-109">\<filter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="860d5-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="860d5-110">Syntax</span></span>  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="860d5-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="860d5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="860d5-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="860d5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="860d5-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="860d5-113">Attributes</span></span>  
  
|<span data-ttu-id="860d5-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="860d5-114">Attribute</span></span>|<span data-ttu-id="860d5-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="860d5-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="860d5-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="860d5-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="860d5-117">Devralınan filtre türünü belirtir <xref:System.Diagnostics.TraceFilter> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="860d5-117">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="860d5-118">Türün karşılık gelen türü ad alanıyla nitelenen adı kullanabileceğiniz <xref:System.Type.FullName%2A> özelliği veya karşılık gelen derleme bilgiler dahil olmak üzere tam olarak nitelenmiş tür adını kullanabilir <xref:System.Type.AssemblyQualifiedName%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="860d5-118">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="860d5-119">Tam olarak nitelenmiş tür adları hakkında daha fazla bilgi için bkz: [belirtme tam olarak nitelenmiş tür adlarını](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="860d5-119">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="860d5-120">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="860d5-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="860d5-121">Dize için belirtilen filtreyi sınıf oluşturucusuna geçirilen.</span><span class="sxs-lookup"><span data-stu-id="860d5-121">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="860d5-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="860d5-122">Child Elements</span></span>  
 <span data-ttu-id="860d5-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="860d5-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="860d5-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="860d5-124">Parent Elements</span></span>  
  
|<span data-ttu-id="860d5-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="860d5-125">Element</span></span>|<span data-ttu-id="860d5-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="860d5-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="860d5-127">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="860d5-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="860d5-128">Toplamak, depolamak ve iletileri ve bir izleme anahtarı ayarlandığı düzeyi izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="860d5-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="860d5-129">Toplamak, depolamak ve izleme iletilerini yönlendirmek dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="860d5-129">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="860d5-130">Toplamak, depolamak ve iletileri yönlendirmek dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="860d5-130">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="860d5-131">Dinleyicileri bir uygun hedef izleme çıkışa doğrudan.</span><span class="sxs-lookup"><span data-stu-id="860d5-131">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="860d5-132">Bir ekler `Listeners` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="860d5-132">Adds a listener to the `Listeners` collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="860d5-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="860d5-133">Remarks</span></span>  
 <span data-ttu-id="860d5-134">`<filter>` Öğe bulunmalıdır bir `<add>` öğesi dinleyicisi türünü belirten bir izleme dinleyicisi için yalnızca bir dinleyicisi adı tanımlanmış bir [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md).</span><span class="sxs-lookup"><span data-stu-id="860d5-134">The `<filter>` element must be contained in an `<add>` element for a trace listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md).</span></span> <span data-ttu-id="860d5-135">Dinleyici olarak tanımlanırsa, bir [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), filtre bu dinleyici için bu öğesinde tanımlanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="860d5-135">If the listener is defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="860d5-136">Bu öğe, makine yapılandırma dosyası (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="860d5-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="860d5-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="860d5-137">Example</span></span>  
 <span data-ttu-id="860d5-138">Aşağıdaki örnek nasıl kullanılacağını gösterir `<filter>` dinleyici için filtre eklemek için öğe `console` içinde `Listeners` koleksiyonu için izleme, belirleme filtresi olay düzeyi'olarak `Error`.</span><span class="sxs-lookup"><span data-stu-id="860d5-138">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for trace, specifying the filter event level as `Error`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <add name="console"   
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"   
            initializeData="Error" />  
        </add>  
        <remove name="Default" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="860d5-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="860d5-139">See Also</span></span>  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>  
 <xref:System.Diagnostics.TraceFilter>  
 [<span data-ttu-id="860d5-140">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="860d5-140">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
