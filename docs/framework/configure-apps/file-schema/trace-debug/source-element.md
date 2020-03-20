---
title: <source> Öğesi
ms.date: 09/29/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
ms.openlocfilehash: 417722ce2f3865350158413307495e3ab435d386
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153301"
---
# <a name="source-element"></a><span data-ttu-id="822c5-102">\<kaynak> Element</span><span class="sxs-lookup"><span data-stu-id="822c5-102">\<source> Element</span></span>
<span data-ttu-id="822c5-103">İletilerin izlenmesini başlatan bir izleme kaynağı belirtir.</span><span class="sxs-lookup"><span data-stu-id="822c5-103">Specifies a trace source that initiates tracing messages.</span></span>  

<span data-ttu-id="822c5-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="822c5-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="822c5-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="822c5-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="822c5-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<kaynaklar>**](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="822c5-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>\
<span data-ttu-id="822c5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<kaynak>**</span><span class="sxs-lookup"><span data-stu-id="822c5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<source>**</span></span>

## <a name="syntax"></a><span data-ttu-id="822c5-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="822c5-108">Syntax</span></span>  
  
```xml  
<source>
  <listeners>...</listeners>  
</source>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="822c5-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="822c5-109">Attributes and Elements</span></span>  
 <span data-ttu-id="822c5-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="822c5-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="822c5-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="822c5-111">Attributes</span></span>  
  
|<span data-ttu-id="822c5-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="822c5-112">Attribute</span></span>|<span data-ttu-id="822c5-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="822c5-113">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="822c5-114">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="822c5-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="822c5-115">İzleme kaynağının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="822c5-115">Specifies the name of the trace source.</span></span>|  
|`switchName`|<span data-ttu-id="822c5-116">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="822c5-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="822c5-117">Uygulamada bir izleme anahtarı örneğinin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="822c5-117">Specifies the name of a trace switch instance in the application.</span></span> <span data-ttu-id="822c5-118">Anahtar bir `<switches>` öğede tanımlanmamışsa, değer anahtarın düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="822c5-118">If the switch is not identified in a `<switches>` element, the value specifies the level for the switch.</span></span>|  
|`switchType`|<span data-ttu-id="822c5-119">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="822c5-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="822c5-120">İzleme anahtarının türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="822c5-120">Specifies the type of the trace switch.</span></span> <span data-ttu-id="822c5-121">Varsa, tür geçerli bir sınıf adı olmalıdır ve boş bir dize olamaz.</span><span class="sxs-lookup"><span data-stu-id="822c5-121">If present, the type must be a valid class name and cannot be an empty string.</span></span>|  
|`extraAttribute`|<span data-ttu-id="822c5-122">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="822c5-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="822c5-123">Bu izleme kaynağı için <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> yöntem tarafından tanımlanan izleme kaynağına özgü bir öznitelik için değeri belirtir.</span><span class="sxs-lookup"><span data-stu-id="822c5-123">Specifies the value for a trace source-specific attribute identified by the <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> method for that trace source.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="822c5-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="822c5-124">Child Elements</span></span>  
  
|<span data-ttu-id="822c5-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="822c5-125">Element</span></span>|<span data-ttu-id="822c5-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="822c5-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="822c5-127">\<dinleyici ler></span><span class="sxs-lookup"><span data-stu-id="822c5-127">\<listeners></span></span>](listeners-element-for-source.md)|<span data-ttu-id="822c5-128">İletileri toplayan, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="822c5-128">Contains listeners that collect, store, and route messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="822c5-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="822c5-129">Parent Elements</span></span>  
  
|<span data-ttu-id="822c5-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="822c5-130">Element</span></span>|<span data-ttu-id="822c5-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="822c5-131">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="822c5-132">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="822c5-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="822c5-133">İletileri toplayan, depolayan ve yönlendiren izleme dinleyicilerini ve izleme anahtarının ayarlandığı düzeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="822c5-133">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="822c5-134">İletileri izlemeyi başlatan izleme kaynakları içerir.</span><span class="sxs-lookup"><span data-stu-id="822c5-134">Contains trace sources that initiate tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="822c5-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="822c5-135">Remarks</span></span>  
 <span data-ttu-id="822c5-136">Bu öğe makine yapılandırma dosyasında (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="822c5-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="822c5-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="822c5-137">Example</span></span>  
 <span data-ttu-id="822c5-138">Aşağıdaki örnek, izleme kaynağını `<source>` `mySource` eklemek ve adlı `sourceSwitch`kaynak anahtarının düzeyini ayarlamak için öğenin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="822c5-138">The following example shows how to use the `<source>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="822c5-139">Konsola izleme bilgileri yazan bir konsol izleme dinleyicisi eklenir.</span><span class="sxs-lookup"><span data-stu-id="822c5-139">A console trace listener is added that writes trace information to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="822c5-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="822c5-140">See also</span></span>

- [<span data-ttu-id="822c5-141">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="822c5-141">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="822c5-142">İzleme Anahtarları</span><span class="sxs-lookup"><span data-stu-id="822c5-142">Trace Switches</span></span>](../../../debug-trace-profile/trace-switches.md)
