---
title: '&lt;kaldırma&gt; öğesi için &lt;dinleyicileri&gt; için &lt;kaynağı&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: cc6772e7a9b98f09df21fd1acf24f578b66ae51e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltremovegt-element-for-ltlistenersgt-for-ltsourcegt"></a><span data-ttu-id="55c6f-102">&lt;kaldırma&gt; öğesi için &lt;dinleyicileri&gt; için &lt;kaynağı&gt;</span><span class="sxs-lookup"><span data-stu-id="55c6f-102">&lt;remove&gt; Element for &lt;listeners&gt; for &lt;source&gt;</span></span>
<span data-ttu-id="55c6f-103">Gelen bir dinleyici kaldırır `Listeners` koleksiyonu için bir izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="55c6f-103">Removes a listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="55c6f-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="55c6f-104">\<configuration></span></span>  
<span data-ttu-id="55c6f-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="55c6f-105">\<system.diagnostics></span></span>  
<span data-ttu-id="55c6f-106">\<Kaynakları ></span><span class="sxs-lookup"><span data-stu-id="55c6f-106">\<sources></span></span>  
<span data-ttu-id="55c6f-107">\<Kaynak ></span><span class="sxs-lookup"><span data-stu-id="55c6f-107">\<source></span></span>  
<span data-ttu-id="55c6f-108">\<dinleyicileri ></span><span class="sxs-lookup"><span data-stu-id="55c6f-108">\<listeners></span></span>  
<span data-ttu-id="55c6f-109">\<kaldırma ></span><span class="sxs-lookup"><span data-stu-id="55c6f-109">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55c6f-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="55c6f-110">Syntax</span></span>  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55c6f-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="55c6f-111">Attributes and Elements</span></span>  
 <span data-ttu-id="55c6f-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="55c6f-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55c6f-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="55c6f-113">Attributes</span></span>  
  
|<span data-ttu-id="55c6f-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="55c6f-114">Attribute</span></span>|<span data-ttu-id="55c6f-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55c6f-115">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="55c6f-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="55c6f-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="55c6f-117">Kaldırmak için dinleyicisinin adını `Listeners` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="55c6f-117">The name of the listener to remove from the `Listeners` collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="55c6f-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="55c6f-118">Child Elements</span></span>  
 <span data-ttu-id="55c6f-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="55c6f-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="55c6f-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="55c6f-120">Parent Elements</span></span>  
  
|<span data-ttu-id="55c6f-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="55c6f-121">Element</span></span>|<span data-ttu-id="55c6f-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55c6f-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="55c6f-123">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="55c6f-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="55c6f-124">Toplamak, depolamak ve iletileri ve izleme anahtarı ayarlandığı düzeyi rota izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="55c6f-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="55c6f-125">İzleme iletileri başlatmak izleme kaynaklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="55c6f-125">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="55c6f-126">İzleme iletileri başlatan bir izleme kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="55c6f-126">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="55c6f-127">Toplamak, depolamak ve iletileri yönlendirmek dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="55c6f-127">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55c6f-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="55c6f-128">Remarks</span></span>  
 <span data-ttu-id="55c6f-129">`<remove>` Öğeyi kaldırır öğesinden belirtilen dinleyici `Listeners` koleksiyonu için bir izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="55c6f-129">The `<remove>` element removes a specified listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="55c6f-130">Bir öğeyi kaldırabilirsiniz `Listeners` çağırarak program aracılığıyla bir izleme kaynağı toplamalarında <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> yöntemi <xref:System.Diagnostics.TraceSource.Listeners%2A> özelliği <xref:System.Diagnostics.TraceSource> örneği.</span><span class="sxs-lookup"><span data-stu-id="55c6f-130">You can remove an element from the `Listeners` collection for a trace source programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> method on the <xref:System.Diagnostics.TraceSource.Listeners%2A> property of the <xref:System.Diagnostics.TraceSource> instance.</span></span>  
  
 <span data-ttu-id="55c6f-131">Bu öğe makine yapılandırma dosyası (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="55c6f-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55c6f-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="55c6f-132">Example</span></span>  
 <span data-ttu-id="55c6f-133">Aşağıdaki örnekte nasıl kullanılacağını gösterir `<remove>` kullanmadan önce öğesi `<add>` dinleyicisi eklemek için öğesi `console` için `Listeners` izleme kaynağı toplamalarında `TraceSourceApp`.</span><span class="sxs-lookup"><span data-stu-id="55c6f-133">The following example shows how to use the `<remove>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="55c6f-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="55c6f-134">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource.Listeners%2A>  
 <xref:System.Diagnostics.TraceSource>  
 [<span data-ttu-id="55c6f-135">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="55c6f-135">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="55c6f-136">\<Clear ></span><span class="sxs-lookup"><span data-stu-id="55c6f-136">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)  
 [<span data-ttu-id="55c6f-137">İzleme Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="55c6f-137">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
