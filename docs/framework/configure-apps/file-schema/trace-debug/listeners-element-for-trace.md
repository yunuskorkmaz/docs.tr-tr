---
title: <trace> için <listeners> öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
ms.openlocfilehash: 84b67532825372e7f69d86e1ef6060f4263587eb
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699346"
---
# <a name="listeners-element-for-trace"></a><span data-ttu-id="73c67-102">\<trace için \<listeners > öğesi ></span><span class="sxs-lookup"><span data-stu-id="73c67-102">\<listeners> Element for \<trace></span></span>
<span data-ttu-id="73c67-103">İletileri toplayan, depolayan ve yönlendiren bir dinleyici belirtir.</span><span class="sxs-lookup"><span data-stu-id="73c67-103">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="73c67-104">Dinleyiciler izleme çıkışını uygun bir hedefe yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="73c67-104">Listeners direct the tracing output to an appropriate target.</span></span>  
  
[<span data-ttu-id="73c67-105"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="73c67-105">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="73c67-106">&nbsp; @ no__t-1[ **\<system. Diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="73c67-106">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="73c67-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<trace >** ](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="73c67-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>  
<span data-ttu-id="73c67-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<listeners >**</span><span class="sxs-lookup"><span data-stu-id="73c67-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<listeners>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73c67-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="73c67-109">Syntax</span></span>  
  
```xml  
<listeners>   
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73c67-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="73c67-110">Attributes and Elements</span></span>  
 <span data-ttu-id="73c67-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="73c67-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73c67-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="73c67-112">Attributes</span></span>  
 <span data-ttu-id="73c67-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="73c67-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="73c67-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="73c67-114">Child Elements</span></span>  
  
|<span data-ttu-id="73c67-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="73c67-115">Element</span></span>|<span data-ttu-id="73c67-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="73c67-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="73c67-117">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="73c67-117">\<add></span></span>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="73c67-118">@No__t-0 koleksiyonuna bir dinleyici ekler.</span><span class="sxs-lookup"><span data-stu-id="73c67-118">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="73c67-119">\<clear ></span><span class="sxs-lookup"><span data-stu-id="73c67-119">\<clear></span></span>](clear-element-for-listeners-for-trace.md)|<span data-ttu-id="73c67-120">İzleme için `Listeners` koleksiyonunu temizler.</span><span class="sxs-lookup"><span data-stu-id="73c67-120">Clears the `Listeners` collection for trace.</span></span>|  
|[<span data-ttu-id="73c67-121">\<remove ></span><span class="sxs-lookup"><span data-stu-id="73c67-121">\<remove></span></span>](remove-element-for-listeners-for-trace.md)|<span data-ttu-id="73c67-122">@No__t-0 koleksiyonundan bir dinleyiciyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="73c67-122">Removes a listener from the `Listeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="73c67-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="73c67-123">Parent Elements</span></span>  
  
|<span data-ttu-id="73c67-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="73c67-124">Element</span></span>|<span data-ttu-id="73c67-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="73c67-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="73c67-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="73c67-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="73c67-127">ASP.NET yapılandırma bölümünün kök öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="73c67-127">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="73c67-128">İzleme iletilerini toplayıp depolayan, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="73c67-128">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73c67-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="73c67-129">Remarks</span></span>  
 <span data-ttu-id="73c67-130">@No__t-0 ve <xref:System.Diagnostics.Trace> sınıfları aynı **dinleyici** koleksiyonunu paylaşır.</span><span class="sxs-lookup"><span data-stu-id="73c67-130">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="73c67-131">Bu sınıflardan birindeki koleksiyona bir dinleyici nesnesi eklerseniz, diğer sınıf aynı dinleyiciyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="73c67-131">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="73c67-132">.NET Framework ile birlikte gelen dinleyici sınıfları <xref:System.Diagnostics.TraceListener> sınıfından türetilir.</span><span class="sxs-lookup"><span data-stu-id="73c67-132">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="73c67-133">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="73c67-133">Configuration File</span></span>  
 <span data-ttu-id="73c67-134">Bu öğe makine yapılandırma dosyasında (Machine. config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="73c67-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73c67-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="73c67-135">Example</span></span>  
 <span data-ttu-id="73c67-136">Aşağıdaki örnek, `MyListener` ve `MyEventListener` dinleyicilerini **dinleyiciler** koleksiyonuna eklemek için **\<listeners >** öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="73c67-136">The following example shows how to use the **\<listeners>** element to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="73c67-137">`MyListener` `MyListener.log` adlı bir dosya oluşturur ve çıktıyı dosyaya yazar.</span><span class="sxs-lookup"><span data-stu-id="73c67-137">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="73c67-138">`MyEventListener` olay günlüğünde bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="73c67-138">`MyEventListener` creates an entry in the event log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="73c67-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73c67-139">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="73c67-140">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="73c67-140">Trace and Debug Settings Schema</span></span>](index.md)
