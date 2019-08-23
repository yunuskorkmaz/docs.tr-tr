---
title: <add>İçin için <listeners> öğesi<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
ms.openlocfilehash: d4ff919991ab1505b2845a225706d32cc1e57d0a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920566"
---
# <a name="add-element-for-listeners-for-trace"></a><span data-ttu-id="5b11e-102">\<Trace için \< \<> > öğesi ekleme ></span><span class="sxs-lookup"><span data-stu-id="5b11e-102">\<add> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="5b11e-103">**Dinleyiciler** koleksiyonuna bir dinleyici ekler.</span><span class="sxs-lookup"><span data-stu-id="5b11e-103">Adds a listener to the **Listeners** collection.</span></span>  
  
 <span data-ttu-id="5b11e-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="5b11e-104">\<configuration></span></span>  
<span data-ttu-id="5b11e-105">\<System. Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="5b11e-105">\<system.diagnostics></span></span>  
<span data-ttu-id="5b11e-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="5b11e-106">\<trace></span></span>  
<span data-ttu-id="5b11e-107">\<dinleyiciler ></span><span class="sxs-lookup"><span data-stu-id="5b11e-107">\<listeners></span></span>  
<span data-ttu-id="5b11e-108">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="5b11e-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b11e-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5b11e-109">Syntax</span></span>  
  
```xml  
<add name="name"   
     type="trace listener class name, Version, Culture, PublicKeyToken"  
     initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5b11e-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5b11e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5b11e-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5b11e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5b11e-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5b11e-112">Attributes</span></span>  
  
|<span data-ttu-id="5b11e-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5b11e-113">Attribute</span></span>|<span data-ttu-id="5b11e-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5b11e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5b11e-115">**type**</span><span class="sxs-lookup"><span data-stu-id="5b11e-115">**type**</span></span>|<span data-ttu-id="5b11e-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="5b11e-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="5b11e-117">Dinleyicinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="5b11e-117">Specifies the type of the listener.</span></span> <span data-ttu-id="5b11e-118">[Tam nitelikli tür adlarını belirtirken](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)belirtilen gereksinimleri karşılayan bir dize kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5b11e-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="5b11e-119">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="5b11e-119">**initializeData**</span></span>|<span data-ttu-id="5b11e-120">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="5b11e-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="5b11e-121">Belirtilen sınıf için oluşturucuya geçirilen dize.</span><span class="sxs-lookup"><span data-stu-id="5b11e-121">The string passed to the constructor for the specified class.</span></span>|  
|<span data-ttu-id="5b11e-122">**name**</span><span class="sxs-lookup"><span data-stu-id="5b11e-122">**name**</span></span>|<span data-ttu-id="5b11e-123">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="5b11e-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="5b11e-124">Dinleyicinin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5b11e-124">Specifies the name of the listener.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5b11e-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5b11e-125">Child Elements</span></span>  
  
|<span data-ttu-id="5b11e-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="5b11e-126">Element</span></span>|<span data-ttu-id="5b11e-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5b11e-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5b11e-128">\<Filtre ></span><span class="sxs-lookup"><span data-stu-id="5b11e-128">\<filter></span></span>](filter-element-for-add-for-listeners-for-trace.md)|<span data-ttu-id="5b11e-129">İzleme için `Listeners` koleksiyondaki bir dinleyiciye bir filtre ekler.</span><span class="sxs-lookup"><span data-stu-id="5b11e-129">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5b11e-130">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5b11e-130">Parent Elements</span></span>  
  
|<span data-ttu-id="5b11e-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="5b11e-131">Element</span></span>|<span data-ttu-id="5b11e-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5b11e-132">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5b11e-133">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="5b11e-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="5b11e-134">İletileri toplayan, depolayan ve yönlendiren bir dinleyici belirtir.</span><span class="sxs-lookup"><span data-stu-id="5b11e-134">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="5b11e-135">Dinleyiciler izleme çıkışını uygun bir hedefe yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="5b11e-135">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="5b11e-136">ASP.NET yapılandırma bölümünün kök öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5b11e-136">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="5b11e-137">İzleme iletilerini toplayıp depolayan, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="5b11e-137">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b11e-138">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5b11e-138">Remarks</span></span>  
 <span data-ttu-id="5b11e-139">Ve sınıfları aynı dinleyicileri toplamayı paylaşır. <xref:System.Diagnostics.Debug> <xref:System.Diagnostics.Trace></span><span class="sxs-lookup"><span data-stu-id="5b11e-139">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="5b11e-140">Bu sınıflardan birindeki koleksiyona bir dinleyici nesnesi eklerseniz, diğer sınıf aynı dinleyiciyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="5b11e-140">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="5b11e-141">Dinleyici sınıfları öğesinden <xref:System.Diagnostics.TraceListener>türetilir.</span><span class="sxs-lookup"><span data-stu-id="5b11e-141">The listener classes derive from the <xref:System.Diagnostics.TraceListener>.</span></span>  
  
 <span data-ttu-id="5b11e-142">İzleme dinleyicisinin `name` özniteliğini belirtmezseniz <xref:System.Diagnostics.TraceListener.Name%2A> , İzleme dinleyicisinin varsayılan değeri boş bir dize ("") olur.</span><span class="sxs-lookup"><span data-stu-id="5b11e-142">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="5b11e-143">Uygulamanızda yalnızca bir dinleyici varsa, bunu bir ad belirtmeden ekleyebilir ve ad için boş bir dize belirterek kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b11e-143">If your application has only one listener, you can add it without specifying a name, and remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="5b11e-144">Bununla birlikte, uygulamanız birden fazla dinleyici içeriyorsa, her bir izleme dinleyicisi için benzersiz adlar belirtmelisiniz. Bu, <xref:System.Diagnostics.Debug.Listeners%2A> ve <xref:System.Diagnostics.Trace.Listeners%2A> koleksiyonları içindeki tek tek izleme dinleyicilerini tanımlamanızı ve yönetmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b11e-144">However, if your application has more than one listener, you should specify unique names for each trace listener, which allows you to identify and manage individual trace listeners within the <xref:System.Diagnostics.Debug.Listeners%2A> and <xref:System.Diagnostics.Trace.Listeners%2A> collections.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5b11e-145">Aynı türde ve aynı ada sahip birden fazla izleme dinleyicisi eklemek, bu tür ve `Listeners` koleksiyona eklenmekte olan adın yalnızca bir izleme dinleyicisine neden olur.</span><span class="sxs-lookup"><span data-stu-id="5b11e-145">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="5b11e-146">Ancak, `Listeners` koleksiyona daha fazla özdeş dinleyici ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b11e-146">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="5b11e-147">**Initializedata** özniteliğinin değeri, oluşturduğunuz dinleyicinin türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="5b11e-147">The value for the **initializeData** attribute depends on the type of listener you create.</span></span> <span data-ttu-id="5b11e-148">Tüm izleme dinleyicileri **ınitializedata**belirtmenizi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="5b11e-148">Not all trace listeners require that you specify **initializeData**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5b11e-149">`initializeData` Özniteliğini kullandığınızda, "ınitializedata" özniteliği bildirilmemiş "derleyici uyarısını alabilirsiniz."</span><span class="sxs-lookup"><span data-stu-id="5b11e-149">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="5b11e-150">Bu uyarı, yapılandırma ayarları <xref:System.Diagnostics.TraceListener> `initializeData` özniteliği tanımayan Özet taban sınıfına göre doğrulandığından oluşur.</span><span class="sxs-lookup"><span data-stu-id="5b11e-150">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="5b11e-151">Genellikle, bir parametresi alan Oluşturucusu olan izleme dinleyicisi uygulamaları için bu uyarıyı yoksayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b11e-151">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="5b11e-152">Aşağıdaki tabloda, .NET Framework eklenen izleme dinleyicileri gösterilmektedir ve **ınitializedata** özniteliklerinin değeri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5b11e-152">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their **initializeData** attributes.</span></span>  
  
|<span data-ttu-id="5b11e-153">Trace dinleyicisi sınıfı</span><span class="sxs-lookup"><span data-stu-id="5b11e-153">Trace listener class</span></span>|<span data-ttu-id="5b11e-154">ınitializedata öznitelik değeri</span><span class="sxs-lookup"><span data-stu-id="5b11e-154">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="5b11e-155"><xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> Oluşturucunun `useErrorStream` değeri.</span><span class="sxs-lookup"><span data-stu-id="5b11e-155">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="5b11e-156">Trace ve Debug çıkışını yazmak`true`için `initializeData` özniteliği "" olarak ayarlayın <xref:System.Console.Error%2A?displayProperty=nameWithType>; "`false` "<xref:System.Console.Out%2A?displayProperty=nameWithType>yazmak için.</span><span class="sxs-lookup"><span data-stu-id="5b11e-156">Set the `initializeData` attribute to "`true`" to write trace and debug output to <xref:System.Console.Error%2A?displayProperty=nameWithType>; "`false`" to write to <xref:System.Console.Out%2A?displayProperty=nameWithType>.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="5b11e-157"><xref:System.Diagnostics.DelimitedListTraceListener> Yazdığı dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="5b11e-157">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="5b11e-158">Mevcut bir olay günlüğü kaynağı adının adı.</span><span class="sxs-lookup"><span data-stu-id="5b11e-158">The name of the name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="5b11e-159"><xref:System.Diagnostics.EventSchemaTraceListener> Yazdığı dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="5b11e-159">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="5b11e-160"><xref:System.Diagnostics.TextWriterTraceListener> Yazdığı dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="5b11e-160">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="5b11e-161"><xref:System.Diagnostics.XmlWriterTraceListener> Yazdığı dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="5b11e-161">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5b11e-162">Örnek</span><span class="sxs-lookup"><span data-stu-id="5b11e-162">Example</span></span>  
 <span data-ttu-id="5b11e-163">Aşağıdaki örnek,  **\<Add >** öğelerinin `MyListener` nasıl kullanılacağını ve dinleyicileri ve `MyEventListener` **dinleyici** koleksiyonuna nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5b11e-163">The following example shows how to use **\<add>** elements to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="5b11e-164">`MyListener`adlı `MyListener.log` bir dosya oluşturur ve çıktıyı dosyaya yazar.</span><span class="sxs-lookup"><span data-stu-id="5b11e-164">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="5b11e-165">`MyEventListener`olay günlüğünde bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5b11e-165">`MyEventListener` creates an entry in the event log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5b11e-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b11e-166">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- [<span data-ttu-id="5b11e-167">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="5b11e-167">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="5b11e-168">İzleme Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="5b11e-168">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
