---
title: '&lt;dinleyicileri&gt; öğesi için &lt;kaynak&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners
helpviewer_keywords:
- listeners element for <source>
- <listeners> element for <source>
ms.assetid: a2991f43-b4d3-4614-a8e7-da392de9697f
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 86b85779f4eff72e8ab910a5ccd32fd369270509
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47085692"
---
# <a name="ltlistenersgt-element-for-ltsourcegt"></a><span data-ttu-id="c04d9-102">&lt;dinleyicileri&gt; öğesi için &lt;kaynak&gt;</span><span class="sxs-lookup"><span data-stu-id="c04d9-102">&lt;listeners&gt; Element for &lt;source&gt;</span></span>
<span data-ttu-id="c04d9-103">Ekler veya kaldırır, dinleyicileri <xref:System.Diagnostics.TraceSource.Listeners%2A> koleksiyonu için bir <xref:System.Diagnostics.TraceSource>.</span><span class="sxs-lookup"><span data-stu-id="c04d9-103">Adds or removes listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A> collection for a <xref:System.Diagnostics.TraceSource>.</span></span> <span data-ttu-id="c04d9-104">Dinleyici günlük, pencere veya metin dosyası gibi uygun bir hedef izleme çıkışa yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="c04d9-104">A listener directs the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
 <span data-ttu-id="c04d9-105">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="c04d9-105">\<configuration></span></span>  
<span data-ttu-id="c04d9-106">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="c04d9-106">\<system.diagnostics></span></span>  
<span data-ttu-id="c04d9-107">\<Kaynakları ></span><span class="sxs-lookup"><span data-stu-id="c04d9-107">\<sources></span></span>  
<span data-ttu-id="c04d9-108">\<Kaynak ></span><span class="sxs-lookup"><span data-stu-id="c04d9-108">\<source></span></span>  
<span data-ttu-id="c04d9-109">\<dinleyicileri > öğesi</span><span class="sxs-lookup"><span data-stu-id="c04d9-109">\<listeners> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c04d9-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c04d9-110">Syntax</span></span>  
  
```xml  
<listeners>   
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c04d9-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c04d9-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c04d9-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c04d9-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c04d9-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c04d9-113">Attributes</span></span>  
 <span data-ttu-id="c04d9-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="c04d9-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c04d9-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c04d9-115">Child Elements</span></span>  
  
|<span data-ttu-id="c04d9-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="c04d9-116">Element</span></span>|<span data-ttu-id="c04d9-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c04d9-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c04d9-118">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="c04d9-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-source.md)|<span data-ttu-id="c04d9-119">Bir ekler `Listeners` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="c04d9-119">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="c04d9-120">\<kaldırma ></span><span class="sxs-lookup"><span data-stu-id="c04d9-120">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-source.md)|<span data-ttu-id="c04d9-121">Bir dinleyicisinden kaldırır `Listeners` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="c04d9-121">Removes a listener from the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="c04d9-122">\<Temizleme ></span><span class="sxs-lookup"><span data-stu-id="c04d9-122">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)|<span data-ttu-id="c04d9-123">Temizler `Listeners` koleksiyonu için bir izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="c04d9-123">Clears the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c04d9-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c04d9-124">Parent Elements</span></span>  
  
|<span data-ttu-id="c04d9-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="c04d9-125">Element</span></span>|<span data-ttu-id="c04d9-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c04d9-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c04d9-127">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="c04d9-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="c04d9-128">Toplamak, depolamak ve iletileri ve bir izleme anahtarı ayarlandığı düzeyi izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c04d9-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="c04d9-129">İzleme iletileri başlatmak iz kaynakları içerir.</span><span class="sxs-lookup"><span data-stu-id="c04d9-129">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="c04d9-130">İzleme iletileri başlatan bir izleme kaynağı belirtir.</span><span class="sxs-lookup"><span data-stu-id="c04d9-130">Specifies a trace source that initiates tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c04d9-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c04d9-131">Remarks</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="c04d9-132">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="c04d9-132">Configuration File</span></span>  
 <span data-ttu-id="c04d9-133">Bu öğe, makine yapılandırma dosyası (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c04d9-133">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c04d9-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="c04d9-134">Example</span></span>  
 <span data-ttu-id="c04d9-135">Aşağıdaki örnek nasıl kullanılacağını gösterir `<listeners>` öğesi eklemek için bir konsol iz dinleyicisi için `mySource` kaynak ve varsayılan İzleme dinleyicisi kaldırmak için.</span><span class="sxs-lookup"><span data-stu-id="c04d9-135">The following example shows how to use the `<listeners>` element to add a console trace listener to the `mySource` source and to remove the default trace listener.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"   
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener">  
            <filter type="System.Diagnostics.EventTypeFilter"   
              initializeData="Error"/>  
          </add>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c04d9-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c04d9-136">See Also</span></span>  
 <xref:System.Diagnostics.TraceListener>  
 [<span data-ttu-id="c04d9-137">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="c04d9-137">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="c04d9-138">İzleme Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="c04d9-138">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
