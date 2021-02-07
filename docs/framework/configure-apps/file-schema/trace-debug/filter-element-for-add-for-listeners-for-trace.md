---
description: 'Hakkında daha fazla bilgi edinin: için <filter> öğesi <add> <listeners><trace>'
title: <filter>İçin için <add> öğesi <listeners><trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
ms.openlocfilehash: a47903a696fcbf2cd7f4eecda526f93955a31f11
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754491"
---
# <a name="filter-element-for-add-for-listeners-for-trace"></a><span data-ttu-id="947c0-103">\<filter>İçin için \<add> öğesi \<listeners>\<trace></span><span class="sxs-lookup"><span data-stu-id="947c0-103">\<filter> Element for \<add> for \<listeners> for \<trace></span></span>

<span data-ttu-id="947c0-104">İzleme için koleksiyondaki bir dinleyiciye bir filtre ekler `Listeners` .</span><span class="sxs-lookup"><span data-stu-id="947c0-104">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-listeners-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**

## <a name="syntax"></a><span data-ttu-id="947c0-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="947c0-105">Syntax</span></span>  
  
```xml  
<filter
  type="traceFilterClassName"
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="947c0-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="947c0-106">Attributes and Elements</span></span>  

 <span data-ttu-id="947c0-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="947c0-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="947c0-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="947c0-108">Attributes</span></span>  
  
|<span data-ttu-id="947c0-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="947c0-109">Attribute</span></span>|<span data-ttu-id="947c0-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="947c0-110">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="947c0-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="947c0-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="947c0-112">Sınıftan devralması gereken filtrenin türünü belirtir <xref:System.Diagnostics.TraceFilter> .</span><span class="sxs-lookup"><span data-stu-id="947c0-112">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="947c0-113">Türün özelliğine karşılık gelen, türün ad alanı nitelenmiş adını kullanabilirsiniz <xref:System.Type.FullName%2A> veya, özelliğine karşılık gelen derleme bilgileri de dahil olmak üzere tam nitelikli tür adını kullanabilirsiniz <xref:System.Type.AssemblyQualifiedName%2A> .</span><span class="sxs-lookup"><span data-stu-id="947c0-113">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="947c0-114">Tam nitelikli tür adları hakkında daha fazla bilgi için bkz. [tam nitelikli tür adlarını belirtme](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="947c0-114">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="947c0-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="947c0-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="947c0-116">Belirtilen filtre sınıfı için oluşturucuya geçirilen dize.</span><span class="sxs-lookup"><span data-stu-id="947c0-116">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="947c0-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="947c0-117">Child Elements</span></span>  

 <span data-ttu-id="947c0-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="947c0-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="947c0-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="947c0-119">Parent Elements</span></span>  
  
|<span data-ttu-id="947c0-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="947c0-120">Element</span></span>|<span data-ttu-id="947c0-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="947c0-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="947c0-122">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="947c0-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="947c0-123">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="947c0-123">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="947c0-124">İzleme iletilerini toplayıp depolayan, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="947c0-124">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="947c0-125">İletileri toplayacak, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="947c0-125">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="947c0-126">Dinleyiciler izleme çıkışını uygun bir hedefe yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="947c0-126">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="947c0-127">Koleksiyona bir dinleyici ekler `Listeners` .</span><span class="sxs-lookup"><span data-stu-id="947c0-127">Adds a listener to the `Listeners` collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="947c0-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="947c0-128">Remarks</span></span>  

 <span data-ttu-id="947c0-129">`<filter>`Öğesi, `<add>` yalnızca içinde tanımlanan bir dinleyicinin adını değil, dinleyicinin türünü belirten bir izleme dinleyicisi öğesi içinde bulunmalıdır [\<sharedListeners>](sharedlisteners-element.md) .</span><span class="sxs-lookup"><span data-stu-id="947c0-129">The `<filter>` element must be contained in an `<add>` element for a trace listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](sharedlisteners-element.md).</span></span> <span data-ttu-id="947c0-130">Dinleyici bir içinde tanımlanmışsa [\<sharedListeners>](sharedlisteners-element.md) , bu dinleyicinin filtresi o öğede tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="947c0-130">If the listener is defined in a [\<sharedListeners>](sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="947c0-131">Bu öğe makine yapılandırma dosyasında (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="947c0-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="947c0-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="947c0-132">Example</span></span>  

 <span data-ttu-id="947c0-133">Aşağıdaki örnek, `<filter>` `console` `Listeners` izleme için koleksiyondaki dinleyiciye filtre eklemek için öğesinin nasıl kullanılacağını gösterir `Error` .</span><span class="sxs-lookup"><span data-stu-id="947c0-133">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for trace, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="947c0-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="947c0-134">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="947c0-135">İzleme ve hata ayıklama ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="947c0-135">Trace and Debug Settings Schema</span></span>](index.md)
