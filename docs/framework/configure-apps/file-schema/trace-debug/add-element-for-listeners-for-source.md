---
title: '&lt;ekleme&gt; öğesi için &lt;dinleyicileri&gt; için &lt;kaynak&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
author: mcleblanc
ms.author: markl
ms.openlocfilehash: c22263fd51b80e7bd99ada8452696debdcc44140
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54507421"
---
# <a name="ltaddgt-element-for-ltlistenersgt-for-ltsourcegt"></a><span data-ttu-id="00a52-102">&lt;ekleme&gt; öğesi için &lt;dinleyicileri&gt; için &lt;kaynak&gt;</span><span class="sxs-lookup"><span data-stu-id="00a52-102">&lt;add&gt; Element for &lt;listeners&gt; for &lt;source&gt;</span></span>
<span data-ttu-id="00a52-103">Bir ekler `Listeners` koleksiyonu için bir izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="00a52-103">Adds a listener to the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="00a52-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="00a52-104">\<configuration></span></span>  
<span data-ttu-id="00a52-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="00a52-105">\<system.diagnostics></span></span>  
<span data-ttu-id="00a52-106">\<Kaynakları ></span><span class="sxs-lookup"><span data-stu-id="00a52-106">\<sources></span></span>  
<span data-ttu-id="00a52-107">\<Kaynak ></span><span class="sxs-lookup"><span data-stu-id="00a52-107">\<source></span></span>  
<span data-ttu-id="00a52-108">\<dinleyicileri ></span><span class="sxs-lookup"><span data-stu-id="00a52-108">\<listeners></span></span>  
<span data-ttu-id="00a52-109">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="00a52-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00a52-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="00a52-110">Syntax</span></span>  
  
```xml  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="00a52-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="00a52-111">Attributes and Elements</span></span>  
 <span data-ttu-id="00a52-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="00a52-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="00a52-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="00a52-113">Attributes</span></span>  
  
|<span data-ttu-id="00a52-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="00a52-114">Attribute</span></span>|<span data-ttu-id="00a52-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="00a52-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="00a52-116">Gerekli öznitelik, bir dinleyicisi başvuran sürece `sharedListeners` koleksiyon, yalnızca ada göre başvurduğu gerek case (bkz [örnek](#example)).</span><span class="sxs-lookup"><span data-stu-id="00a52-116">Required attribute, unless you're referencing a listener in the `sharedListeners` collection, in which case you only need to refer to it by name (see the [Example](#example)).</span></span><br /><br /> <span data-ttu-id="00a52-117">Dinleyici türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="00a52-117">Specifies the type of the listener.</span></span> <span data-ttu-id="00a52-118">Belirtilen gereksinimleri karşılayan bir dize kullanmalısınız [belirtme tam olarak nitelenmiş tür adlarını](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="00a52-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="00a52-119">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="00a52-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="00a52-120">Belirtilen sınıf için oluşturucuya geçirilen dizesi.</span><span class="sxs-lookup"><span data-stu-id="00a52-120">The string passed to the constructor for the specified class.</span></span> <span data-ttu-id="00a52-121">A <xref:System.Configuration.ConfigurationException> sınıfı bir dize alan bir oluşturucu yoksa, oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="00a52-121">A <xref:System.Configuration.ConfigurationException> is thrown if the class does not have a constructor that takes a string.</span></span>|  
|`name`|<span data-ttu-id="00a52-122">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="00a52-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="00a52-123">Dinleyicisinin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="00a52-123">Specifies the name of the listener.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="00a52-124">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="00a52-124">Optional attribute.</span></span><br /><br /> <span data-ttu-id="00a52-125">Belirtir <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> İzleme dinleyicisi için özellik değeri.</span><span class="sxs-lookup"><span data-stu-id="00a52-125">Specifies the <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> property value for the trace listener.</span></span>|  
|<span data-ttu-id="00a52-126">[özel öznitelikler]</span><span class="sxs-lookup"><span data-stu-id="00a52-126">[custom attributes]</span></span>|<span data-ttu-id="00a52-127">İsteğe bağlı öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="00a52-127">Optional attributes.</span></span><br /><br /> <span data-ttu-id="00a52-128">Tarafından tanımlanan dinleyicisi özel öznitelikler için bir değer belirtir <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> bu dinleyici için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="00a52-128">Specifies the value for listener-specific attributes identified by the <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> method for that listener.</span></span> <span data-ttu-id="00a52-129"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> ek bir öznitelik için benzersiz örneğidir <xref:System.Diagnostics.DelimitedListTraceListener> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="00a52-129"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> is an example of an extra attribute unique to the <xref:System.Diagnostics.DelimitedListTraceListener> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="00a52-130">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="00a52-130">Child Elements</span></span>  
  
|<span data-ttu-id="00a52-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="00a52-131">Element</span></span>|<span data-ttu-id="00a52-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="00a52-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="00a52-133">\<Filtre ></span><span class="sxs-lookup"><span data-stu-id="00a52-133">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-source.md)|<span data-ttu-id="00a52-134">Bir dinleyicisi için bir filtre ekler `Listeners` koleksiyonu için bir izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="00a52-134">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="00a52-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="00a52-135">Parent Elements</span></span>  
  
|<span data-ttu-id="00a52-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="00a52-136">Element</span></span>|<span data-ttu-id="00a52-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="00a52-137">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="00a52-138">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="00a52-138">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="00a52-139">Toplamak, depolamak ve iletileri ve bir izleme anahtarı ayarlandığı düzeyi izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="00a52-139">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="00a52-140">İzleme iletileri başlatmak iz kaynakları içerir.</span><span class="sxs-lookup"><span data-stu-id="00a52-140">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="00a52-141">İzleme iletileri başlatan bir izleme kaynağı belirtir.</span><span class="sxs-lookup"><span data-stu-id="00a52-141">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="00a52-142">Toplamak, depolamak ve iletileri yönlendirmek dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="00a52-142">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00a52-143">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="00a52-143">Remarks</span></span>  
 <span data-ttu-id="00a52-144">.NET Framework ile birlikte gelen dinleyici sınıfların türetilmesi <xref:System.Diagnostics.TraceListener> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="00a52-144">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="00a52-145">Siz belirtmezseniz `name` İzleme dinleyicisi özniteliği <xref:System.Diagnostics.TraceListener.Name%2A> İzleme dinleyicisi özelliği varsayılan olarak boş bir dize olarak ("").</span><span class="sxs-lookup"><span data-stu-id="00a52-145">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> property of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="00a52-146">Uygulamanızın yalnızca bir dinleyicisi varsa, bir adı belirtmeden ekleyebilir ve boş bir dize adı belirterek kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00a52-146">If your application has only one listener, you can add it without specifying a name, and you can remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="00a52-147">Ancak, uygulamanızın birden fazla dinleyici varsa, tanımlamak ve yönetmek, tek tek izleme dinleyicilerine olanak tanıyan her İzleme dinleyicisi için benzersiz bir ad belirtmeniz gerekir <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="00a52-147">However, if your application has more than one listener, you should specify a unique name for each trace listener, which allows you to identify and manage individual trace listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="00a52-148">Birden fazla İzleme dinleyicisi aynı türde ve aynı adı yalnızca bir izleme dinleyicisi sonuçlarında türü ekleyip eklenmesini ad `Listeners` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="00a52-148">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="00a52-149">Ancak, program aracılığıyla birden fazla özdeş dinleyicilere ekleyebilirsiniz `Listeners` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="00a52-149">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="00a52-150">Değeri `initializeData` özniteliği oluşturduğunuz dinleyici türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="00a52-150">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="00a52-151">Tüm izleme dinleyicilerine belirtmenizi gerektiren `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="00a52-151">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="00a52-152">Kullanırken `initializeData` özniteliği, "'initializeData' özniteliği. bildirilmedi" uyarı derleyici alabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="00a52-152">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="00a52-153">Bu uyarı oluşur yapılandırma ayarlarını soyut temel sınıf doğrulanır <xref:System.Diagnostics.TraceListener>, hangi tanımıyor `initializeData` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="00a52-153">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="00a52-154">Genellikle, bir parametre alan bir oluşturucu sahip İzleme dinleyicisi uygulamaları için bu uyarıyı yoksayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00a52-154">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="00a52-155">Aşağıdaki tablo .NET Framework ile birlikte izleme dinleyicilerine gösterir ve değerinin açıklanmıştır kendi `initializeData` öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="00a52-155">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="00a52-156">İzleme dinleyicisi sınıfı</span><span class="sxs-lookup"><span data-stu-id="00a52-156">Trace listener class</span></span>|<span data-ttu-id="00a52-157">initializeData özniteliği değeri</span><span class="sxs-lookup"><span data-stu-id="00a52-157">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="00a52-158">`useErrorStream` Değerini <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="00a52-158">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="00a52-159">Ayarlama `initializeData` özniteliğini "`true`"yazmak için izleme ve hata ayıklama için standart hata akışı; çıktı ayarlayın"`false`" standart çıkış akışına yazmak için.</span><span class="sxs-lookup"><span data-stu-id="00a52-159">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="00a52-160">Dosya adı <xref:System.Diagnostics.DelimitedListTraceListener> yazar.</span><span class="sxs-lookup"><span data-stu-id="00a52-160">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="00a52-161">Mevcut bir olay günlüğü kaynağı adı.</span><span class="sxs-lookup"><span data-stu-id="00a52-161">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="00a52-162">Dosyanın adı, <xref:System.Diagnostics.EventSchemaTraceListener> yazar.</span><span class="sxs-lookup"><span data-stu-id="00a52-162">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="00a52-163">Dosyanın adı, <xref:System.Diagnostics.TextWriterTraceListener> yazar.</span><span class="sxs-lookup"><span data-stu-id="00a52-163">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="00a52-164">Dosyanın adı, <xref:System.Diagnostics.XmlWriterTraceListener> yazar.</span><span class="sxs-lookup"><span data-stu-id="00a52-164">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="00a52-165">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="00a52-165">Configuration File</span></span>  
 <span data-ttu-id="00a52-166">Bu öğe, makine yapılandırma dosyası (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="00a52-166">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00a52-167">Örnek</span><span class="sxs-lookup"><span data-stu-id="00a52-167">Example</span></span>  
 <span data-ttu-id="00a52-168">Aşağıdaki örnek nasıl kullanılacağını gösterir `<add>` dinleyiciler eklemek için öğeleri `console` ve `textListener` için `Listeners` iz kaynağı için koleksiyon `TraceSourceApp`.</span><span class="sxs-lookup"><span data-stu-id="00a52-168">The following example shows how to use `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="00a52-169">`textListener` Dinleyici için dosya myListener.log izleme çıktısına yazar.</span><span class="sxs-lookup"><span data-stu-id="00a52-169">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="00a52-170">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00a52-170">See also</span></span>
- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="00a52-171">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="00a52-171">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [<span data-ttu-id="00a52-172">İzleme Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="00a52-172">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
