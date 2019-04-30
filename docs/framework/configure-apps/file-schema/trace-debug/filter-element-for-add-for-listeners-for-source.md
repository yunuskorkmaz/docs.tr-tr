---
title: <filter> Öğe için <add> için <listeners> için <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
ms.openlocfilehash: 3abfd0bdd40f98a9e4774677fc2cd5068c14333f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673777"
---
# <a name="filter-element-for-add-for-listeners-for-source"></a><span data-ttu-id="baec8-102">\<Filtre > öğesi için \<Ekle > için \<dinleyicileri > için \<kaynak ></span><span class="sxs-lookup"><span data-stu-id="baec8-102">\<filter> Element for \<add> for \<listeners> for \<source></span></span>
<span data-ttu-id="baec8-103">Bir dinleyicisi için bir filtre ekler `Listeners` koleksiyonu için bir izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="baec8-103">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="baec8-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="baec8-104">\<configuration></span></span>  
<span data-ttu-id="baec8-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="baec8-105">\<system.diagnostics></span></span>  
<span data-ttu-id="baec8-106">\<Kaynakları ></span><span class="sxs-lookup"><span data-stu-id="baec8-106">\<sources></span></span>  
<span data-ttu-id="baec8-107">\<Kaynak ></span><span class="sxs-lookup"><span data-stu-id="baec8-107">\<source></span></span>  
<span data-ttu-id="baec8-108">\<dinleyicileri ></span><span class="sxs-lookup"><span data-stu-id="baec8-108">\<listeners></span></span>  
<span data-ttu-id="baec8-109">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="baec8-109">\<add></span></span>  
<span data-ttu-id="baec8-110">\<Filtre ></span><span class="sxs-lookup"><span data-stu-id="baec8-110">\<filter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="baec8-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="baec8-111">Syntax</span></span>  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="baec8-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="baec8-112">Attributes and Elements</span></span>  
 <span data-ttu-id="baec8-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="baec8-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="baec8-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="baec8-114">Attributes</span></span>  
  
|<span data-ttu-id="baec8-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="baec8-115">Attribute</span></span>|<span data-ttu-id="baec8-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="baec8-116">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="baec8-117">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="baec8-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="baec8-118">Devralınan filtre türünü belirtir <xref:System.Diagnostics.TraceFilter> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="baec8-118">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="baec8-119">Türün karşılık gelen türü ad alanıyla nitelenen adı kullanabileceğiniz <xref:System.Type.FullName%2A> özelliği veya karşılık gelen derleme bilgiler dahil olmak üzere tam olarak nitelenmiş tür adını kullanabilir <xref:System.Type.AssemblyQualifiedName%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="baec8-119">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="baec8-120">Tam olarak nitelenmiş tür adları hakkında daha fazla bilgi için bkz: [belirtme tam olarak nitelenmiş tür adlarını](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="baec8-120">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="baec8-121">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="baec8-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="baec8-122">Dize için belirtilen filtreyi sınıf oluşturucusuna geçirilen.</span><span class="sxs-lookup"><span data-stu-id="baec8-122">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="baec8-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="baec8-123">Child Elements</span></span>  
 <span data-ttu-id="baec8-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="baec8-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="baec8-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="baec8-125">Parent Elements</span></span>  
  
|<span data-ttu-id="baec8-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="baec8-126">Element</span></span>|<span data-ttu-id="baec8-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="baec8-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="baec8-128">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="baec8-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="baec8-129">Toplamak, depolamak ve iletileri ve bir izleme anahtarı ayarlandığı düzeyi izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="baec8-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="baec8-130">İzleme iletileri başlatmak iz kaynakları içerir.</span><span class="sxs-lookup"><span data-stu-id="baec8-130">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="baec8-131">İzleme iletileri başlatan bir izleme kaynağı belirtir.</span><span class="sxs-lookup"><span data-stu-id="baec8-131">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="baec8-132">Toplamak, depolamak ve iletileri yönlendirmek dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="baec8-132">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="baec8-133">Dinleyicileri bir uygun hedef izleme çıkışa doğrudan.</span><span class="sxs-lookup"><span data-stu-id="baec8-133">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="baec8-134">Bir ekler `Listeners` koleksiyonu için bir izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="baec8-134">Adds a listener to the `Listeners` collection for a trace source.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="baec8-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="baec8-135">Remarks</span></span>  
 <span data-ttu-id="baec8-136">`<filter>` Öğe bulunmalıdır bir `<add>` öğesi dinleyicisi türünü belirten bir izleme kaynağı dinleyicisi için yalnızca bir dinleyicisi adı tanımlanmış bir [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md).</span><span class="sxs-lookup"><span data-stu-id="baec8-136">The `<filter>` element must be contained in an `<add>` element for a trace source listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md).</span></span> <span data-ttu-id="baec8-137">Dinleyici olarak tanımlanırsa, bir [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), filtre bu dinleyici için bu öğesinde tanımlanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="baec8-137">If the listener is defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="baec8-138">Bu öğe, makine yapılandırma dosyası (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="baec8-138">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="baec8-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="baec8-139">Example</span></span>  
 <span data-ttu-id="baec8-140">Aşağıdaki örnek nasıl kullanılacağını gösterir `<filter>` dinleyici için filtre eklemek için öğe `console` içinde `Listeners` iz kaynağı için koleksiyon `myTraceSource`, filtre olay düzeyi'olarak belirterek `Error`.</span><span class="sxs-lookup"><span data-stu-id="baec8-140">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for the trace source `myTraceSource`, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="baec8-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="baec8-141">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="baec8-142">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="baec8-142">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
