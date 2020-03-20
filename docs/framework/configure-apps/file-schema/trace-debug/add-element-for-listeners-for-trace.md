---
title: <add><listeners> Için element<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
ms.openlocfilehash: c64673908dc9afe67d97c08f93e5b9d9533bd34d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153678"
---
# <a name="add-element-for-listeners-for-trace"></a><span data-ttu-id="6e2ac-102">\<izleme> \<için> \<dinleyiciler için> Öğesi ekleyin</span><span class="sxs-lookup"><span data-stu-id="6e2ac-102">\<add> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="6e2ac-103">**Dinleyici** koleksiyonuna bir dinleyici ekler.</span><span class="sxs-lookup"><span data-stu-id="6e2ac-103">Adds a listener to the **Listeners** collection.</span></span>  

<span data-ttu-id="6e2ac-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6e2ac-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6e2ac-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="6e2ac-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="6e2ac-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<izleme>**](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="6e2ac-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>\
<span data-ttu-id="6e2ac-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dinleyici ler>**](listeners-element-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="6e2ac-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)</span></span>\
<span data-ttu-id="6e2ac-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>ekleyin**</span><span class="sxs-lookup"><span data-stu-id="6e2ac-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="6e2ac-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e2ac-109">Syntax</span></span>  
  
```xml  
<add name="name"
     type="trace listener class name, Version, Culture, PublicKeyToken"  
     initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6e2ac-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6e2ac-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6e2ac-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6e2ac-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6e2ac-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6e2ac-112">Attributes</span></span>  
  
|<span data-ttu-id="6e2ac-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6e2ac-113">Attribute</span></span>|<span data-ttu-id="6e2ac-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e2ac-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6e2ac-115">**Türü**</span><span class="sxs-lookup"><span data-stu-id="6e2ac-115">**type**</span></span>|<span data-ttu-id="6e2ac-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6e2ac-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="6e2ac-117">Dinleyicinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="6e2ac-117">Specifies the type of the listener.</span></span> <span data-ttu-id="6e2ac-118">[Tam Nitelikli Tür Adları Belirtme'de](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)belirtilen gereksinimleri karşılayan bir dize kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6e2ac-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="6e2ac-119">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="6e2ac-119">**initializeData**</span></span>|<span data-ttu-id="6e2ac-120">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6e2ac-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="6e2ac-121">Dize, belirtilen sınıfın oluşturucuya geçti.</span><span class="sxs-lookup"><span data-stu-id="6e2ac-121">The string passed to the constructor for the specified class.</span></span>|  
|<span data-ttu-id="6e2ac-122">**Adı**</span><span class="sxs-lookup"><span data-stu-id="6e2ac-122">**name**</span></span>|<span data-ttu-id="6e2ac-123">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6e2ac-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="6e2ac-124">Dinleyicinin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6e2ac-124">Specifies the name of the listener.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6e2ac-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6e2ac-125">Child Elements</span></span>  
  
|<span data-ttu-id="6e2ac-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="6e2ac-126">Element</span></span>|<span data-ttu-id="6e2ac-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e2ac-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6e2ac-128">\<filtre></span><span class="sxs-lookup"><span data-stu-id="6e2ac-128">\<filter></span></span>](filter-element-for-add-for-listeners-for-trace.md)|<span data-ttu-id="6e2ac-129">`Listeners` İzleme için koleksiyondaki bir dinleyiciye filtre ekler.</span><span class="sxs-lookup"><span data-stu-id="6e2ac-129">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6e2ac-130">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6e2ac-130">Parent Elements</span></span>  
  
|<span data-ttu-id="6e2ac-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="6e2ac-131">Element</span></span>|<span data-ttu-id="6e2ac-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e2ac-132">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6e2ac-133">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="6e2ac-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="6e2ac-134">İletileri toplayan, depolayan ve gönderen bir dinleyici belirtir.</span><span class="sxs-lookup"><span data-stu-id="6e2ac-134">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="6e2ac-135">Dinleyiciler izleme çıktısını uygun bir hedefe yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="6e2ac-135">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="6e2ac-136">ASP.NET yapılandırma bölümünün kök öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6e2ac-136">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="6e2ac-137">İletileri toplayan, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="6e2ac-137">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e2ac-138">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e2ac-138">Remarks</span></span>  
 <span data-ttu-id="6e2ac-139">Ve <xref:System.Diagnostics.Debug> <xref:System.Diagnostics.Trace> sınıflar aynı **Dinleyici** koleksiyonunu paylaşır.</span><span class="sxs-lookup"><span data-stu-id="6e2ac-139">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="6e2ac-140">Bu sınıflardan birinde koleksiyona bir dinleyici nesnesi eklerseniz, diğer sınıf aynı dinleyiciyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="6e2ac-140">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="6e2ac-141">Dinleyici sınıfları. <xref:System.Diagnostics.TraceListener></span><span class="sxs-lookup"><span data-stu-id="6e2ac-141">The listener classes derive from the <xref:System.Diagnostics.TraceListener>.</span></span>  
  
 <span data-ttu-id="6e2ac-142">İzleme dinleyicisinin özniteliğini `name` belirtmezseniz, izleme <xref:System.Diagnostics.TraceListener.Name%2A> dinleyicisinin varsayılan olarak boş bir dize ("") olduğunu belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e2ac-142">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="6e2ac-143">Uygulamanızda yalnızca bir dinleyici varsa, bir ad belirtmeden ekleyebilir ve ad için boş bir dize belirterek kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e2ac-143">If your application has only one listener, you can add it without specifying a name, and remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="6e2ac-144">Ancak, uygulamanızda birden fazla dinleyici varsa, her izleme dinleyicisi için benzersiz adlar belirtmeniz gerekir, <xref:System.Diagnostics.Debug.Listeners%2A> bu <xref:System.Diagnostics.Trace.Listeners%2A> da izleme dinleyicilerini ve koleksiyonlarını tek tek belirlemenize ve yönetmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="6e2ac-144">However, if your application has more than one listener, you should specify unique names for each trace listener, which allows you to identify and manage individual trace listeners within the <xref:System.Diagnostics.Debug.Listeners%2A> and <xref:System.Diagnostics.Trace.Listeners%2A> collections.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6e2ac-145">Aynı türden ve aynı ada sahip birden fazla izleme dinleyicisi eklemek, koleksiyona bu tür `Listeners` ve addan yalnızca bir izleme dinleyicisi eklenmesiyle sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="6e2ac-145">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="6e2ac-146">Ancak, `Listeners` koleksiyona programlı olarak birden çok aynı dinleyici ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e2ac-146">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="6e2ac-147">**InitializeData** özniteliğinin değeri, oluşturduğunuz dinleyici türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="6e2ac-147">The value for the **initializeData** attribute depends on the type of listener you create.</span></span> <span data-ttu-id="6e2ac-148">Tüm izleme **dinleyicileri, initializeData**belirtmenizi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="6e2ac-148">Not all trace listeners require that you specify **initializeData**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6e2ac-149">Özniteliği kullandığınızda, `initializeData` derleyici uyarı alabilirsiniz "'InitializeData' özniteliği ilan edilmez."</span><span class="sxs-lookup"><span data-stu-id="6e2ac-149">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="6e2ac-150">Yapılandırma ayarları özniteliği tanımayan <xref:System.Diagnostics.TraceListener> `initializeData` soyut taban sınıfa karşı doğrulandığı için bu uyarı oluşur.</span><span class="sxs-lookup"><span data-stu-id="6e2ac-150">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="6e2ac-151">Genellikle, bir parametre alan bir oluşturucu ya da izleme dinleyicisi uygulamaları için bu uyarıyı yoksayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e2ac-151">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="6e2ac-152">Aşağıdaki tabloda .NET Framework'e dahil olan izleme dinleyicileri gösterilmektedir ve **initializeData** özniteliklerinin değerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="6e2ac-152">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their **initializeData** attributes.</span></span>  
  
|<span data-ttu-id="6e2ac-153">İzleme dinleyici sınıfı</span><span class="sxs-lookup"><span data-stu-id="6e2ac-153">Trace listener class</span></span>|<span data-ttu-id="6e2ac-154">initializeData öznitelik değeri</span><span class="sxs-lookup"><span data-stu-id="6e2ac-154">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="6e2ac-155">Oluşturucunun `useErrorStream` <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> değeri.</span><span class="sxs-lookup"><span data-stu-id="6e2ac-155">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="6e2ac-156">İz `initializeData` ve hata`true`ayıklama çıktısı yazmak için <xref:System.Console.Error%2A?displayProperty=nameWithType>özniteliği " " olarak ayarlayın; "`false`" " <xref:System.Console.Out%2A?displayProperty=nameWithType>yazmak için .</span><span class="sxs-lookup"><span data-stu-id="6e2ac-156">Set the `initializeData` attribute to "`true`" to write trace and debug output to <xref:System.Console.Error%2A?displayProperty=nameWithType>; "`false`" to write to <xref:System.Console.Out%2A?displayProperty=nameWithType>.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="6e2ac-157"><xref:System.Diagnostics.DelimitedListTraceListener> Yazdığı dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="6e2ac-157">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="6e2ac-158">Varolan bir olay günlüğü kaynağının adı.</span><span class="sxs-lookup"><span data-stu-id="6e2ac-158">The name of the name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="6e2ac-159"><xref:System.Diagnostics.EventSchemaTraceListener> Yazdığı dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="6e2ac-159">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="6e2ac-160"><xref:System.Diagnostics.TextWriterTraceListener> Yazdığı dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="6e2ac-160">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="6e2ac-161"><xref:System.Diagnostics.XmlWriterTraceListener> Yazdığı dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="6e2ac-161">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6e2ac-162">Örnek</span><span class="sxs-lookup"><span data-stu-id="6e2ac-162">Example</span></span>  
 <span data-ttu-id="6e2ac-163">Aşağıdaki örnek, dinleyicileri `MyListener` ve `MyEventListener` **Dinleyiciler** koleksiyonuna eklemek için \*\* \<>\*\* öğelerini nasıl kullanacağımı gösterir.</span><span class="sxs-lookup"><span data-stu-id="6e2ac-163">The following example shows how to use **\<add>** elements to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="6e2ac-164">`MyListener`adlı `MyListener.log` bir dosya oluşturur ve çıktıyı dosyaya yazar.</span><span class="sxs-lookup"><span data-stu-id="6e2ac-164">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="6e2ac-165">`MyEventListener`olay günlüğünde bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6e2ac-165">`MyEventListener` creates an entry in the event log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6e2ac-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e2ac-166">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- [<span data-ttu-id="6e2ac-167">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="6e2ac-167">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6e2ac-168">İz Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="6e2ac-168">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
