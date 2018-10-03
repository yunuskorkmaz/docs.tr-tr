---
title: '&lt;dinleyicileri&gt; öğesi için &lt;izleme&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
author: mcleblanc
ms.author: markl
ms.openlocfilehash: bfcf96c553f85aeb0a40dfd6ea36667d504e8eee
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48028007"
---
# <a name="ltlistenersgt-element-for-lttracegt"></a><span data-ttu-id="6c73b-102">&lt;dinleyicileri&gt; öğesi için &lt;izleme&gt;</span><span class="sxs-lookup"><span data-stu-id="6c73b-102">&lt;listeners&gt; Element for &lt;trace&gt;</span></span>
<span data-ttu-id="6c73b-103">Toplar, depolar, bir dinleyici belirtir ve iletileri yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="6c73b-103">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="6c73b-104">Dinleyicileri bir uygun hedef izleme çıkışa doğrudan.</span><span class="sxs-lookup"><span data-stu-id="6c73b-104">Listeners direct the tracing output to an appropriate target.</span></span>  
  
 <span data-ttu-id="6c73b-105">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="6c73b-105">\<configuration> Element</span></span>  
<span data-ttu-id="6c73b-106">\<System.Diagnostics > öğesi</span><span class="sxs-lookup"><span data-stu-id="6c73b-106">\<system.diagnostics> Element</span></span>  
<span data-ttu-id="6c73b-107">\<İzleme > öğesi</span><span class="sxs-lookup"><span data-stu-id="6c73b-107">\<trace> Element</span></span>  
<span data-ttu-id="6c73b-108">\<dinleyicileri > öğesi için \<İzleme ></span><span class="sxs-lookup"><span data-stu-id="6c73b-108">\<listeners> Element for \<trace></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c73b-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6c73b-109">Syntax</span></span>  
  
```xml  
<listeners>   
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6c73b-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6c73b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6c73b-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6c73b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6c73b-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6c73b-112">Attributes</span></span>  
 <span data-ttu-id="6c73b-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="6c73b-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6c73b-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6c73b-114">Child Elements</span></span>  
  
|<span data-ttu-id="6c73b-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="6c73b-115">Element</span></span>|<span data-ttu-id="6c73b-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c73b-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6c73b-117">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="6c73b-117">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|<span data-ttu-id="6c73b-118">Bir ekler `Listeners` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="6c73b-118">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="6c73b-119">\<Temizleme ></span><span class="sxs-lookup"><span data-stu-id="6c73b-119">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-trace.md)|<span data-ttu-id="6c73b-120">Temizler `Listeners` izleme için koleksiyon.</span><span class="sxs-lookup"><span data-stu-id="6c73b-120">Clears the `Listeners` collection for trace.</span></span>|  
|[<span data-ttu-id="6c73b-121">\<kaldırma ></span><span class="sxs-lookup"><span data-stu-id="6c73b-121">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)|<span data-ttu-id="6c73b-122">Bir dinleyicisinden kaldırır `Listeners` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="6c73b-122">Removes a listener from the `Listeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6c73b-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6c73b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="6c73b-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="6c73b-124">Element</span></span>|<span data-ttu-id="6c73b-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c73b-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6c73b-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="6c73b-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="6c73b-127">ASP.NET yapılandırma bölümü için olan kök öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c73b-127">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="6c73b-128">Toplamak, depolamak ve izleme iletilerini yönlendirmek dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="6c73b-128">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c73b-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6c73b-129">Remarks</span></span>  
 <span data-ttu-id="6c73b-130"><xref:System.Diagnostics.Debug> Ve <xref:System.Diagnostics.Trace> sınıfları paylaşma aynı **dinleyicileri** koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="6c73b-130">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="6c73b-131">Bu sınıflardan birine koleksiyonuna bir dinleyici nesne eklerseniz, başka bir sınıfın aynı dinleyicisi kullanır.</span><span class="sxs-lookup"><span data-stu-id="6c73b-131">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="6c73b-132">.NET Framework ile birlikte gelen dinleyici sınıfların türetilmesi <xref:System.Diagnostics.TraceListener> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6c73b-132">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="6c73b-133">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="6c73b-133">Configuration File</span></span>  
 <span data-ttu-id="6c73b-134">Bu öğe, makine yapılandırma dosyası (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6c73b-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c73b-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="6c73b-135">Example</span></span>  
 <span data-ttu-id="6c73b-136">Aşağıdaki örnek nasıl kullanılacağını gösterir  **\<dinleyicileri >** dinleyiciler eklemek için öğe `MyListener` ve `MyEventListener` için **dinleyicileri** koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="6c73b-136">The following example shows how to use the **\<listeners>** element to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="6c73b-137">`MyListener` adlı bir dosya oluşturur `MyListener.log` ve çıkış dosyasına yazar.</span><span class="sxs-lookup"><span data-stu-id="6c73b-137">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="6c73b-138">`MyEventListener` olay günlüğünde bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6c73b-138">`MyEventListener` creates an entry in the event log.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="true" indentsize="0">  
      <listeners>  
        <add name="myListener"   
          type="System.Diagnostics.TextWriterTraceListener,   
            system, version=1.0.3300.0, Culture=neutral,   
            PublicKeyToken=b77a5c561934e089"   
          initializeData="c:\myListener.log" />  
        <add name="MyEventListener"  
          type="System.Diagnostics.EventLogTraceListener,   
            system, version=1.0.3300.0, Culture=neutral,   
            PublicKeyToken=b77a5c561934e089"  
          initializeData="MyConfigEventLog"/>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6c73b-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6c73b-139">See Also</span></span>  
 <xref:System.Diagnostics.TraceListener>  
 [<span data-ttu-id="6c73b-140">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="6c73b-140">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
