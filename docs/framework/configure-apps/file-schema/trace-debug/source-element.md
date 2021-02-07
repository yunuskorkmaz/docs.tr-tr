---
description: 'Daha fazla bilgi edinin: <source> öğesi'
title: <source> Öğesi
ms.date: 09/29/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
ms.openlocfilehash: acf510dd5813900f36ac431418d55bbc6c2f364a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750591"
---
# <a name="source-element"></a><span data-ttu-id="6d8af-103">\<source> Öğesi</span><span class="sxs-lookup"><span data-stu-id="6d8af-103">\<source> Element</span></span>

<span data-ttu-id="6d8af-104">İzleme iletilerini Başlatan bir izleme kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6d8af-104">Specifies a trace source that initiates tracing messages.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<source>**

## <a name="syntax"></a><span data-ttu-id="6d8af-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="6d8af-105">Syntax</span></span>  
  
```xml  
<source>
  <listeners>...</listeners>  
</source>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6d8af-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6d8af-106">Attributes and Elements</span></span>  

 <span data-ttu-id="6d8af-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6d8af-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6d8af-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6d8af-108">Attributes</span></span>  
  
|<span data-ttu-id="6d8af-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6d8af-109">Attribute</span></span>|<span data-ttu-id="6d8af-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6d8af-110">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="6d8af-111">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6d8af-111">Optional attribute.</span></span><br /><br /> <span data-ttu-id="6d8af-112">İzleme kaynağının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6d8af-112">Specifies the name of the trace source.</span></span>|  
|`switchName`|<span data-ttu-id="6d8af-113">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6d8af-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="6d8af-114">Uygulamadaki bir izleme anahtarı örneğinin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6d8af-114">Specifies the name of a trace switch instance in the application.</span></span> <span data-ttu-id="6d8af-115">Anahtar bir `<switches>` öğesinde tanımlanmamışsa, değer anahtar düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6d8af-115">If the switch is not identified in a `<switches>` element, the value specifies the level for the switch.</span></span>|  
|`switchType`|<span data-ttu-id="6d8af-116">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6d8af-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="6d8af-117">İzleme anahtarının türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="6d8af-117">Specifies the type of the trace switch.</span></span> <span data-ttu-id="6d8af-118">Varsa, türün geçerli bir sınıf adı olması ve boş bir dize olmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6d8af-118">If present, the type must be a valid class name and cannot be an empty string.</span></span>|  
|`extraAttribute`|<span data-ttu-id="6d8af-119">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6d8af-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="6d8af-120">Bu izleme kaynağı için yöntemi tarafından tanımlanan izleme kaynağına özgü bir özniteliğin değerini belirtir <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> .</span><span class="sxs-lookup"><span data-stu-id="6d8af-120">Specifies the value for a trace source-specific attribute identified by the <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> method for that trace source.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6d8af-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6d8af-121">Child Elements</span></span>  
  
|<span data-ttu-id="6d8af-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="6d8af-122">Element</span></span>|<span data-ttu-id="6d8af-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6d8af-123">Description</span></span>|  
|-------------|-----------------|  
|[\<listeners>](listeners-element-for-source.md)|<span data-ttu-id="6d8af-124">İletileri toplayacak, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="6d8af-124">Contains listeners that collect, store, and route messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6d8af-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6d8af-125">Parent Elements</span></span>  
  
|<span data-ttu-id="6d8af-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="6d8af-126">Element</span></span>|<span data-ttu-id="6d8af-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6d8af-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6d8af-128">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="6d8af-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="6d8af-129">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6d8af-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="6d8af-130">İzleme iletilerini Başlatan izleme kaynaklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="6d8af-130">Contains trace sources that initiate tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d8af-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6d8af-131">Remarks</span></span>  

 <span data-ttu-id="6d8af-132">Bu öğe makine yapılandırma dosyasında (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6d8af-132">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d8af-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="6d8af-133">Example</span></span>  

 <span data-ttu-id="6d8af-134">Aşağıdaki örnek, `<source>` izleme kaynağını eklemek `mySource` ve adlı kaynak anahtarın düzeyini ayarlamak için öğesinin nasıl kullanılacağını gösterir `sourceSwitch` .</span><span class="sxs-lookup"><span data-stu-id="6d8af-134">The following example shows how to use the `<source>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="6d8af-135">İzleme bilgilerini konsola yazan bir konsol izleme dinleyicisi eklenir.</span><span class="sxs-lookup"><span data-stu-id="6d8af-135">A console trace listener is added that writes trace information to the console.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch" switchType="System.Diagnostics.SourceSwitch"  >  
        <listeners>  
          <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
            <filter type="System.Diagnostics.EventTypeFilter" initializeData="Error" />  
          </add>  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
        <switches>  
           <add name="sourceSwitch" value="Warning" />  
        </switches>
  </system.diagnostics>
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6d8af-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d8af-136">See also</span></span>

- [<span data-ttu-id="6d8af-137">İzleme ve hata ayıklama ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="6d8af-137">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6d8af-138">İzleme Anahtarları</span><span class="sxs-lookup"><span data-stu-id="6d8af-138">Trace Switches</span></span>](../../../debug-trace-profile/trace-switches.md)
