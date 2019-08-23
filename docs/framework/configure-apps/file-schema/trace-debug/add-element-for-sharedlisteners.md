---
title: <sharedListeners> için <add> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <sharedListeners>
- add element for <sharedListeners>
ms.assetid: 1595e1bc-2492-421f-8384-7f382eb8eb57
ms.openlocfilehash: c4b83834fb7aaf64a696b85bd2c8da47cfba2397
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927204"
---
# <a name="add-element-for-sharedlisteners"></a><span data-ttu-id="954df-102">\<sharedListeners için \<> öğesi ekleyin ></span><span class="sxs-lookup"><span data-stu-id="954df-102">\<add> Element for \<sharedListeners></span></span>
<span data-ttu-id="954df-103">`sharedListeners` Koleksiyona bir dinleyici ekler.</span><span class="sxs-lookup"><span data-stu-id="954df-103">Adds a listener to the `sharedListeners` collection.</span></span> <span data-ttu-id="954df-104">`sharedListeners`, herhangi [ \<bir kaynak >](source-element.md) veya [ \<izleme >](trace-element.md) başvurmasına yönelik bir dinleyici koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="954df-104">`sharedListeners` is a collection of listeners that any [\<source>](source-element.md) or [\<trace>](trace-element.md) can reference.</span></span>  <span data-ttu-id="954df-105">Varsayılan olarak, `sharedListeners` koleksiyondaki dinleyiciler bir `Listeners` koleksiyona yerleştirilmez.</span><span class="sxs-lookup"><span data-stu-id="954df-105">By default, listeners in the `sharedListeners` collection are not placed in a `Listeners` collection.</span></span> <span data-ttu-id="954df-106">Bunlar, [ \<kaynak >](source-element.md) veya [ \<izleme >](trace-element.md)adına göre eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="954df-106">They must be added by name to the [\<source>](source-element.md) or [\<trace>](trace-element.md).</span></span> <span data-ttu-id="954df-107">Çalışma zamanında koddaki `sharedListeners` koleksiyondaki dinleyicileri almak mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="954df-107">It is not possible to get the listeners in the `sharedListeners` collection in code at run time.</span></span>  
  
 <span data-ttu-id="954df-108">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="954df-108">\<configuration></span></span>  
<span data-ttu-id="954df-109">&nbsp;&nbsp;\<System. Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="954df-109">&nbsp;&nbsp;\<system.diagnostics></span></span>  
<span data-ttu-id="954df-110">&nbsp;&nbsp;&nbsp;&nbsp;\<sharedListeners > öğesi</span><span class="sxs-lookup"><span data-stu-id="954df-110">&nbsp;&nbsp;&nbsp;&nbsp;\<sharedListeners> Element</span></span>  
<span data-ttu-id="954df-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="954df-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="954df-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="954df-112">Syntax</span></span>  
  
```xml  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"
  traceOutputOptions = "None"
/>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="954df-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="954df-113">Attributes and Elements</span></span>  
 <span data-ttu-id="954df-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="954df-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="954df-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="954df-115">Attributes</span></span>  
  
|<span data-ttu-id="954df-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="954df-116">Attribute</span></span>|<span data-ttu-id="954df-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="954df-117">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="954df-118">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="954df-118">Required attribute.</span></span><br /><br /> <span data-ttu-id="954df-119">Paylaşılan dinleyiciyi bir `Listeners` koleksiyona eklemek için kullanılan dinleyicinin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="954df-119">Specifies the name of the listener that is used to add the shared listener to a `Listeners` collection.</span></span>|  
|`type`|<span data-ttu-id="954df-120">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="954df-120">Required attribute.</span></span><br /><br /> <span data-ttu-id="954df-121">Dinleyicinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="954df-121">Specifies the type of the listener.</span></span> <span data-ttu-id="954df-122">[Tam nitelikli tür adlarını belirtirken](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)belirtilen gereksinimleri karşılayan bir dize kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="954df-122">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="954df-123">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="954df-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="954df-124">Belirtilen sınıf için oluşturucuya geçirilen dize.</span><span class="sxs-lookup"><span data-stu-id="954df-124">The string passed to the constructor for the specified class.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="954df-125">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="954df-125">Optional attribute.</span></span><br/><br/><span data-ttu-id="954df-126">İzleme çıktısına yazılacak verileri gösteren bir veya <xref:System.Diagnostics.TraceOptions> daha fazla numaralandırma üyesinin dize temsili.</span><span class="sxs-lookup"><span data-stu-id="954df-126">The string representation of one or more <xref:System.Diagnostics.TraceOptions> enumeration members that indicates the data to be written to the trace output.</span></span> <span data-ttu-id="954df-127">Birden çok öğe virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="954df-127">Multiple items are separated by commas.</span></span> <span data-ttu-id="954df-128">Varsayılan değer "none" dır.</span><span class="sxs-lookup"><span data-stu-id="954df-128">The default value is "None".</span></span>|

### <a name="child-elements"></a><span data-ttu-id="954df-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="954df-129">Child Elements</span></span>  
  
|<span data-ttu-id="954df-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="954df-130">Element</span></span>|<span data-ttu-id="954df-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="954df-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="954df-132">\<Filtre ></span><span class="sxs-lookup"><span data-stu-id="954df-132">\<filter></span></span>](filter-element-for-add-for-sharedlisteners.md)|<span data-ttu-id="954df-133">`sharedListeners` Koleksiyondaki bir dinleyiciye bir filtre ekler.</span><span class="sxs-lookup"><span data-stu-id="954df-133">Adds a filter to a listener in the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="954df-134">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="954df-134">Parent Elements</span></span>  
  
|<span data-ttu-id="954df-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="954df-135">Element</span></span>|<span data-ttu-id="954df-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="954df-136">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="954df-137">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="954df-137">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="954df-138">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="954df-138">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="954df-139">Herhangi bir kaynak veya izleme öğesinin başvurmasına yönelik bir dinleyici koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="954df-139">A collection of listeners that any source or trace element can reference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="954df-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="954df-140">Remarks</span></span>  
 <span data-ttu-id="954df-141">.NET Framework ile birlikte gelen dinleyici sınıfları <xref:System.Diagnostics.TraceListener> sınıfından türetilir.</span><span class="sxs-lookup"><span data-stu-id="954df-141">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="954df-142">`name` Özniteliğin değeri, bir izleme ya da izleme kaynağı için bir `Listeners` koleksiyona paylaşılan dinleyiciyi eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="954df-142">The value for the `name` attribute is used to add the shared listener to a `Listeners` collection for either a trace or a trace source.</span></span> <span data-ttu-id="954df-143">`initializeData` Özniteliğin değeri, oluşturduğunuz dinleyicinin türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="954df-143">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="954df-144">Tüm izleme dinleyicileri belirtmeniz `initializeData`gerekmez.</span><span class="sxs-lookup"><span data-stu-id="954df-144">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="954df-145">`initializeData` Özniteliğini kullandığınızda, "ınitializedata" özniteliği bildirilmemiş "derleyici uyarısını alabilirsiniz."</span><span class="sxs-lookup"><span data-stu-id="954df-145">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="954df-146">Bu uyarı, yapılandırma ayarları <xref:System.Diagnostics.TraceListener> `initializeData` özniteliği tanımayan Özet taban sınıfına göre doğrulandığından oluşur.</span><span class="sxs-lookup"><span data-stu-id="954df-146">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="954df-147">Genellikle, bir parametresi alan Oluşturucusu olan izleme dinleyicisi uygulamaları için bu uyarıyı yoksayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="954df-147">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="954df-148">Aşağıdaki tabloda, .NET Framework eklenen izleme dinleyicileri gösterilmektedir ve `initializeData` özniteliklerinin değerleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="954df-148">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="954df-149">Trace dinleyicisi sınıfı</span><span class="sxs-lookup"><span data-stu-id="954df-149">Trace listener class</span></span>|<span data-ttu-id="954df-150">ınitializedata öznitelik değeri</span><span class="sxs-lookup"><span data-stu-id="954df-150">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|<span data-ttu-id="954df-151"><xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> Oluşturucunun `useErrorStream` değeri.</span><span class="sxs-lookup"><span data-stu-id="954df-151">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="954df-152">" `initializeData` `false`" Özniteliğini, izleme ve hata ayıklama çıkışını standart hata akışına yazmak için "" olarak ayarlayın; standart çıkış akışına yazmak için "" olarak ayarlayın.`true`</span><span class="sxs-lookup"><span data-stu-id="954df-152">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|<span data-ttu-id="954df-153"><xref:System.Diagnostics.DelimitedListTraceListener> Yazdığı dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="954df-153">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="954df-154">Var olan bir olay günlüğü kaynağının adı.</span><span class="sxs-lookup"><span data-stu-id="954df-154">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="954df-155"><xref:System.Diagnostics.EventSchemaTraceListener> Yazdığı dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="954df-155">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="954df-156"><xref:System.Diagnostics.TextWriterTraceListener> Yazdığı dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="954df-156">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|<span data-ttu-id="954df-157"><xref:System.Diagnostics.XmlWriterTraceListener> Yazdığı dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="954df-157">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="954df-158">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="954df-158">Configuration File</span></span>  
 <span data-ttu-id="954df-159">Bu öğe makine yapılandırma dosyasında (Machine. config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="954df-159">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="954df-160">Örnek</span><span class="sxs-lookup"><span data-stu-id="954df-160">Example</span></span>  
 <span data-ttu-id="954df-161">Aşağıdaki `<add>` örnek, <xref:System.Diagnostics.TextWriterTraceListener> `textListener` öğesini koleksiyona eklemek için öğesinin nasıl kullanılacağını gösterir. `sharedListeners`</span><span class="sxs-lookup"><span data-stu-id="954df-161">The following example shows how to use `<add>` elements to add the <xref:System.Diagnostics.TextWriterTraceListener>`textListener` to the `sharedListeners` collection.</span></span>   <span data-ttu-id="954df-162">`textListener`, izleme kaynağı `Listeners` `TraceSourceApp`için koleksiyona adına eklenir.</span><span class="sxs-lookup"><span data-stu-id="954df-162">`textListener` is added by name to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="954df-163">Dinleyici `textListener` , izleme çıkışını MyListener. log dosyasına yazar.</span><span class="sxs-lookup"><span data-stu-id="954df-163">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="954df-164">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="954df-164">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="954df-165">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="954df-165">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="954df-166">İzleme Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="954df-166">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
