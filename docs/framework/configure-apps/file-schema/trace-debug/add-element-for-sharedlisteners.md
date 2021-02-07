---
description: 'İçin: öğesi hakkında daha fazla bilgi <add><sharedListeners>'
title: <sharedListeners> için <add> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <sharedListeners>
- add element for <sharedListeners>
ms.assetid: 1595e1bc-2492-421f-8384-7f382eb8eb57
ms.openlocfilehash: df3348fa0cbb357b2ceeb5d9db940a1ae3ae102c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726084"
---
# <a name="add-element-for-sharedlisteners"></a><span data-ttu-id="c48f3-103">\<sharedListeners> için \<add> Öğesi</span><span class="sxs-lookup"><span data-stu-id="c48f3-103">\<add> Element for \<sharedListeners></span></span>

<span data-ttu-id="c48f3-104">Koleksiyona bir dinleyici ekler `sharedListeners` .</span><span class="sxs-lookup"><span data-stu-id="c48f3-104">Adds a listener to the `sharedListeners` collection.</span></span> <span data-ttu-id="c48f3-105">`sharedListeners` , herhangi bir veya başvuruda bulunan bir dinleyici koleksiyonudur [\<source>](source-element.md) [\<trace>](trace-element.md) .</span><span class="sxs-lookup"><span data-stu-id="c48f3-105">`sharedListeners` is a collection of listeners that any [\<source>](source-element.md) or [\<trace>](trace-element.md) can reference.</span></span>  <span data-ttu-id="c48f3-106">Varsayılan olarak, `sharedListeners` koleksiyondaki dinleyiciler bir koleksiyona yerleştirilmez `Listeners` .</span><span class="sxs-lookup"><span data-stu-id="c48f3-106">By default, listeners in the `sharedListeners` collection are not placed in a `Listeners` collection.</span></span> <span data-ttu-id="c48f3-107">Ya da adına göre eklenmelidir [\<source>](source-element.md) [\<trace>](trace-element.md) .</span><span class="sxs-lookup"><span data-stu-id="c48f3-107">They must be added by name to the [\<source>](source-element.md) or [\<trace>](trace-element.md).</span></span> <span data-ttu-id="c48f3-108">`sharedListeners`Çalışma zamanında koddaki koleksiyondaki dinleyicileri almak mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="c48f3-108">It is not possible to get the listeners in the `sharedListeners` collection in code at run time.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="c48f3-109">Syntax</span><span class="sxs-lookup"><span data-stu-id="c48f3-109">Syntax</span></span>  
  
```xml  
<add name="name"
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"
  traceOutputOptions = "None"
/>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c48f3-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c48f3-110">Attributes and Elements</span></span>  

 <span data-ttu-id="c48f3-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c48f3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c48f3-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c48f3-112">Attributes</span></span>  
  
|<span data-ttu-id="c48f3-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c48f3-113">Attribute</span></span>|<span data-ttu-id="c48f3-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c48f3-114">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="c48f3-115">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="c48f3-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="c48f3-116">Paylaşılan dinleyiciyi bir koleksiyona eklemek için kullanılan dinleyicinin adını belirtir `Listeners` .</span><span class="sxs-lookup"><span data-stu-id="c48f3-116">Specifies the name of the listener that is used to add the shared listener to a `Listeners` collection.</span></span>|  
|`type`|<span data-ttu-id="c48f3-117">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="c48f3-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="c48f3-118">Dinleyicinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="c48f3-118">Specifies the type of the listener.</span></span> <span data-ttu-id="c48f3-119">[Tam nitelikli tür adlarını belirtirken](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)belirtilen gereksinimleri karşılayan bir dize kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c48f3-119">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="c48f3-120">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="c48f3-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="c48f3-121">Belirtilen sınıf için oluşturucuya geçirilen dize.</span><span class="sxs-lookup"><span data-stu-id="c48f3-121">The string passed to the constructor for the specified class.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="c48f3-122">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="c48f3-122">Optional attribute.</span></span><br/><br/><span data-ttu-id="c48f3-123"><xref:System.Diagnostics.TraceOptions>İzleme çıktısına yazılacak verileri gösteren bir veya daha fazla numaralandırma üyesinin dize temsili.</span><span class="sxs-lookup"><span data-stu-id="c48f3-123">The string representation of one or more <xref:System.Diagnostics.TraceOptions> enumeration members that indicates the data to be written to the trace output.</span></span> <span data-ttu-id="c48f3-124">Birden çok öğe virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="c48f3-124">Multiple items are separated by commas.</span></span> <span data-ttu-id="c48f3-125">Varsayılan değer "none" dır.</span><span class="sxs-lookup"><span data-stu-id="c48f3-125">The default value is "None".</span></span>|

### <a name="child-elements"></a><span data-ttu-id="c48f3-126">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c48f3-126">Child Elements</span></span>  
  
|<span data-ttu-id="c48f3-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="c48f3-127">Element</span></span>|<span data-ttu-id="c48f3-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c48f3-128">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-sharedlisteners.md)|<span data-ttu-id="c48f3-129">Koleksiyondaki bir dinleyiciye bir filtre ekler `sharedListeners` .</span><span class="sxs-lookup"><span data-stu-id="c48f3-129">Adds a filter to a listener in the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c48f3-130">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c48f3-130">Parent Elements</span></span>  
  
|<span data-ttu-id="c48f3-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="c48f3-131">Element</span></span>|<span data-ttu-id="c48f3-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c48f3-132">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c48f3-133">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="c48f3-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="c48f3-134">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c48f3-134">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="c48f3-135">Herhangi bir kaynak veya izleme öğesinin başvurmasına yönelik bir dinleyici koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="c48f3-135">A collection of listeners that any source or trace element can reference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c48f3-136">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c48f3-136">Remarks</span></span>  

 <span data-ttu-id="c48f3-137">.NET Framework ile birlikte gelen dinleyici sınıfları <xref:System.Diagnostics.TraceListener> sınıfından türetilir.</span><span class="sxs-lookup"><span data-stu-id="c48f3-137">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="c48f3-138">Özniteliğin değeri, `name` `Listeners` bir izleme ya da izleme kaynağı için bir koleksiyona paylaşılan dinleyiciyi eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c48f3-138">The value for the `name` attribute is used to add the shared listener to a `Listeners` collection for either a trace or a trace source.</span></span> <span data-ttu-id="c48f3-139">Özniteliğin değeri, `initializeData` oluşturduğunuz dinleyicinin türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c48f3-139">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="c48f3-140">Tüm izleme dinleyicileri belirtmeniz gerekmez `initializeData` .</span><span class="sxs-lookup"><span data-stu-id="c48f3-140">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c48f3-141">`initializeData`Özniteliğini kullandığınızda, "ınitializedata" özniteliği bildirilmemiş "derleyici uyarısını alabilirsiniz."</span><span class="sxs-lookup"><span data-stu-id="c48f3-141">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="c48f3-142">Bu uyarı, yapılandırma ayarları özniteliği tanımayan Özet taban sınıfına göre doğrulandığından oluşur <xref:System.Diagnostics.TraceListener> `initializeData` .</span><span class="sxs-lookup"><span data-stu-id="c48f3-142">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="c48f3-143">Genellikle, bir parametresi alan Oluşturucusu olan izleme dinleyicisi uygulamaları için bu uyarıyı yoksayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c48f3-143">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="c48f3-144">Aşağıdaki tabloda, .NET Framework eklenen izleme dinleyicileri gösterilmektedir ve özniteliklerinin değerleri açıklanmaktadır `initializeData` .</span><span class="sxs-lookup"><span data-stu-id="c48f3-144">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="c48f3-145">Trace dinleyicisi sınıfı</span><span class="sxs-lookup"><span data-stu-id="c48f3-145">Trace listener class</span></span>|<span data-ttu-id="c48f3-146">ınitializedata öznitelik değeri</span><span class="sxs-lookup"><span data-stu-id="c48f3-146">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|<span data-ttu-id="c48f3-147">`useErrorStream` <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> Oluşturucunun değeri.</span><span class="sxs-lookup"><span data-stu-id="c48f3-147">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="c48f3-148">`initializeData`"" Özniteliğini, `true` izleme ve hata ayıklama çıkışını standart hata akışına yazmak için "" olarak ayarlayın; `false` Standart çıkış akışına yazmak için "" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c48f3-148">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|<span data-ttu-id="c48f3-149">Yazdığı dosyanın adı <xref:System.Diagnostics.DelimitedListTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="c48f3-149">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="c48f3-150">Var olan bir olay günlüğü kaynağının adı.</span><span class="sxs-lookup"><span data-stu-id="c48f3-150">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="c48f3-151">Yazdığı dosyanın adı <xref:System.Diagnostics.EventSchemaTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="c48f3-151">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="c48f3-152">Yazdığı dosyanın adı <xref:System.Diagnostics.TextWriterTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="c48f3-152">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|<span data-ttu-id="c48f3-153">Yazdığı dosyanın adı <xref:System.Diagnostics.XmlWriterTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="c48f3-153">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="c48f3-154">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="c48f3-154">Configuration File</span></span>  

 <span data-ttu-id="c48f3-155">Bu öğe makine yapılandırma dosyasında (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c48f3-155">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c48f3-156">Örnek</span><span class="sxs-lookup"><span data-stu-id="c48f3-156">Example</span></span>  

 <span data-ttu-id="c48f3-157">Aşağıdaki örnek `<add>` , öğesini koleksiyona eklemek için öğesinin nasıl kullanılacağını gösterir <xref:System.Diagnostics.TextWriterTraceListener> `textListener` `sharedListeners` .</span><span class="sxs-lookup"><span data-stu-id="c48f3-157">The following example shows how to use `<add>` elements to add the <xref:System.Diagnostics.TextWriterTraceListener>`textListener` to the `sharedListeners` collection.</span></span>   <span data-ttu-id="c48f3-158">`textListener` , `Listeners` izleme kaynağı için koleksiyona adına eklenir `TraceSourceApp` .</span><span class="sxs-lookup"><span data-stu-id="c48f3-158">`textListener` is added by name to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="c48f3-159">`textListener`Dinleyici, izleme çıkışını myListener. log dosyasına yazar.</span><span class="sxs-lookup"><span data-stu-id="c48f3-159">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c48f3-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c48f3-160">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="c48f3-161">İzleme ve hata ayıklama ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="c48f3-161">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c48f3-162">İz Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="c48f3-162">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
