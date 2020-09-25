---
title: <add>İçin için öğesi <listeners><source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
ms.openlocfilehash: a5abaffbad986785b8879297883da9614f0a8103
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201700"
---
# <a name="add-element-for-listeners-for-source"></a><span data-ttu-id="985c0-102">\<add>İçin için öğesi \<listeners>\<source></span><span class="sxs-lookup"><span data-stu-id="985c0-102">\<add> Element for \<listeners> for \<source></span></span>

<span data-ttu-id="985c0-103">`Listeners`İzleme kaynağı için koleksiyona bir dinleyici ekler.</span><span class="sxs-lookup"><span data-stu-id="985c0-103">Adds a listener to the `Listeners` collection for a trace source.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="985c0-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="985c0-104">Syntax</span></span>  
  
```xml  
<add name="name"
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="985c0-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="985c0-105">Attributes and Elements</span></span>  

 <span data-ttu-id="985c0-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="985c0-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="985c0-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="985c0-107">Attributes</span></span>  
  
|<span data-ttu-id="985c0-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="985c0-108">Attribute</span></span>|<span data-ttu-id="985c0-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="985c0-109">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="985c0-110">Koleksiyonda bir dinleyiciye başvurmadığınız müddetçe gerekli özniteliği, `sharedListeners` Bu durumda yalnızca ada göre buraya başvurmanız gerekir ( [örneğe](#example)bakın).</span><span class="sxs-lookup"><span data-stu-id="985c0-110">Required attribute, unless you're referencing a listener in the `sharedListeners` collection, in which case you only need to refer to it by name (see the [Example](#example)).</span></span><br /><br /> <span data-ttu-id="985c0-111">Dinleyicinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="985c0-111">Specifies the type of the listener.</span></span> <span data-ttu-id="985c0-112">[Tam nitelikli tür adlarını belirtirken](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)belirtilen gereksinimleri karşılayan bir dize kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="985c0-112">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="985c0-113">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="985c0-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="985c0-114">Belirtilen sınıf için oluşturucuya geçirilen dize.</span><span class="sxs-lookup"><span data-stu-id="985c0-114">The string passed to the constructor for the specified class.</span></span> <span data-ttu-id="985c0-115"><xref:System.Configuration.ConfigurationException>Sınıfın bir dize alan Oluşturucusu yoksa, oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="985c0-115">A <xref:System.Configuration.ConfigurationException> is thrown if the class does not have a constructor that takes a string.</span></span>|  
|`name`|<span data-ttu-id="985c0-116">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="985c0-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="985c0-117">Dinleyicinin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="985c0-117">Specifies the name of the listener.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="985c0-118">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="985c0-118">Optional attribute.</span></span><br /><br /> <span data-ttu-id="985c0-119"><xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A>İzleme dinleyicisi için özellik değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="985c0-119">Specifies the <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> property value for the trace listener.</span></span>|  
|<span data-ttu-id="985c0-120">[özel öznitelikler]</span><span class="sxs-lookup"><span data-stu-id="985c0-120">[custom attributes]</span></span>|<span data-ttu-id="985c0-121">İsteğe bağlı öznitelikler.</span><span class="sxs-lookup"><span data-stu-id="985c0-121">Optional attributes.</span></span><br /><br /> <span data-ttu-id="985c0-122">Bu dinleyicinin yöntemi tarafından tanımlanan dinleyiciye özgü özniteliklerin değerini belirtir <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> .</span><span class="sxs-lookup"><span data-stu-id="985c0-122">Specifies the value for listener-specific attributes identified by the <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> method for that listener.</span></span> <span data-ttu-id="985c0-123"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> , sınıfına özgü olan ek bir özniteliğe örnektir <xref:System.Diagnostics.DelimitedListTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="985c0-123"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> is an example of an extra attribute unique to the <xref:System.Diagnostics.DelimitedListTraceListener> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="985c0-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="985c0-124">Child Elements</span></span>  
  
|<span data-ttu-id="985c0-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="985c0-125">Element</span></span>|<span data-ttu-id="985c0-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="985c0-126">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-listeners-for-source.md)|<span data-ttu-id="985c0-127">İzleme kaynağı için koleksiyondaki bir dinleyiciye bir filtre ekler `Listeners` .</span><span class="sxs-lookup"><span data-stu-id="985c0-127">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="985c0-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="985c0-128">Parent Elements</span></span>  
  
|<span data-ttu-id="985c0-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="985c0-129">Element</span></span>|<span data-ttu-id="985c0-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="985c0-130">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="985c0-131">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="985c0-131">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="985c0-132">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="985c0-132">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="985c0-133">İzleme iletilerini Başlatan izleme kaynaklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="985c0-133">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="985c0-134">İzleme iletilerini Başlatan bir izleme kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="985c0-134">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="985c0-135">İletileri toplayacak, depolayan ve yönlendiren dinleyicileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="985c0-135">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="985c0-136">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="985c0-136">Remarks</span></span>  

 <span data-ttu-id="985c0-137">.NET Framework ile birlikte gelen dinleyici sınıfları <xref:System.Diagnostics.TraceListener> sınıfından türetilir.</span><span class="sxs-lookup"><span data-stu-id="985c0-137">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="985c0-138">`name`İzleme dinleyicisinin özniteliğini belirtmezseniz, <xref:System.Diagnostics.TraceListener.Name%2A> İzleme dinleyicisinin özelliği varsayılan olarak boş bir dize ("") olur.</span><span class="sxs-lookup"><span data-stu-id="985c0-138">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> property of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="985c0-139">Uygulamanızda yalnızca bir dinleyici varsa, bunu bir ad belirtmeden ekleyebilir ve ad için boş bir dize belirterek kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="985c0-139">If your application has only one listener, you can add it without specifying a name, and you can remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="985c0-140">Ancak, uygulamanız birden fazla dinleyici içeriyorsa, her bir izleme dinleyicisi için, koleksiyonda bireysel izleme dinleyicilerini tanımlamanızı ve yönetmenizi sağlayan benzersiz bir ad belirtmeniz gerekir <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="985c0-140">However, if your application has more than one listener, you should specify a unique name for each trace listener, which allows you to identify and manage individual trace listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="985c0-141">Aynı türde ve aynı ada sahip birden fazla izleme dinleyicisi eklemek, bu tür ve koleksiyona eklenmekte olan adın yalnızca bir izleme dinleyicisine neden olur `Listeners` .</span><span class="sxs-lookup"><span data-stu-id="985c0-141">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="985c0-142">Ancak, koleksiyona daha fazla özdeş dinleyici ekleyebilirsiniz `Listeners` .</span><span class="sxs-lookup"><span data-stu-id="985c0-142">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="985c0-143">Özniteliğin değeri, `initializeData` oluşturduğunuz dinleyicinin türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="985c0-143">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="985c0-144">Tüm izleme dinleyicileri belirtmeniz gerekmez `initializeData` .</span><span class="sxs-lookup"><span data-stu-id="985c0-144">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="985c0-145">`initializeData`Özniteliğini kullandığınızda, "ınitializedata" özniteliği bildirilmemiş "derleyici uyarısını alabilirsiniz."</span><span class="sxs-lookup"><span data-stu-id="985c0-145">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="985c0-146">Bu uyarı, yapılandırma ayarları özniteliği tanımayan Özet taban sınıfına göre doğrulandığından oluşur <xref:System.Diagnostics.TraceListener> `initializeData` .</span><span class="sxs-lookup"><span data-stu-id="985c0-146">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="985c0-147">Genellikle, bir parametresi alan Oluşturucusu olan izleme dinleyicisi uygulamaları için bu uyarıyı yoksayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="985c0-147">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="985c0-148">Aşağıdaki tabloda, .NET Framework eklenen izleme dinleyicileri gösterilmektedir ve özniteliklerinin değerleri açıklanmaktadır `initializeData` .</span><span class="sxs-lookup"><span data-stu-id="985c0-148">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="985c0-149">Trace dinleyicisi sınıfı</span><span class="sxs-lookup"><span data-stu-id="985c0-149">Trace listener class</span></span>|<span data-ttu-id="985c0-150">ınitializedata öznitelik değeri</span><span class="sxs-lookup"><span data-stu-id="985c0-150">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="985c0-151">`useErrorStream` <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> Oluşturucunun değeri.</span><span class="sxs-lookup"><span data-stu-id="985c0-151">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="985c0-152">`initializeData`"" Özniteliğini, `true` izleme ve hata ayıklama çıkışını standart hata akışına yazmak için "" olarak ayarlayın; `false` Standart çıkış akışına yazmak için "" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="985c0-152">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="985c0-153">Yazdığı dosyanın adı <xref:System.Diagnostics.DelimitedListTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="985c0-153">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="985c0-154">Var olan bir olay günlüğü kaynağının adı.</span><span class="sxs-lookup"><span data-stu-id="985c0-154">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="985c0-155">Yazdığı dosyanın adı <xref:System.Diagnostics.EventSchemaTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="985c0-155">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="985c0-156">Yazdığı dosyanın adı <xref:System.Diagnostics.TextWriterTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="985c0-156">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="985c0-157">Yazdığı dosyanın adı <xref:System.Diagnostics.XmlWriterTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="985c0-157">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="985c0-158">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="985c0-158">Configuration File</span></span>  

 <span data-ttu-id="985c0-159">Bu öğe makine yapılandırma dosyasında (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="985c0-159">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="985c0-160">Örnek</span><span class="sxs-lookup"><span data-stu-id="985c0-160">Example</span></span>  

 <span data-ttu-id="985c0-161">Aşağıdaki örnek, `<add>` `console` `textListener` `Listeners` izleme kaynağı için dinleyicileri ve koleksiyona eklemek üzere öğelerin nasıl kullanılacağını gösterir `TraceSourceApp` .</span><span class="sxs-lookup"><span data-stu-id="985c0-161">The following example shows how to use `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="985c0-162">`textListener`Dinleyici, izleme çıkışını myListener. log dosyasına yazar.</span><span class="sxs-lookup"><span data-stu-id="985c0-162">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="985c0-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="985c0-163">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="985c0-164">İzleme ve hata ayıklama ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="985c0-164">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="985c0-165">İz Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="985c0-165">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
