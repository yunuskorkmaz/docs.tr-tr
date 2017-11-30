---
title: "&lt;ekleme&gt; öğesi için &lt;sharedListeners&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <sharedListeners>
- add element for <sharedListeners>
ms.assetid: 1595e1bc-2492-421f-8384-7f382eb8eb57
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: fd8e7d18ca72cbeb558876eefcde17ebdc6c095f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-element-for-ltsharedlistenersgt"></a><span data-ttu-id="44c30-102">&lt;ekleme&gt; öğesi için &lt;sharedListeners&gt;</span><span class="sxs-lookup"><span data-stu-id="44c30-102">&lt;add&gt; Element for &lt;sharedListeners&gt;</span></span>
<span data-ttu-id="44c30-103">Bir dinleyici ekler `sharedListeners` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="44c30-103">Adds a listener to the `sharedListeners` collection.</span></span> <span data-ttu-id="44c30-104">`sharedListeners`dinleyicileri herhangi bir koleksiyonudur [ \<kaynak >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) veya [ \<İzleme >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md) başvuruda bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="44c30-104">`sharedListeners` is a collection of listeners that any [\<source>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) or [\<trace>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md) can reference.</span></span>  <span data-ttu-id="44c30-105">Varsayılan olarak, dinleyicileri `sharedListeners` koleksiyonu içinde değil yerleştirilir bir `Listeners` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="44c30-105">By default, listeners in the `sharedListeners` collection are not placed in a `Listeners` collection.</span></span> <span data-ttu-id="44c30-106">Adına eklenmesi gerekir [ \<kaynak >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) veya [ \<İzleme >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md).</span><span class="sxs-lookup"><span data-stu-id="44c30-106">They must be added by name to the [\<source>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) or [\<trace>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md).</span></span> <span data-ttu-id="44c30-107">Dinleyicileri almak mümkün değil `sharedListeners` çalışma zamanında kodda koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="44c30-107">It is not possible to get the listeners in the `sharedListeners` collection in code at run time.</span></span>  
  
 <span data-ttu-id="44c30-108">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="44c30-108">\<configuration></span></span>  
<span data-ttu-id="44c30-109">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="44c30-109">\<system.diagnostics></span></span>  
<span data-ttu-id="44c30-110">\<sharedListeners > öğesi</span><span class="sxs-lookup"><span data-stu-id="44c30-110">\<sharedListeners> Element</span></span>  
<span data-ttu-id="44c30-111">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="44c30-111">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44c30-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="44c30-112">Syntax</span></span>  
  
```xml  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44c30-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="44c30-113">Attributes and Elements</span></span>  
 <span data-ttu-id="44c30-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="44c30-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44c30-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="44c30-115">Attributes</span></span>  
  
|<span data-ttu-id="44c30-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="44c30-116">Attribute</span></span>|<span data-ttu-id="44c30-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="44c30-117">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="44c30-118">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="44c30-118">Required attribute.</span></span><br /><br /> <span data-ttu-id="44c30-119">Paylaşılan dinleyicisi eklemek için kullanılan dinleyicisinin adını belirten bir `Listeners` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="44c30-119">Specifies the name of the listener that is used to add the shared listener to a `Listeners` collection.</span></span>|  
|`type`|<span data-ttu-id="44c30-120">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="44c30-120">Required attribute.</span></span><br /><br /> <span data-ttu-id="44c30-121">Dinleyici türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="44c30-121">Specifies the type of the listener.</span></span> <span data-ttu-id="44c30-122">Belirtilen gereksinimleri karşılayan bir dize kullanmalısınız [belirtme tam olarak nitelenmiş tür adları](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="44c30-122">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="44c30-123">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="44c30-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="44c30-124">Dize için belirtilen sınıf oluşturucuya geçirilen.</span><span class="sxs-lookup"><span data-stu-id="44c30-124">The string passed to the constructor for the specified class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="44c30-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="44c30-125">Child Elements</span></span>  
  
|<span data-ttu-id="44c30-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="44c30-126">Element</span></span>|<span data-ttu-id="44c30-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="44c30-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="44c30-128">\<Filtre ></span><span class="sxs-lookup"><span data-stu-id="44c30-128">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-sharedlisteners.md)|<span data-ttu-id="44c30-129">Bir dinleyici için bir filtre ekler `sharedListeners` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="44c30-129">Adds a filter to a listener in the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="44c30-130">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="44c30-130">Parent Elements</span></span>  
  
|<span data-ttu-id="44c30-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="44c30-131">Element</span></span>|<span data-ttu-id="44c30-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="44c30-132">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="44c30-133">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="44c30-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="44c30-134">Toplamak, depolamak ve iletileri ve izleme anahtarı ayarlandığı düzeyi rota izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="44c30-134">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="44c30-135">Herhangi bir kaynak veya trace ögesi başvurabilir dinleyicileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="44c30-135">A collection of listeners that any source or trace element can reference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44c30-136">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="44c30-136">Remarks</span></span>  
 <span data-ttu-id="44c30-137">.NET Framework ile birlikte gelen dinleyicisi sınıfları türetin <xref:System.Diagnostics.TraceListener> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="44c30-137">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="44c30-138">Değeri `name` özniteliği paylaşılan dinleyicisi eklemek için kullanılan bir `Listeners` koleksiyonu bir izleme ve izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="44c30-138">The value for the `name` attribute is used to add the shared listener to a `Listeners` collection for either a trace or a trace source.</span></span> <span data-ttu-id="44c30-139">Değeri `initializeData` özniteliği oluşturduğunuz dinleyicisi türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="44c30-139">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="44c30-140">Tüm izleme dinleyicileri, belirttiğiniz gerektiren `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="44c30-140">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="44c30-141">Kullandığınızda `initializeData` özniteliği, "'initializeData' özniteliği yok bildirildi." uyarı derleyici alabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="44c30-141">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="44c30-142">Yapılandırma ayarları Özet temel sınıf karşı doğrulandığı için bu uyarıyı oluşur <xref:System.Diagnostics.TraceListener>, hangi tanımıyor `initializeData` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="44c30-142">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="44c30-143">Genellikle, bir parametre alan bir oluşturucuya sahip İzleme dinleyicisi uygulamaları için bu uyarıyı yoksayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44c30-143">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="44c30-144">Aşağıdaki tabloda .NET Framework ile birlikte izleme dinleyicilerini gösterir ve değerini açıklar kendi `initializeData` öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="44c30-144">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="44c30-145">İzleme dinleyicisi sınıfı</span><span class="sxs-lookup"><span data-stu-id="44c30-145">Trace listener class</span></span>|<span data-ttu-id="44c30-146">initializeData özniteliği değeri</span><span class="sxs-lookup"><span data-stu-id="44c30-146">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|<span data-ttu-id="44c30-147">`useErrorStream` Değerini <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="44c30-147">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="44c30-148">Ayarlama `initializeData` özniteliğini "`true`"yazmak için izleme ve hata ayıklama için standart hata akışı; çıktı ayarlayın"`false`" standart çıktı akışına yazmak için.</span><span class="sxs-lookup"><span data-stu-id="44c30-148">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|<span data-ttu-id="44c30-149">Dosyanın adını <xref:System.Diagnostics.DelimitedListTraceListener> yazar.</span><span class="sxs-lookup"><span data-stu-id="44c30-149">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="44c30-150">Var olan bir olay günlüğü kaynağı adı.</span><span class="sxs-lookup"><span data-stu-id="44c30-150">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="44c30-151">Dosya adı, <xref:System.Diagnostics.EventSchemaTraceListener> yazar.</span><span class="sxs-lookup"><span data-stu-id="44c30-151">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="44c30-152">Dosya adı, <xref:System.Diagnostics.TextWriterTraceListener> yazar.</span><span class="sxs-lookup"><span data-stu-id="44c30-152">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|<span data-ttu-id="44c30-153">Dosya adı, <xref:System.Diagnostics.XmlWriterTraceListener> yazar.</span><span class="sxs-lookup"><span data-stu-id="44c30-153">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="44c30-154">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="44c30-154">Configuration File</span></span>  
 <span data-ttu-id="44c30-155">Bu öğe makine yapılandırma dosyası (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="44c30-155">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44c30-156">Örnek</span><span class="sxs-lookup"><span data-stu-id="44c30-156">Example</span></span>  
 <span data-ttu-id="44c30-157">Aşağıdaki örnekte nasıl kullanılacağını gösterir `<add>` eklemek için öğeleri <xref:System.Diagnostics.TextWriterTraceListener> `textListener` için `sharedListeners` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="44c30-157">The following example shows how to use `<add>` elements to add the <xref:System.Diagnostics.TextWriterTraceListener>`textListener` to the `sharedListeners` collection.</span></span>   <span data-ttu-id="44c30-158">`textListener`adına tarafından eklenen `Listeners` izleme kaynağı toplamalarında `TraceSourceApp`.</span><span class="sxs-lookup"><span data-stu-id="44c30-158">`textListener` is added by name to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="44c30-159">`textListener` Dinleyicisi dosya myListener.log izleme çıktısı yazar.</span><span class="sxs-lookup"><span data-stu-id="44c30-159">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="44c30-160">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="44c30-160">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TraceListener>  
 [<span data-ttu-id="44c30-161">İzleme ve hata ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="44c30-161">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="44c30-162">İzleme dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="44c30-162">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
