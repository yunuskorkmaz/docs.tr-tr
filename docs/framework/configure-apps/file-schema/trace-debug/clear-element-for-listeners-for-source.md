---
title: '&lt;Clear&gt; öğesi için &lt;dinleyicileri&gt; için &lt;kaynağı&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/clear
helpviewer_keywords:
- <clear> element for <listeners> for <source>
- clear element for <listeners> for <source>
ms.assetid: 76796bb2-9c0b-4526-8135-8bf18b16d8d9
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 8c6ef51dae36e94fa4a4fdc5ad8983380e78bde3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltcleargt-element-for-ltlistenersgt-for-ltsourcegt"></a><span data-ttu-id="4613d-102">&lt;Clear&gt; öğesi için &lt;dinleyicileri&gt; için &lt;kaynağı&gt;</span><span class="sxs-lookup"><span data-stu-id="4613d-102">&lt;clear&gt; Element for &lt;listeners&gt; for &lt;source&gt;</span></span>
<span data-ttu-id="4613d-103">Temizler `Listeners` koleksiyonu için bir izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="4613d-103">Clears the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="4613d-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="4613d-104">\<configuration></span></span>  
<span data-ttu-id="4613d-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="4613d-105">\<system.diagnostics></span></span>  
<span data-ttu-id="4613d-106">\<Kaynakları ></span><span class="sxs-lookup"><span data-stu-id="4613d-106">\<sources></span></span>  
<span data-ttu-id="4613d-107">\<Kaynak ></span><span class="sxs-lookup"><span data-stu-id="4613d-107">\<source></span></span>  
<span data-ttu-id="4613d-108">\<dinleyicileri ></span><span class="sxs-lookup"><span data-stu-id="4613d-108">\<listeners></span></span>  
<span data-ttu-id="4613d-109">\<Clear ></span><span class="sxs-lookup"><span data-stu-id="4613d-109">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4613d-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4613d-110">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4613d-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4613d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="4613d-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4613d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4613d-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4613d-113">Attributes</span></span>  
 <span data-ttu-id="4613d-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="4613d-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4613d-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4613d-115">Child Elements</span></span>  
 <span data-ttu-id="4613d-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="4613d-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4613d-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4613d-117">Parent Elements</span></span>  
  
|<span data-ttu-id="4613d-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="4613d-118">Element</span></span>|<span data-ttu-id="4613d-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4613d-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4613d-120">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="4613d-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="4613d-121">Toplamak, depolamak ve iletileri ve izleme anahtarı ayarlandığı düzeyi rota izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4613d-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="4613d-122">İzleme iletileri başlatmak izleme kaynaklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="4613d-122">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="4613d-123">İzleme iletileri başlatan bir izleme kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4613d-123">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="4613d-124">Toplamak, depolamak ve iletileri yönlendirmek dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4613d-124">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4613d-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4613d-125">Remarks</span></span>  
 <span data-ttu-id="4613d-126">`<clear>` Öğeyi kaldırır gelen tüm dinleyicileri `Listeners` koleksiyonu için bir izleme kaynağı dahil olmak üzere <xref:System.Diagnostics.DefaultTraceListener>.</span><span class="sxs-lookup"><span data-stu-id="4613d-126">The `<clear>` element removes all listeners from the `Listeners` collection for a trace source, including the <xref:System.Diagnostics.DefaultTraceListener>.</span></span> <span data-ttu-id="4613d-127">Kullanabileceğiniz `<clear>` kullanmadan önce öğesi `<add>` öğe koleksiyonda diğer etkin dinleyicileri olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="4613d-127">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="4613d-128">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="4613d-128">Configuration File</span></span>  
 <span data-ttu-id="4613d-129">Bu öğe makine yapılandırma dosyası (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4613d-129">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4613d-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="4613d-130">Example</span></span>  
 <span data-ttu-id="4613d-131">Aşağıdaki örnekte nasıl kullanılacağını gösterir `<clear>` kullanmadan önce öğesi `<add>` dinleyicileri eklemek için öğeleri `console` ve `textListener` için `Listeners` izleme kaynağı toplamalarında `TraceSourceApp`.</span><span class="sxs-lookup"><span data-stu-id="4613d-131">The following example shows how to use the `<clear>` element before using the `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
       <source name="TraceSourceApp" switchName="sourceSwitch"   
         switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <clear/>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"   
        type="System.Diagnostics.TextWriterTraceListener"   
        initializeData="myListener.log"/>  
    </sharedListeners>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a><span data-ttu-id="4613d-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4613d-132">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TraceListener>  
 [<span data-ttu-id="4613d-133">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="4613d-133">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="4613d-134">İzleme Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="4613d-134">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
