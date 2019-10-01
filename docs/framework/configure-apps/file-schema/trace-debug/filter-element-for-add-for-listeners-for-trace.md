---
title: <trace> için <listeners> için <add> <filter> öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
ms.openlocfilehash: f6b1ec99c5aab8e85df7f1920aca32f49a5be066
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699357"
---
# <a name="filter-element-for-add-for-listeners-for-trace"></a><span data-ttu-id="c339f-102">\<trace > için \<listeners için \<add > öğesi ekleme ></span><span class="sxs-lookup"><span data-stu-id="c339f-102">\<filter> Element for \<add> for \<listeners> for \<trace></span></span>
<span data-ttu-id="c339f-103">Bir izleme için `Listeners` koleksiyonundaki bir dinleyiciye bir filtre ekler.</span><span class="sxs-lookup"><span data-stu-id="c339f-103">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>  
  
[<span data-ttu-id="c339f-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="c339f-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="c339f-105">&nbsp; @ no__t-1[ **\<system. Diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="c339f-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="c339f-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<trace >** ](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="c339f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>  
<span data-ttu-id="c339f-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<listeners >** ](listeners-element-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="c339f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)</span></span>  
<span data-ttu-id="c339f-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7[ **&nbsp;0add >** ](add-element-for-listeners-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="c339f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-listeners-for-trace.md)</span></span>  
<span data-ttu-id="c339f-109">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 @ no__t-8 @ no__t-9 **&nbsp;1filter >**</span><span class="sxs-lookup"><span data-stu-id="c339f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c339f-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c339f-110">Syntax</span></span>  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c339f-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c339f-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c339f-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c339f-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c339f-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c339f-113">Attributes</span></span>  
  
|<span data-ttu-id="c339f-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c339f-114">Attribute</span></span>|<span data-ttu-id="c339f-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c339f-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="c339f-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="c339f-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="c339f-117">@No__t-0 sınıfından devralması gereken filtrenin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="c339f-117">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="c339f-118">Türün <xref:System.Type.FullName%2A> özelliğine karşılık gelen ad alanı nitelenmiş adını kullanabilir veya <xref:System.Type.AssemblyQualifiedName%2A> özelliğine karşılık gelen derleme bilgileri de dahil olmak üzere tam tür adı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c339f-118">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="c339f-119">Tam nitelikli tür adları hakkında daha fazla bilgi için bkz. [tam nitelikli tür adlarını belirtme](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="c339f-119">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="c339f-120">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="c339f-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="c339f-121">Belirtilen filtre sınıfı için oluşturucuya geçirilen dize.</span><span class="sxs-lookup"><span data-stu-id="c339f-121">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c339f-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c339f-122">Child Elements</span></span>  
 <span data-ttu-id="c339f-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="c339f-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c339f-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c339f-124">Parent Elements</span></span>  
  
|<span data-ttu-id="c339f-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="c339f-125">Element</span></span>|<span data-ttu-id="c339f-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c339f-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c339f-127">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="c339f-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="c339f-128">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c339f-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="c339f-129">İzleme iletilerini toplayıp depolayan, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="c339f-129">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="c339f-130">İletileri toplayacak, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="c339f-130">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="c339f-131">Dinleyiciler izleme çıkışını uygun bir hedefe yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="c339f-131">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="c339f-132">@No__t-0 koleksiyonuna bir dinleyici ekler.</span><span class="sxs-lookup"><span data-stu-id="c339f-132">Adds a listener to the `Listeners` collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c339f-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c339f-133">Remarks</span></span>  
 <span data-ttu-id="c339f-134">@No__t-0 öğesi, yalnızca bir [\<sharedListeners >](sharedlisteners-element.md)tanımlanmış bir dinleyicinin adını değil, dinleyicinin türünü belirten bir izleme dinleyicisi için bir `<add>` öğesinde bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c339f-134">The `<filter>` element must be contained in an `<add>` element for a trace listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](sharedlisteners-element.md).</span></span> <span data-ttu-id="c339f-135">Dinleyici bir [\<sharedListeners >](sharedlisteners-element.md)tanımlanmışsa, bu dinleyicinin filtresi o öğede tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c339f-135">If the listener is defined in a [\<sharedListeners>](sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="c339f-136">Bu öğe makine yapılandırma dosyasında (Machine. config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c339f-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c339f-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="c339f-137">Example</span></span>  
 <span data-ttu-id="c339f-138">Aşağıdaki örnek, Trace için `Listeners` koleksiyonunda `Error` olarak filtre olay düzeyini belirterek `console` dinleyicisine bir filtre eklemek için `<filter>` öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c339f-138">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for trace, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c339f-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c339f-139">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="c339f-140">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="c339f-140">Trace and Debug Settings Schema</span></span>](index.md)
