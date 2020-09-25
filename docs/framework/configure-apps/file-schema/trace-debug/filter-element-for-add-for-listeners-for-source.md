---
title: <filter>İçin için <add> öğesi <listeners><source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
ms.openlocfilehash: 2b83fd10da506202427aaeee454411822ff1ae5b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201687"
---
# <a name="filter-element-for-add-for-listeners-for-source"></a><span data-ttu-id="ad046-102">\<filter>İçin için \<add> öğesi \<listeners>\<source></span><span class="sxs-lookup"><span data-stu-id="ad046-102">\<filter> Element for \<add> for \<listeners> for \<source></span></span>

<span data-ttu-id="ad046-103">İzleme kaynağı için koleksiyondaki bir dinleyiciye bir filtre ekler `Listeners` .</span><span class="sxs-lookup"><span data-stu-id="ad046-103">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-listeners-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**

## <a name="syntax"></a><span data-ttu-id="ad046-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="ad046-104">Syntax</span></span>  
  
```xml  
<filter
  type="traceFilterClassName"
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ad046-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ad046-105">Attributes and Elements</span></span>  

 <span data-ttu-id="ad046-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ad046-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ad046-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ad046-107">Attributes</span></span>  
  
|<span data-ttu-id="ad046-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ad046-108">Attribute</span></span>|<span data-ttu-id="ad046-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ad046-109">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="ad046-110">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="ad046-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="ad046-111">Sınıftan devralması gereken filtrenin türünü belirtir <xref:System.Diagnostics.TraceFilter> .</span><span class="sxs-lookup"><span data-stu-id="ad046-111">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="ad046-112">Türün özelliğine karşılık gelen, türün ad alanı nitelenmiş adını kullanabilirsiniz <xref:System.Type.FullName%2A> veya, özelliğine karşılık gelen derleme bilgileri de dahil olmak üzere tam nitelikli tür adını kullanabilirsiniz <xref:System.Type.AssemblyQualifiedName%2A> .</span><span class="sxs-lookup"><span data-stu-id="ad046-112">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="ad046-113">Tam nitelikli tür adları hakkında daha fazla bilgi için bkz. [tam nitelikli tür adlarını belirtme](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="ad046-113">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="ad046-114">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="ad046-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="ad046-115">Belirtilen filtre sınıfı için oluşturucuya geçirilen dize.</span><span class="sxs-lookup"><span data-stu-id="ad046-115">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ad046-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ad046-116">Child Elements</span></span>  

 <span data-ttu-id="ad046-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="ad046-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ad046-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ad046-118">Parent Elements</span></span>  
  
|<span data-ttu-id="ad046-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="ad046-119">Element</span></span>|<span data-ttu-id="ad046-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ad046-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ad046-121">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="ad046-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="ad046-122">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ad046-122">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="ad046-123">İzleme iletilerini Başlatan izleme kaynaklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="ad046-123">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="ad046-124">İzleme iletilerini Başlatan bir izleme kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ad046-124">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="ad046-125">İletileri toplayacak, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="ad046-125">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="ad046-126">Dinleyiciler izleme çıkışını uygun bir hedefe yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="ad046-126">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="ad046-127">`Listeners`İzleme kaynağı için koleksiyona bir dinleyici ekler.</span><span class="sxs-lookup"><span data-stu-id="ad046-127">Adds a listener to the `Listeners` collection for a trace source.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad046-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ad046-128">Remarks</span></span>  

 <span data-ttu-id="ad046-129">`<filter>`Öğesi, `<add>` yalnızca içinde tanımlanan bir dinleyicinin adı değil, dinleyicinin türünü belirten bir izleme kaynağı dinleyicisi için bir öğe içinde bulunmalıdır [\<sharedListeners>](sharedlisteners-element.md) .</span><span class="sxs-lookup"><span data-stu-id="ad046-129">The `<filter>` element must be contained in an `<add>` element for a trace source listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](sharedlisteners-element.md).</span></span> <span data-ttu-id="ad046-130">Dinleyici bir içinde tanımlanmışsa [\<sharedListeners>](sharedlisteners-element.md) , bu dinleyicinin filtresi o öğede tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ad046-130">If the listener is defined in a [\<sharedListeners>](sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="ad046-131">Bu öğe makine yapılandırma dosyasında (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ad046-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad046-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="ad046-132">Example</span></span>  

 <span data-ttu-id="ad046-133">Aşağıdaki örnek, `<filter>` `console` `Listeners` izleme kaynağı için koleksiyondaki dinleyiciye bir filtre eklemek için öğesinin nasıl kullanılacağını gösterir `myTraceSource` `Error` .</span><span class="sxs-lookup"><span data-stu-id="ad046-133">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for the trace source `myTraceSource`, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ad046-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad046-134">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="ad046-135">İzleme ve hata ayıklama ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="ad046-135">Trace and Debug Settings Schema</span></span>](index.md)
