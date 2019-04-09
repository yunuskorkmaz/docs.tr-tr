---
title: <filter> Öğe için <add> için <listeners> için <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
ms.openlocfilehash: 5961125e1b8d0d0f5711f8b942b68ba71d61888f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59143435"
---
# <a name="filter-element-for-add-for-listeners-for-trace"></a><span data-ttu-id="d2157-102">\<Filtre > öğesi için \<Ekle > için \<dinleyicileri > için \<İzleme ></span><span class="sxs-lookup"><span data-stu-id="d2157-102">\<filter> Element for \<add> for \<listeners> for \<trace></span></span>
<span data-ttu-id="d2157-103">Bir dinleyicisi için bir filtre ekler `Listeners` koleksiyonu için bir izleme.</span><span class="sxs-lookup"><span data-stu-id="d2157-103">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>  
  
 <span data-ttu-id="d2157-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="d2157-104">\<configuration></span></span>  
<span data-ttu-id="d2157-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="d2157-105">\<system.diagnostics></span></span>  
<span data-ttu-id="d2157-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="d2157-106">\<trace></span></span>  
<span data-ttu-id="d2157-107">\<dinleyicileri ></span><span class="sxs-lookup"><span data-stu-id="d2157-107">\<listeners></span></span>  
<span data-ttu-id="d2157-108">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="d2157-108">\<add></span></span>  
<span data-ttu-id="d2157-109">\<Filtre ></span><span class="sxs-lookup"><span data-stu-id="d2157-109">\<filter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2157-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d2157-110">Syntax</span></span>  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d2157-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d2157-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d2157-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d2157-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d2157-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d2157-113">Attributes</span></span>  
  
|<span data-ttu-id="d2157-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d2157-114">Attribute</span></span>|<span data-ttu-id="d2157-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d2157-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="d2157-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d2157-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="d2157-117">Devralınan filtre türünü belirtir <xref:System.Diagnostics.TraceFilter> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d2157-117">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="d2157-118">Türün karşılık gelen türü ad alanıyla nitelenen adı kullanabileceğiniz <xref:System.Type.FullName%2A> özelliği veya karşılık gelen derleme bilgiler dahil olmak üzere tam olarak nitelenmiş tür adını kullanabilir <xref:System.Type.AssemblyQualifiedName%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="d2157-118">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="d2157-119">Tam olarak nitelenmiş tür adları hakkında daha fazla bilgi için bkz: [belirtme tam olarak nitelenmiş tür adlarını](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="d2157-119">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="d2157-120">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d2157-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="d2157-121">Dize için belirtilen filtreyi sınıf oluşturucusuna geçirilen.</span><span class="sxs-lookup"><span data-stu-id="d2157-121">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d2157-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d2157-122">Child Elements</span></span>  
 <span data-ttu-id="d2157-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="d2157-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d2157-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d2157-124">Parent Elements</span></span>  
  
|<span data-ttu-id="d2157-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="d2157-125">Element</span></span>|<span data-ttu-id="d2157-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d2157-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d2157-127">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="d2157-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="d2157-128">Toplamak, depolamak ve iletileri ve bir izleme anahtarı ayarlandığı düzeyi izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2157-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="d2157-129">Toplamak, depolamak ve izleme iletilerini yönlendirmek dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="d2157-129">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="d2157-130">Toplamak, depolamak ve iletileri yönlendirmek dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="d2157-130">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="d2157-131">Dinleyicileri bir uygun hedef izleme çıkışa doğrudan.</span><span class="sxs-lookup"><span data-stu-id="d2157-131">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="d2157-132">Bir ekler `Listeners` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d2157-132">Adds a listener to the `Listeners` collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2157-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d2157-133">Remarks</span></span>  
 <span data-ttu-id="d2157-134">`<filter>` Öğe bulunmalıdır bir `<add>` öğesi dinleyicisi türünü belirten bir izleme dinleyicisi için yalnızca bir dinleyicisi adı tanımlanmış bir [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md).</span><span class="sxs-lookup"><span data-stu-id="d2157-134">The `<filter>` element must be contained in an `<add>` element for a trace listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md).</span></span> <span data-ttu-id="d2157-135">Dinleyici olarak tanımlanırsa, bir [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), filtre bu dinleyici için bu öğesinde tanımlanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d2157-135">If the listener is defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="d2157-136">Bu öğe, makine yapılandırma dosyası (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d2157-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2157-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="d2157-137">Example</span></span>  
 <span data-ttu-id="d2157-138">Aşağıdaki örnek nasıl kullanılacağını gösterir `<filter>` dinleyici için filtre eklemek için öğe `console` içinde `Listeners` koleksiyonu için izleme, belirleme filtresi olay düzeyi'olarak `Error`.</span><span class="sxs-lookup"><span data-stu-id="d2157-138">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for trace, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d2157-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2157-139">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="d2157-140">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="d2157-140">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
