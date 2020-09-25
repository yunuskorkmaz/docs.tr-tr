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
ms.openlocfilehash: f0ede5f9dc19e9589afc888e7fcd01785bc1840c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91174036"
---
# <a name="add-element-for-sharedlisteners"></a><span data-ttu-id="0c500-102">\<sharedListeners> için \<add> Öğesi</span><span class="sxs-lookup"><span data-stu-id="0c500-102">\<add> Element for \<sharedListeners></span></span>

<span data-ttu-id="0c500-103">Koleksiyona bir dinleyici ekler `sharedListeners` .</span><span class="sxs-lookup"><span data-stu-id="0c500-103">Adds a listener to the `sharedListeners` collection.</span></span> <span data-ttu-id="0c500-104">`sharedListeners` , herhangi bir veya başvuruda bulunan bir dinleyici koleksiyonudur [\<source>](source-element.md) [\<trace>](trace-element.md) .</span><span class="sxs-lookup"><span data-stu-id="0c500-104">`sharedListeners` is a collection of listeners that any [\<source>](source-element.md) or [\<trace>](trace-element.md) can reference.</span></span>  <span data-ttu-id="0c500-105">Varsayılan olarak, `sharedListeners` koleksiyondaki dinleyiciler bir koleksiyona yerleştirilmez `Listeners` .</span><span class="sxs-lookup"><span data-stu-id="0c500-105">By default, listeners in the `sharedListeners` collection are not placed in a `Listeners` collection.</span></span> <span data-ttu-id="0c500-106">Ya da adına göre eklenmelidir [\<source>](source-element.md) [\<trace>](trace-element.md) .</span><span class="sxs-lookup"><span data-stu-id="0c500-106">They must be added by name to the [\<source>](source-element.md) or [\<trace>](trace-element.md).</span></span> <span data-ttu-id="0c500-107">`sharedListeners`Çalışma zamanında koddaki koleksiyondaki dinleyicileri almak mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="0c500-107">It is not possible to get the listeners in the `sharedListeners` collection in code at run time.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="0c500-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="0c500-108">Syntax</span></span>  
  
```xml  
<add name="name"
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"
  traceOutputOptions = "None"
/>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c500-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0c500-109">Attributes and Elements</span></span>  

 <span data-ttu-id="0c500-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0c500-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c500-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0c500-111">Attributes</span></span>  
  
|<span data-ttu-id="0c500-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0c500-112">Attribute</span></span>|<span data-ttu-id="0c500-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0c500-113">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="0c500-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0c500-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="0c500-115">Paylaşılan dinleyiciyi bir koleksiyona eklemek için kullanılan dinleyicinin adını belirtir `Listeners` .</span><span class="sxs-lookup"><span data-stu-id="0c500-115">Specifies the name of the listener that is used to add the shared listener to a `Listeners` collection.</span></span>|  
|`type`|<span data-ttu-id="0c500-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0c500-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="0c500-117">Dinleyicinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="0c500-117">Specifies the type of the listener.</span></span> <span data-ttu-id="0c500-118">[Tam nitelikli tür adlarını belirtirken](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)belirtilen gereksinimleri karşılayan bir dize kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0c500-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="0c500-119">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0c500-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="0c500-120">Belirtilen sınıf için oluşturucuya geçirilen dize.</span><span class="sxs-lookup"><span data-stu-id="0c500-120">The string passed to the constructor for the specified class.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="0c500-121">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0c500-121">Optional attribute.</span></span><br/><br/><span data-ttu-id="0c500-122"><xref:System.Diagnostics.TraceOptions>İzleme çıktısına yazılacak verileri gösteren bir veya daha fazla numaralandırma üyesinin dize temsili.</span><span class="sxs-lookup"><span data-stu-id="0c500-122">The string representation of one or more <xref:System.Diagnostics.TraceOptions> enumeration members that indicates the data to be written to the trace output.</span></span> <span data-ttu-id="0c500-123">Birden çok öğe virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="0c500-123">Multiple items are separated by commas.</span></span> <span data-ttu-id="0c500-124">Varsayılan değer "none" dır.</span><span class="sxs-lookup"><span data-stu-id="0c500-124">The default value is "None".</span></span>|

### <a name="child-elements"></a><span data-ttu-id="0c500-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0c500-125">Child Elements</span></span>  
  
|<span data-ttu-id="0c500-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="0c500-126">Element</span></span>|<span data-ttu-id="0c500-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0c500-127">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-sharedlisteners.md)|<span data-ttu-id="0c500-128">Koleksiyondaki bir dinleyiciye bir filtre ekler `sharedListeners` .</span><span class="sxs-lookup"><span data-stu-id="0c500-128">Adds a filter to a listener in the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0c500-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0c500-129">Parent Elements</span></span>  
  
|<span data-ttu-id="0c500-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="0c500-130">Element</span></span>|<span data-ttu-id="0c500-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0c500-131">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0c500-132">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="0c500-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="0c500-133">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0c500-133">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="0c500-134">Herhangi bir kaynak veya izleme öğesinin başvurmasına yönelik bir dinleyici koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="0c500-134">A collection of listeners that any source or trace element can reference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c500-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0c500-135">Remarks</span></span>  

 <span data-ttu-id="0c500-136">.NET Framework ile birlikte gelen dinleyici sınıfları <xref:System.Diagnostics.TraceListener> sınıfından türetilir.</span><span class="sxs-lookup"><span data-stu-id="0c500-136">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="0c500-137">Özniteliğin değeri, `name` `Listeners` bir izleme ya da izleme kaynağı için bir koleksiyona paylaşılan dinleyiciyi eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0c500-137">The value for the `name` attribute is used to add the shared listener to a `Listeners` collection for either a trace or a trace source.</span></span> <span data-ttu-id="0c500-138">Özniteliğin değeri, `initializeData` oluşturduğunuz dinleyicinin türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0c500-138">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="0c500-139">Tüm izleme dinleyicileri belirtmeniz gerekmez `initializeData` .</span><span class="sxs-lookup"><span data-stu-id="0c500-139">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0c500-140">`initializeData`Özniteliğini kullandığınızda, "ınitializedata" özniteliği bildirilmemiş "derleyici uyarısını alabilirsiniz."</span><span class="sxs-lookup"><span data-stu-id="0c500-140">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="0c500-141">Bu uyarı, yapılandırma ayarları özniteliği tanımayan Özet taban sınıfına göre doğrulandığından oluşur <xref:System.Diagnostics.TraceListener> `initializeData` .</span><span class="sxs-lookup"><span data-stu-id="0c500-141">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="0c500-142">Genellikle, bir parametresi alan Oluşturucusu olan izleme dinleyicisi uygulamaları için bu uyarıyı yoksayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0c500-142">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="0c500-143">Aşağıdaki tabloda, .NET Framework eklenen izleme dinleyicileri gösterilmektedir ve özniteliklerinin değerleri açıklanmaktadır `initializeData` .</span><span class="sxs-lookup"><span data-stu-id="0c500-143">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="0c500-144">Trace dinleyicisi sınıfı</span><span class="sxs-lookup"><span data-stu-id="0c500-144">Trace listener class</span></span>|<span data-ttu-id="0c500-145">ınitializedata öznitelik değeri</span><span class="sxs-lookup"><span data-stu-id="0c500-145">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|<span data-ttu-id="0c500-146">`useErrorStream` <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> Oluşturucunun değeri.</span><span class="sxs-lookup"><span data-stu-id="0c500-146">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="0c500-147">`initializeData`"" Özniteliğini, `true` izleme ve hata ayıklama çıkışını standart hata akışına yazmak için "" olarak ayarlayın; `false` Standart çıkış akışına yazmak için "" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0c500-147">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|<span data-ttu-id="0c500-148">Yazdığı dosyanın adı <xref:System.Diagnostics.DelimitedListTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="0c500-148">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="0c500-149">Var olan bir olay günlüğü kaynağının adı.</span><span class="sxs-lookup"><span data-stu-id="0c500-149">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="0c500-150">Yazdığı dosyanın adı <xref:System.Diagnostics.EventSchemaTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="0c500-150">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="0c500-151">Yazdığı dosyanın adı <xref:System.Diagnostics.TextWriterTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="0c500-151">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|<span data-ttu-id="0c500-152">Yazdığı dosyanın adı <xref:System.Diagnostics.XmlWriterTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="0c500-152">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="0c500-153">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="0c500-153">Configuration File</span></span>  

 <span data-ttu-id="0c500-154">Bu öğe makine yapılandırma dosyasında (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0c500-154">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c500-155">Örnek</span><span class="sxs-lookup"><span data-stu-id="0c500-155">Example</span></span>  

 <span data-ttu-id="0c500-156">Aşağıdaki örnek `<add>` , öğesini koleksiyona eklemek için öğesinin nasıl kullanılacağını gösterir <xref:System.Diagnostics.TextWriterTraceListener> `textListener` `sharedListeners` .</span><span class="sxs-lookup"><span data-stu-id="0c500-156">The following example shows how to use `<add>` elements to add the <xref:System.Diagnostics.TextWriterTraceListener>`textListener` to the `sharedListeners` collection.</span></span>   <span data-ttu-id="0c500-157">`textListener` , `Listeners` izleme kaynağı için koleksiyona adına eklenir `TraceSourceApp` .</span><span class="sxs-lookup"><span data-stu-id="0c500-157">`textListener` is added by name to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="0c500-158">`textListener`Dinleyici, izleme çıkışını myListener. log dosyasına yazar.</span><span class="sxs-lookup"><span data-stu-id="0c500-158">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0c500-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c500-159">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="0c500-160">İzleme ve hata ayıklama ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="0c500-160">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="0c500-161">İz Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="0c500-161">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
