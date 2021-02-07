---
description: 'Daha fazla bilgi edinin: <trace> öğesi'
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
ms.openlocfilehash: 470bc300911656a9c9951e52e3883ba5c8b01c59
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750331"
---
# <a name="trace-element"></a><span data-ttu-id="b4032-103">\<trace> Öğesi</span><span class="sxs-lookup"><span data-stu-id="b4032-103">\<trace> Element</span></span>

<span data-ttu-id="b4032-104">İzleme iletilerini toplayıp depolayan, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="b4032-104">Contains listeners that collect, store, and route tracing messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<trace>**  
  
## <a name="syntax"></a><span data-ttu-id="b4032-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="b4032-105">Syntax</span></span>  
  
```xml  
<trace autoflush="true|false"
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b4032-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b4032-106">Attributes and Elements</span></span>  

 <span data-ttu-id="b4032-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b4032-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b4032-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b4032-108">Attributes</span></span>  
  
|<span data-ttu-id="b4032-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b4032-109">Attribute</span></span>|<span data-ttu-id="b4032-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b4032-110">Description</span></span>|  
|---------------|-----------------|  
|`autoflush`|<span data-ttu-id="b4032-111">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b4032-111">Optional attribute.</span></span><br /><br /> <span data-ttu-id="b4032-112">İzleme dinleyicilerinin her yazma işleminden sonra çıktı arabelleğini otomatik olarak temizlemesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b4032-112">Specifies whether the trace listeners automatically flush the output buffer after every write operation.</span></span>|  
|`indentsize`|<span data-ttu-id="b4032-113">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b4032-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="b4032-114">Girintilendirmek için boşluk sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b4032-114">Specifies the number of spaces to indent.</span></span>|  
|`useGlobalLock`|<span data-ttu-id="b4032-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b4032-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="b4032-116">Genel kilidin kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b4032-116">Indicates whether the global lock should be used.</span></span>|  
  
## <a name="autoflush-attribute"></a><span data-ttu-id="b4032-117">Oto Temizleme özniteliği</span><span class="sxs-lookup"><span data-stu-id="b4032-117">autoflush Attribute</span></span>  
  
|<span data-ttu-id="b4032-118">Değer</span><span class="sxs-lookup"><span data-stu-id="b4032-118">Value</span></span>|<span data-ttu-id="b4032-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b4032-119">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="b4032-120">, Çıkış arabelleğini otomatik olarak temizlemez.</span><span class="sxs-lookup"><span data-stu-id="b4032-120">Does not automatically flush the output buffer.</span></span> <span data-ttu-id="b4032-121">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="b4032-121">This is the default.</span></span>|  
|`true`|<span data-ttu-id="b4032-122">Çıktı arabelleğini otomatik olarak temizler.</span><span class="sxs-lookup"><span data-stu-id="b4032-122">Automatically flushes the output buffer.</span></span>|  
  
## <a name="usegloballock-attribute"></a><span data-ttu-id="b4032-123">useGlobalLock özniteliği</span><span class="sxs-lookup"><span data-stu-id="b4032-123">useGlobalLock Attribute</span></span>  
  
|<span data-ttu-id="b4032-124">Değer</span><span class="sxs-lookup"><span data-stu-id="b4032-124">Value</span></span>|<span data-ttu-id="b4032-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b4032-125">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="b4032-126">Dinleyicisi iş parçacığı güvenli ise, genel kilidi kullanmaz; Aksi takdirde, genel kilidi kullanır.</span><span class="sxs-lookup"><span data-stu-id="b4032-126">Does not use the global lock if the listener is thread safe; otherwise, uses the global lock.</span></span>|  
|`true`|<span data-ttu-id="b4032-127">Dinleyicinin iş parçacığı güvenli olup olmamasına bakılmaksızın genel kilidi kullanır.</span><span class="sxs-lookup"><span data-stu-id="b4032-127">Uses the global lock regardless of whether the listener is thread safe.</span></span> <span data-ttu-id="b4032-128">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="b4032-128">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b4032-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b4032-129">Child Elements</span></span>  
  
|<span data-ttu-id="b4032-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="b4032-130">Element</span></span>|<span data-ttu-id="b4032-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b4032-131">Description</span></span>|  
|-------------|-----------------|  
|[\<listeners>](listeners-element-for-trace.md)|<span data-ttu-id="b4032-132">İletileri toplayan, depolayan ve yönlendiren bir dinleyici belirtir.</span><span class="sxs-lookup"><span data-stu-id="b4032-132">Specifies a listener that collects, stores, and routes messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b4032-133">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b4032-133">Parent Elements</span></span>  
  
|<span data-ttu-id="b4032-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="b4032-134">Element</span></span>|<span data-ttu-id="b4032-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b4032-135">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b4032-136">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="b4032-136">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="b4032-137">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b4032-137">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b4032-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="b4032-138">Example</span></span>  

 <span data-ttu-id="b4032-139">Aşağıdaki örnek, bir `<trace>` dinleyicinin koleksiyona eklemek için öğesinin nasıl kullanılacağını gösterir `MyListener` `Listeners` .</span><span class="sxs-lookup"><span data-stu-id="b4032-139">The following example shows how to use the `<trace>` element to add the listener `MyListener` to the `Listeners` collection.</span></span> <span data-ttu-id="b4032-140">`MyListener` adlı bir dosya oluşturur `MyListener.log` ve çıktıyı dosyaya yazar.</span><span class="sxs-lookup"><span data-stu-id="b4032-140">`MyListener` creates a file that is named `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="b4032-141">`useGlobalLock`Özniteliği olarak ayarlanır `false` ; Bu, izleme dinleyicisi iş parçacığı güvenli ise genel kilidin kullanılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="b4032-141">The `useGlobalLock` attribute is set to `false`, which causes the global lock not to be used if the trace listener is thread safe.</span></span> <span data-ttu-id="b4032-142">`autoflush`Özniteliği olarak ayarlanır `true` ; Bu, İzleme dinleyicisinin, yöntemin çağrılmasının ne olursa olsun dosyaya yazmasına neden olur <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b4032-142">The `autoflush` attribute is set to `true`, which causes the trace listener to write to the file regardless of whether the <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> method is called.</span></span> <span data-ttu-id="b4032-143">`indentsize`Öznitelik 0 (sıfır) olarak ayarlanır, bu da yöntem çağrıldığında dinleyicinin sıfır boşluk girintilemesini sağlar <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b4032-143">The `indentsize` attribute is set to 0 (zero), which causes the listener to indent zero spaces when the <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> method is called.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b4032-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b4032-144">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [<span data-ttu-id="b4032-145">İzleme ve hata ayıklama ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="b4032-145">Trace and Debug Settings Schema</span></span>](index.md)
