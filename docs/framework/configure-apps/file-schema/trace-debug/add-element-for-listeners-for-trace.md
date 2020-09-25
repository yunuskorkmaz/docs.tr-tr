---
title: <add>İçin için öğesi <listeners><trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
ms.openlocfilehash: da5c0ccae08a32c324a1633b5a7ff7592efa6e2d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91174049"
---
# <a name="add-element-for-listeners-for-trace"></a><span data-ttu-id="f8ed0-102">\<add>İçin için öğesi \<listeners>\<trace></span><span class="sxs-lookup"><span data-stu-id="f8ed0-102">\<add> Element for \<listeners> for \<trace></span></span>

<span data-ttu-id="f8ed0-103">**Dinleyiciler** koleksiyonuna bir dinleyici ekler.</span><span class="sxs-lookup"><span data-stu-id="f8ed0-103">Adds a listener to the **Listeners** collection.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="f8ed0-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="f8ed0-104">Syntax</span></span>  
  
```xml  
<add name="name"
     type="trace listener class name, Version, Culture, PublicKeyToken"  
     initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f8ed0-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f8ed0-105">Attributes and Elements</span></span>  

 <span data-ttu-id="f8ed0-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f8ed0-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f8ed0-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f8ed0-107">Attributes</span></span>  
  
|<span data-ttu-id="f8ed0-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f8ed0-108">Attribute</span></span>|<span data-ttu-id="f8ed0-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f8ed0-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f8ed0-110">**türüyle**</span><span class="sxs-lookup"><span data-stu-id="f8ed0-110">**type**</span></span>|<span data-ttu-id="f8ed0-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="f8ed0-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="f8ed0-112">Dinleyicinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="f8ed0-112">Specifies the type of the listener.</span></span> <span data-ttu-id="f8ed0-113">[Tam nitelikli tür adlarını belirtirken](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)belirtilen gereksinimleri karşılayan bir dize kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f8ed0-113">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="f8ed0-114">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="f8ed0-114">**initializeData**</span></span>|<span data-ttu-id="f8ed0-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="f8ed0-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="f8ed0-116">Belirtilen sınıf için oluşturucuya geçirilen dize.</span><span class="sxs-lookup"><span data-stu-id="f8ed0-116">The string passed to the constructor for the specified class.</span></span>|  
|<span data-ttu-id="f8ed0-117">**ada**</span><span class="sxs-lookup"><span data-stu-id="f8ed0-117">**name**</span></span>|<span data-ttu-id="f8ed0-118">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="f8ed0-118">Optional attribute.</span></span><br /><br /> <span data-ttu-id="f8ed0-119">Dinleyicinin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f8ed0-119">Specifies the name of the listener.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f8ed0-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f8ed0-120">Child Elements</span></span>  
  
|<span data-ttu-id="f8ed0-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="f8ed0-121">Element</span></span>|<span data-ttu-id="f8ed0-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f8ed0-122">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-listeners-for-trace.md)|<span data-ttu-id="f8ed0-123">İzleme için koleksiyondaki bir dinleyiciye bir filtre ekler `Listeners` .</span><span class="sxs-lookup"><span data-stu-id="f8ed0-123">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f8ed0-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f8ed0-124">Parent Elements</span></span>  
  
|<span data-ttu-id="f8ed0-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="f8ed0-125">Element</span></span>|<span data-ttu-id="f8ed0-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f8ed0-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f8ed0-127">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="f8ed0-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="f8ed0-128">İletileri toplayan, depolayan ve yönlendiren bir dinleyici belirtir.</span><span class="sxs-lookup"><span data-stu-id="f8ed0-128">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="f8ed0-129">Dinleyiciler izleme çıkışını uygun bir hedefe yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="f8ed0-129">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="f8ed0-130">ASP.NET yapılandırma bölümünün kök öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f8ed0-130">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="f8ed0-131">İzleme iletilerini toplayıp depolayan, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="f8ed0-131">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8ed0-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f8ed0-132">Remarks</span></span>  

 <span data-ttu-id="f8ed0-133"><xref:System.Diagnostics.Debug>Ve <xref:System.Diagnostics.Trace> sınıfları aynı **dinleyicileri** toplamayı paylaşır.</span><span class="sxs-lookup"><span data-stu-id="f8ed0-133">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="f8ed0-134">Bu sınıflardan birindeki koleksiyona bir dinleyici nesnesi eklerseniz, diğer sınıf aynı dinleyiciyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="f8ed0-134">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="f8ed0-135">Dinleyici sınıfları öğesinden türetilir <xref:System.Diagnostics.TraceListener> .</span><span class="sxs-lookup"><span data-stu-id="f8ed0-135">The listener classes derive from the <xref:System.Diagnostics.TraceListener>.</span></span>  
  
 <span data-ttu-id="f8ed0-136">`name`İzleme dinleyicisinin özniteliğini belirtmezseniz, <xref:System.Diagnostics.TraceListener.Name%2A> İzleme dinleyicisinin varsayılan değeri boş bir dize ("") olur.</span><span class="sxs-lookup"><span data-stu-id="f8ed0-136">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="f8ed0-137">Uygulamanızda yalnızca bir dinleyici varsa, bunu bir ad belirtmeden ekleyebilir ve ad için boş bir dize belirterek kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8ed0-137">If your application has only one listener, you can add it without specifying a name, and remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="f8ed0-138">Bununla birlikte, uygulamanız birden fazla dinleyici içeriyorsa, her bir izleme dinleyicisi için benzersiz adlar belirtmelisiniz. Bu, ve koleksiyonları içindeki tek tek izleme dinleyicilerini tanımlamanızı ve yönetmenizi sağlar <xref:System.Diagnostics.Debug.Listeners%2A> <xref:System.Diagnostics.Trace.Listeners%2A> .</span><span class="sxs-lookup"><span data-stu-id="f8ed0-138">However, if your application has more than one listener, you should specify unique names for each trace listener, which allows you to identify and manage individual trace listeners within the <xref:System.Diagnostics.Debug.Listeners%2A> and <xref:System.Diagnostics.Trace.Listeners%2A> collections.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f8ed0-139">Aynı türde ve aynı ada sahip birden fazla izleme dinleyicisi eklemek, bu tür ve koleksiyona eklenmekte olan adın yalnızca bir izleme dinleyicisine neden olur `Listeners` .</span><span class="sxs-lookup"><span data-stu-id="f8ed0-139">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="f8ed0-140">Ancak, koleksiyona daha fazla özdeş dinleyici ekleyebilirsiniz `Listeners` .</span><span class="sxs-lookup"><span data-stu-id="f8ed0-140">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="f8ed0-141">**Initializedata** özniteliğinin değeri, oluşturduğunuz dinleyicinin türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="f8ed0-141">The value for the **initializeData** attribute depends on the type of listener you create.</span></span> <span data-ttu-id="f8ed0-142">Tüm izleme dinleyicileri **ınitializedata**belirtmenizi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="f8ed0-142">Not all trace listeners require that you specify **initializeData**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f8ed0-143">`initializeData`Özniteliğini kullandığınızda, "ınitializedata" özniteliği bildirilmemiş "derleyici uyarısını alabilirsiniz."</span><span class="sxs-lookup"><span data-stu-id="f8ed0-143">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="f8ed0-144">Bu uyarı, yapılandırma ayarları özniteliği tanımayan Özet taban sınıfına göre doğrulandığından oluşur <xref:System.Diagnostics.TraceListener> `initializeData` .</span><span class="sxs-lookup"><span data-stu-id="f8ed0-144">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="f8ed0-145">Genellikle, bir parametresi alan Oluşturucusu olan izleme dinleyicisi uygulamaları için bu uyarıyı yoksayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8ed0-145">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="f8ed0-146">Aşağıdaki tabloda, .NET Framework eklenen izleme dinleyicileri gösterilmektedir ve **ınitializedata** özniteliklerinin değeri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f8ed0-146">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their **initializeData** attributes.</span></span>  
  
|<span data-ttu-id="f8ed0-147">Trace dinleyicisi sınıfı</span><span class="sxs-lookup"><span data-stu-id="f8ed0-147">Trace listener class</span></span>|<span data-ttu-id="f8ed0-148">ınitializedata öznitelik değeri</span><span class="sxs-lookup"><span data-stu-id="f8ed0-148">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="f8ed0-149">`useErrorStream` <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> Oluşturucunun değeri.</span><span class="sxs-lookup"><span data-stu-id="f8ed0-149">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="f8ed0-150">`initializeData` `true` Trace ve Debug çıkışını yazmak için özniteliği "" olarak ayarlayın <xref:System.Console.Error%2A?displayProperty=nameWithType> ; " `false` " yazmak için <xref:System.Console.Out%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f8ed0-150">Set the `initializeData` attribute to "`true`" to write trace and debug output to <xref:System.Console.Error%2A?displayProperty=nameWithType>; "`false`" to write to <xref:System.Console.Out%2A?displayProperty=nameWithType>.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="f8ed0-151">Yazdığı dosyanın adı <xref:System.Diagnostics.DelimitedListTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="f8ed0-151">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="f8ed0-152">Mevcut bir olay günlüğü kaynağı adının adı.</span><span class="sxs-lookup"><span data-stu-id="f8ed0-152">The name of the name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="f8ed0-153">Yazdığı dosyanın adı <xref:System.Diagnostics.EventSchemaTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="f8ed0-153">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="f8ed0-154">Yazdığı dosyanın adı <xref:System.Diagnostics.TextWriterTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="f8ed0-154">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="f8ed0-155">Yazdığı dosyanın adı <xref:System.Diagnostics.XmlWriterTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="f8ed0-155">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f8ed0-156">Örnek</span><span class="sxs-lookup"><span data-stu-id="f8ed0-156">Example</span></span>  

 <span data-ttu-id="f8ed0-157">Aşağıdaki örnek, **\<add>** dinleyicileri `MyListener` ve `MyEventListener` **dinleyici** koleksiyonuna eklemek için öğelerin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f8ed0-157">The following example shows how to use **\<add>** elements to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="f8ed0-158">`MyListener` adlı bir dosya oluşturur `MyListener.log` ve çıktıyı dosyaya yazar.</span><span class="sxs-lookup"><span data-stu-id="f8ed0-158">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="f8ed0-159">`MyEventListener` olay günlüğünde bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f8ed0-159">`MyEventListener` creates an entry in the event log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f8ed0-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f8ed0-160">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- [<span data-ttu-id="f8ed0-161">İzleme ve hata ayıklama ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="f8ed0-161">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="f8ed0-162">İz Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="f8ed0-162">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
