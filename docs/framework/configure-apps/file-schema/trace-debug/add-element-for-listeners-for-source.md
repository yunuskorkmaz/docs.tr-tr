---
title: "&lt;ekleme&gt; öğesi için &lt;dinleyicileri&gt; için &lt;kaynağı&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
caps.latest.revision: "15"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 86177010d8ed70302b51ec9c416a3295009e7394
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-element-for-ltlistenersgt-for-ltsourcegt"></a><span data-ttu-id="c5166-102">&lt;ekleme&gt; öğesi için &lt;dinleyicileri&gt; için &lt;kaynağı&gt;</span><span class="sxs-lookup"><span data-stu-id="c5166-102">&lt;add&gt; Element for &lt;listeners&gt; for &lt;source&gt;</span></span>
<span data-ttu-id="c5166-103">Bir dinleyici ekler `Listeners` koleksiyonu için bir izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="c5166-103">Adds a listener to the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="c5166-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="c5166-104">\<configuration></span></span>  
<span data-ttu-id="c5166-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="c5166-105">\<system.diagnostics></span></span>  
<span data-ttu-id="c5166-106">\<Kaynakları ></span><span class="sxs-lookup"><span data-stu-id="c5166-106">\<sources></span></span>  
<span data-ttu-id="c5166-107">\<Kaynak ></span><span class="sxs-lookup"><span data-stu-id="c5166-107">\<source></span></span>  
<span data-ttu-id="c5166-108">\<dinleyicileri ></span><span class="sxs-lookup"><span data-stu-id="c5166-108">\<listeners></span></span>  
<span data-ttu-id="c5166-109">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="c5166-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5166-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c5166-110">Syntax</span></span>  
  
```xml  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5166-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c5166-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c5166-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c5166-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5166-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c5166-113">Attributes</span></span>  
  
|<span data-ttu-id="c5166-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c5166-114">Attribute</span></span>|<span data-ttu-id="c5166-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c5166-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="c5166-116">Öznitelik, bir dinleyici başvuran sürece gerekli `sharedListeners` koleksiyon, bu durumda yalnızca ada göre başvurduğu gerek (bkz [örnek](#example)).</span><span class="sxs-lookup"><span data-stu-id="c5166-116">Required attribute, unless you're referencing a listener in the `sharedListeners` collection, in which case you only need to refer to it by name (see the [Example](#example)).</span></span><br /><br /> <span data-ttu-id="c5166-117">Dinleyici türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5166-117">Specifies the type of the listener.</span></span> <span data-ttu-id="c5166-118">Belirtilen gereksinimleri karşılayan bir dize kullanmalısınız [belirtme tam olarak nitelenmiş tür adları](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="c5166-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="c5166-119">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="c5166-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="c5166-120">Dize için belirtilen sınıf oluşturucuya geçirilen.</span><span class="sxs-lookup"><span data-stu-id="c5166-120">The string passed to the constructor for the specified class.</span></span> <span data-ttu-id="c5166-121">A <xref:System.Configuration.ConfigurationException> sınıfı bir dize alır bir oluşturucuya sahip değilse oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c5166-121">A <xref:System.Configuration.ConfigurationException> is thrown if the class does not have a constructor that takes a string.</span></span>|  
|`name`|<span data-ttu-id="c5166-122">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="c5166-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="c5166-123">Dinleyici adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5166-123">Specifies the name of the listener.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="c5166-124">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="c5166-124">Optional attribute.</span></span><br /><br /> <span data-ttu-id="c5166-125">Belirtir <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> İzleme dinleyicisi için özellik değeri.</span><span class="sxs-lookup"><span data-stu-id="c5166-125">Specifies the <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> property value for the trace listener.</span></span>|  
|<span data-ttu-id="c5166-126">[özel öznitelikler]</span><span class="sxs-lookup"><span data-stu-id="c5166-126">[custom attributes]</span></span>|<span data-ttu-id="c5166-127">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="c5166-127">Optional attributes.</span></span><br /><br /> <span data-ttu-id="c5166-128">Tarafından tanımlanan dinleyici özel öznitelikleri için değer belirtir <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> bu dinleyici için yöntem.</span><span class="sxs-lookup"><span data-stu-id="c5166-128">Specifies the value for listener-specific attributes identified by the <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> method for that listener.</span></span> <span data-ttu-id="c5166-129"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A>ek bir öznitelik için benzersiz örneğidir <xref:System.Diagnostics.DelimitedListTraceListener> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c5166-129"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> is an example of an extra attribute unique to the <xref:System.Diagnostics.DelimitedListTraceListener> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c5166-130">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c5166-130">Child Elements</span></span>  
  
|<span data-ttu-id="c5166-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="c5166-131">Element</span></span>|<span data-ttu-id="c5166-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c5166-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c5166-133">\<Filtre ></span><span class="sxs-lookup"><span data-stu-id="c5166-133">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-source.md)|<span data-ttu-id="c5166-134">Bir dinleyici için bir filtre ekler `Listeners` koleksiyonu için bir izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="c5166-134">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c5166-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c5166-135">Parent Elements</span></span>  
  
|<span data-ttu-id="c5166-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="c5166-136">Element</span></span>|<span data-ttu-id="c5166-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c5166-137">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c5166-138">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="c5166-138">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="c5166-139">Toplamak, depolamak ve iletileri ve izleme anahtarı ayarlandığı düzeyi rota izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5166-139">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="c5166-140">İzleme iletileri başlatmak izleme kaynaklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="c5166-140">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="c5166-141">İzleme iletileri başlatan bir izleme kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5166-141">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="c5166-142">Toplamak, depolamak ve iletileri yönlendirmek dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5166-142">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5166-143">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c5166-143">Remarks</span></span>  
 <span data-ttu-id="c5166-144">.NET Framework ile birlikte gelen dinleyicisi sınıfları türetin <xref:System.Diagnostics.TraceListener> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c5166-144">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="c5166-145">Belirtmezseniz, `name` İzleme dinleyicisi özniteliği <xref:System.Diagnostics.TraceListener.Name%2A> İzleme dinleyicisi özelliği varsayılan olarak boş bir dize ("").</span><span class="sxs-lookup"><span data-stu-id="c5166-145">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> property of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="c5166-146">Yalnızca tek bir dinleyici uygulamanız varsa, bir adı belirtmeden ekleyebilir ve boş bir dize adı belirterek kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5166-146">If your application has only one listener, you can add it without specifying a name, and you can remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="c5166-147">Ancak, birden çok dinleyici uygulamanız varsa, tanımlamanıza ve tek tek izleme dinleyicileri yönetmenize olanak tanıyan her İzleme dinleyicisi için benzersiz bir ad belirtmeniz gerekir <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="c5166-147">However, if your application has more than one listener, you should specify a unique name for each trace listener, which allows you to identify and manage individual trace listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c5166-148">Birden fazla İzleme dinleyicisi aynı türde ve aynı ekleme yalnızca bir izleme dinleyicisi sonuçlarında türü ve eklenmesini adlandırın `Listeners` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="c5166-148">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="c5166-149">Ancak, program aracılığıyla birden çok özdeş dinleyici ekleyebilirsiniz `Listeners` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="c5166-149">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="c5166-150">Değeri `initializeData` özniteliği oluşturduğunuz dinleyicisi türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c5166-150">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="c5166-151">Tüm izleme dinleyicileri, belirttiğiniz gerektiren `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="c5166-151">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c5166-152">Kullandığınızda `initializeData` özniteliği, "'initializeData' özniteliği yok bildirildi." uyarı derleyici alabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="c5166-152">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="c5166-153">Yapılandırma ayarları Özet temel sınıf karşı doğrulandığı için bu uyarıyı oluşur <xref:System.Diagnostics.TraceListener>, hangi tanımıyor `initializeData` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="c5166-153">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="c5166-154">Genellikle, bir parametre alan bir oluşturucuya sahip İzleme dinleyicisi uygulamaları için bu uyarıyı yoksayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5166-154">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="c5166-155">Aşağıdaki tabloda .NET Framework ile birlikte izleme dinleyicilerini gösterir ve değerini açıklar kendi `initializeData` öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="c5166-155">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="c5166-156">İzleme dinleyicisi sınıfı</span><span class="sxs-lookup"><span data-stu-id="c5166-156">Trace listener class</span></span>|<span data-ttu-id="c5166-157">initializeData özniteliği değeri</span><span class="sxs-lookup"><span data-stu-id="c5166-157">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="c5166-158">`useErrorStream` Değerini <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="c5166-158">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="c5166-159">Ayarlama `initializeData` özniteliğini "`true`"yazmak için izleme ve hata ayıklama için standart hata akışı; çıktı ayarlayın"`false`" standart çıktı akışına yazmak için.</span><span class="sxs-lookup"><span data-stu-id="c5166-159">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="c5166-160">Dosyanın adını <xref:System.Diagnostics.DelimitedListTraceListener> yazar.</span><span class="sxs-lookup"><span data-stu-id="c5166-160">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="c5166-161">Var olan bir olay günlüğü kaynağı adı.</span><span class="sxs-lookup"><span data-stu-id="c5166-161">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="c5166-162">Dosya adı, <xref:System.Diagnostics.EventSchemaTraceListener> yazar.</span><span class="sxs-lookup"><span data-stu-id="c5166-162">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="c5166-163">Dosya adı, <xref:System.Diagnostics.TextWriterTraceListener> yazar.</span><span class="sxs-lookup"><span data-stu-id="c5166-163">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="c5166-164">Dosya adı, <xref:System.Diagnostics.XmlWriterTraceListener> yazar.</span><span class="sxs-lookup"><span data-stu-id="c5166-164">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="c5166-165">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="c5166-165">Configuration File</span></span>  
 <span data-ttu-id="c5166-166">Bu öğe makine yapılandırma dosyası (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c5166-166">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5166-167">Örnek</span><span class="sxs-lookup"><span data-stu-id="c5166-167">Example</span></span>  
 <span data-ttu-id="c5166-168">Aşağıdaki örnekte nasıl kullanılacağını gösterir `<add>` dinleyicileri eklemek için öğeleri `console` ve `textListener` için `Listeners` izleme kaynağı toplamalarında `TraceSourceApp`.</span><span class="sxs-lookup"><span data-stu-id="c5166-168">The following example shows how to use `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="c5166-169">`textListener` Dinleyicisi dosya myListener.log izleme çıktısı yazar.</span><span class="sxs-lookup"><span data-stu-id="c5166-169">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"   
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
          <remove name="Default"/>  
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
  
## <a name="see-also"></a><span data-ttu-id="c5166-170">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c5166-170">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TraceListener>  
 [<span data-ttu-id="c5166-171">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="c5166-171">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="c5166-172">İzleme Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="c5166-172">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
