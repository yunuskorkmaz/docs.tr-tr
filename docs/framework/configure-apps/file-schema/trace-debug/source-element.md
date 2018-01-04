---
title: "&lt;Kaynak&gt; öğesi"
ms.date: 09/29/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: d6c5c65be8a540fdbba64d5a604c0963f9797e0a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsourcegt-element"></a><span data-ttu-id="73691-102">&lt;Kaynak&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="73691-102">&lt;source&gt; Element</span></span>
<span data-ttu-id="73691-103">İzleme iletileri başlatan bir izleme kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="73691-103">Specifies a trace source that initiates tracing messages.</span></span>  
  
 <span data-ttu-id="73691-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="73691-104">\<configuration></span></span>  
<span data-ttu-id="73691-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="73691-105">\<system.diagnostics></span></span>  
<span data-ttu-id="73691-106">\<Kaynakları ></span><span class="sxs-lookup"><span data-stu-id="73691-106">\<sources></span></span>  
<span data-ttu-id="73691-107">\<Kaynak ></span><span class="sxs-lookup"><span data-stu-id="73691-107">\<source></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73691-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="73691-108">Syntax</span></span>  
  
```xml  
<source>   
  <listeners>...</listeners>  
</source>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73691-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="73691-109">Attributes and Elements</span></span>  
 <span data-ttu-id="73691-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="73691-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73691-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="73691-111">Attributes</span></span>  
  
|<span data-ttu-id="73691-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="73691-112">Attribute</span></span>|<span data-ttu-id="73691-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="73691-113">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="73691-114">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="73691-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="73691-115">İzleme kaynağı adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="73691-115">Specifies the name of the trace source.</span></span>|  
|`switchName`|<span data-ttu-id="73691-116">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="73691-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="73691-117">Uygulama izleme anahtar örneğinin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="73691-117">Specifies the name of a trace switch instance in the application.</span></span> <span data-ttu-id="73691-118">Anahtar belirlediyseniz değil, bir `<switches>` öğesi, değer anahtar düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="73691-118">If the switch is not identified in a `<switches>` element, the value specifies the level for the switch.</span></span>|  
|`switchType`|<span data-ttu-id="73691-119">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="73691-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="73691-120">İzleme anahtarı türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="73691-120">Specifies the type of the trace switch.</span></span> <span data-ttu-id="73691-121">Varsa, türü geçerli bir sınıf adı olmalı ve boş bir dize olamaz.</span><span class="sxs-lookup"><span data-stu-id="73691-121">If present, the type must be a valid class name and cannot be an empty string.</span></span>|  
|`extraAttribute`|<span data-ttu-id="73691-122">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="73691-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="73691-123">Tarafından tanımlanan bir izleme kaynağı özgü öznitelik değerini belirtir <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> yöntemi için bu izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="73691-123">Specifies the value for a trace source-specific attribute identified by the <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> method for that trace source.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="73691-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="73691-124">Child Elements</span></span>  
  
|<span data-ttu-id="73691-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="73691-125">Element</span></span>|<span data-ttu-id="73691-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="73691-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="73691-127">\<dinleyicileri ></span><span class="sxs-lookup"><span data-stu-id="73691-127">\<listeners></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-source.md)|<span data-ttu-id="73691-128">Toplamak, depolamak ve iletileri yönlendirmek dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="73691-128">Contains listeners that collect, store, and route messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="73691-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="73691-129">Parent Elements</span></span>  
  
|<span data-ttu-id="73691-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="73691-130">Element</span></span>|<span data-ttu-id="73691-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="73691-131">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="73691-132">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="73691-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="73691-133">Toplamak, depolamak ve iletileri ve izleme anahtarı ayarlandığı düzeyi rota izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="73691-133">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="73691-134">İzleme iletileri başlatmak izleme kaynaklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="73691-134">Contains trace sources that initiate tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73691-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="73691-135">Remarks</span></span>  
 <span data-ttu-id="73691-136">Bu öğe makine yapılandırma dosyası (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="73691-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73691-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="73691-137">Example</span></span>  
 <span data-ttu-id="73691-138">Aşağıdaki örnekte nasıl kullanılacağını gösterir `<source>` izleme kaynağı eklemek için öğesi `mySource` ve kaynak anahtarı düzeyini ayarlamak için adlandırılmış `sourceSwitch`.</span><span class="sxs-lookup"><span data-stu-id="73691-138">The following example shows how to use the `<source>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="73691-139">Bir konsol İzleme dinleyicisi, izleme bilgilerini konsola eklenir.</span><span class="sxs-lookup"><span data-stu-id="73691-139">A console trace listener is added that writes trace information to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="73691-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="73691-140">See Also</span></span>  
 [<span data-ttu-id="73691-141">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="73691-141">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="73691-142">İzleme Anahtarları</span><span class="sxs-lookup"><span data-stu-id="73691-142">Trace Switches</span></span>](../../../../../docs/framework/debug-trace-profile/trace-switches.md)
