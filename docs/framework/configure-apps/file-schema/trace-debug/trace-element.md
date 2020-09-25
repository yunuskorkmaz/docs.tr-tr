---
title: <trace> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace
- http://schemas.microsoft.com/.NetConfiguration/v2.0#trace
helpviewer_keywords:
- <trace> element
- listeners
- trace element
- trace listener, <trace> element
ms.assetid: 7931c942-63c1-47c3-a045-9d9de3cacdbf
ms.openlocfilehash: 617b42a0be2be272a78b33be997cce632d1c6dcb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198931"
---
# <a name="trace-element"></a><span data-ttu-id="6f29c-102">\<trace> Öğesi</span><span class="sxs-lookup"><span data-stu-id="6f29c-102">\<trace> Element</span></span>

<span data-ttu-id="6f29c-103">İzleme iletilerini toplayıp depolayan, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="6f29c-103">Contains listeners that collect, store, and route tracing messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<trace>**  
  
## <a name="syntax"></a><span data-ttu-id="6f29c-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="6f29c-104">Syntax</span></span>  
  
```xml  
<trace autoflush="true|false"
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6f29c-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6f29c-105">Attributes and Elements</span></span>  

 <span data-ttu-id="6f29c-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6f29c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6f29c-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6f29c-107">Attributes</span></span>  
  
|<span data-ttu-id="6f29c-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6f29c-108">Attribute</span></span>|<span data-ttu-id="6f29c-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f29c-109">Description</span></span>|  
|---------------|-----------------|  
|`autoflush`|<span data-ttu-id="6f29c-110">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6f29c-110">Optional attribute.</span></span><br /><br /> <span data-ttu-id="6f29c-111">İzleme dinleyicilerinin her yazma işleminden sonra çıktı arabelleğini otomatik olarak temizlemesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f29c-111">Specifies whether the trace listeners automatically flush the output buffer after every write operation.</span></span>|  
|`indentsize`|<span data-ttu-id="6f29c-112">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6f29c-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="6f29c-113">Girintilendirmek için boşluk sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f29c-113">Specifies the number of spaces to indent.</span></span>|  
|`useGlobalLock`|<span data-ttu-id="6f29c-114">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6f29c-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="6f29c-115">Genel kilidin kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f29c-115">Indicates whether the global lock should be used.</span></span>|  
  
## <a name="autoflush-attribute"></a><span data-ttu-id="6f29c-116">Oto Temizleme özniteliği</span><span class="sxs-lookup"><span data-stu-id="6f29c-116">autoflush Attribute</span></span>  
  
|<span data-ttu-id="6f29c-117">Değer</span><span class="sxs-lookup"><span data-stu-id="6f29c-117">Value</span></span>|<span data-ttu-id="6f29c-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f29c-118">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="6f29c-119">, Çıkış arabelleğini otomatik olarak temizlemez.</span><span class="sxs-lookup"><span data-stu-id="6f29c-119">Does not automatically flush the output buffer.</span></span> <span data-ttu-id="6f29c-120">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="6f29c-120">This is the default.</span></span>|  
|`true`|<span data-ttu-id="6f29c-121">Çıktı arabelleğini otomatik olarak temizler.</span><span class="sxs-lookup"><span data-stu-id="6f29c-121">Automatically flushes the output buffer.</span></span>|  
  
## <a name="usegloballock-attribute"></a><span data-ttu-id="6f29c-122">useGlobalLock özniteliği</span><span class="sxs-lookup"><span data-stu-id="6f29c-122">useGlobalLock Attribute</span></span>  
  
|<span data-ttu-id="6f29c-123">Değer</span><span class="sxs-lookup"><span data-stu-id="6f29c-123">Value</span></span>|<span data-ttu-id="6f29c-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f29c-124">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="6f29c-125">Dinleyicisi iş parçacığı güvenli ise, genel kilidi kullanmaz; Aksi takdirde, genel kilidi kullanır.</span><span class="sxs-lookup"><span data-stu-id="6f29c-125">Does not use the global lock if the listener is thread safe; otherwise, uses the global lock.</span></span>|  
|`true`|<span data-ttu-id="6f29c-126">Dinleyicinin iş parçacığı güvenli olup olmamasına bakılmaksızın genel kilidi kullanır.</span><span class="sxs-lookup"><span data-stu-id="6f29c-126">Uses the global lock regardless of whether the listener is thread safe.</span></span> <span data-ttu-id="6f29c-127">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="6f29c-127">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6f29c-128">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6f29c-128">Child Elements</span></span>  
  
|<span data-ttu-id="6f29c-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="6f29c-129">Element</span></span>|<span data-ttu-id="6f29c-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f29c-130">Description</span></span>|  
|-------------|-----------------|  
|[\<listeners>](listeners-element-for-trace.md)|<span data-ttu-id="6f29c-131">İletileri toplayan, depolayan ve yönlendiren bir dinleyici belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f29c-131">Specifies a listener that collects, stores, and routes messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6f29c-132">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6f29c-132">Parent Elements</span></span>  
  
|<span data-ttu-id="6f29c-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="6f29c-133">Element</span></span>|<span data-ttu-id="6f29c-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f29c-134">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6f29c-135">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="6f29c-135">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="6f29c-136">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f29c-136">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6f29c-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="6f29c-137">Example</span></span>  

 <span data-ttu-id="6f29c-138">Aşağıdaki örnek, bir `<trace>` dinleyicinin koleksiyona eklemek için öğesinin nasıl kullanılacağını gösterir `MyListener` `Listeners` .</span><span class="sxs-lookup"><span data-stu-id="6f29c-138">The following example shows how to use the `<trace>` element to add the listener `MyListener` to the `Listeners` collection.</span></span> <span data-ttu-id="6f29c-139">`MyListener` adlı bir dosya oluşturur `MyListener.log` ve çıktıyı dosyaya yazar.</span><span class="sxs-lookup"><span data-stu-id="6f29c-139">`MyListener` creates a file that is named `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="6f29c-140">`useGlobalLock`Özniteliği olarak ayarlanır `false` ; Bu, izleme dinleyicisi iş parçacığı güvenli ise genel kilidin kullanılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="6f29c-140">The `useGlobalLock` attribute is set to `false`, which causes the global lock not to be used if the trace listener is thread safe.</span></span> <span data-ttu-id="6f29c-141">`autoflush`Özniteliği olarak ayarlanır `true` ; Bu, İzleme dinleyicisinin, yöntemin çağrılmasının ne olursa olsun dosyaya yazmasına neden olur <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6f29c-141">The `autoflush` attribute is set to `true`, which causes the trace listener to write to the file regardless of whether the <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> method is called.</span></span> <span data-ttu-id="6f29c-142">`indentsize`Öznitelik 0 (sıfır) olarak ayarlanır, bu da yöntem çağrıldığında dinleyicinin sıfır boşluk girintilemesini sağlar <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6f29c-142">The `indentsize` attribute is set to 0 (zero), which causes the listener to indent zero spaces when the <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> method is called.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace useGlobalLock="false" autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6f29c-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f29c-143">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [<span data-ttu-id="6f29c-144">İzleme ve hata ayıklama ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="6f29c-144">Trace and Debug Settings Schema</span></span>](index.md)
