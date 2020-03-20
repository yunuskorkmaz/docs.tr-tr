---
title: <sharedListeners> için <add> öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <sharedListeners>
- add element for <sharedListeners>
ms.assetid: 1595e1bc-2492-421f-8384-7f382eb8eb57
ms.openlocfilehash: 5588892ec75a791eda1eb043936c0af95e79354e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153613"
---
# <a name="add-element-for-sharedlisteners"></a><span data-ttu-id="40650-102">\<paylaşılan Dinleyiciler \<için> Öğesi></span><span class="sxs-lookup"><span data-stu-id="40650-102">\<add> Element for \<sharedListeners></span></span>
<span data-ttu-id="40650-103">`sharedListeners` Koleksiyona bir dinleyici ekler.</span><span class="sxs-lookup"><span data-stu-id="40650-103">Adds a listener to the `sharedListeners` collection.</span></span> <span data-ttu-id="40650-104">`sharedListeners`herhangi [ \<](source-element.md) bir kaynağın>veya [ \<izleme>](trace-element.md) başvurulabileceği bir dinleyici topluluğudur.</span><span class="sxs-lookup"><span data-stu-id="40650-104">`sharedListeners` is a collection of listeners that any [\<source>](source-element.md) or [\<trace>](trace-element.md) can reference.</span></span>  <span data-ttu-id="40650-105">Varsayılan olarak, `sharedListeners` koleksiyondaki dinleyiciler koleksiyona `Listeners` yerleştirilmez.</span><span class="sxs-lookup"><span data-stu-id="40650-105">By default, listeners in the `sharedListeners` collection are not placed in a `Listeners` collection.</span></span> <span data-ttu-id="40650-106">Kaynak [ \<>](source-element.md) veya [ \<izleme>](trace-element.md)adile eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="40650-106">They must be added by name to the [\<source>](source-element.md) or [\<trace>](trace-element.md).</span></span> <span data-ttu-id="40650-107">Dinleyicileri çalışma zamanında kod halinde `sharedListeners` toplama almak mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="40650-107">It is not possible to get the listeners in the `sharedListeners` collection in code at run time.</span></span>  

<span data-ttu-id="40650-108">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="40650-108">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="40650-109">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="40650-109">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="40650-110">&nbsp;&nbsp;&nbsp;&nbsp;[**\<paylaşılanDinleyiciler>**](sharedlisteners-element.md)</span><span class="sxs-lookup"><span data-stu-id="40650-110">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)</span></span>\
<span data-ttu-id="40650-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>ekleyin**</span><span class="sxs-lookup"><span data-stu-id="40650-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="40650-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="40650-112">Syntax</span></span>  
  
```xml  
<add name="name"
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"
  traceOutputOptions = "None"
/>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="40650-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="40650-113">Attributes and Elements</span></span>  
 <span data-ttu-id="40650-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="40650-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="40650-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="40650-115">Attributes</span></span>  
  
|<span data-ttu-id="40650-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="40650-116">Attribute</span></span>|<span data-ttu-id="40650-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40650-117">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="40650-118">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="40650-118">Required attribute.</span></span><br /><br /> <span data-ttu-id="40650-119">Paylaşılan dinleyiciyi koleksiyona `Listeners` eklemek için kullanılan dinleyicinin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="40650-119">Specifies the name of the listener that is used to add the shared listener to a `Listeners` collection.</span></span>|  
|`type`|<span data-ttu-id="40650-120">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="40650-120">Required attribute.</span></span><br /><br /> <span data-ttu-id="40650-121">Dinleyicinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="40650-121">Specifies the type of the listener.</span></span> <span data-ttu-id="40650-122">[Tam Nitelikli Tür Adları Belirtme'de](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)belirtilen gereksinimleri karşılayan bir dize kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="40650-122">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="40650-123">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="40650-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="40650-124">Dize, belirtilen sınıfın oluşturucuya geçti.</span><span class="sxs-lookup"><span data-stu-id="40650-124">The string passed to the constructor for the specified class.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="40650-125">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="40650-125">Optional attribute.</span></span><br/><br/><span data-ttu-id="40650-126">İzleme çıktısına yazılacak <xref:System.Diagnostics.TraceOptions> verileri gösteren bir veya daha fazla numaralandırma üyesinin dize gösterimi.</span><span class="sxs-lookup"><span data-stu-id="40650-126">The string representation of one or more <xref:System.Diagnostics.TraceOptions> enumeration members that indicates the data to be written to the trace output.</span></span> <span data-ttu-id="40650-127">Birden çok öğe virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="40650-127">Multiple items are separated by commas.</span></span> <span data-ttu-id="40650-128">Varsayılan değer "Yok"dur.</span><span class="sxs-lookup"><span data-stu-id="40650-128">The default value is "None".</span></span>|

### <a name="child-elements"></a><span data-ttu-id="40650-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="40650-129">Child Elements</span></span>  
  
|<span data-ttu-id="40650-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="40650-130">Element</span></span>|<span data-ttu-id="40650-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40650-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="40650-132">\<filtre></span><span class="sxs-lookup"><span data-stu-id="40650-132">\<filter></span></span>](filter-element-for-add-for-sharedlisteners.md)|<span data-ttu-id="40650-133">`sharedListeners` Koleksiyondaki bir dinleyiciye filtre ekler.</span><span class="sxs-lookup"><span data-stu-id="40650-133">Adds a filter to a listener in the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="40650-134">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="40650-134">Parent Elements</span></span>  
  
|<span data-ttu-id="40650-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="40650-135">Element</span></span>|<span data-ttu-id="40650-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40650-136">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="40650-137">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="40650-137">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="40650-138">İletileri toplayan, depolayan ve yönlendiren izleme dinleyicilerini ve izleme anahtarının ayarlandığı düzeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="40650-138">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="40650-139">Herhangi bir kaynak veya izleme öğesinin başvuruda bulunabileceği dinleyici koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="40650-139">A collection of listeners that any source or trace element can reference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40650-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="40650-140">Remarks</span></span>  
 <span data-ttu-id="40650-141">.NET Framework ile gönderilen dinleyici sınıfları <xref:System.Diagnostics.TraceListener> sınıftan türetilmiştir.</span><span class="sxs-lookup"><span data-stu-id="40650-141">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="40650-142">Öznitelik değeri, `name` paylaşılan dinleyiciyi bir izleme veya `Listeners` izleme kaynağı için bir koleksiyona eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="40650-142">The value for the `name` attribute is used to add the shared listener to a `Listeners` collection for either a trace or a trace source.</span></span> <span data-ttu-id="40650-143">Öznitelik değeri `initializeData` oluşturduğunuz dinleyici türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="40650-143">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="40650-144">Tüm izleme dinleyicileri belirtmenizi `initializeData`gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="40650-144">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="40650-145">Özniteliği kullandığınızda, `initializeData` derleyici uyarı alabilirsiniz "'InitializeData' özniteliği ilan edilmez."</span><span class="sxs-lookup"><span data-stu-id="40650-145">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="40650-146">Yapılandırma ayarları özniteliği tanımayan <xref:System.Diagnostics.TraceListener> `initializeData` soyut taban sınıfa karşı doğrulandığı için bu uyarı oluşur.</span><span class="sxs-lookup"><span data-stu-id="40650-146">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="40650-147">Genellikle, bir parametre alan bir oluşturucu ya da izleme dinleyicisi uygulamaları için bu uyarıyı yoksayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="40650-147">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="40650-148">Aşağıdaki tabloda .NET Framework'e dahil olan izleme dinleyicileri `initializeData` gösterilmektedir ve özniteliklerinin değerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="40650-148">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="40650-149">İzleme dinleyici sınıfı</span><span class="sxs-lookup"><span data-stu-id="40650-149">Trace listener class</span></span>|<span data-ttu-id="40650-150">initializeData öznitelik değeri</span><span class="sxs-lookup"><span data-stu-id="40650-150">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|<span data-ttu-id="40650-151">Oluşturucunun `useErrorStream` <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> değeri.</span><span class="sxs-lookup"><span data-stu-id="40650-151">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="40650-152">İzleme `initializeData` ve hata`true`ayıklama çıktısını standart hata akışına yazmak için " " özniteliğini ayarlayın; standart çıktı`false`akışına yazmak için " " olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="40650-152">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|<span data-ttu-id="40650-153"><xref:System.Diagnostics.DelimitedListTraceListener> Yazdığı dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="40650-153">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="40650-154">Varolan bir olay günlüğü kaynağının adı.</span><span class="sxs-lookup"><span data-stu-id="40650-154">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="40650-155"><xref:System.Diagnostics.EventSchemaTraceListener> Yazdığı dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="40650-155">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="40650-156"><xref:System.Diagnostics.TextWriterTraceListener> Yazdığı dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="40650-156">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|<span data-ttu-id="40650-157"><xref:System.Diagnostics.XmlWriterTraceListener> Yazdığı dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="40650-157">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="40650-158">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="40650-158">Configuration File</span></span>  
 <span data-ttu-id="40650-159">Bu öğe makine yapılandırma dosyasında (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="40650-159">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40650-160">Örnek</span><span class="sxs-lookup"><span data-stu-id="40650-160">Example</span></span>  
 <span data-ttu-id="40650-161">Aşağıdaki örnek, koleksiyona `<add>` eklemek için <xref:System.Diagnostics.TextWriterTraceListener> `textListener` öğelerin nasıl kullanılacağını `sharedListeners` gösterir.</span><span class="sxs-lookup"><span data-stu-id="40650-161">The following example shows how to use `<add>` elements to add the <xref:System.Diagnostics.TextWriterTraceListener>`textListener` to the `sharedListeners` collection.</span></span>   <span data-ttu-id="40650-162">`textListener`izleme kaynağı `TraceSourceApp`için `Listeners` koleksiyona ad ile eklenir.</span><span class="sxs-lookup"><span data-stu-id="40650-162">`textListener` is added by name to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="40650-163">`textListener` Dinleyici myListener.log dosyasına izleme çıktısı yazar.</span><span class="sxs-lookup"><span data-stu-id="40650-163">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="40650-164">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40650-164">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="40650-165">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="40650-165">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="40650-166">İz Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="40650-166">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
