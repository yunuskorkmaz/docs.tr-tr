---
title: <add><listeners> Için element<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
ms.openlocfilehash: 883eef32172c5a7f900197995b4c57c3d5a84e19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153691"
---
# <a name="add-element-for-listeners-for-source"></a><span data-ttu-id="3aa28-102">\<kaynak> \<için> \<dinleyiciler için> Öğesi ekleyin</span><span class="sxs-lookup"><span data-stu-id="3aa28-102">\<add> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="3aa28-103">İzleme kaynağı için `Listeners` koleksiyona dinleyici ekler.</span><span class="sxs-lookup"><span data-stu-id="3aa28-103">Adds a listener to the `Listeners` collection for a trace source.</span></span>  

<span data-ttu-id="3aa28-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3aa28-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3aa28-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="3aa28-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="3aa28-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<kaynaklar>**](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="3aa28-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>\
<span data-ttu-id="3aa28-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<kaynak>**](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="3aa28-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>\
<span data-ttu-id="3aa28-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dinleyici ler>**](listeners-element-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="3aa28-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)</span></span>\
<span data-ttu-id="3aa28-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>ekleyin**</span><span class="sxs-lookup"><span data-stu-id="3aa28-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="3aa28-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3aa28-110">Syntax</span></span>  
  
```xml  
<add name="name"
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3aa28-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3aa28-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3aa28-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3aa28-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3aa28-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3aa28-113">Attributes</span></span>  
  
|<span data-ttu-id="3aa28-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3aa28-114">Attribute</span></span>|<span data-ttu-id="3aa28-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3aa28-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="3aa28-116">`sharedListeners` Koleksiyonda bir dinleyiciye başvurmadığınız sürece gerekli öznitelik, bu durumda yalnızca ada göre başvurmanız gerekir [(Bkz. Örnek).](#example)</span><span class="sxs-lookup"><span data-stu-id="3aa28-116">Required attribute, unless you're referencing a listener in the `sharedListeners` collection, in which case you only need to refer to it by name (see the [Example](#example)).</span></span><br /><br /> <span data-ttu-id="3aa28-117">Dinleyicinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="3aa28-117">Specifies the type of the listener.</span></span> <span data-ttu-id="3aa28-118">[Tam Nitelikli Tür Adları Belirtme'de](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)belirtilen gereksinimleri karşılayan bir dize kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3aa28-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="3aa28-119">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="3aa28-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="3aa28-120">Dize, belirtilen sınıfın oluşturucuya geçti.</span><span class="sxs-lookup"><span data-stu-id="3aa28-120">The string passed to the constructor for the specified class.</span></span> <span data-ttu-id="3aa28-121">Sınıfın <xref:System.Configuration.ConfigurationException> dize alan bir oluşturucusu yoksa a atılır.</span><span class="sxs-lookup"><span data-stu-id="3aa28-121">A <xref:System.Configuration.ConfigurationException> is thrown if the class does not have a constructor that takes a string.</span></span>|  
|`name`|<span data-ttu-id="3aa28-122">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="3aa28-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="3aa28-123">Dinleyicinin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3aa28-123">Specifies the name of the listener.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="3aa28-124">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="3aa28-124">Optional attribute.</span></span><br /><br /> <span data-ttu-id="3aa28-125">İzleme dinleyicisinin <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> özellik değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3aa28-125">Specifies the <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> property value for the trace listener.</span></span>|  
|<span data-ttu-id="3aa28-126">[özel öznitelikler]</span><span class="sxs-lookup"><span data-stu-id="3aa28-126">[custom attributes]</span></span>|<span data-ttu-id="3aa28-127">İsteğe bağlı öznitelikler.</span><span class="sxs-lookup"><span data-stu-id="3aa28-127">Optional attributes.</span></span><br /><br /> <span data-ttu-id="3aa28-128">Dinleyiciye özgü özniteliklerin <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3aa28-128">Specifies the value for listener-specific attributes identified by the <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> method for that listener.</span></span> <span data-ttu-id="3aa28-129"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A><xref:System.Diagnostics.DelimitedListTraceListener> sınıfa özgü ek bir öznitelik örneğidir.</span><span class="sxs-lookup"><span data-stu-id="3aa28-129"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> is an example of an extra attribute unique to the <xref:System.Diagnostics.DelimitedListTraceListener> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3aa28-130">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3aa28-130">Child Elements</span></span>  
  
|<span data-ttu-id="3aa28-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="3aa28-131">Element</span></span>|<span data-ttu-id="3aa28-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3aa28-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3aa28-133">\<filtre></span><span class="sxs-lookup"><span data-stu-id="3aa28-133">\<filter></span></span>](filter-element-for-add-for-listeners-for-source.md)|<span data-ttu-id="3aa28-134">İzleme kaynağı için `Listeners` koleksiyondaki dinleyiciye filtre ekler.</span><span class="sxs-lookup"><span data-stu-id="3aa28-134">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3aa28-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3aa28-135">Parent Elements</span></span>  
  
|<span data-ttu-id="3aa28-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="3aa28-136">Element</span></span>|<span data-ttu-id="3aa28-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3aa28-137">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3aa28-138">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="3aa28-138">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="3aa28-139">İletileri toplayan, depolayan ve yönlendiren izleme dinleyicilerini ve izleme anahtarının ayarlandığı düzeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="3aa28-139">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="3aa28-140">İletileri izlemeyi başlatan izleme kaynakları içerir.</span><span class="sxs-lookup"><span data-stu-id="3aa28-140">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="3aa28-141">İletilerin izlenmesini başlatan bir izleme kaynağı belirtir.</span><span class="sxs-lookup"><span data-stu-id="3aa28-141">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="3aa28-142">İletileri toplayan, depolayan ve yönlendiren dinleyicileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="3aa28-142">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3aa28-143">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3aa28-143">Remarks</span></span>  
 <span data-ttu-id="3aa28-144">.NET Framework ile gönderilen dinleyici sınıfları <xref:System.Diagnostics.TraceListener> sınıftan türetilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3aa28-144">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="3aa28-145">İzleme dinleyicisinin özniteliğini `name` belirtmezseniz, izleme <xref:System.Diagnostics.TraceListener.Name%2A> dinleyicisinin özelliği varsayılan olarak boş bir dize ("") olur.</span><span class="sxs-lookup"><span data-stu-id="3aa28-145">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> property of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="3aa28-146">Uygulamanızda yalnızca bir dinleyici varsa, bir ad belirtmeden ekleyebilirsiniz ve ad için boş bir dize belirterek kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3aa28-146">If your application has only one listener, you can add it without specifying a name, and you can remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="3aa28-147">Ancak, uygulamanızda birden fazla dinleyici varsa, <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> koleksiyondaki tek tek izleme dinleyicilerini tanımlamanızı ve yönetmeniz için her izleme dinleyicisi için benzersiz bir ad belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3aa28-147">However, if your application has more than one listener, you should specify a unique name for each trace listener, which allows you to identify and manage individual trace listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3aa28-148">Aynı türden ve aynı ada sahip birden fazla izleme dinleyicisi eklemek, koleksiyona bu tür `Listeners` ve addan yalnızca bir izleme dinleyicisi eklenmesiyle sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="3aa28-148">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="3aa28-149">Ancak, `Listeners` koleksiyona programlı olarak birden çok aynı dinleyici ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3aa28-149">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="3aa28-150">Öznitelik değeri `initializeData` oluşturduğunuz dinleyici türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="3aa28-150">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="3aa28-151">Tüm izleme dinleyicileri belirtmenizi `initializeData`gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="3aa28-151">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3aa28-152">Özniteliği kullandığınızda, `initializeData` derleyici uyarı alabilirsiniz "'InitializeData' özniteliği ilan edilmez."</span><span class="sxs-lookup"><span data-stu-id="3aa28-152">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="3aa28-153">Yapılandırma ayarları özniteliği tanımayan <xref:System.Diagnostics.TraceListener> `initializeData` soyut taban sınıfa karşı doğrulandığı için bu uyarı oluşur.</span><span class="sxs-lookup"><span data-stu-id="3aa28-153">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="3aa28-154">Genellikle, bir parametre alan bir oluşturucu ya da izleme dinleyicisi uygulamaları için bu uyarıyı yoksayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3aa28-154">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="3aa28-155">Aşağıdaki tabloda .NET Framework'e dahil olan izleme dinleyicileri `initializeData` gösterilmektedir ve özniteliklerinin değerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="3aa28-155">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="3aa28-156">İzleme dinleyici sınıfı</span><span class="sxs-lookup"><span data-stu-id="3aa28-156">Trace listener class</span></span>|<span data-ttu-id="3aa28-157">initializeData öznitelik değeri</span><span class="sxs-lookup"><span data-stu-id="3aa28-157">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="3aa28-158">Oluşturucunun `useErrorStream` <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> değeri.</span><span class="sxs-lookup"><span data-stu-id="3aa28-158">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="3aa28-159">İzleme `initializeData` ve hata`true`ayıklama çıktısını standart hata akışına yazmak için " " özniteliğini ayarlayın; standart çıktı`false`akışına yazmak için " " olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="3aa28-159">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="3aa28-160"><xref:System.Diagnostics.DelimitedListTraceListener> Yazdığı dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="3aa28-160">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="3aa28-161">Varolan bir olay günlüğü kaynağının adı.</span><span class="sxs-lookup"><span data-stu-id="3aa28-161">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="3aa28-162"><xref:System.Diagnostics.EventSchemaTraceListener> Yazdığı dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="3aa28-162">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="3aa28-163"><xref:System.Diagnostics.TextWriterTraceListener> Yazdığı dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="3aa28-163">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="3aa28-164"><xref:System.Diagnostics.XmlWriterTraceListener> Yazdığı dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="3aa28-164">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="3aa28-165">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="3aa28-165">Configuration File</span></span>  
 <span data-ttu-id="3aa28-166">Bu öğe makine yapılandırma dosyasında (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3aa28-166">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3aa28-167">Örnek</span><span class="sxs-lookup"><span data-stu-id="3aa28-167">Example</span></span>  
 <span data-ttu-id="3aa28-168">Aşağıdaki örnek, dinleyicileri `<add>` `console` ve `textListener` izleme kaynağı `Listeners` `TraceSourceApp`için koleksiyona öğeleri nasıl kullanacağımı gösterir.</span><span class="sxs-lookup"><span data-stu-id="3aa28-168">The following example shows how to use `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="3aa28-169">`textListener` Dinleyici myListener.log dosyasına izleme çıktısı yazar.</span><span class="sxs-lookup"><span data-stu-id="3aa28-169">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3aa28-170">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3aa28-170">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="3aa28-171">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="3aa28-171">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="3aa28-172">İz Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="3aa28-172">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
