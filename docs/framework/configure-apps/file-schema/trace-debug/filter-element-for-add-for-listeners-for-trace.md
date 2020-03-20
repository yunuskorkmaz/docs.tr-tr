---
title: <filter><add> Için <listeners> element<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
ms.openlocfilehash: b6c2c2bf7fe953a75f9d8129039ef33b4d8a3f56
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153472"
---
# <a name="filter-element-for-add-for-listeners-for-trace"></a><span data-ttu-id="a0691-102">\<izleme> \<için> \<dinleyiciler \<için> eklemek için> Öğesi'ni filtreleyin</span><span class="sxs-lookup"><span data-stu-id="a0691-102">\<filter> Element for \<add> for \<listeners> for \<trace></span></span>
<span data-ttu-id="a0691-103">`Listeners` İzleme için koleksiyondaki bir dinleyiciye filtre ekler.</span><span class="sxs-lookup"><span data-stu-id="a0691-103">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>  

<span data-ttu-id="a0691-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a0691-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a0691-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="a0691-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="a0691-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<izleme>**](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="a0691-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>\
<span data-ttu-id="a0691-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dinleyici ler>**](listeners-element-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="a0691-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)</span></span>\
<span data-ttu-id="a0691-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>ekleyin**](add-element-for-listeners-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="a0691-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-listeners-for-trace.md)</span></span>\
<span data-ttu-id="a0691-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filtre>**</span><span class="sxs-lookup"><span data-stu-id="a0691-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**</span></span>

## <a name="syntax"></a><span data-ttu-id="a0691-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a0691-110">Syntax</span></span>  
  
```xml  
<filter
  type="traceFilterClassName"
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a0691-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a0691-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a0691-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a0691-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a0691-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a0691-113">Attributes</span></span>  
  
|<span data-ttu-id="a0691-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a0691-114">Attribute</span></span>|<span data-ttu-id="a0691-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0691-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="a0691-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a0691-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="a0691-117"><xref:System.Diagnostics.TraceFilter> Sınıftan devralması gereken filtrenin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="a0691-117">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="a0691-118">Türün <xref:System.Type.FullName%2A> özelliğine karşılık gelen ad alanı nitelikli adını kullanabilir veya <xref:System.Type.AssemblyQualifiedName%2A> derleme bilgilerini de içeren ve özelliğe karşılık gelen tam nitelikli tür adını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0691-118">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="a0691-119">Tam nitelikli tür adları hakkında bilgi için [bkz.](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)</span><span class="sxs-lookup"><span data-stu-id="a0691-119">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="a0691-120">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a0691-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a0691-121">Dize, belirtilen filtre sınıfı için oluşturucuya geçti.</span><span class="sxs-lookup"><span data-stu-id="a0691-121">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a0691-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a0691-122">Child Elements</span></span>  
 <span data-ttu-id="a0691-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="a0691-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a0691-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a0691-124">Parent Elements</span></span>  
  
|<span data-ttu-id="a0691-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="a0691-125">Element</span></span>|<span data-ttu-id="a0691-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0691-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a0691-127">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="a0691-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="a0691-128">İletileri toplayan, depolayan ve yönlendiren izleme dinleyicilerini ve izleme anahtarının ayarlandığı düzeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="a0691-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="a0691-129">İletileri toplayan, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="a0691-129">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="a0691-130">İletileri toplayan, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="a0691-130">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="a0691-131">Dinleyiciler izleme çıktısını uygun bir hedefe yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="a0691-131">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="a0691-132">`Listeners` Koleksiyona bir dinleyici ekler.</span><span class="sxs-lookup"><span data-stu-id="a0691-132">Adds a listener to the `Listeners` collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0691-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a0691-133">Remarks</span></span>  
 <span data-ttu-id="a0691-134">Öğe, `<filter>` yalnızca paylaşılan `<add>` Dinleyici [ \<>](sharedlisteners-element.md)tanımlanan bir dinleyicinin adını değil, dinleyicinin türünü belirten bir izleme dinleyicisi için bir öğede bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a0691-134">The `<filter>` element must be contained in an `<add>` element for a trace listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](sharedlisteners-element.md).</span></span> <span data-ttu-id="a0691-135">Dinleyici [ \<paylaşılan ](sharedlisteners-element.md)dinleyici>tanımlanırsa, bu dinleyicinin filtresi bu öğede tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a0691-135">If the listener is defined in a [\<sharedListeners>](sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="a0691-136">Bu öğe makine yapılandırma dosyasında (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a0691-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0691-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="a0691-137">Example</span></span>  
 <span data-ttu-id="a0691-138">Aşağıdaki örnekte, izleme `<filter>` için `console` `Listeners` koleksiyondaki dinleyiciye bir filtre eklemek için öğenin nasıl kullanılacağı `Error`gösterilmektedir ve filtre olay düzeyini .</span><span class="sxs-lookup"><span data-stu-id="a0691-138">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for trace, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a0691-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0691-139">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="a0691-140">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="a0691-140">Trace and Debug Settings Schema</span></span>](index.md)
