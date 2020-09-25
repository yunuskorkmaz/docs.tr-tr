---
title: <filter>İçin için <add> öğesi <listeners><trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
ms.openlocfilehash: d856fc742bc2dca51095ce0866dcbfdaadadf64d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176116"
---
# <a name="filter-element-for-add-for-listeners-for-trace"></a><span data-ttu-id="8b379-102">\<filter>İçin için \<add> öğesi \<listeners>\<trace></span><span class="sxs-lookup"><span data-stu-id="8b379-102">\<filter> Element for \<add> for \<listeners> for \<trace></span></span>

<span data-ttu-id="8b379-103">İzleme için koleksiyondaki bir dinleyiciye bir filtre ekler `Listeners` .</span><span class="sxs-lookup"><span data-stu-id="8b379-103">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-listeners-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**

## <a name="syntax"></a><span data-ttu-id="8b379-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="8b379-104">Syntax</span></span>  
  
```xml  
<filter
  type="traceFilterClassName"
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8b379-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8b379-105">Attributes and Elements</span></span>  

 <span data-ttu-id="8b379-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8b379-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8b379-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8b379-107">Attributes</span></span>  
  
|<span data-ttu-id="8b379-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8b379-108">Attribute</span></span>|<span data-ttu-id="8b379-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8b379-109">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="8b379-110">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="8b379-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="8b379-111">Sınıftan devralması gereken filtrenin türünü belirtir <xref:System.Diagnostics.TraceFilter> .</span><span class="sxs-lookup"><span data-stu-id="8b379-111">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="8b379-112">Türün özelliğine karşılık gelen, türün ad alanı nitelenmiş adını kullanabilirsiniz <xref:System.Type.FullName%2A> veya, özelliğine karşılık gelen derleme bilgileri de dahil olmak üzere tam nitelikli tür adını kullanabilirsiniz <xref:System.Type.AssemblyQualifiedName%2A> .</span><span class="sxs-lookup"><span data-stu-id="8b379-112">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="8b379-113">Tam nitelikli tür adları hakkında daha fazla bilgi için bkz. [tam nitelikli tür adlarını belirtme](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="8b379-113">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="8b379-114">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="8b379-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="8b379-115">Belirtilen filtre sınıfı için oluşturucuya geçirilen dize.</span><span class="sxs-lookup"><span data-stu-id="8b379-115">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8b379-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8b379-116">Child Elements</span></span>  

 <span data-ttu-id="8b379-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="8b379-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8b379-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8b379-118">Parent Elements</span></span>  
  
|<span data-ttu-id="8b379-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="8b379-119">Element</span></span>|<span data-ttu-id="8b379-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8b379-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="8b379-121">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="8b379-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="8b379-122">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8b379-122">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="8b379-123">İzleme iletilerini toplayıp depolayan, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="8b379-123">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="8b379-124">İletileri toplayacak, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="8b379-124">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="8b379-125">Dinleyiciler izleme çıkışını uygun bir hedefe yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="8b379-125">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="8b379-126">Koleksiyona bir dinleyici ekler `Listeners` .</span><span class="sxs-lookup"><span data-stu-id="8b379-126">Adds a listener to the `Listeners` collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b379-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8b379-127">Remarks</span></span>  

 <span data-ttu-id="8b379-128">`<filter>`Öğesi, `<add>` yalnızca içinde tanımlanan bir dinleyicinin adını değil, dinleyicinin türünü belirten bir izleme dinleyicisi öğesi içinde bulunmalıdır [\<sharedListeners>](sharedlisteners-element.md) .</span><span class="sxs-lookup"><span data-stu-id="8b379-128">The `<filter>` element must be contained in an `<add>` element for a trace listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](sharedlisteners-element.md).</span></span> <span data-ttu-id="8b379-129">Dinleyici bir içinde tanımlanmışsa [\<sharedListeners>](sharedlisteners-element.md) , bu dinleyicinin filtresi o öğede tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8b379-129">If the listener is defined in a [\<sharedListeners>](sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="8b379-130">Bu öğe makine yapılandırma dosyasında (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8b379-130">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b379-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="8b379-131">Example</span></span>  

 <span data-ttu-id="8b379-132">Aşağıdaki örnek, `<filter>` `console` `Listeners` izleme için koleksiyondaki dinleyiciye filtre eklemek için öğesinin nasıl kullanılacağını gösterir `Error` .</span><span class="sxs-lookup"><span data-stu-id="8b379-132">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for trace, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8b379-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b379-133">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="8b379-134">İzleme ve hata ayıklama ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="8b379-134">Trace and Debug Settings Schema</span></span>](index.md)
