---
title: '&lt;kaldırma&gt; öğesi için &lt;dinleyicileri&gt; için &lt;kaynak&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
ms.openlocfilehash: 9f3d8eefdf74f0960f3fe530f77a67c0706e4585
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083489"
---
# <a name="ltremovegt-element-for-ltlistenersgt-for-ltsourcegt"></a><span data-ttu-id="d41f9-102">&lt;kaldırma&gt; öğesi için &lt;dinleyicileri&gt; için &lt;kaynak&gt;</span><span class="sxs-lookup"><span data-stu-id="d41f9-102">&lt;remove&gt; Element for &lt;listeners&gt; for &lt;source&gt;</span></span>
<span data-ttu-id="d41f9-103">Bir dinleyicisinden kaldırır `Listeners` koleksiyonu için bir izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="d41f9-103">Removes a listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="d41f9-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="d41f9-104">\<configuration></span></span>  
<span data-ttu-id="d41f9-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="d41f9-105">\<system.diagnostics></span></span>  
<span data-ttu-id="d41f9-106">\<Kaynakları ></span><span class="sxs-lookup"><span data-stu-id="d41f9-106">\<sources></span></span>  
<span data-ttu-id="d41f9-107">\<Kaynak ></span><span class="sxs-lookup"><span data-stu-id="d41f9-107">\<source></span></span>  
<span data-ttu-id="d41f9-108">\<dinleyicileri ></span><span class="sxs-lookup"><span data-stu-id="d41f9-108">\<listeners></span></span>  
<span data-ttu-id="d41f9-109">\<kaldırma ></span><span class="sxs-lookup"><span data-stu-id="d41f9-109">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d41f9-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d41f9-110">Syntax</span></span>  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d41f9-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d41f9-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d41f9-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d41f9-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d41f9-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d41f9-113">Attributes</span></span>  
  
|<span data-ttu-id="d41f9-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d41f9-114">Attribute</span></span>|<span data-ttu-id="d41f9-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d41f9-115">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="d41f9-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d41f9-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="d41f9-117">Dinleyiciyi kaldırmak için adını `Listeners` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d41f9-117">The name of the listener to remove from the `Listeners` collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d41f9-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d41f9-118">Child Elements</span></span>  
 <span data-ttu-id="d41f9-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="d41f9-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d41f9-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d41f9-120">Parent Elements</span></span>  
  
|<span data-ttu-id="d41f9-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="d41f9-121">Element</span></span>|<span data-ttu-id="d41f9-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d41f9-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d41f9-123">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="d41f9-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="d41f9-124">Toplamak, depolamak ve iletileri ve bir izleme anahtarı ayarlandığı düzeyi izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d41f9-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="d41f9-125">İzleme iletileri başlatmak iz kaynakları içerir.</span><span class="sxs-lookup"><span data-stu-id="d41f9-125">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="d41f9-126">İzleme iletileri başlatan bir izleme kaynağı belirtir.</span><span class="sxs-lookup"><span data-stu-id="d41f9-126">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="d41f9-127">Toplamak, depolamak ve iletileri yönlendirmek dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d41f9-127">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d41f9-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d41f9-128">Remarks</span></span>  
 <span data-ttu-id="d41f9-129">`<remove>` Öğeyi kaldırır belirtilen dinleyicisinden `Listeners` koleksiyonu için bir izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="d41f9-129">The `<remove>` element removes a specified listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="d41f9-130">Bir öğeyi kaldırmanız `Listeners` koleksiyonu için bir izleme kaynağı çağırarak programlama yoluyla <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> metodunda <xref:System.Diagnostics.TraceSource.Listeners%2A> özelliği <xref:System.Diagnostics.TraceSource> örneği.</span><span class="sxs-lookup"><span data-stu-id="d41f9-130">You can remove an element from the `Listeners` collection for a trace source programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> method on the <xref:System.Diagnostics.TraceSource.Listeners%2A> property of the <xref:System.Diagnostics.TraceSource> instance.</span></span>  
  
 <span data-ttu-id="d41f9-131">Bu öğe, makine yapılandırma dosyası (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d41f9-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d41f9-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="d41f9-132">Example</span></span>  
 <span data-ttu-id="d41f9-133">Aşağıdaki örnek nasıl kullanılacağını gösterir `<remove>` kullanmadan önce öğesi `<add>` dinleyici eklemek için öğe `console` için `Listeners` iz kaynağı için koleksiyon `TraceSourceApp`.</span><span class="sxs-lookup"><span data-stu-id="d41f9-133">The following example shows how to use the `<remove>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d41f9-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d41f9-134">See also</span></span>
- <xref:System.Diagnostics.TraceSource.Listeners%2A>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="d41f9-135">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="d41f9-135">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [<span data-ttu-id="d41f9-136">\<Temizleme ></span><span class="sxs-lookup"><span data-stu-id="d41f9-136">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)
- [<span data-ttu-id="d41f9-137">İzleme Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="d41f9-137">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
