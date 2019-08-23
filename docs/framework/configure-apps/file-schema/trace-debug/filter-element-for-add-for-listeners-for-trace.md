---
title: <filter><add> İçin için<listeners> öğesi<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
ms.openlocfilehash: afde5381a7dd7dfe6a1a9d238a2029511bd9bae2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927131"
---
# <a name="filter-element-for-add-for-listeners-for-trace"></a><span data-ttu-id="43bb8-102">\<Trace için \< \< >forListeners>için\<> öğesini filtreleyin ></span><span class="sxs-lookup"><span data-stu-id="43bb8-102">\<filter> Element for \<add> for \<listeners> for \<trace></span></span>
<span data-ttu-id="43bb8-103">İzleme için `Listeners` koleksiyondaki bir dinleyiciye bir filtre ekler.</span><span class="sxs-lookup"><span data-stu-id="43bb8-103">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>  
  
 <span data-ttu-id="43bb8-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="43bb8-104">\<configuration></span></span>  
<span data-ttu-id="43bb8-105">\<System. Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="43bb8-105">\<system.diagnostics></span></span>  
<span data-ttu-id="43bb8-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="43bb8-106">\<trace></span></span>  
<span data-ttu-id="43bb8-107">\<dinleyiciler ></span><span class="sxs-lookup"><span data-stu-id="43bb8-107">\<listeners></span></span>  
<span data-ttu-id="43bb8-108">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="43bb8-108">\<add></span></span>  
<span data-ttu-id="43bb8-109">\<Filtre ></span><span class="sxs-lookup"><span data-stu-id="43bb8-109">\<filter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43bb8-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="43bb8-110">Syntax</span></span>  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43bb8-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="43bb8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="43bb8-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="43bb8-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43bb8-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="43bb8-113">Attributes</span></span>  
  
|<span data-ttu-id="43bb8-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="43bb8-114">Attribute</span></span>|<span data-ttu-id="43bb8-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43bb8-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="43bb8-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="43bb8-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="43bb8-117"><xref:System.Diagnostics.TraceFilter> Sınıftan devralması gereken filtrenin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="43bb8-117">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="43bb8-118">Türün <xref:System.Type.FullName%2A> özelliğine karşılık gelen, türün ad alanı nitelenmiş adını kullanabilirsiniz veya, <xref:System.Type.AssemblyQualifiedName%2A> özelliğine karşılık gelen derleme bilgileri de dahil olmak üzere tam nitelikli tür adını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43bb8-118">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="43bb8-119">Tam nitelikli tür adları hakkında daha fazla bilgi için bkz. [tam nitelikli tür adlarını belirtme](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="43bb8-119">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="43bb8-120">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="43bb8-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="43bb8-121">Belirtilen filtre sınıfı için oluşturucuya geçirilen dize.</span><span class="sxs-lookup"><span data-stu-id="43bb8-121">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="43bb8-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="43bb8-122">Child Elements</span></span>  
 <span data-ttu-id="43bb8-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="43bb8-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="43bb8-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="43bb8-124">Parent Elements</span></span>  
  
|<span data-ttu-id="43bb8-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="43bb8-125">Element</span></span>|<span data-ttu-id="43bb8-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43bb8-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="43bb8-127">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="43bb8-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="43bb8-128">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="43bb8-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="43bb8-129">İzleme iletilerini toplayıp depolayan, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="43bb8-129">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="43bb8-130">İletileri toplayacak, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="43bb8-130">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="43bb8-131">Dinleyiciler izleme çıkışını uygun bir hedefe yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="43bb8-131">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="43bb8-132">`Listeners` Koleksiyona bir dinleyici ekler.</span><span class="sxs-lookup"><span data-stu-id="43bb8-132">Adds a listener to the `Listeners` collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43bb8-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="43bb8-133">Remarks</span></span>  
 <span data-ttu-id="43bb8-134">Öğe, [yalnızca \<sharedListeners >](sharedlisteners-element.md)tanımlı `<add>` bir dinleyicinin adını değil, dinleyicinin türünü belirten bir izleme dinleyicisi öğesi içinde bulunmalıdır. `<filter>`</span><span class="sxs-lookup"><span data-stu-id="43bb8-134">The `<filter>` element must be contained in an `<add>` element for a trace listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](sharedlisteners-element.md).</span></span> <span data-ttu-id="43bb8-135">Dinleyici bir [ \<sharedListeners >](sharedlisteners-element.md)tanımlanmışsa, bu dinleyicinin filtresi o öğede tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="43bb8-135">If the listener is defined in a [\<sharedListeners>](sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="43bb8-136">Bu öğe makine yapılandırma dosyasında (Machine. config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="43bb8-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43bb8-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="43bb8-137">Example</span></span>  
 <span data-ttu-id="43bb8-138">Aşağıdaki `<filter>` örnek, `console` izlemeiçin`Listeners` koleksiyondaki dinleyiciye filtre eklemek için öğesinin nasıl kullanılacağını gösterir. `Error`</span><span class="sxs-lookup"><span data-stu-id="43bb8-138">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for trace, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="43bb8-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43bb8-139">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="43bb8-140">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="43bb8-140">Trace and Debug Settings Schema</span></span>](index.md)
