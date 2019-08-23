---
title: <filter><add> İçin için<listeners> öğesi<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
ms.openlocfilehash: 0d25d0b955a94986147922914068c8a1cf2d96c4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920526"
---
# <a name="filter-element-for-add-for-listeners-for-source"></a><span data-ttu-id="e8424-102">\<Kaynak > için \< \<dinleyicileriçin> eklemekiçin>öğesinifiltreleyin\<></span><span class="sxs-lookup"><span data-stu-id="e8424-102">\<filter> Element for \<add> for \<listeners> for \<source></span></span>
<span data-ttu-id="e8424-103">İzleme kaynağı için `Listeners` koleksiyondaki bir dinleyiciye bir filtre ekler.</span><span class="sxs-lookup"><span data-stu-id="e8424-103">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="e8424-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="e8424-104">\<configuration></span></span>  
<span data-ttu-id="e8424-105">\<System. Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="e8424-105">\<system.diagnostics></span></span>  
<span data-ttu-id="e8424-106">\<Kaynaklar ></span><span class="sxs-lookup"><span data-stu-id="e8424-106">\<sources></span></span>  
<span data-ttu-id="e8424-107">\<Kaynak ></span><span class="sxs-lookup"><span data-stu-id="e8424-107">\<source></span></span>  
<span data-ttu-id="e8424-108">\<dinleyiciler ></span><span class="sxs-lookup"><span data-stu-id="e8424-108">\<listeners></span></span>  
<span data-ttu-id="e8424-109">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="e8424-109">\<add></span></span>  
<span data-ttu-id="e8424-110">\<Filtre ></span><span class="sxs-lookup"><span data-stu-id="e8424-110">\<filter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8424-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e8424-111">Syntax</span></span>  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e8424-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e8424-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e8424-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e8424-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e8424-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e8424-114">Attributes</span></span>  
  
|<span data-ttu-id="e8424-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e8424-115">Attribute</span></span>|<span data-ttu-id="e8424-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e8424-116">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="e8424-117">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e8424-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="e8424-118"><xref:System.Diagnostics.TraceFilter> Sınıftan devralması gereken filtrenin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="e8424-118">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="e8424-119">Türün <xref:System.Type.FullName%2A> özelliğine karşılık gelen, türün ad alanı nitelenmiş adını kullanabilirsiniz veya, <xref:System.Type.AssemblyQualifiedName%2A> özelliğine karşılık gelen derleme bilgileri de dahil olmak üzere tam nitelikli tür adını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8424-119">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="e8424-120">Tam nitelikli tür adları hakkında daha fazla bilgi için bkz. [tam nitelikli tür adlarını belirtme](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="e8424-120">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="e8424-121">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e8424-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="e8424-122">Belirtilen filtre sınıfı için oluşturucuya geçirilen dize.</span><span class="sxs-lookup"><span data-stu-id="e8424-122">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e8424-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e8424-123">Child Elements</span></span>  
 <span data-ttu-id="e8424-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="e8424-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e8424-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e8424-125">Parent Elements</span></span>  
  
|<span data-ttu-id="e8424-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="e8424-126">Element</span></span>|<span data-ttu-id="e8424-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e8424-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e8424-128">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="e8424-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="e8424-129">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e8424-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="e8424-130">İzleme iletilerini Başlatan izleme kaynaklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="e8424-130">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="e8424-131">İzleme iletilerini Başlatan bir izleme kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e8424-131">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="e8424-132">İletileri toplayacak, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="e8424-132">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="e8424-133">Dinleyiciler izleme çıkışını uygun bir hedefe yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="e8424-133">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="e8424-134">İzleme kaynağı için `Listeners` koleksiyona bir dinleyici ekler.</span><span class="sxs-lookup"><span data-stu-id="e8424-134">Adds a listener to the `Listeners` collection for a trace source.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8424-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e8424-135">Remarks</span></span>  
 <span data-ttu-id="e8424-136">Öğe, [yalnızca \<sharedListeners >](sharedlisteners-element.md)tanımlı `<add>` bir dinleyicinin adını değil, dinleyicinin türünü belirten bir izleme kaynağı dinleyicisi için bir öğe içinde bulunmalıdır. `<filter>`</span><span class="sxs-lookup"><span data-stu-id="e8424-136">The `<filter>` element must be contained in an `<add>` element for a trace source listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](sharedlisteners-element.md).</span></span> <span data-ttu-id="e8424-137">Dinleyici bir [ \<sharedListeners >](sharedlisteners-element.md)tanımlanmışsa, bu dinleyicinin filtresi o öğede tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e8424-137">If the listener is defined in a [\<sharedListeners>](sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="e8424-138">Bu öğe makine yapılandırma dosyasında (Machine. config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e8424-138">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8424-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="e8424-139">Example</span></span>  
 <span data-ttu-id="e8424-140">Aşağıdaki örnek, izleme `<filter>` `Listeners` `console` kaynağı`myTraceSource`içinkoleksiyondaki dinleyiciye bir filtre eklemek için öğesinin nasıl kullanılacağını gösterir. `Error`</span><span class="sxs-lookup"><span data-stu-id="e8424-140">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for the trace source `myTraceSource`, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e8424-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e8424-141">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="e8424-142">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="e8424-142">Trace and Debug Settings Schema</span></span>](index.md)
