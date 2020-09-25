---
title: <source> Öğesi
ms.date: 09/29/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
ms.openlocfilehash: e9c6a06ca9e481ecc2277e1d1ea76a0b99edb158
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173828"
---
# <a name="source-element"></a><span data-ttu-id="fff46-102">\<source> Öğesi</span><span class="sxs-lookup"><span data-stu-id="fff46-102">\<source> Element</span></span>

<span data-ttu-id="fff46-103">İzleme iletilerini Başlatan bir izleme kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fff46-103">Specifies a trace source that initiates tracing messages.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<source>**

## <a name="syntax"></a><span data-ttu-id="fff46-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="fff46-104">Syntax</span></span>  
  
```xml  
<source>
  <listeners>...</listeners>  
</source>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fff46-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fff46-105">Attributes and Elements</span></span>  

 <span data-ttu-id="fff46-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fff46-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fff46-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fff46-107">Attributes</span></span>  
  
|<span data-ttu-id="fff46-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fff46-108">Attribute</span></span>|<span data-ttu-id="fff46-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fff46-109">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="fff46-110">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="fff46-110">Optional attribute.</span></span><br /><br /> <span data-ttu-id="fff46-111">İzleme kaynağının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fff46-111">Specifies the name of the trace source.</span></span>|  
|`switchName`|<span data-ttu-id="fff46-112">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="fff46-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="fff46-113">Uygulamadaki bir izleme anahtarı örneğinin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fff46-113">Specifies the name of a trace switch instance in the application.</span></span> <span data-ttu-id="fff46-114">Anahtar bir `<switches>` öğesinde tanımlanmamışsa, değer anahtar düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fff46-114">If the switch is not identified in a `<switches>` element, the value specifies the level for the switch.</span></span>|  
|`switchType`|<span data-ttu-id="fff46-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="fff46-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="fff46-116">İzleme anahtarının türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="fff46-116">Specifies the type of the trace switch.</span></span> <span data-ttu-id="fff46-117">Varsa, türün geçerli bir sınıf adı olması ve boş bir dize olmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fff46-117">If present, the type must be a valid class name and cannot be an empty string.</span></span>|  
|`extraAttribute`|<span data-ttu-id="fff46-118">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="fff46-118">Optional attribute.</span></span><br /><br /> <span data-ttu-id="fff46-119">Bu izleme kaynağı için yöntemi tarafından tanımlanan izleme kaynağına özgü bir özniteliğin değerini belirtir <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> .</span><span class="sxs-lookup"><span data-stu-id="fff46-119">Specifies the value for a trace source-specific attribute identified by the <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> method for that trace source.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fff46-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fff46-120">Child Elements</span></span>  
  
|<span data-ttu-id="fff46-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="fff46-121">Element</span></span>|<span data-ttu-id="fff46-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fff46-122">Description</span></span>|  
|-------------|-----------------|  
|[\<listeners>](listeners-element-for-source.md)|<span data-ttu-id="fff46-123">İletileri toplayacak, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="fff46-123">Contains listeners that collect, store, and route messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fff46-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fff46-124">Parent Elements</span></span>  
  
|<span data-ttu-id="fff46-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="fff46-125">Element</span></span>|<span data-ttu-id="fff46-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fff46-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="fff46-127">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="fff46-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="fff46-128">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fff46-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="fff46-129">İzleme iletilerini Başlatan izleme kaynaklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="fff46-129">Contains trace sources that initiate tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fff46-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fff46-130">Remarks</span></span>  

 <span data-ttu-id="fff46-131">Bu öğe makine yapılandırma dosyasında (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fff46-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fff46-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="fff46-132">Example</span></span>  

 <span data-ttu-id="fff46-133">Aşağıdaki örnek, `<source>` izleme kaynağını eklemek `mySource` ve adlı kaynak anahtarın düzeyini ayarlamak için öğesinin nasıl kullanılacağını gösterir `sourceSwitch` .</span><span class="sxs-lookup"><span data-stu-id="fff46-133">The following example shows how to use the `<source>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="fff46-134">İzleme bilgilerini konsola yazan bir konsol izleme dinleyicisi eklenir.</span><span class="sxs-lookup"><span data-stu-id="fff46-134">A console trace listener is added that writes trace information to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fff46-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fff46-135">See also</span></span>

- [<span data-ttu-id="fff46-136">İzleme ve hata ayıklama ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="fff46-136">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="fff46-137">İzleme Anahtarları</span><span class="sxs-lookup"><span data-stu-id="fff46-137">Trace Switches</span></span>](../../../debug-trace-profile/trace-switches.md)
