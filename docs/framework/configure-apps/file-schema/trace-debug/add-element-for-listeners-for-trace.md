---
description: 'Hakkında daha fazla bilgi edinin: için <add> öğesi <listeners><trace>'
title: <add>İçin için öğesi <listeners><trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
ms.openlocfilehash: ffc0823e0c0ce1dcd9d9f19853929496b3248177
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639789"
---
# <a name="add-element-for-listeners-for-trace"></a><span data-ttu-id="9e9a0-103">\<add>İçin için öğesi \<listeners>\<trace></span><span class="sxs-lookup"><span data-stu-id="9e9a0-103">\<add> Element for \<listeners> for \<trace></span></span>

<span data-ttu-id="9e9a0-104">**Dinleyiciler** koleksiyonuna bir dinleyici ekler.</span><span class="sxs-lookup"><span data-stu-id="9e9a0-104">Adds a listener to the **Listeners** collection.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="9e9a0-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="9e9a0-105">Syntax</span></span>  
  
```xml  
<add name="name"
     type="trace listener class name, Version, Culture, PublicKeyToken"  
     initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9e9a0-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9e9a0-106">Attributes and Elements</span></span>  

 <span data-ttu-id="9e9a0-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9e9a0-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9e9a0-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9e9a0-108">Attributes</span></span>  
  
|<span data-ttu-id="9e9a0-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9e9a0-109">Attribute</span></span>|<span data-ttu-id="9e9a0-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9e9a0-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9e9a0-111">**türüyle**</span><span class="sxs-lookup"><span data-stu-id="9e9a0-111">**type**</span></span>|<span data-ttu-id="9e9a0-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="9e9a0-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="9e9a0-113">Dinleyicinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="9e9a0-113">Specifies the type of the listener.</span></span> <span data-ttu-id="9e9a0-114">[Tam nitelikli tür adlarını belirtirken](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)belirtilen gereksinimleri karşılayan bir dize kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9e9a0-114">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="9e9a0-115">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="9e9a0-115">**initializeData**</span></span>|<span data-ttu-id="9e9a0-116">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="9e9a0-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="9e9a0-117">Belirtilen sınıf için oluşturucuya geçirilen dize.</span><span class="sxs-lookup"><span data-stu-id="9e9a0-117">The string passed to the constructor for the specified class.</span></span>|  
|<span data-ttu-id="9e9a0-118">**ada**</span><span class="sxs-lookup"><span data-stu-id="9e9a0-118">**name**</span></span>|<span data-ttu-id="9e9a0-119">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="9e9a0-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="9e9a0-120">Dinleyicinin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9e9a0-120">Specifies the name of the listener.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9e9a0-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9e9a0-121">Child Elements</span></span>  
  
|<span data-ttu-id="9e9a0-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="9e9a0-122">Element</span></span>|<span data-ttu-id="9e9a0-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9e9a0-123">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-listeners-for-trace.md)|<span data-ttu-id="9e9a0-124">İzleme için koleksiyondaki bir dinleyiciye bir filtre ekler `Listeners` .</span><span class="sxs-lookup"><span data-stu-id="9e9a0-124">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9e9a0-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9e9a0-125">Parent Elements</span></span>  
  
|<span data-ttu-id="9e9a0-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="9e9a0-126">Element</span></span>|<span data-ttu-id="9e9a0-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9e9a0-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9e9a0-128">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="9e9a0-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="9e9a0-129">İletileri toplayan, depolayan ve yönlendiren bir dinleyici belirtir.</span><span class="sxs-lookup"><span data-stu-id="9e9a0-129">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="9e9a0-130">Dinleyiciler izleme çıkışını uygun bir hedefe yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="9e9a0-130">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="9e9a0-131">ASP.NET yapılandırma bölümünün kök öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9e9a0-131">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="9e9a0-132">İzleme iletilerini toplayıp depolayan, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="9e9a0-132">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e9a0-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9e9a0-133">Remarks</span></span>  

 <span data-ttu-id="9e9a0-134"><xref:System.Diagnostics.Debug>Ve <xref:System.Diagnostics.Trace> sınıfları aynı **dinleyicileri** toplamayı paylaşır.</span><span class="sxs-lookup"><span data-stu-id="9e9a0-134">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="9e9a0-135">Bu sınıflardan birindeki koleksiyona bir dinleyici nesnesi eklerseniz, diğer sınıf aynı dinleyiciyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="9e9a0-135">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="9e9a0-136">Dinleyici sınıfları öğesinden türetilir <xref:System.Diagnostics.TraceListener> .</span><span class="sxs-lookup"><span data-stu-id="9e9a0-136">The listener classes derive from the <xref:System.Diagnostics.TraceListener>.</span></span>  
  
 <span data-ttu-id="9e9a0-137">`name`İzleme dinleyicisinin özniteliğini belirtmezseniz, <xref:System.Diagnostics.TraceListener.Name%2A> İzleme dinleyicisinin varsayılan değeri boş bir dize ("") olur.</span><span class="sxs-lookup"><span data-stu-id="9e9a0-137">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="9e9a0-138">Uygulamanızda yalnızca bir dinleyici varsa, bunu bir ad belirtmeden ekleyebilir ve ad için boş bir dize belirterek kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e9a0-138">If your application has only one listener, you can add it without specifying a name, and remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="9e9a0-139">Bununla birlikte, uygulamanız birden fazla dinleyici içeriyorsa, her bir izleme dinleyicisi için benzersiz adlar belirtmelisiniz. Bu, ve koleksiyonları içindeki tek tek izleme dinleyicilerini tanımlamanızı ve yönetmenizi sağlar <xref:System.Diagnostics.Debug.Listeners%2A> <xref:System.Diagnostics.Trace.Listeners%2A> .</span><span class="sxs-lookup"><span data-stu-id="9e9a0-139">However, if your application has more than one listener, you should specify unique names for each trace listener, which allows you to identify and manage individual trace listeners within the <xref:System.Diagnostics.Debug.Listeners%2A> and <xref:System.Diagnostics.Trace.Listeners%2A> collections.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9e9a0-140">Aynı türde ve aynı ada sahip birden fazla izleme dinleyicisi eklemek, bu tür ve koleksiyona eklenmekte olan adın yalnızca bir izleme dinleyicisine neden olur `Listeners` .</span><span class="sxs-lookup"><span data-stu-id="9e9a0-140">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="9e9a0-141">Ancak, koleksiyona daha fazla özdeş dinleyici ekleyebilirsiniz `Listeners` .</span><span class="sxs-lookup"><span data-stu-id="9e9a0-141">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="9e9a0-142">**Initializedata** özniteliğinin değeri, oluşturduğunuz dinleyicinin türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="9e9a0-142">The value for the **initializeData** attribute depends on the type of listener you create.</span></span> <span data-ttu-id="9e9a0-143">Tüm izleme dinleyicileri **ınitializedata** belirtmenizi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="9e9a0-143">Not all trace listeners require that you specify **initializeData**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9e9a0-144">`initializeData`Özniteliğini kullandığınızda, "ınitializedata" özniteliği bildirilmemiş "derleyici uyarısını alabilirsiniz."</span><span class="sxs-lookup"><span data-stu-id="9e9a0-144">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="9e9a0-145">Bu uyarı, yapılandırma ayarları özniteliği tanımayan Özet taban sınıfına göre doğrulandığından oluşur <xref:System.Diagnostics.TraceListener> `initializeData` .</span><span class="sxs-lookup"><span data-stu-id="9e9a0-145">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="9e9a0-146">Genellikle, bir parametresi alan Oluşturucusu olan izleme dinleyicisi uygulamaları için bu uyarıyı yoksayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e9a0-146">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="9e9a0-147">Aşağıdaki tabloda, .NET Framework eklenen izleme dinleyicileri gösterilmektedir ve **ınitializedata** özniteliklerinin değeri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9e9a0-147">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their **initializeData** attributes.</span></span>  
  
|<span data-ttu-id="9e9a0-148">Trace dinleyicisi sınıfı</span><span class="sxs-lookup"><span data-stu-id="9e9a0-148">Trace listener class</span></span>|<span data-ttu-id="9e9a0-149">ınitializedata öznitelik değeri</span><span class="sxs-lookup"><span data-stu-id="9e9a0-149">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="9e9a0-150">`useErrorStream` <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> Oluşturucunun değeri.</span><span class="sxs-lookup"><span data-stu-id="9e9a0-150">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="9e9a0-151">`initializeData` `true` Trace ve Debug çıkışını yazmak için özniteliği "" olarak ayarlayın <xref:System.Console.Error%2A?displayProperty=nameWithType> ; " `false` " yazmak için <xref:System.Console.Out%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="9e9a0-151">Set the `initializeData` attribute to "`true`" to write trace and debug output to <xref:System.Console.Error%2A?displayProperty=nameWithType>; "`false`" to write to <xref:System.Console.Out%2A?displayProperty=nameWithType>.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="9e9a0-152">Yazdığı dosyanın adı <xref:System.Diagnostics.DelimitedListTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="9e9a0-152">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="9e9a0-153">Mevcut bir olay günlüğü kaynağı adının adı.</span><span class="sxs-lookup"><span data-stu-id="9e9a0-153">The name of the name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="9e9a0-154">Yazdığı dosyanın adı <xref:System.Diagnostics.EventSchemaTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="9e9a0-154">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="9e9a0-155">Yazdığı dosyanın adı <xref:System.Diagnostics.TextWriterTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="9e9a0-155">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="9e9a0-156">Yazdığı dosyanın adı <xref:System.Diagnostics.XmlWriterTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="9e9a0-156">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9e9a0-157">Örnek</span><span class="sxs-lookup"><span data-stu-id="9e9a0-157">Example</span></span>  

 <span data-ttu-id="9e9a0-158">Aşağıdaki örnek, **\<add>** dinleyicileri `MyListener` ve `MyEventListener` **dinleyici** koleksiyonuna eklemek için öğelerin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9e9a0-158">The following example shows how to use **\<add>** elements to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="9e9a0-159">`MyListener` adlı bir dosya oluşturur `MyListener.log` ve çıktıyı dosyaya yazar.</span><span class="sxs-lookup"><span data-stu-id="9e9a0-159">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="9e9a0-160">`MyEventListener` olay günlüğünde bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9e9a0-160">`MyEventListener` creates an entry in the event log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9e9a0-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e9a0-161">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- [<span data-ttu-id="9e9a0-162">İzleme ve hata ayıklama ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="9e9a0-162">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="9e9a0-163">İz Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="9e9a0-163">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
