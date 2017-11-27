---
title: "&lt;Filtre&gt; öğesi için &lt;ekleme&gt; için &lt;sharedListeners&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add/filter
helpviewer_keywords:
- filter element for <add> for <sharedListeners>
- initializeData attribute
- <filter> element for <add> for <sharedListeners>
- filters, trace listeners
- trace listeners, filters
ms.assetid: 7d4e7faa-2e4e-4379-ac76-f6cd7f2f8fac
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ce4134d9059d1f1d5bd2e435a3cc87d3fbccd422
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltfiltergt-element-for-ltaddgt-for-ltsharedlistenersgt"></a><span data-ttu-id="5fe38-102">&lt;Filtre&gt; öğesi için &lt;ekleme&gt; için &lt;sharedListeners&gt;</span><span class="sxs-lookup"><span data-stu-id="5fe38-102">&lt;filter&gt; Element for &lt;add&gt; for &lt;sharedListeners&gt;</span></span>
<span data-ttu-id="5fe38-103">Bir dinleyici için bir filtre ekler `sharedListeners` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="5fe38-103">Adds a filter to a listener in the `sharedListeners` collection.</span></span>  
  
 <span data-ttu-id="5fe38-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="5fe38-104">\<configuration></span></span>  
<span data-ttu-id="5fe38-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="5fe38-105">\<system.diagnostics></span></span>  
<span data-ttu-id="5fe38-106">\<sharedListeners > öğesi</span><span class="sxs-lookup"><span data-stu-id="5fe38-106">\<sharedListeners> Element</span></span>  
<span data-ttu-id="5fe38-107">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="5fe38-107">\<add></span></span>  
<span data-ttu-id="5fe38-108">\<Filtre ></span><span class="sxs-lookup"><span data-stu-id="5fe38-108">\<filter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fe38-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5fe38-109">Syntax</span></span>  
  
```xml  
<filter type="System.Diagnostics.EventTypeFilter"   
  initializeData="Warning" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5fe38-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5fe38-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5fe38-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5fe38-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5fe38-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5fe38-112">Attributes</span></span>  
  
|<span data-ttu-id="5fe38-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5fe38-113">Attribute</span></span>|<span data-ttu-id="5fe38-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5fe38-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5fe38-115">**türü**</span><span class="sxs-lookup"><span data-stu-id="5fe38-115">**type**</span></span>|<span data-ttu-id="5fe38-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="5fe38-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="5fe38-117">Filtre türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="5fe38-117">Specifies the type of the filter.</span></span> <span data-ttu-id="5fe38-118">Türünün tam adını kullanabilirsiniz (biçiminde <xref:System.Type.FullName%2A?displayProperty=nameWithType> özelliği), ya da derleme bilgileri dahil tam olarak nitelenmiş tür adını kullanabilirsiniz (biçiminde <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> özelliği).</span><span class="sxs-lookup"><span data-stu-id="5fe38-118">You can use only the full name of the type (in the format of the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property), or you can use the fully qualified type name including the assembly information (in the format of the <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> property).</span></span> <span data-ttu-id="5fe38-119">Tam olarak nitelenmiş tür adları oluşturma hakkında daha fazla bilgi için bkz: [belirtme tam olarak nitelenmiş tür adları](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="5fe38-119">For information on creating a fully qualified type name, see [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="5fe38-120">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="5fe38-120">**initializeData**</span></span>|<span data-ttu-id="5fe38-121">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="5fe38-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="5fe38-122">Dize için belirtilen sınıf oluşturucuya geçirilen.</span><span class="sxs-lookup"><span data-stu-id="5fe38-122">The string passed to the constructor for the specified class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5fe38-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5fe38-123">Child Elements</span></span>  
 <span data-ttu-id="5fe38-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="5fe38-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5fe38-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5fe38-125">Parent Elements</span></span>  
  
|<span data-ttu-id="5fe38-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="5fe38-126">Element</span></span>|<span data-ttu-id="5fe38-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5fe38-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5fe38-128">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="5fe38-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="5fe38-129">Toplamak, depolamak ve iletileri ve izleme anahtarı ayarlandığı düzeyi rota izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5fe38-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="5fe38-130">Herhangi bir kaynak veya trace ögesi başvurabilir dinleyicileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="5fe38-130">A collection of listeners that any source or trace element can reference.</span></span>|  
|`add`|<span data-ttu-id="5fe38-131">Bir dinleyici ekler **sharedListeners** koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="5fe38-131">Adds a listener to the **sharedListeners** collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5fe38-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5fe38-132">Remarks</span></span>  
 <span data-ttu-id="5fe38-133">Dinleyici tanımlanmış olması durumunda bir `<add>` öğesinin `<sharedListeners>` öğesi, bu dinleyici için filtre tanımlanmalıdır içinde bir `<filter>` alt öğesi `<add>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="5fe38-133">If a listener is defined in an `<add>` element of the `<sharedListeners>` element, the filter for that listener should be defined in a `<filter>` element that is a child of the `<add>` element.</span></span>  
  
 <span data-ttu-id="5fe38-134">Bu öğe makine yapılandırma dosyası (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5fe38-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fe38-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="5fe38-135">Example</span></span>  
 <span data-ttu-id="5fe38-136">Aşağıdaki örnekte nasıl kullanılacağını gösterir `<filter>` İzleme dinleyicisi filtre eklemek için öğesi `console` içinde `sharedListeners` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="5fe38-136">The following example shows how to use the `<filter>` element to add a filter to the trace listener `console` in the `sharedListeners` collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5fe38-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5fe38-137">See Also</span></span>  
 <xref:System.Diagnostics.TraceFilter>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.TraceSource>  
 [<span data-ttu-id="5fe38-138">İzleme ve hata ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="5fe38-138">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
