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
ms.openlocfilehash: 0c7665898f8c625c2d07b67ea6c7fe25113fddd8
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699485"
---
# <a name="add-element-for-sharedlisteners"></a><span data-ttu-id="40847-102">\< \<sharedListeners için > öğesi ekleyin ></span><span class="sxs-lookup"><span data-stu-id="40847-102">\<add> Element for \<sharedListeners></span></span>
<span data-ttu-id="40847-103">@No__t-0 koleksiyonuna bir dinleyici ekler.</span><span class="sxs-lookup"><span data-stu-id="40847-103">Adds a listener to the `sharedListeners` collection.</span></span> <span data-ttu-id="40847-104">`sharedListeners`, herhangi bir [\<source >](source-element.md) veya [@no__t 4trace >](trace-element.md) başvurmasına yönelik bir dinleyici koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="40847-104">`sharedListeners` is a collection of listeners that any [\<source>](source-element.md) or [\<trace>](trace-element.md) can reference.</span></span>  <span data-ttu-id="40847-105">Varsayılan olarak, `sharedListeners` koleksiyonundaki dinleyiciler bir `Listeners` koleksiyonuna yerleştirilmez.</span><span class="sxs-lookup"><span data-stu-id="40847-105">By default, listeners in the `sharedListeners` collection are not placed in a `Listeners` collection.</span></span> <span data-ttu-id="40847-106">[@No__t-1source >](source-element.md) veya [\<trace >](trace-element.md)adına göre eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="40847-106">They must be added by name to the [\<source>](source-element.md) or [\<trace>](trace-element.md).</span></span> <span data-ttu-id="40847-107">Çalışma zamanında koddaki `sharedListeners` koleksiyonundaki dinleyicileri almak mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="40847-107">It is not possible to get the listeners in the `sharedListeners` collection in code at run time.</span></span>  
  
[<span data-ttu-id="40847-108"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="40847-108">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="40847-109">&nbsp; @ no__t-1[ **\<system. Diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="40847-109">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="40847-110">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<sharedListeners >** ](sharedlisteners-element.md)</span><span class="sxs-lookup"><span data-stu-id="40847-110">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)</span></span>  
<span data-ttu-id="40847-111">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<add >**</span><span class="sxs-lookup"><span data-stu-id="40847-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40847-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="40847-112">Syntax</span></span>  
  
```xml  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"
  traceOutputOptions = "None"
/>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="40847-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="40847-113">Attributes and Elements</span></span>  
 <span data-ttu-id="40847-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="40847-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="40847-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="40847-115">Attributes</span></span>  
  
|<span data-ttu-id="40847-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="40847-116">Attribute</span></span>|<span data-ttu-id="40847-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40847-117">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="40847-118">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="40847-118">Required attribute.</span></span><br /><br /> <span data-ttu-id="40847-119">@No__t-0 koleksiyonuna paylaşılan dinleyiciyi eklemek için kullanılan dinleyicinin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="40847-119">Specifies the name of the listener that is used to add the shared listener to a `Listeners` collection.</span></span>|  
|`type`|<span data-ttu-id="40847-120">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="40847-120">Required attribute.</span></span><br /><br /> <span data-ttu-id="40847-121">Dinleyicinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="40847-121">Specifies the type of the listener.</span></span> <span data-ttu-id="40847-122">[Tam nitelikli tür adlarını belirtirken](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)belirtilen gereksinimleri karşılayan bir dize kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="40847-122">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="40847-123">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="40847-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="40847-124">Belirtilen sınıf için oluşturucuya geçirilen dize.</span><span class="sxs-lookup"><span data-stu-id="40847-124">The string passed to the constructor for the specified class.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="40847-125">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="40847-125">Optional attribute.</span></span><br/><br/><span data-ttu-id="40847-126">İzleme çıktısına yazılacak verileri gösteren bir veya daha fazla <xref:System.Diagnostics.TraceOptions> numaralandırma üyesinin dize temsili.</span><span class="sxs-lookup"><span data-stu-id="40847-126">The string representation of one or more <xref:System.Diagnostics.TraceOptions> enumeration members that indicates the data to be written to the trace output.</span></span> <span data-ttu-id="40847-127">Birden çok öğe virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="40847-127">Multiple items are separated by commas.</span></span> <span data-ttu-id="40847-128">Varsayılan değer "none" dır.</span><span class="sxs-lookup"><span data-stu-id="40847-128">The default value is "None".</span></span>|

### <a name="child-elements"></a><span data-ttu-id="40847-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="40847-129">Child Elements</span></span>  
  
|<span data-ttu-id="40847-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="40847-130">Element</span></span>|<span data-ttu-id="40847-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40847-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="40847-132">\<filtre ></span><span class="sxs-lookup"><span data-stu-id="40847-132">\<filter></span></span>](filter-element-for-add-for-sharedlisteners.md)|<span data-ttu-id="40847-133">@No__t-0 koleksiyonundaki bir dinleyiciye bir filtre ekler.</span><span class="sxs-lookup"><span data-stu-id="40847-133">Adds a filter to a listener in the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="40847-134">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="40847-134">Parent Elements</span></span>  
  
|<span data-ttu-id="40847-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="40847-135">Element</span></span>|<span data-ttu-id="40847-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40847-136">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="40847-137">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="40847-137">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="40847-138">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="40847-138">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="40847-139">Herhangi bir kaynak veya izleme öğesinin başvurmasına yönelik bir dinleyici koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="40847-139">A collection of listeners that any source or trace element can reference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40847-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="40847-140">Remarks</span></span>  
 <span data-ttu-id="40847-141">.NET Framework ile birlikte gelen dinleyici sınıfları <xref:System.Diagnostics.TraceListener> sınıfından türetilir.</span><span class="sxs-lookup"><span data-stu-id="40847-141">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="40847-142">@No__t-0 özniteliğinin değeri, bir izleme ya da izleme kaynağı için bir `Listeners` koleksiyonuna paylaşılan dinleyiciyi eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="40847-142">The value for the `name` attribute is used to add the shared listener to a `Listeners` collection for either a trace or a trace source.</span></span> <span data-ttu-id="40847-143">@No__t-0 özniteliğinin değeri, oluşturduğunuz dinleyicinin türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="40847-143">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="40847-144">Tüm izleme dinleyicileri `initializeData` belirtmenizi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="40847-144">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="40847-145">@No__t-0 özniteliğini kullandığınızda, "ınitializedata ' özniteliği bildirilmemiş" derleyici uyarısını alabilirsiniz. "</span><span class="sxs-lookup"><span data-stu-id="40847-145">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="40847-146">Yapılandırma ayarları, `initializeData` özniteliğini tanımayan <xref:System.Diagnostics.TraceListener> soyut taban sınıfına göre doğrulandığından bu uyarı oluşur.</span><span class="sxs-lookup"><span data-stu-id="40847-146">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="40847-147">Genellikle, bir parametresi alan Oluşturucusu olan izleme dinleyicisi uygulamaları için bu uyarıyı yoksayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="40847-147">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="40847-148">Aşağıdaki tabloda, .NET Framework eklenen izleme dinleyicileri gösterilmektedir ve `initializeData` özniteliklerinin değeri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="40847-148">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="40847-149">Trace dinleyicisi sınıfı</span><span class="sxs-lookup"><span data-stu-id="40847-149">Trace listener class</span></span>|<span data-ttu-id="40847-150">ınitializedata öznitelik değeri</span><span class="sxs-lookup"><span data-stu-id="40847-150">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|<span data-ttu-id="40847-151">@No__t-1 oluşturucusunun `useErrorStream` değeri.</span><span class="sxs-lookup"><span data-stu-id="40847-151">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="40847-152">Standart hata akışına Trace ve Debug çıkışını yazmak için `initializeData` özniteliğini "`true`" olarak ayarlayın. Standart çıkış akışına yazmak için bunu "`false`" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="40847-152">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|<span data-ttu-id="40847-153">@No__t-0 ' ın yazdığı dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="40847-153">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="40847-154">Var olan bir olay günlüğü kaynağının adı.</span><span class="sxs-lookup"><span data-stu-id="40847-154">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="40847-155">@No__t 0 ' ın yazdığı dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="40847-155">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="40847-156">@No__t 0 ' ın yazdığı dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="40847-156">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|<span data-ttu-id="40847-157">@No__t 0 ' ın yazdığı dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="40847-157">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="40847-158">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="40847-158">Configuration File</span></span>  
 <span data-ttu-id="40847-159">Bu öğe makine yapılandırma dosyasında (Machine. config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="40847-159">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40847-160">Örnek</span><span class="sxs-lookup"><span data-stu-id="40847-160">Example</span></span>  
 <span data-ttu-id="40847-161">Aşağıdaki örnek, <xref:System.Diagnostics.TextWriterTraceListener> @ no__t-2 ' i `sharedListeners` koleksiyonuna eklemek için `<add>` öğelerinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="40847-161">The following example shows how to use `<add>` elements to add the <xref:System.Diagnostics.TextWriterTraceListener>`textListener` to the `sharedListeners` collection.</span></span>   <span data-ttu-id="40847-162">`textListener`, `TraceSourceApp` izleme kaynağı için `Listeners` koleksiyonuna eklenir.</span><span class="sxs-lookup"><span data-stu-id="40847-162">`textListener` is added by name to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="40847-163">@No__t-0 dinleyicisi, izleme çıkışını myListener. log dosyasına yazar.</span><span class="sxs-lookup"><span data-stu-id="40847-163">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="40847-164">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40847-164">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="40847-165">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="40847-165">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="40847-166">İzleme Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="40847-166">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
