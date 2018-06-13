---
title: '&lt;Kaynak&gt; öğesi'
ms.date: 09/29/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b7c2a71b129a0ad7d1c2a72b18b8a69a111f9495
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752578"
---
# <a name="ltsourcegt-element"></a><span data-ttu-id="9dd65-102">&lt;Kaynak&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="9dd65-102">&lt;source&gt; Element</span></span>
<span data-ttu-id="9dd65-103">İzleme iletileri başlatan bir izleme kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9dd65-103">Specifies a trace source that initiates tracing messages.</span></span>  
  
 <span data-ttu-id="9dd65-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="9dd65-104">\<configuration></span></span>  
<span data-ttu-id="9dd65-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="9dd65-105">\<system.diagnostics></span></span>  
<span data-ttu-id="9dd65-106">\<Kaynakları ></span><span class="sxs-lookup"><span data-stu-id="9dd65-106">\<sources></span></span>  
<span data-ttu-id="9dd65-107">\<Kaynak ></span><span class="sxs-lookup"><span data-stu-id="9dd65-107">\<source></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9dd65-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9dd65-108">Syntax</span></span>  
  
```xml  
<source>   
  <listeners>...</listeners>  
</source>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9dd65-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9dd65-109">Attributes and Elements</span></span>  
 <span data-ttu-id="9dd65-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9dd65-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9dd65-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9dd65-111">Attributes</span></span>  
  
|<span data-ttu-id="9dd65-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9dd65-112">Attribute</span></span>|<span data-ttu-id="9dd65-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9dd65-113">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="9dd65-114">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="9dd65-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="9dd65-115">İzleme kaynağı adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9dd65-115">Specifies the name of the trace source.</span></span>|  
|`switchName`|<span data-ttu-id="9dd65-116">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="9dd65-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="9dd65-117">Uygulama izleme anahtar örneğinin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9dd65-117">Specifies the name of a trace switch instance in the application.</span></span> <span data-ttu-id="9dd65-118">Anahtar belirlediyseniz değil, bir `<switches>` öğesi, değer anahtar düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9dd65-118">If the switch is not identified in a `<switches>` element, the value specifies the level for the switch.</span></span>|  
|`switchType`|<span data-ttu-id="9dd65-119">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="9dd65-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="9dd65-120">İzleme anahtarı türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="9dd65-120">Specifies the type of the trace switch.</span></span> <span data-ttu-id="9dd65-121">Varsa, türü geçerli bir sınıf adı olmalı ve boş bir dize olamaz.</span><span class="sxs-lookup"><span data-stu-id="9dd65-121">If present, the type must be a valid class name and cannot be an empty string.</span></span>|  
|`extraAttribute`|<span data-ttu-id="9dd65-122">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="9dd65-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="9dd65-123">Tarafından tanımlanan bir izleme kaynağı özgü öznitelik değerini belirtir <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> yöntemi için bu izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="9dd65-123">Specifies the value for a trace source-specific attribute identified by the <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> method for that trace source.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9dd65-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9dd65-124">Child Elements</span></span>  
  
|<span data-ttu-id="9dd65-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="9dd65-125">Element</span></span>|<span data-ttu-id="9dd65-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9dd65-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9dd65-127">\<dinleyicileri ></span><span class="sxs-lookup"><span data-stu-id="9dd65-127">\<listeners></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-source.md)|<span data-ttu-id="9dd65-128">Toplamak, depolamak ve iletileri yönlendirmek dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="9dd65-128">Contains listeners that collect, store, and route messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9dd65-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9dd65-129">Parent Elements</span></span>  
  
|<span data-ttu-id="9dd65-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="9dd65-130">Element</span></span>|<span data-ttu-id="9dd65-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9dd65-131">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9dd65-132">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="9dd65-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="9dd65-133">Toplamak, depolamak ve iletileri ve izleme anahtarı ayarlandığı düzeyi rota izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9dd65-133">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="9dd65-134">İzleme iletileri başlatmak izleme kaynaklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="9dd65-134">Contains trace sources that initiate tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9dd65-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9dd65-135">Remarks</span></span>  
 <span data-ttu-id="9dd65-136">Bu öğe makine yapılandırma dosyası (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9dd65-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9dd65-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="9dd65-137">Example</span></span>  
 <span data-ttu-id="9dd65-138">Aşağıdaki örnekte nasıl kullanılacağını gösterir `<source>` izleme kaynağı eklemek için öğesi `mySource` ve kaynak anahtarı düzeyini ayarlamak için adlandırılmış `sourceSwitch`.</span><span class="sxs-lookup"><span data-stu-id="9dd65-138">The following example shows how to use the `<source>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="9dd65-139">Bir konsol İzleme dinleyicisi, izleme bilgilerini konsola eklenir.</span><span class="sxs-lookup"><span data-stu-id="9dd65-139">A console trace listener is added that writes trace information to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9dd65-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9dd65-140">See Also</span></span>  
 [<span data-ttu-id="9dd65-141">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="9dd65-141">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="9dd65-142">İzleme Anahtarları</span><span class="sxs-lookup"><span data-stu-id="9dd65-142">Trace Switches</span></span>](../../../../../docs/framework/debug-trace-profile/trace-switches.md)
