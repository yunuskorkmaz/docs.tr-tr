---
title: <source> için <listeners> için <add> <filter> öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
ms.openlocfilehash: ec288685f47c8a35e2371c31d359b604a4967196
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697169"
---
# <a name="filter-element-for-add-for-listeners-for-source"></a><span data-ttu-id="018f2-102">\<source > için \<add > \<listeners için \<filter > öğesi ></span><span class="sxs-lookup"><span data-stu-id="018f2-102">\<filter> Element for \<add> for \<listeners> for \<source></span></span>
<span data-ttu-id="018f2-103">İzleme kaynağı için `Listeners` koleksiyonundaki bir dinleyiciye filtre ekler.</span><span class="sxs-lookup"><span data-stu-id="018f2-103">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>  
  
[<span data-ttu-id="018f2-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="018f2-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="018f2-105">&nbsp; @ no__t-1[ **\<system. Diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="018f2-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="018f2-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<sources >** ](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="018f2-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>  
<span data-ttu-id="018f2-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<source >** ](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="018f2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>  
<span data-ttu-id="018f2-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7[ **&nbsp;0listeners >** ](listeners-element-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="018f2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)</span></span>  
<span data-ttu-id="018f2-109">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 @ no__t-8 @ no__t-9[ **&nbsp;2add >** ](add-element-for-listeners-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="018f2-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-listeners-for-source.md)</span></span>  
<span data-ttu-id="018f2-110">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 @ no__t-8 @ no__t-9 @ no__t-10 @ no__t-11 **&nbsp;3filter >**</span><span class="sxs-lookup"><span data-stu-id="018f2-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="018f2-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="018f2-111">Syntax</span></span>  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="018f2-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="018f2-112">Attributes and Elements</span></span>  
 <span data-ttu-id="018f2-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="018f2-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="018f2-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="018f2-114">Attributes</span></span>  
  
|<span data-ttu-id="018f2-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="018f2-115">Attribute</span></span>|<span data-ttu-id="018f2-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="018f2-116">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="018f2-117">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="018f2-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="018f2-118">@No__t-0 sınıfından devralması gereken filtrenin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="018f2-118">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="018f2-119">Türün <xref:System.Type.FullName%2A> özelliğine karşılık gelen ad alanı nitelenmiş adını kullanabilir veya <xref:System.Type.AssemblyQualifiedName%2A> özelliğine karşılık gelen derleme bilgileri de dahil olmak üzere tam tür adı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="018f2-119">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="018f2-120">Tam nitelikli tür adları hakkında daha fazla bilgi için bkz. [tam nitelikli tür adlarını belirtme](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="018f2-120">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="018f2-121">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="018f2-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="018f2-122">Belirtilen filtre sınıfı için oluşturucuya geçirilen dize.</span><span class="sxs-lookup"><span data-stu-id="018f2-122">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="018f2-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="018f2-123">Child Elements</span></span>  
 <span data-ttu-id="018f2-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="018f2-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="018f2-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="018f2-125">Parent Elements</span></span>  
  
|<span data-ttu-id="018f2-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="018f2-126">Element</span></span>|<span data-ttu-id="018f2-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="018f2-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="018f2-128">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="018f2-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="018f2-129">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="018f2-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="018f2-130">İzleme iletilerini Başlatan izleme kaynaklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="018f2-130">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="018f2-131">İzleme iletilerini Başlatan bir izleme kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="018f2-131">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="018f2-132">İletileri toplayacak, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="018f2-132">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="018f2-133">Dinleyiciler izleme çıkışını uygun bir hedefe yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="018f2-133">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="018f2-134">İzleme kaynağı için `Listeners` koleksiyonuna bir dinleyici ekler.</span><span class="sxs-lookup"><span data-stu-id="018f2-134">Adds a listener to the `Listeners` collection for a trace source.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="018f2-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="018f2-135">Remarks</span></span>  
 <span data-ttu-id="018f2-136">@No__t-0 öğesi, yalnızca bir [\<sharedListeners >](sharedlisteners-element.md)tanımlanan dinleyicinin adını değil, dinleyicinin türünü belirten bir izleme kaynak dinleyicisi için bir `<add>` öğesinde bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="018f2-136">The `<filter>` element must be contained in an `<add>` element for a trace source listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](sharedlisteners-element.md).</span></span> <span data-ttu-id="018f2-137">Dinleyici bir [\<sharedListeners >](sharedlisteners-element.md)tanımlanmışsa, bu dinleyicinin filtresi o öğede tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="018f2-137">If the listener is defined in a [\<sharedListeners>](sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="018f2-138">Bu öğe makine yapılandırma dosyasında (Machine. config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="018f2-138">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="018f2-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="018f2-139">Example</span></span>  
 <span data-ttu-id="018f2-140">Aşağıdaki örnek, `Error` olarak filtre olay düzeyini belirterek, izleme kaynağı `myTraceSource` için `Listeners` koleksiyonundaki dinleyic@no__t iye bir filtre eklemek için `<filter>` öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="018f2-140">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for the trace source `myTraceSource`, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="018f2-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="018f2-141">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="018f2-142">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="018f2-142">Trace and Debug Settings Schema</span></span>](index.md)
