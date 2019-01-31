---
title: <add> için <sharedListeners> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <sharedListeners>
- add element for <sharedListeners>
ms.assetid: 1595e1bc-2492-421f-8384-7f382eb8eb57
ms.openlocfilehash: cbce115c6a485c5642a60528614480324e3e5665
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55274054"
---
# <a name="add-element-for-sharedlisteners"></a><span data-ttu-id="6b8b4-102">\<Ekle > öğesi için \<sharedListeners ></span><span class="sxs-lookup"><span data-stu-id="6b8b4-102">\<add> Element for \<sharedListeners></span></span>
<span data-ttu-id="6b8b4-103">Bir ekler `sharedListeners` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="6b8b4-103">Adds a listener to the `sharedListeners` collection.</span></span> <span data-ttu-id="6b8b4-104">`sharedListeners` dinleyicileri herhangi bir koleksiyonudur [ \<kaynak >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) veya [ \<İzleme >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md) başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6b8b4-104">`sharedListeners` is a collection of listeners that any [\<source>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) or [\<trace>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md) can reference.</span></span>  <span data-ttu-id="6b8b4-105">Varsayılan olarak, dinleyicileri `sharedListeners` koleksiyon yerleştirildiğinde değil bir `Listeners` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="6b8b4-105">By default, listeners in the `sharedListeners` collection are not placed in a `Listeners` collection.</span></span> <span data-ttu-id="6b8b4-106">Ada göre eklenmelidir [ \<kaynak >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) veya [ \<İzleme >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md).</span><span class="sxs-lookup"><span data-stu-id="6b8b4-106">They must be added by name to the [\<source>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) or [\<trace>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md).</span></span> <span data-ttu-id="6b8b4-107">Dinleyiciler almak mümkün değildir `sharedListeners` çalışma zamanında kod koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="6b8b4-107">It is not possible to get the listeners in the `sharedListeners` collection in code at run time.</span></span>  
  
 <span data-ttu-id="6b8b4-108">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="6b8b4-108">\<configuration></span></span>  
<span data-ttu-id="6b8b4-109">&nbsp;&nbsp;\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="6b8b4-109">&nbsp;&nbsp;\<system.diagnostics></span></span>  
<span data-ttu-id="6b8b4-110">&nbsp;&nbsp;&nbsp;&nbsp;\<sharedListeners > öğesi</span><span class="sxs-lookup"><span data-stu-id="6b8b4-110">&nbsp;&nbsp;&nbsp;&nbsp;\<sharedListeners> Element</span></span>  
<span data-ttu-id="6b8b4-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<add></span><span class="sxs-lookup"><span data-stu-id="6b8b4-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b8b4-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6b8b4-112">Syntax</span></span>  
  
```xml  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"
  traceOutputOptions = "None"
/>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6b8b4-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6b8b4-113">Attributes and Elements</span></span>  
 <span data-ttu-id="6b8b4-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6b8b4-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6b8b4-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6b8b4-115">Attributes</span></span>  
  
|<span data-ttu-id="6b8b4-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6b8b4-116">Attribute</span></span>|<span data-ttu-id="6b8b4-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6b8b4-117">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="6b8b4-118">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6b8b4-118">Required attribute.</span></span><br /><br /> <span data-ttu-id="6b8b4-119">Paylaşılan dinleyici için eklemek için kullanılan dinleyicisinin adını belirten bir `Listeners` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="6b8b4-119">Specifies the name of the listener that is used to add the shared listener to a `Listeners` collection.</span></span>|  
|`type`|<span data-ttu-id="6b8b4-120">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6b8b4-120">Required attribute.</span></span><br /><br /> <span data-ttu-id="6b8b4-121">Dinleyici türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="6b8b4-121">Specifies the type of the listener.</span></span> <span data-ttu-id="6b8b4-122">Belirtilen gereksinimleri karşılayan bir dize kullanmalısınız [belirtme tam olarak nitelenmiş tür adlarını](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="6b8b4-122">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="6b8b4-123">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6b8b4-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="6b8b4-124">Belirtilen sınıf için oluşturucuya geçirilen dizesi.</span><span class="sxs-lookup"><span data-stu-id="6b8b4-124">The string passed to the constructor for the specified class.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="6b8b4-125">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6b8b4-125">Optional attribute.</span></span><br/><br/><span data-ttu-id="6b8b4-126">Bir veya daha fazla dize gösterimi <xref:System.Diagnostics.TraceOptions> izleme çıktısına yazılmasına verileri gösteren numaralandırma üyeleri.</span><span class="sxs-lookup"><span data-stu-id="6b8b4-126">The string representation of one or more <xref:System.Diagnostics.TraceOptions> enumeration members that indicates the data to be written to the trace output.</span></span> <span data-ttu-id="6b8b4-127">Birden çok öğe virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="6b8b4-127">Multiple items are separated by commas.</span></span> <span data-ttu-id="6b8b4-128">Varsayılan değer "None" dir.</span><span class="sxs-lookup"><span data-stu-id="6b8b4-128">The default value is "None".</span></span>|

### <a name="child-elements"></a><span data-ttu-id="6b8b4-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6b8b4-129">Child Elements</span></span>  
  
|<span data-ttu-id="6b8b4-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="6b8b4-130">Element</span></span>|<span data-ttu-id="6b8b4-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6b8b4-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6b8b4-132">\<Filtre ></span><span class="sxs-lookup"><span data-stu-id="6b8b4-132">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-sharedlisteners.md)|<span data-ttu-id="6b8b4-133">Bir dinleyicisi için bir filtre ekler `sharedListeners` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="6b8b4-133">Adds a filter to a listener in the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6b8b4-134">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6b8b4-134">Parent Elements</span></span>  
  
|<span data-ttu-id="6b8b4-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="6b8b4-135">Element</span></span>|<span data-ttu-id="6b8b4-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6b8b4-136">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6b8b4-137">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="6b8b4-137">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="6b8b4-138">Toplamak, depolamak ve iletileri ve bir izleme anahtarı ayarlandığı düzeyi izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6b8b4-138">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="6b8b4-139">Herhangi bir kaynak veya trace ögesi başvurabilirsiniz dinleyicileri koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="6b8b4-139">A collection of listeners that any source or trace element can reference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b8b4-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6b8b4-140">Remarks</span></span>  
 <span data-ttu-id="6b8b4-141">.NET Framework ile birlikte gelen dinleyici sınıfların türetilmesi <xref:System.Diagnostics.TraceListener> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6b8b4-141">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="6b8b4-142">Değeri `name` özniteliği için paylaşılan dinleyici eklemek için kullanılan bir `Listeners` koleksiyonu için bir izleme ya da bir izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="6b8b4-142">The value for the `name` attribute is used to add the shared listener to a `Listeners` collection for either a trace or a trace source.</span></span> <span data-ttu-id="6b8b4-143">Değeri `initializeData` özniteliği oluşturduğunuz dinleyici türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="6b8b4-143">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="6b8b4-144">Tüm izleme dinleyicilerine belirtmenizi gerektiren `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="6b8b4-144">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6b8b4-145">Kullanırken `initializeData` özniteliği, "'initializeData' özniteliği. bildirilmedi" uyarı derleyici alabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="6b8b4-145">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="6b8b4-146">Bu uyarı oluşur yapılandırma ayarlarını soyut temel sınıf doğrulanır <xref:System.Diagnostics.TraceListener>, hangi tanımıyor `initializeData` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="6b8b4-146">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="6b8b4-147">Genellikle, bir parametre alan bir oluşturucu sahip İzleme dinleyicisi uygulamaları için bu uyarıyı yoksayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6b8b4-147">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="6b8b4-148">Aşağıdaki tablo .NET Framework ile birlikte izleme dinleyicilerine gösterir ve değerinin açıklanmıştır kendi `initializeData` öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="6b8b4-148">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="6b8b4-149">İzleme dinleyicisi sınıfı</span><span class="sxs-lookup"><span data-stu-id="6b8b4-149">Trace listener class</span></span>|<span data-ttu-id="6b8b4-150">initializeData özniteliği değeri</span><span class="sxs-lookup"><span data-stu-id="6b8b4-150">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|<span data-ttu-id="6b8b4-151">`useErrorStream` Değerini <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="6b8b4-151">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="6b8b4-152">Ayarlama `initializeData` özniteliğini "`true`"yazmak için izleme ve hata ayıklama için standart hata akışı; çıktı ayarlayın"`false`" standart çıkış akışına yazmak için.</span><span class="sxs-lookup"><span data-stu-id="6b8b4-152">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|<span data-ttu-id="6b8b4-153">Dosya adı <xref:System.Diagnostics.DelimitedListTraceListener> yazar.</span><span class="sxs-lookup"><span data-stu-id="6b8b4-153">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="6b8b4-154">Mevcut bir olay günlüğü kaynağı adı.</span><span class="sxs-lookup"><span data-stu-id="6b8b4-154">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="6b8b4-155">Dosyanın adı, <xref:System.Diagnostics.EventSchemaTraceListener> yazar.</span><span class="sxs-lookup"><span data-stu-id="6b8b4-155">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="6b8b4-156">Dosyanın adı, <xref:System.Diagnostics.TextWriterTraceListener> yazar.</span><span class="sxs-lookup"><span data-stu-id="6b8b4-156">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|<span data-ttu-id="6b8b4-157">Dosyanın adı, <xref:System.Diagnostics.XmlWriterTraceListener> yazar.</span><span class="sxs-lookup"><span data-stu-id="6b8b4-157">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="6b8b4-158">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="6b8b4-158">Configuration File</span></span>  
 <span data-ttu-id="6b8b4-159">Bu öğe, makine yapılandırma dosyası (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6b8b4-159">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b8b4-160">Örnek</span><span class="sxs-lookup"><span data-stu-id="6b8b4-160">Example</span></span>  
 <span data-ttu-id="6b8b4-161">Aşağıdaki örnek nasıl kullanılacağını gösterir `<add>` eklemek için öğeleri <xref:System.Diagnostics.TextWriterTraceListener> `textListener` için `sharedListeners` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="6b8b4-161">The following example shows how to use `<add>` elements to add the <xref:System.Diagnostics.TextWriterTraceListener>`textListener` to the `sharedListeners` collection.</span></span>   <span data-ttu-id="6b8b4-162">`textListener` adına tarafından eklenen `Listeners` iz kaynağı için koleksiyon `TraceSourceApp`.</span><span class="sxs-lookup"><span data-stu-id="6b8b4-162">`textListener` is added by name to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="6b8b4-163">`textListener` Dinleyici için dosya myListener.log izleme çıktısına yazar.</span><span class="sxs-lookup"><span data-stu-id="6b8b4-163">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6b8b4-164">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b8b4-164">See also</span></span>
- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="6b8b4-165">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="6b8b4-165">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [<span data-ttu-id="6b8b4-166">İzleme Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="6b8b4-166">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
