---
title: <source> Öğesi
ms.date: 09/29/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
ms.openlocfilehash: 55120e292ac2a2c822c5510563d1aa167ca921e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920449"
---
# <a name="source-element"></a><span data-ttu-id="a6555-102">\<Kaynak > öğesi</span><span class="sxs-lookup"><span data-stu-id="a6555-102">\<source> Element</span></span>
<span data-ttu-id="a6555-103">İzleme iletilerini Başlatan bir izleme kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a6555-103">Specifies a trace source that initiates tracing messages.</span></span>  
  
 <span data-ttu-id="a6555-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="a6555-104">\<configuration></span></span>  
<span data-ttu-id="a6555-105">\<System. Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="a6555-105">\<system.diagnostics></span></span>  
<span data-ttu-id="a6555-106">\<Kaynaklar ></span><span class="sxs-lookup"><span data-stu-id="a6555-106">\<sources></span></span>  
<span data-ttu-id="a6555-107">\<Kaynak ></span><span class="sxs-lookup"><span data-stu-id="a6555-107">\<source></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6555-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a6555-108">Syntax</span></span>  
  
```xml  
<source>   
  <listeners>...</listeners>  
</source>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6555-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a6555-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a6555-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a6555-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6555-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a6555-111">Attributes</span></span>  
  
|<span data-ttu-id="a6555-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a6555-112">Attribute</span></span>|<span data-ttu-id="a6555-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a6555-113">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="a6555-114">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a6555-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a6555-115">İzleme kaynağının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a6555-115">Specifies the name of the trace source.</span></span>|  
|`switchName`|<span data-ttu-id="a6555-116">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a6555-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a6555-117">Uygulamadaki bir izleme anahtarı örneğinin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a6555-117">Specifies the name of a trace switch instance in the application.</span></span> <span data-ttu-id="a6555-118">Anahtar bir `<switches>` öğesinde tanımlanmamışsa, değer anahtar düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a6555-118">If the switch is not identified in a `<switches>` element, the value specifies the level for the switch.</span></span>|  
|`switchType`|<span data-ttu-id="a6555-119">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a6555-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a6555-120">İzleme anahtarının türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="a6555-120">Specifies the type of the trace switch.</span></span> <span data-ttu-id="a6555-121">Varsa, türün geçerli bir sınıf adı olması ve boş bir dize olmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a6555-121">If present, the type must be a valid class name and cannot be an empty string.</span></span>|  
|`extraAttribute`|<span data-ttu-id="a6555-122">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a6555-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a6555-123">Bu izleme kaynağı için <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> yöntemi tarafından tanımlanan izleme kaynağına özgü bir özniteliğin değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a6555-123">Specifies the value for a trace source-specific attribute identified by the <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> method for that trace source.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a6555-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a6555-124">Child Elements</span></span>  
  
|<span data-ttu-id="a6555-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="a6555-125">Element</span></span>|<span data-ttu-id="a6555-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a6555-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6555-127">\<dinleyiciler ></span><span class="sxs-lookup"><span data-stu-id="a6555-127">\<listeners></span></span>](listeners-element-for-source.md)|<span data-ttu-id="a6555-128">İletileri toplayacak, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="a6555-128">Contains listeners that collect, store, and route messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a6555-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a6555-129">Parent Elements</span></span>  
  
|<span data-ttu-id="a6555-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="a6555-130">Element</span></span>|<span data-ttu-id="a6555-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a6555-131">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a6555-132">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="a6555-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="a6555-133">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a6555-133">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="a6555-134">İzleme iletilerini Başlatan izleme kaynaklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="a6555-134">Contains trace sources that initiate tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6555-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a6555-135">Remarks</span></span>  
 <span data-ttu-id="a6555-136">Bu öğe makine yapılandırma dosyasında (Machine. config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a6555-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6555-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="a6555-137">Example</span></span>  
 <span data-ttu-id="a6555-138">Aşağıdaki örnek, izleme kaynağını `<source>` `mySource` eklemek ve adlı `sourceSwitch`kaynak anahtarın düzeyini ayarlamak için öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6555-138">The following example shows how to use the `<source>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="a6555-139">İzleme bilgilerini konsola yazan bir konsol izleme dinleyicisi eklenir.</span><span class="sxs-lookup"><span data-stu-id="a6555-139">A console trace listener is added that writes trace information to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a6555-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6555-140">See also</span></span>

- [<span data-ttu-id="a6555-141">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="a6555-141">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a6555-142">İzleme Anahtarları</span><span class="sxs-lookup"><span data-stu-id="a6555-142">Trace Switches</span></span>](../../../debug-trace-profile/trace-switches.md)
