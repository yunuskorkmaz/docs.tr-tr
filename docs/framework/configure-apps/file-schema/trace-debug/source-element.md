---
title: <source> Öğesi
ms.date: 09/29/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
ms.openlocfilehash: c4f7e31422ccd8129599db1120f9b0cb327d9319
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697206"
---
# <a name="source-element"></a><span data-ttu-id="15316-102">\<source > öğesi</span><span class="sxs-lookup"><span data-stu-id="15316-102">\<source> Element</span></span>
<span data-ttu-id="15316-103">İzleme iletilerini Başlatan bir izleme kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="15316-103">Specifies a trace source that initiates tracing messages.</span></span>  
  
[<span data-ttu-id="15316-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="15316-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="15316-105">&nbsp; @ no__t-1[ **\<system. Diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="15316-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="15316-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<sources >** ](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="15316-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>  
<span data-ttu-id="15316-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<source >**</span><span class="sxs-lookup"><span data-stu-id="15316-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<source>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15316-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="15316-108">Syntax</span></span>  
  
```xml  
<source>   
  <listeners>...</listeners>  
</source>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="15316-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="15316-109">Attributes and Elements</span></span>  
 <span data-ttu-id="15316-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="15316-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="15316-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="15316-111">Attributes</span></span>  
  
|<span data-ttu-id="15316-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="15316-112">Attribute</span></span>|<span data-ttu-id="15316-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15316-113">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="15316-114">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="15316-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="15316-115">İzleme kaynağının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="15316-115">Specifies the name of the trace source.</span></span>|  
|`switchName`|<span data-ttu-id="15316-116">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="15316-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="15316-117">Uygulamadaki bir izleme anahtarı örneğinin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="15316-117">Specifies the name of a trace switch instance in the application.</span></span> <span data-ttu-id="15316-118">Anahtar `<switches>` öğesinde tanımlanmamışsa değer, anahtarın düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="15316-118">If the switch is not identified in a `<switches>` element, the value specifies the level for the switch.</span></span>|  
|`switchType`|<span data-ttu-id="15316-119">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="15316-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="15316-120">İzleme anahtarının türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="15316-120">Specifies the type of the trace switch.</span></span> <span data-ttu-id="15316-121">Varsa, türün geçerli bir sınıf adı olması ve boş bir dize olmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="15316-121">If present, the type must be a valid class name and cannot be an empty string.</span></span>|  
|`extraAttribute`|<span data-ttu-id="15316-122">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="15316-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="15316-123">Bu izleme kaynağı için <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> yöntemiyle tanımlanan izleme kaynağına özgü bir özniteliğin değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="15316-123">Specifies the value for a trace source-specific attribute identified by the <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> method for that trace source.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="15316-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="15316-124">Child Elements</span></span>  
  
|<span data-ttu-id="15316-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="15316-125">Element</span></span>|<span data-ttu-id="15316-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15316-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="15316-127">\<listeners ></span><span class="sxs-lookup"><span data-stu-id="15316-127">\<listeners></span></span>](listeners-element-for-source.md)|<span data-ttu-id="15316-128">İletileri toplayacak, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="15316-128">Contains listeners that collect, store, and route messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="15316-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="15316-129">Parent Elements</span></span>  
  
|<span data-ttu-id="15316-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="15316-130">Element</span></span>|<span data-ttu-id="15316-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15316-131">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="15316-132">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="15316-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="15316-133">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="15316-133">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="15316-134">İzleme iletilerini Başlatan izleme kaynaklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="15316-134">Contains trace sources that initiate tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15316-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="15316-135">Remarks</span></span>  
 <span data-ttu-id="15316-136">Bu öğe makine yapılandırma dosyasında (Machine. config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="15316-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15316-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="15316-137">Example</span></span>  
 <span data-ttu-id="15316-138">Aşağıdaki örnek, `mySource` izleme kaynağını eklemek ve `sourceSwitch` adlı kaynak anahtarın düzeyini ayarlamak için `<source>` öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="15316-138">The following example shows how to use the `<source>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="15316-139">İzleme bilgilerini konsola yazan bir konsol izleme dinleyicisi eklenir.</span><span class="sxs-lookup"><span data-stu-id="15316-139">A console trace listener is added that writes trace information to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="15316-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15316-140">See also</span></span>

- [<span data-ttu-id="15316-141">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="15316-141">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="15316-142">İzleme Anahtarları</span><span class="sxs-lookup"><span data-stu-id="15316-142">Trace Switches</span></span>](../../../debug-trace-profile/trace-switches.md)
