---
title: <filter><add> Için <listeners> element<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
ms.openlocfilehash: 0cb668782de263d5f784691f46cb8b74541d942b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153522"
---
# <a name="filter-element-for-add-for-listeners-for-source"></a><span data-ttu-id="16b25-102">\<kaynak> \<için> \<dinleyiciler \<için> eklemek için> Öğesi'ni filtreleyin</span><span class="sxs-lookup"><span data-stu-id="16b25-102">\<filter> Element for \<add> for \<listeners> for \<source></span></span>
<span data-ttu-id="16b25-103">İzleme kaynağı için `Listeners` koleksiyondaki dinleyiciye filtre ekler.</span><span class="sxs-lookup"><span data-stu-id="16b25-103">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>  

<span data-ttu-id="16b25-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="16b25-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="16b25-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="16b25-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="16b25-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<kaynaklar>**](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="16b25-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>\
<span data-ttu-id="16b25-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<kaynak>**](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="16b25-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>\
<span data-ttu-id="16b25-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dinleyici ler>**](listeners-element-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="16b25-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)</span></span>\
<span data-ttu-id="16b25-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>ekleyin**](add-element-for-listeners-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="16b25-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-listeners-for-source.md)</span></span>\
<span data-ttu-id="16b25-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filtre>**</span><span class="sxs-lookup"><span data-stu-id="16b25-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**</span></span>

## <a name="syntax"></a><span data-ttu-id="16b25-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="16b25-111">Syntax</span></span>  
  
```xml  
<filter
  type="traceFilterClassName"
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="16b25-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="16b25-112">Attributes and Elements</span></span>  
 <span data-ttu-id="16b25-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="16b25-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="16b25-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="16b25-114">Attributes</span></span>  
  
|<span data-ttu-id="16b25-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="16b25-115">Attribute</span></span>|<span data-ttu-id="16b25-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="16b25-116">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="16b25-117">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="16b25-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="16b25-118"><xref:System.Diagnostics.TraceFilter> Sınıftan devralması gereken filtrenin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="16b25-118">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="16b25-119">Türün <xref:System.Type.FullName%2A> özelliğine karşılık gelen ad alanı nitelikli adını kullanabilir veya <xref:System.Type.AssemblyQualifiedName%2A> derleme bilgilerini de içeren ve özelliğe karşılık gelen tam nitelikli tür adını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16b25-119">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="16b25-120">Tam nitelikli tür adları hakkında bilgi için [bkz.](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)</span><span class="sxs-lookup"><span data-stu-id="16b25-120">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="16b25-121">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="16b25-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="16b25-122">Dize, belirtilen filtre sınıfı için oluşturucuya geçti.</span><span class="sxs-lookup"><span data-stu-id="16b25-122">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="16b25-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="16b25-123">Child Elements</span></span>  
 <span data-ttu-id="16b25-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="16b25-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="16b25-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="16b25-125">Parent Elements</span></span>  
  
|<span data-ttu-id="16b25-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="16b25-126">Element</span></span>|<span data-ttu-id="16b25-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="16b25-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="16b25-128">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="16b25-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="16b25-129">İletileri toplayan, depolayan ve yönlendiren izleme dinleyicilerini ve izleme anahtarının ayarlandığı düzeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="16b25-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="16b25-130">İletileri izlemeyi başlatan izleme kaynakları içerir.</span><span class="sxs-lookup"><span data-stu-id="16b25-130">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="16b25-131">İletilerin izlenmesini başlatan bir izleme kaynağı belirtir.</span><span class="sxs-lookup"><span data-stu-id="16b25-131">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="16b25-132">İletileri toplayan, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="16b25-132">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="16b25-133">Dinleyiciler izleme çıktısını uygun bir hedefe yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="16b25-133">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="16b25-134">İzleme kaynağı için `Listeners` koleksiyona dinleyici ekler.</span><span class="sxs-lookup"><span data-stu-id="16b25-134">Adds a listener to the `Listeners` collection for a trace source.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16b25-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="16b25-135">Remarks</span></span>  
 <span data-ttu-id="16b25-136">Öğe, `<filter>` yalnızca paylaşılan `<add>` [ \<Dinleyiciler>](sharedlisteners-element.md)tanımlanan bir dinleyicinin adını değil, dinleyicinin türünü belirten bir izleme kaynağı dinleyicisi için bir öğeiçermelidir.</span><span class="sxs-lookup"><span data-stu-id="16b25-136">The `<filter>` element must be contained in an `<add>` element for a trace source listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](sharedlisteners-element.md).</span></span> <span data-ttu-id="16b25-137">Dinleyici [ \<paylaşılan ](sharedlisteners-element.md)dinleyici>tanımlanırsa, bu dinleyicinin filtresi bu öğede tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="16b25-137">If the listener is defined in a [\<sharedListeners>](sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="16b25-138">Bu öğe makine yapılandırma dosyasında (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="16b25-138">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16b25-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="16b25-139">Example</span></span>  
 <span data-ttu-id="16b25-140">Aşağıdaki örnek, izleme kaynağı `<filter>` `console` `myTraceSource`için `Error` `Listeners` koleksiyondaki dinleyiciye bir filtre eklemek için öğenin nasıl kullanılacağını gösterir ve filtre olay düzeyini .</span><span class="sxs-lookup"><span data-stu-id="16b25-140">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for the trace source `myTraceSource`, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="16b25-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16b25-141">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="16b25-142">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="16b25-142">Trace and Debug Settings Schema</span></span>](index.md)
