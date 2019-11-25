---
title: <trace> için <listeners> <add> öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
ms.openlocfilehash: eb3e9cf4a6d138998cfde865cda8ed4146be26d0
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088979"
---
# <a name="add-element-for-listeners-for-trace"></a><span data-ttu-id="a174f-102">\<Trace > \<dinleyicileri için > öğesi \<ekleyin ></span><span class="sxs-lookup"><span data-stu-id="a174f-102">\<add> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="a174f-103">**Dinleyiciler** koleksiyonuna bir dinleyici ekler.</span><span class="sxs-lookup"><span data-stu-id="a174f-103">Adds a listener to the **Listeners** collection.</span></span>  

<span data-ttu-id="a174f-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="a174f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a174f-105">[**System. diagnostics\<** ](system-diagnostics-element.md) &nbsp;&nbsp;</span><span class="sxs-lookup"><span data-stu-id="a174f-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="a174f-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<izleme >** ](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="a174f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>\
<span data-ttu-id="a174f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dinleyicileri >** ](listeners-element-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="a174f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)</span></span>\
<span data-ttu-id="a174f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<add >**</span><span class="sxs-lookup"><span data-stu-id="a174f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="a174f-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a174f-109">Syntax</span></span>  
  
```xml  
<add name="name"   
     type="trace listener class name, Version, Culture, PublicKeyToken"  
     initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a174f-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a174f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a174f-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a174f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a174f-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a174f-112">Attributes</span></span>  
  
|<span data-ttu-id="a174f-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a174f-113">Attribute</span></span>|<span data-ttu-id="a174f-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a174f-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a174f-115">**türüyle**</span><span class="sxs-lookup"><span data-stu-id="a174f-115">**type**</span></span>|<span data-ttu-id="a174f-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a174f-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="a174f-117">Dinleyicinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="a174f-117">Specifies the type of the listener.</span></span> <span data-ttu-id="a174f-118">[Tam nitelikli tür adlarını belirtirken](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)belirtilen gereksinimleri karşılayan bir dize kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a174f-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="a174f-119">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="a174f-119">**initializeData**</span></span>|<span data-ttu-id="a174f-120">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a174f-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a174f-121">Belirtilen sınıf için oluşturucuya geçirilen dize.</span><span class="sxs-lookup"><span data-stu-id="a174f-121">The string passed to the constructor for the specified class.</span></span>|  
|<span data-ttu-id="a174f-122">**ada**</span><span class="sxs-lookup"><span data-stu-id="a174f-122">**name**</span></span>|<span data-ttu-id="a174f-123">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a174f-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a174f-124">Dinleyicinin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a174f-124">Specifies the name of the listener.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a174f-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a174f-125">Child Elements</span></span>  
  
|<span data-ttu-id="a174f-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="a174f-126">Element</span></span>|<span data-ttu-id="a174f-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a174f-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a174f-128">Filtre > \<</span><span class="sxs-lookup"><span data-stu-id="a174f-128">\<filter></span></span>](filter-element-for-add-for-listeners-for-trace.md)|<span data-ttu-id="a174f-129">İzleme için `Listeners` koleksiyonundaki bir dinleyiciye bir filtre ekler.</span><span class="sxs-lookup"><span data-stu-id="a174f-129">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a174f-130">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a174f-130">Parent Elements</span></span>  
  
|<span data-ttu-id="a174f-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="a174f-131">Element</span></span>|<span data-ttu-id="a174f-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a174f-132">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a174f-133">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="a174f-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="a174f-134">İletileri toplayan, depolayan ve yönlendiren bir dinleyici belirtir.</span><span class="sxs-lookup"><span data-stu-id="a174f-134">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="a174f-135">Dinleyiciler izleme çıkışını uygun bir hedefe yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="a174f-135">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="a174f-136">ASP.NET yapılandırma bölümünün kök öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a174f-136">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="a174f-137">İzleme iletilerini toplayıp depolayan, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="a174f-137">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a174f-138">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a174f-138">Remarks</span></span>  
 <span data-ttu-id="a174f-139"><xref:System.Diagnostics.Debug> ve <xref:System.Diagnostics.Trace> sınıfları aynı **dinleyici** koleksiyonunu paylaşır.</span><span class="sxs-lookup"><span data-stu-id="a174f-139">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="a174f-140">Bu sınıflardan birindeki koleksiyona bir dinleyici nesnesi eklerseniz, diğer sınıf aynı dinleyiciyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="a174f-140">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="a174f-141">Dinleyici sınıfları <xref:System.Diagnostics.TraceListener>türetilir.</span><span class="sxs-lookup"><span data-stu-id="a174f-141">The listener classes derive from the <xref:System.Diagnostics.TraceListener>.</span></span>  
  
 <span data-ttu-id="a174f-142">İzleme dinleyicisinin `name` özniteliğini belirtmezseniz, İzleme dinleyicisinin <xref:System.Diagnostics.TraceListener.Name%2A> varsayılan olarak boş bir dize ("") olur.</span><span class="sxs-lookup"><span data-stu-id="a174f-142">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="a174f-143">Uygulamanızda yalnızca bir dinleyici varsa, bunu bir ad belirtmeden ekleyebilir ve ad için boş bir dize belirterek kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a174f-143">If your application has only one listener, you can add it without specifying a name, and remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="a174f-144">Ancak, uygulamanız birden fazla dinleyici içeriyorsa, her bir izleme dinleyicisi için benzersiz adlar belirtmelisiniz ve bu, <xref:System.Diagnostics.Debug.Listeners%2A> ve <xref:System.Diagnostics.Trace.Listeners%2A> koleksiyonlarında bireysel izleme dinleyicilerini tanımlamanızı ve yönetmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a174f-144">However, if your application has more than one listener, you should specify unique names for each trace listener, which allows you to identify and manage individual trace listeners within the <xref:System.Diagnostics.Debug.Listeners%2A> and <xref:System.Diagnostics.Trace.Listeners%2A> collections.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a174f-145">Aynı türde ve aynı ada sahip birden fazla izleme dinleyicisi eklemek, bu tür ve adın yalnızca bir izleme dinleyicisine `Listeners` koleksiyonuna eklendiğine neden olur.</span><span class="sxs-lookup"><span data-stu-id="a174f-145">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="a174f-146">Ancak, `Listeners` koleksiyonuna program aracılığıyla birden çok özdeş dinleyici ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a174f-146">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="a174f-147">**Initializedata** özniteliğinin değeri, oluşturduğunuz dinleyicinin türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a174f-147">The value for the **initializeData** attribute depends on the type of listener you create.</span></span> <span data-ttu-id="a174f-148">Tüm izleme dinleyicileri **ınitializedata**belirtmenizi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="a174f-148">Not all trace listeners require that you specify **initializeData**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a174f-149">`initializeData` özniteliğini kullandığınızda, "ınitializedata ' özniteliği bildirilmemiş" derleyici uyarısını alabilirsiniz. "</span><span class="sxs-lookup"><span data-stu-id="a174f-149">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="a174f-150">Yapılandırma ayarları, `initializeData` özniteliğini tanımayan <xref:System.Diagnostics.TraceListener>soyut taban sınıfına göre doğrulandığından bu uyarı oluşur.</span><span class="sxs-lookup"><span data-stu-id="a174f-150">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="a174f-151">Genellikle, bir parametresi alan Oluşturucusu olan izleme dinleyicisi uygulamaları için bu uyarıyı yoksayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a174f-151">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="a174f-152">Aşağıdaki tabloda, .NET Framework eklenen izleme dinleyicileri gösterilmektedir ve **ınitializedata** özniteliklerinin değeri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a174f-152">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their **initializeData** attributes.</span></span>  
  
|<span data-ttu-id="a174f-153">Trace dinleyicisi sınıfı</span><span class="sxs-lookup"><span data-stu-id="a174f-153">Trace listener class</span></span>|<span data-ttu-id="a174f-154">ınitializedata öznitelik değeri</span><span class="sxs-lookup"><span data-stu-id="a174f-154">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="a174f-155"><xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> oluşturucusunun `useErrorStream` değeri.</span><span class="sxs-lookup"><span data-stu-id="a174f-155">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="a174f-156"><xref:System.Console.Out%2A?displayProperty=nameWithType>yazmak için `initializeData` özniteliğini "`true`" olarak ayarlayın ve <xref:System.Console.Error%2A?displayProperty=nameWithType>, "`false`" çıktısını ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="a174f-156">Set the `initializeData` attribute to "`true`" to write trace and debug output to <xref:System.Console.Error%2A?displayProperty=nameWithType>; "`false`" to write to <xref:System.Console.Out%2A?displayProperty=nameWithType>.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="a174f-157"><xref:System.Diagnostics.DelimitedListTraceListener> yazdığı dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="a174f-157">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="a174f-158">Mevcut bir olay günlüğü kaynağı adının adı.</span><span class="sxs-lookup"><span data-stu-id="a174f-158">The name of the name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="a174f-159"><xref:System.Diagnostics.EventSchemaTraceListener> yazdığı dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="a174f-159">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="a174f-160"><xref:System.Diagnostics.TextWriterTraceListener> yazdığı dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="a174f-160">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="a174f-161"><xref:System.Diagnostics.XmlWriterTraceListener> yazdığı dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="a174f-161">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a174f-162">Örnek</span><span class="sxs-lookup"><span data-stu-id="a174f-162">Example</span></span>  
 <span data-ttu-id="a174f-163">Aşağıdaki örnek **, dinleyicileri `MyListener`** ve `MyEventListener` dinleyici koleksiyonuna eklemek için **\<ekleme >** öğelerinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a174f-163">The following example shows how to use **\<add>** elements to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="a174f-164">`MyListener`, `MyListener.log` adlı bir dosya oluşturur ve çıktıyı dosyaya yazar.</span><span class="sxs-lookup"><span data-stu-id="a174f-164">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="a174f-165">`MyEventListener` olay günlüğünde bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a174f-165">`MyEventListener` creates an entry in the event log.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
            <add name="MyEventListener"  
                 type="System.Diagnostics.EventLogTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"                 initializeData="MyConfigEventLog"/>  
            <add name="configConsoleListener"  
                 type="System.Diagnostics.ConsoleTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a174f-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a174f-166">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- [<span data-ttu-id="a174f-167">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="a174f-167">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a174f-168">İzleme Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="a174f-168">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
