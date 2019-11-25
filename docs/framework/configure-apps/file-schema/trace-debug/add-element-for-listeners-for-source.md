---
title: <source> için <listeners> <add> öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
ms.openlocfilehash: c32205310f9fc451a5a55a943f925ee52f65c8a8
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088995"
---
# <a name="add-element-for-listeners-for-source"></a><span data-ttu-id="2b707-102">\<kaynak için \<dinleyicileri > için > öğesi \<ekleyin ></span><span class="sxs-lookup"><span data-stu-id="2b707-102">\<add> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="2b707-103">İzleme kaynağı için `Listeners` koleksiyonuna bir dinleyici ekler.</span><span class="sxs-lookup"><span data-stu-id="2b707-103">Adds a listener to the `Listeners` collection for a trace source.</span></span>  

<span data-ttu-id="2b707-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="2b707-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2b707-105">[**System. diagnostics\<** ](system-diagnostics-element.md) &nbsp;&nbsp;</span><span class="sxs-lookup"><span data-stu-id="2b707-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="2b707-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<kaynakları >** ](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="2b707-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>\
<span data-ttu-id="2b707-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<kaynak >** ](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="2b707-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>\
<span data-ttu-id="2b707-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**dinleyicileri >** ](listeners-element-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="2b707-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)</span></span>\
<span data-ttu-id="2b707-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<ekleme >**</span><span class="sxs-lookup"><span data-stu-id="2b707-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="2b707-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2b707-110">Syntax</span></span>  
  
```xml  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2b707-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2b707-111">Attributes and Elements</span></span>  
 <span data-ttu-id="2b707-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2b707-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2b707-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2b707-113">Attributes</span></span>  
  
|<span data-ttu-id="2b707-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2b707-114">Attribute</span></span>|<span data-ttu-id="2b707-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2b707-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="2b707-116">`sharedListeners` koleksiyonundaki bir dinleyiciye başvurmadığınız müddetçe gerekli özniteliği, bu durumda yalnızca ada göre başvurmak zorunda değilsiniz ( [örneğe](#example)bakın).</span><span class="sxs-lookup"><span data-stu-id="2b707-116">Required attribute, unless you're referencing a listener in the `sharedListeners` collection, in which case you only need to refer to it by name (see the [Example](#example)).</span></span><br /><br /> <span data-ttu-id="2b707-117">Dinleyicinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="2b707-117">Specifies the type of the listener.</span></span> <span data-ttu-id="2b707-118">[Tam nitelikli tür adlarını belirtirken](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)belirtilen gereksinimleri karşılayan bir dize kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2b707-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="2b707-119">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="2b707-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="2b707-120">Belirtilen sınıf için oluşturucuya geçirilen dize.</span><span class="sxs-lookup"><span data-stu-id="2b707-120">The string passed to the constructor for the specified class.</span></span> <span data-ttu-id="2b707-121">Sınıfın bir dize alan Oluşturucusu yoksa bir <xref:System.Configuration.ConfigurationException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2b707-121">A <xref:System.Configuration.ConfigurationException> is thrown if the class does not have a constructor that takes a string.</span></span>|  
|`name`|<span data-ttu-id="2b707-122">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="2b707-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="2b707-123">Dinleyicinin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2b707-123">Specifies the name of the listener.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="2b707-124">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="2b707-124">Optional attribute.</span></span><br /><br /> <span data-ttu-id="2b707-125">İzleme dinleyicisi için <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> özellik değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2b707-125">Specifies the <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> property value for the trace listener.</span></span>|  
|<span data-ttu-id="2b707-126">[özel öznitelikler]</span><span class="sxs-lookup"><span data-stu-id="2b707-126">[custom attributes]</span></span>|<span data-ttu-id="2b707-127">İsteğe bağlı öznitelikler.</span><span class="sxs-lookup"><span data-stu-id="2b707-127">Optional attributes.</span></span><br /><br /> <span data-ttu-id="2b707-128">Bu dinleyicinin <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> yöntemi tarafından tanımlanan dinleyiciye özgü özniteliklerin değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2b707-128">Specifies the value for listener-specific attributes identified by the <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> method for that listener.</span></span> <span data-ttu-id="2b707-129"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A>, <xref:System.Diagnostics.DelimitedListTraceListener> sınıfına özgü olan fazladan bir özniteliğe örnektir.</span><span class="sxs-lookup"><span data-stu-id="2b707-129"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> is an example of an extra attribute unique to the <xref:System.Diagnostics.DelimitedListTraceListener> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2b707-130">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2b707-130">Child Elements</span></span>  
  
|<span data-ttu-id="2b707-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="2b707-131">Element</span></span>|<span data-ttu-id="2b707-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2b707-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2b707-133">Filtre > \<</span><span class="sxs-lookup"><span data-stu-id="2b707-133">\<filter></span></span>](filter-element-for-add-for-listeners-for-source.md)|<span data-ttu-id="2b707-134">İzleme kaynağı için `Listeners` koleksiyonundaki bir dinleyiciye bir filtre ekler.</span><span class="sxs-lookup"><span data-stu-id="2b707-134">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2b707-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2b707-135">Parent Elements</span></span>  
  
|<span data-ttu-id="2b707-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="2b707-136">Element</span></span>|<span data-ttu-id="2b707-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2b707-137">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2b707-138">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="2b707-138">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="2b707-139">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2b707-139">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="2b707-140">İzleme iletilerini Başlatan izleme kaynaklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="2b707-140">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="2b707-141">İzleme iletilerini Başlatan bir izleme kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2b707-141">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="2b707-142">İletileri toplayacak, depolayan ve yönlendiren dinleyicileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="2b707-142">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b707-143">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2b707-143">Remarks</span></span>  
 <span data-ttu-id="2b707-144">.NET Framework ile birlikte gelen dinleyici sınıfları <xref:System.Diagnostics.TraceListener> sınıfından türetilir.</span><span class="sxs-lookup"><span data-stu-id="2b707-144">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="2b707-145">İzleme dinleyicisinin `name` özniteliğini belirtmezseniz, İzleme dinleyicisinin <xref:System.Diagnostics.TraceListener.Name%2A> özelliği varsayılan olarak boş bir dize ("") olur.</span><span class="sxs-lookup"><span data-stu-id="2b707-145">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> property of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="2b707-146">Uygulamanızda yalnızca bir dinleyici varsa, bunu bir ad belirtmeden ekleyebilir ve ad için boş bir dize belirterek kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b707-146">If your application has only one listener, you can add it without specifying a name, and you can remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="2b707-147">Ancak, uygulamanız birden fazla dinleyici içeriyorsa, her izleme dinleyicisi için benzersiz bir ad belirtmeniz gerekir. Bu, <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> koleksiyonundaki bireysel izleme dinleyicilerini tanımlamanızı ve yönetmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="2b707-147">However, if your application has more than one listener, you should specify a unique name for each trace listener, which allows you to identify and manage individual trace listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2b707-148">Aynı türde ve aynı ada sahip birden fazla izleme dinleyicisi eklemek, bu tür ve adın yalnızca bir izleme dinleyicisine `Listeners` koleksiyonuna eklendiğine neden olur.</span><span class="sxs-lookup"><span data-stu-id="2b707-148">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="2b707-149">Ancak, `Listeners` koleksiyonuna program aracılığıyla birden çok özdeş dinleyici ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b707-149">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="2b707-150">`initializeData` özniteliğinin değeri, oluşturduğunuz dinleyicinin türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="2b707-150">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="2b707-151">Tüm izleme dinleyicileri `initializeData`belirtmenizi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="2b707-151">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2b707-152">`initializeData` özniteliğini kullandığınızda, "ınitializedata ' özniteliği bildirilmemiş" derleyici uyarısını alabilirsiniz. "</span><span class="sxs-lookup"><span data-stu-id="2b707-152">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="2b707-153">Yapılandırma ayarları, `initializeData` özniteliğini tanımayan <xref:System.Diagnostics.TraceListener>soyut taban sınıfına göre doğrulandığından bu uyarı oluşur.</span><span class="sxs-lookup"><span data-stu-id="2b707-153">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="2b707-154">Genellikle, bir parametresi alan Oluşturucusu olan izleme dinleyicisi uygulamaları için bu uyarıyı yoksayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b707-154">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="2b707-155">Aşağıdaki tabloda, .NET Framework dahil edilen izleme dinleyicileri gösterilmektedir ve `initializeData` özniteliklerinin değerleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2b707-155">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="2b707-156">Trace dinleyicisi sınıfı</span><span class="sxs-lookup"><span data-stu-id="2b707-156">Trace listener class</span></span>|<span data-ttu-id="2b707-157">ınitializedata öznitelik değeri</span><span class="sxs-lookup"><span data-stu-id="2b707-157">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="2b707-158"><xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> oluşturucusunun `useErrorStream` değeri.</span><span class="sxs-lookup"><span data-stu-id="2b707-158">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="2b707-159">Standart hata akışına Trace ve Debug çıkışını yazmak için `initializeData` özniteliğini "`true`" olarak ayarlayın. Standart çıkış akışına yazmak için bunu "`false`" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2b707-159">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="2b707-160"><xref:System.Diagnostics.DelimitedListTraceListener> yazdığı dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="2b707-160">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="2b707-161">Var olan bir olay günlüğü kaynağının adı.</span><span class="sxs-lookup"><span data-stu-id="2b707-161">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="2b707-162"><xref:System.Diagnostics.EventSchemaTraceListener> yazdığı dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="2b707-162">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="2b707-163"><xref:System.Diagnostics.TextWriterTraceListener> yazdığı dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="2b707-163">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="2b707-164"><xref:System.Diagnostics.XmlWriterTraceListener> yazdığı dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="2b707-164">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="2b707-165">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="2b707-165">Configuration File</span></span>  
 <span data-ttu-id="2b707-166">Bu öğe makine yapılandırma dosyasında (Machine. config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2b707-166">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b707-167">Örnek</span><span class="sxs-lookup"><span data-stu-id="2b707-167">Example</span></span>  
 <span data-ttu-id="2b707-168">Aşağıdaki örnek, `<add>` öğelerinin `console` ve `textListener` izleme kaynağı `TraceSourceApp`için `Listeners` koleksiyonuna nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="2b707-168">The following example shows how to use `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="2b707-169">`textListener` dinleyicisi izleme çıkışını myListener. log dosyasına yazar.</span><span class="sxs-lookup"><span data-stu-id="2b707-169">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2b707-170">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b707-170">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="2b707-171">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="2b707-171">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="2b707-172">İzleme Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="2b707-172">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
