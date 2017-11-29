---
title: "&lt;kaldırma&gt; öğesi için &lt;dinleyicileri&gt; için &lt;kaynağı&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
caps.latest.revision: "6"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 6170c02296859d9c47e5288f287a4371d7cb0c56
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltremovegt-element-for-ltlistenersgt-for-ltsourcegt"></a><span data-ttu-id="df784-102">&lt;kaldırma&gt; öğesi için &lt;dinleyicileri&gt; için &lt;kaynağı&gt;</span><span class="sxs-lookup"><span data-stu-id="df784-102">&lt;remove&gt; Element for &lt;listeners&gt; for &lt;source&gt;</span></span>
<span data-ttu-id="df784-103">Gelen bir dinleyici kaldırır `Listeners` koleksiyonu için bir izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="df784-103">Removes a listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="df784-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="df784-104">\<configuration></span></span>  
<span data-ttu-id="df784-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="df784-105">\<system.diagnostics></span></span>  
<span data-ttu-id="df784-106">\<Kaynakları ></span><span class="sxs-lookup"><span data-stu-id="df784-106">\<sources></span></span>  
<span data-ttu-id="df784-107">\<Kaynak ></span><span class="sxs-lookup"><span data-stu-id="df784-107">\<source></span></span>  
<span data-ttu-id="df784-108">\<dinleyicileri ></span><span class="sxs-lookup"><span data-stu-id="df784-108">\<listeners></span></span>  
<span data-ttu-id="df784-109">\<kaldırma ></span><span class="sxs-lookup"><span data-stu-id="df784-109">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df784-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="df784-110">Syntax</span></span>  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="df784-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="df784-111">Attributes and Elements</span></span>  
 <span data-ttu-id="df784-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="df784-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="df784-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="df784-113">Attributes</span></span>  
  
|<span data-ttu-id="df784-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="df784-114">Attribute</span></span>|<span data-ttu-id="df784-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="df784-115">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="df784-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="df784-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="df784-117">Kaldırmak için dinleyicisinin adını `Listeners` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="df784-117">The name of the listener to remove from the `Listeners` collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="df784-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="df784-118">Child Elements</span></span>  
 <span data-ttu-id="df784-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="df784-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="df784-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="df784-120">Parent Elements</span></span>  
  
|<span data-ttu-id="df784-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="df784-121">Element</span></span>|<span data-ttu-id="df784-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="df784-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="df784-123">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="df784-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="df784-124">Toplamak, depolamak ve iletileri ve izleme anahtarı ayarlandığı düzeyi rota izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="df784-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="df784-125">İzleme iletileri başlatmak izleme kaynaklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="df784-125">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="df784-126">İzleme iletileri başlatan bir izleme kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="df784-126">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="df784-127">Toplamak, depolamak ve iletileri yönlendirmek dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="df784-127">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df784-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="df784-128">Remarks</span></span>  
 <span data-ttu-id="df784-129">`<remove>` Öğeyi kaldırır öğesinden belirtilen dinleyici `Listeners` koleksiyonu için bir izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="df784-129">The `<remove>` element removes a specified listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="df784-130">Bir öğeyi kaldırabilirsiniz `Listeners` çağırarak program aracılığıyla bir izleme kaynağı toplamalarında <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> yöntemi <xref:System.Diagnostics.TraceSource.Listeners%2A> özelliği <xref:System.Diagnostics.TraceSource> örneği.</span><span class="sxs-lookup"><span data-stu-id="df784-130">You can remove an element from the `Listeners` collection for a trace source programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> method on the <xref:System.Diagnostics.TraceSource.Listeners%2A> property of the <xref:System.Diagnostics.TraceSource> instance.</span></span>  
  
 <span data-ttu-id="df784-131">Bu öğe makine yapılandırma dosyası (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="df784-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df784-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="df784-132">Example</span></span>  
 <span data-ttu-id="df784-133">Aşağıdaki örnekte nasıl kullanılacağını gösterir `<remove>` kullanmadan önce öğesi `<add>` dinleyicisi eklemek için öğesi `console` için `Listeners` izleme kaynağı toplamalarında `TraceSourceApp`.</span><span class="sxs-lookup"><span data-stu-id="df784-133">The following example shows how to use the `<remove>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"   
         switchType="System.Diagnostics.SourceSwitch" >  
         <listeners>  
           <remove name="Default"/>  
           <add name="console"   
             type="System.Diagnostics.ConsoleTraceListener" />  
         </listeners>  
      </source>  
    </sources>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a><span data-ttu-id="df784-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="df784-134">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource.Listeners%2A>  
 <xref:System.Diagnostics.TraceSource>  
 [<span data-ttu-id="df784-135">İzleme ve hata ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="df784-135">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="df784-136">\<Clear ></span><span class="sxs-lookup"><span data-stu-id="df784-136">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)  
 [<span data-ttu-id="df784-137">İzleme dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="df784-137">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
