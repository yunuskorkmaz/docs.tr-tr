---
title: <trace> için <listeners> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
ms.openlocfilehash: fd12be1b775d7611ef3f16d23147470313bf9866
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153379"
---
# <a name="listeners-element-for-trace"></a><span data-ttu-id="728c2-102">\<trace> için \<listeners> Öğesi</span><span class="sxs-lookup"><span data-stu-id="728c2-102">\<listeners> Element for \<trace></span></span>
<span data-ttu-id="728c2-103">İletileri toplayan, depolayan ve yönlendiren bir dinleyici belirtir.</span><span class="sxs-lookup"><span data-stu-id="728c2-103">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="728c2-104">Dinleyiciler izleme çıkışını uygun bir hedefe yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="728c2-104">Listeners direct the tracing output to an appropriate target.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<listeners>**

## <a name="syntax"></a><span data-ttu-id="728c2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="728c2-105">Syntax</span></span>  
  
```xml  
<listeners>
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="728c2-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="728c2-106">Attributes and Elements</span></span>  
 <span data-ttu-id="728c2-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="728c2-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="728c2-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="728c2-108">Attributes</span></span>  
 <span data-ttu-id="728c2-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="728c2-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="728c2-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="728c2-110">Child Elements</span></span>  
  
|<span data-ttu-id="728c2-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="728c2-111">Element</span></span>|<span data-ttu-id="728c2-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="728c2-112">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="728c2-113">Koleksiyona bir dinleyici ekler `Listeners` .</span><span class="sxs-lookup"><span data-stu-id="728c2-113">Adds a listener to the `Listeners` collection.</span></span>|  
|[\<clear>](clear-element-for-listeners-for-trace.md)|<span data-ttu-id="728c2-114">`Listeners`İzleme için koleksiyonu temizler.</span><span class="sxs-lookup"><span data-stu-id="728c2-114">Clears the `Listeners` collection for trace.</span></span>|  
|[\<remove>](remove-element-for-listeners-for-trace.md)|<span data-ttu-id="728c2-115">Koleksiyondan bir dinleyiciyi kaldırır `Listeners` .</span><span class="sxs-lookup"><span data-stu-id="728c2-115">Removes a listener from the `Listeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="728c2-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="728c2-116">Parent Elements</span></span>  
  
|<span data-ttu-id="728c2-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="728c2-117">Element</span></span>|<span data-ttu-id="728c2-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="728c2-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="728c2-119">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="728c2-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="728c2-120">ASP.NET yapılandırma bölümünün kök öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="728c2-120">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="728c2-121">İzleme iletilerini toplayıp depolayan, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="728c2-121">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="728c2-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="728c2-122">Remarks</span></span>  
 <span data-ttu-id="728c2-123"><xref:System.Diagnostics.Debug>Ve <xref:System.Diagnostics.Trace> sınıfları aynı **dinleyicileri** toplamayı paylaşır.</span><span class="sxs-lookup"><span data-stu-id="728c2-123">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="728c2-124">Bu sınıflardan birindeki koleksiyona bir dinleyici nesnesi eklerseniz, diğer sınıf aynı dinleyiciyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="728c2-124">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="728c2-125">.NET Framework ile birlikte gelen dinleyici sınıfları <xref:System.Diagnostics.TraceListener> sınıfından türetilir.</span><span class="sxs-lookup"><span data-stu-id="728c2-125">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="728c2-126">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="728c2-126">Configuration File</span></span>  
 <span data-ttu-id="728c2-127">Bu öğe makine yapılandırma dosyasında (Machine. config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="728c2-127">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="728c2-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="728c2-128">Example</span></span>  
 <span data-ttu-id="728c2-129">Aşağıdaki örnek, **\<listeners>** dinleyicileri `MyListener` ve `MyEventListener` **dinleyici** koleksiyonuna eklemek için öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="728c2-129">The following example shows how to use the **\<listeners>** element to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="728c2-130">`MyListener`adlı bir dosya oluşturur `MyListener.log` ve çıktıyı dosyaya yazar.</span><span class="sxs-lookup"><span data-stu-id="728c2-130">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="728c2-131">`MyEventListener`olay günlüğünde bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="728c2-131">`MyEventListener` creates an entry in the event log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="728c2-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="728c2-132">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="728c2-133">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="728c2-133">Trace and Debug Settings Schema</span></span>](index.md)
