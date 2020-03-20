---
title: <filter><add> Için element<sharedListeners>
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
ms.openlocfilehash: 6fb52cdfa5792ab6059b60d8dbb91c107cd666ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153459"
---
# <a name="filter-element-for-add-for-sharedlisteners"></a><span data-ttu-id="7c060-102">\<paylaşılan Dinleyiciler \<için \<> eklemek için> Öğesi'ni filtreleme></span><span class="sxs-lookup"><span data-stu-id="7c060-102">\<filter> Element for \<add> for \<sharedListeners></span></span>
<span data-ttu-id="7c060-103">`sharedListeners` Koleksiyondaki bir dinleyiciye filtre ekler.</span><span class="sxs-lookup"><span data-stu-id="7c060-103">Adds a filter to a listener in the `sharedListeners` collection.</span></span>  

<span data-ttu-id="7c060-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7c060-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7c060-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="7c060-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="7c060-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<paylaşılanDinleyiciler>**](sharedlisteners-element.md)</span><span class="sxs-lookup"><span data-stu-id="7c060-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)</span></span>\
<span data-ttu-id="7c060-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>ekleyin**](add-element-for-sharedlisteners.md)</span><span class="sxs-lookup"><span data-stu-id="7c060-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-sharedlisteners.md)</span></span>\
<span data-ttu-id="7c060-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filtre>**</span><span class="sxs-lookup"><span data-stu-id="7c060-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**</span></span>

## <a name="syntax"></a><span data-ttu-id="7c060-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7c060-109">Syntax</span></span>  
  
```xml  
<filter type="System.Diagnostics.EventTypeFilter"
  initializeData="Warning" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7c060-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7c060-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7c060-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7c060-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7c060-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7c060-112">Attributes</span></span>  
  
|<span data-ttu-id="7c060-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7c060-113">Attribute</span></span>|<span data-ttu-id="7c060-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7c060-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7c060-115">**Türü**</span><span class="sxs-lookup"><span data-stu-id="7c060-115">**type**</span></span>|<span data-ttu-id="7c060-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="7c060-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="7c060-117">Filtrenin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="7c060-117">Specifies the type of the filter.</span></span> <span data-ttu-id="7c060-118">Yalnızca türün tam adını <xref:System.Type.FullName%2A?displayProperty=nameWithType> (özelliğin biçiminde) veya derleme bilgilerini de içeren tam nitelikli tür adını <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> (özelliğin biçiminde) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c060-118">You can use only the full name of the type (in the format of the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property), or you can use the fully qualified type name including the assembly information (in the format of the <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> property).</span></span> <span data-ttu-id="7c060-119">Tam nitelikli tür adı oluşturma hakkında bilgi için [bkz.](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)</span><span class="sxs-lookup"><span data-stu-id="7c060-119">For information on creating a fully qualified type name, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="7c060-120">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="7c060-120">**initializeData**</span></span>|<span data-ttu-id="7c060-121">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="7c060-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="7c060-122">Dize, belirtilen sınıfın oluşturucuya geçti.</span><span class="sxs-lookup"><span data-stu-id="7c060-122">The string passed to the constructor for the specified class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7c060-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7c060-123">Child Elements</span></span>  
 <span data-ttu-id="7c060-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="7c060-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7c060-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7c060-125">Parent Elements</span></span>  
  
|<span data-ttu-id="7c060-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="7c060-126">Element</span></span>|<span data-ttu-id="7c060-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7c060-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7c060-128">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="7c060-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="7c060-129">İletileri toplayan, depolayan ve yönlendiren izleme dinleyicilerini ve izleme anahtarının ayarlandığı düzeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="7c060-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="7c060-130">Herhangi bir kaynak veya izleme öğesinin başvuruda bulunabileceği dinleyici koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="7c060-130">A collection of listeners that any source or trace element can reference.</span></span>|  
|`add`|<span data-ttu-id="7c060-131">**Paylaşılan Dinleyici** koleksiyonuna bir dinleyici ekler.</span><span class="sxs-lookup"><span data-stu-id="7c060-131">Adds a listener to the **sharedListeners** collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c060-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7c060-132">Remarks</span></span>  
 <span data-ttu-id="7c060-133">Bir `<add>` dinleyici `<sharedListeners>` öğenin bir öğesi nde tanımlanırsa, bu dinleyici için `<filter>` filtre `<add>` öğenin bir alt öğesi olan bir öğe tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7c060-133">If a listener is defined in an `<add>` element of the `<sharedListeners>` element, the filter for that listener should be defined in a `<filter>` element that is a child of the `<add>` element.</span></span>  
  
 <span data-ttu-id="7c060-134">Bu öğe makine yapılandırma dosyasında (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7c060-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c060-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="7c060-135">Example</span></span>  
 <span data-ttu-id="7c060-136">Aşağıdaki örnek, `<filter>` `console` koleksiyondaki izleme dinleyicisine bir filtre eklemek için `sharedListeners` öğenin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7c060-136">The following example shows how to use the `<filter>` element to add a filter to the trace listener `console` in the `sharedListeners` collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7c060-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7c060-137">See also</span></span>

- <xref:System.Diagnostics.TraceFilter>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="7c060-138">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="7c060-138">Trace and Debug Settings Schema</span></span>](index.md)
