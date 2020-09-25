---
title: <filter>İçin için öğesi <add><sharedListeners>
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
ms.openlocfilehash: e140148a342e31d6ade7def8849d8a7738301704
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173932"
---
# <a name="filter-element-for-add-for-sharedlisteners"></a><span data-ttu-id="db503-102">\<filter>İçin için öğesi \<add>\<sharedListeners></span><span class="sxs-lookup"><span data-stu-id="db503-102">\<filter> Element for \<add> for \<sharedListeners></span></span>

<span data-ttu-id="db503-103">Koleksiyondaki bir dinleyiciye bir filtre ekler `sharedListeners` .</span><span class="sxs-lookup"><span data-stu-id="db503-103">Adds a filter to a listener in the `sharedListeners` collection.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-sharedlisteners.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**

## <a name="syntax"></a><span data-ttu-id="db503-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="db503-104">Syntax</span></span>  
  
```xml  
<filter type="System.Diagnostics.EventTypeFilter"
  initializeData="Warning" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="db503-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="db503-105">Attributes and Elements</span></span>  

 <span data-ttu-id="db503-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="db503-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="db503-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="db503-107">Attributes</span></span>  
  
|<span data-ttu-id="db503-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="db503-108">Attribute</span></span>|<span data-ttu-id="db503-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="db503-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="db503-110">**türüyle**</span><span class="sxs-lookup"><span data-stu-id="db503-110">**type**</span></span>|<span data-ttu-id="db503-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="db503-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="db503-112">Filtrenin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="db503-112">Specifies the type of the filter.</span></span> <span data-ttu-id="db503-113">Türün tam adını ( <xref:System.Type.FullName%2A?displayProperty=nameWithType> özelliğinin biçiminde) veya derleme bilgileri de dahil olmak üzere tam nitelikli tür adını ( <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> özelliğin biçiminde) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db503-113">You can use only the full name of the type (in the format of the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property), or you can use the fully qualified type name including the assembly information (in the format of the <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> property).</span></span> <span data-ttu-id="db503-114">Tam nitelikli tür adı oluşturma hakkında bilgi için, bkz. [tam nitelikli tür adları belirtme](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="db503-114">For information on creating a fully qualified type name, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="db503-115">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="db503-115">**initializeData**</span></span>|<span data-ttu-id="db503-116">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="db503-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="db503-117">Belirtilen sınıf için oluşturucuya geçirilen dize.</span><span class="sxs-lookup"><span data-stu-id="db503-117">The string passed to the constructor for the specified class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="db503-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="db503-118">Child Elements</span></span>  

 <span data-ttu-id="db503-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="db503-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="db503-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="db503-120">Parent Elements</span></span>  
  
|<span data-ttu-id="db503-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="db503-121">Element</span></span>|<span data-ttu-id="db503-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="db503-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="db503-123">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="db503-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="db503-124">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="db503-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="db503-125">Herhangi bir kaynak veya izleme öğesinin başvurmasına yönelik bir dinleyici koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="db503-125">A collection of listeners that any source or trace element can reference.</span></span>|  
|`add`|<span data-ttu-id="db503-126">**SharedListeners** koleksiyonuna bir dinleyici ekler.</span><span class="sxs-lookup"><span data-stu-id="db503-126">Adds a listener to the **sharedListeners** collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db503-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="db503-127">Remarks</span></span>  

 <span data-ttu-id="db503-128">Bir dinleyici `<add>` öğenin öğesi içinde tanımlanmışsa `<sharedListeners>` , bu dinleyicinin filtresi `<filter>` öğenin alt öğesi olan bir öğe içinde tanımlanmalıdır `<add>` .</span><span class="sxs-lookup"><span data-stu-id="db503-128">If a listener is defined in an `<add>` element of the `<sharedListeners>` element, the filter for that listener should be defined in a `<filter>` element that is a child of the `<add>` element.</span></span>  
  
 <span data-ttu-id="db503-129">Bu öğe makine yapılandırma dosyasında (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="db503-129">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db503-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="db503-130">Example</span></span>  

 <span data-ttu-id="db503-131">Aşağıdaki örnek, `<filter>` koleksiyonundaki izleme dinleyicisine bir filtre eklemek için öğesinin nasıl kullanılacağını gösterir `console` `sharedListeners` .</span><span class="sxs-lookup"><span data-stu-id="db503-131">The following example shows how to use the `<filter>` element to add a filter to the trace listener `console` in the `sharedListeners` collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="db503-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db503-132">See also</span></span>

- <xref:System.Diagnostics.TraceFilter>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="db503-133">İzleme ve hata ayıklama ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="db503-133">Trace and Debug Settings Schema</span></span>](index.md)
