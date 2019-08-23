---
title: <filter>İçin için <add> öğesi<sharedListeners>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add/filter
helpviewer_keywords:
- filter element for <add> for <sharedListeners>
- initializeData attribute
- <filter> element for <add> for <sharedListeners>
- filters, trace listeners
- trace listeners, filters
ms.assetid: 7d4e7faa-2e4e-4379-ac76-f6cd7f2f8fac
ms.openlocfilehash: 571a3add232f3e4f9747040dc104b85e8cc3085e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920504"
---
# <a name="filter-element-for-add-for-sharedlisteners"></a><span data-ttu-id="e034a-102">\<sharedListeners için \<> \<eklemek için > öğesini filtreleyin ></span><span class="sxs-lookup"><span data-stu-id="e034a-102">\<filter> Element for \<add> for \<sharedListeners></span></span>
<span data-ttu-id="e034a-103">`sharedListeners` Koleksiyondaki bir dinleyiciye bir filtre ekler.</span><span class="sxs-lookup"><span data-stu-id="e034a-103">Adds a filter to a listener in the `sharedListeners` collection.</span></span>  
  
 <span data-ttu-id="e034a-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="e034a-104">\<configuration></span></span>  
<span data-ttu-id="e034a-105">\<System. Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="e034a-105">\<system.diagnostics></span></span>  
<span data-ttu-id="e034a-106">\<sharedListeners > öğesi</span><span class="sxs-lookup"><span data-stu-id="e034a-106">\<sharedListeners> Element</span></span>  
<span data-ttu-id="e034a-107">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="e034a-107">\<add></span></span>  
<span data-ttu-id="e034a-108">\<Filtre ></span><span class="sxs-lookup"><span data-stu-id="e034a-108">\<filter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e034a-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e034a-109">Syntax</span></span>  
  
```xml  
<filter type="System.Diagnostics.EventTypeFilter"   
  initializeData="Warning" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e034a-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e034a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e034a-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e034a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e034a-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e034a-112">Attributes</span></span>  
  
|<span data-ttu-id="e034a-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e034a-113">Attribute</span></span>|<span data-ttu-id="e034a-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e034a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e034a-115">**type**</span><span class="sxs-lookup"><span data-stu-id="e034a-115">**type**</span></span>|<span data-ttu-id="e034a-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e034a-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="e034a-117">Filtrenin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="e034a-117">Specifies the type of the filter.</span></span> <span data-ttu-id="e034a-118">Türün tam adını ( <xref:System.Type.FullName%2A?displayProperty=nameWithType> özelliğinin biçiminde) veya derleme bilgileri de dahil olmak üzere tam nitelikli tür adını ( <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> özelliğin biçiminde) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e034a-118">You can use only the full name of the type (in the format of the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property), or you can use the fully qualified type name including the assembly information (in the format of the <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> property).</span></span> <span data-ttu-id="e034a-119">Tam nitelikli tür adı oluşturma hakkında bilgi için, bkz. [tam nitelikli tür adları belirtme](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="e034a-119">For information on creating a fully qualified type name, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="e034a-120">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="e034a-120">**initializeData**</span></span>|<span data-ttu-id="e034a-121">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e034a-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="e034a-122">Belirtilen sınıf için oluşturucuya geçirilen dize.</span><span class="sxs-lookup"><span data-stu-id="e034a-122">The string passed to the constructor for the specified class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e034a-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e034a-123">Child Elements</span></span>  
 <span data-ttu-id="e034a-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="e034a-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e034a-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e034a-125">Parent Elements</span></span>  
  
|<span data-ttu-id="e034a-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="e034a-126">Element</span></span>|<span data-ttu-id="e034a-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e034a-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e034a-128">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="e034a-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="e034a-129">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e034a-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="e034a-130">Herhangi bir kaynak veya izleme öğesinin başvurmasına yönelik bir dinleyici koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="e034a-130">A collection of listeners that any source or trace element can reference.</span></span>|  
|`add`|<span data-ttu-id="e034a-131">**SharedListeners** koleksiyonuna bir dinleyici ekler.</span><span class="sxs-lookup"><span data-stu-id="e034a-131">Adds a listener to the **sharedListeners** collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e034a-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e034a-132">Remarks</span></span>  
 <span data-ttu-id="e034a-133">`<add>` Bir dinleyici `<sharedListeners>` öğenin öğesi içinde tanımlanmışsa, bu dinleyicinin filtresi `<add>` öğenin alt öğesi olan bir `<filter>` öğe içinde tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e034a-133">If a listener is defined in an `<add>` element of the `<sharedListeners>` element, the filter for that listener should be defined in a `<filter>` element that is a child of the `<add>` element.</span></span>  
  
 <span data-ttu-id="e034a-134">Bu öğe makine yapılandırma dosyasında (Machine. config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e034a-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e034a-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="e034a-135">Example</span></span>  
 <span data-ttu-id="e034a-136">Aşağıdaki örnek, `<filter>` `sharedListeners` koleksiyonundaki izleme dinleyicisine `console` bir filtre eklemek için öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e034a-136">The following example shows how to use the `<filter>` element to add a filter to the trace listener `console` in the `sharedListeners` collection.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" >  
        <listeners>  
          <add name="console" />  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="console"   
        type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"   
          initializeData="Error" />  
      </add>  
    </sharedListeners>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e034a-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e034a-137">See also</span></span>

- <xref:System.Diagnostics.TraceFilter>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="e034a-138">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="e034a-138">Trace and Debug Settings Schema</span></span>](index.md)
