---
title: <trace> için <listeners> öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
ms.openlocfilehash: fd12be1b775d7611ef3f16d23147470313bf9866
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153379"
---
# <a name="listeners-element-for-trace"></a><span data-ttu-id="b4543-102">\<izleme> için \<Element> dinleyici</span><span class="sxs-lookup"><span data-stu-id="b4543-102">\<listeners> Element for \<trace></span></span>
<span data-ttu-id="b4543-103">İletileri toplayan, depolayan ve gönderen bir dinleyici belirtir.</span><span class="sxs-lookup"><span data-stu-id="b4543-103">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="b4543-104">Dinleyiciler izleme çıktısını uygun bir hedefe yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="b4543-104">Listeners direct the tracing output to an appropriate target.</span></span>  

<span data-ttu-id="b4543-105">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b4543-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b4543-106">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="b4543-106">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="b4543-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<izleme>**](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="b4543-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>\
<span data-ttu-id="b4543-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dinleyici ler>**</span><span class="sxs-lookup"><span data-stu-id="b4543-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<listeners>**</span></span>

## <a name="syntax"></a><span data-ttu-id="b4543-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b4543-109">Syntax</span></span>  
  
```xml  
<listeners>
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b4543-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b4543-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b4543-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b4543-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b4543-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b4543-112">Attributes</span></span>  
 <span data-ttu-id="b4543-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="b4543-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b4543-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b4543-114">Child Elements</span></span>  
  
|<span data-ttu-id="b4543-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="b4543-115">Element</span></span>|<span data-ttu-id="b4543-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b4543-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b4543-117">\<>ekleyin</span><span class="sxs-lookup"><span data-stu-id="b4543-117">\<add></span></span>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="b4543-118">`Listeners` Koleksiyona bir dinleyici ekler.</span><span class="sxs-lookup"><span data-stu-id="b4543-118">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="b4543-119">\<açık></span><span class="sxs-lookup"><span data-stu-id="b4543-119">\<clear></span></span>](clear-element-for-listeners-for-trace.md)|<span data-ttu-id="b4543-120">İzleme için `Listeners` koleksiyonu temizler.</span><span class="sxs-lookup"><span data-stu-id="b4543-120">Clears the `Listeners` collection for trace.</span></span>|  
|[<span data-ttu-id="b4543-121">\<>kaldırmak</span><span class="sxs-lookup"><span data-stu-id="b4543-121">\<remove></span></span>](remove-element-for-listeners-for-trace.md)|<span data-ttu-id="b4543-122">Dinleyiciyi `Listeners` koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="b4543-122">Removes a listener from the `Listeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b4543-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b4543-123">Parent Elements</span></span>  
  
|<span data-ttu-id="b4543-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="b4543-124">Element</span></span>|<span data-ttu-id="b4543-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b4543-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b4543-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="b4543-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="b4543-127">ASP.NET yapılandırma bölümünün kök öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b4543-127">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="b4543-128">İletileri toplayan, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="b4543-128">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4543-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b4543-129">Remarks</span></span>  
 <span data-ttu-id="b4543-130">Ve <xref:System.Diagnostics.Debug> <xref:System.Diagnostics.Trace> sınıflar aynı **Dinleyici** koleksiyonunu paylaşır.</span><span class="sxs-lookup"><span data-stu-id="b4543-130">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="b4543-131">Bu sınıflardan birinde koleksiyona bir dinleyici nesnesi eklerseniz, diğer sınıf aynı dinleyiciyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="b4543-131">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="b4543-132">.NET Framework ile gönderilen dinleyici sınıfları <xref:System.Diagnostics.TraceListener> sınıftan türetilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b4543-132">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="b4543-133">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="b4543-133">Configuration File</span></span>  
 <span data-ttu-id="b4543-134">Bu öğe makine yapılandırma dosyasında (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b4543-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4543-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="b4543-135">Example</span></span>  
 <span data-ttu-id="b4543-136">Aşağıdaki örnek, `MyListener` \*\* \<dinleyicileri ve\*\* **Dinleyicikoleksiyonunu** eklemek `MyEventListener` için dinleyici>öğenin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b4543-136">The following example shows how to use the **\<listeners>** element to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="b4543-137">`MyListener`adlı `MyListener.log` bir dosya oluşturur ve çıktıyı dosyaya yazar.</span><span class="sxs-lookup"><span data-stu-id="b4543-137">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="b4543-138">`MyEventListener`olay günlüğünde bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b4543-138">`MyEventListener` creates an entry in the event log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b4543-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b4543-139">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="b4543-140">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="b4543-140">Trace and Debug Settings Schema</span></span>](index.md)
