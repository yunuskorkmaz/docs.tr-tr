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
ms.openlocfilehash: 02fd794eb7b7b7f46f7f7bc4e43036cb4a4758ed
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699178"
---
# <a name="trace-element"></a><span data-ttu-id="fcd1b-102">\<Trace > öğesi</span><span class="sxs-lookup"><span data-stu-id="fcd1b-102">\<trace> Element</span></span>
<span data-ttu-id="fcd1b-103">İzleme iletilerini toplayıp depolayan, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="fcd1b-103">Contains listeners that collect, store, and route tracing messages.</span></span>  
  
[<span data-ttu-id="fcd1b-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="fcd1b-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="fcd1b-105">[ **System. diagnostics\<** &nbsp;&nbsp;>](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="fcd1b-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="fcd1b-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<izleme >**</span><span class="sxs-lookup"><span data-stu-id="fcd1b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<trace>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcd1b-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fcd1b-107">Syntax</span></span>  
  
```xml  
<trace autoflush="true|false"   
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fcd1b-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fcd1b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="fcd1b-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fcd1b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fcd1b-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fcd1b-110">Attributes</span></span>  
  
|<span data-ttu-id="fcd1b-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fcd1b-111">Attribute</span></span>|<span data-ttu-id="fcd1b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fcd1b-112">Description</span></span>|  
|---------------|-----------------|  
|`autoflush`|<span data-ttu-id="fcd1b-113">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="fcd1b-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="fcd1b-114">İzleme dinleyicilerinin her yazma işleminden sonra çıktı arabelleğini otomatik olarak temizlemesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fcd1b-114">Specifies whether the trace listeners automatically flush the output buffer after every write operation.</span></span>|  
|`indentsize`|<span data-ttu-id="fcd1b-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="fcd1b-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="fcd1b-116">Girintilendirmek için boşluk sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fcd1b-116">Specifies the number of spaces to indent.</span></span>|  
|`useGlobalLock`|<span data-ttu-id="fcd1b-117">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="fcd1b-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="fcd1b-118">Genel kilidin kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fcd1b-118">Indicates whether the global lock should be used.</span></span>|  
  
## <a name="autoflush-attribute"></a><span data-ttu-id="fcd1b-119">Oto Temizleme özniteliği</span><span class="sxs-lookup"><span data-stu-id="fcd1b-119">autoflush Attribute</span></span>  
  
|<span data-ttu-id="fcd1b-120">Değer</span><span class="sxs-lookup"><span data-stu-id="fcd1b-120">Value</span></span>|<span data-ttu-id="fcd1b-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fcd1b-121">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="fcd1b-122">, Çıkış arabelleğini otomatik olarak temizlemez.</span><span class="sxs-lookup"><span data-stu-id="fcd1b-122">Does not automatically flush the output buffer.</span></span> <span data-ttu-id="fcd1b-123">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="fcd1b-123">This is the default.</span></span>|  
|`true`|<span data-ttu-id="fcd1b-124">Çıktı arabelleğini otomatik olarak temizler.</span><span class="sxs-lookup"><span data-stu-id="fcd1b-124">Automatically flushes the output buffer.</span></span>|  
  
## <a name="usegloballock-attribute"></a><span data-ttu-id="fcd1b-125">useGlobalLock özniteliği</span><span class="sxs-lookup"><span data-stu-id="fcd1b-125">useGlobalLock Attribute</span></span>  
  
|<span data-ttu-id="fcd1b-126">Değer</span><span class="sxs-lookup"><span data-stu-id="fcd1b-126">Value</span></span>|<span data-ttu-id="fcd1b-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fcd1b-127">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="fcd1b-128">Dinleyicisi iş parçacığı güvenli ise, genel kilidi kullanmaz; Aksi takdirde, genel kilidi kullanır.</span><span class="sxs-lookup"><span data-stu-id="fcd1b-128">Does not use the global lock if the listener is thread safe; otherwise, uses the global lock.</span></span>|  
|`true`|<span data-ttu-id="fcd1b-129">Dinleyicinin iş parçacığı güvenli olup olmamasına bakılmaksızın genel kilidi kullanır.</span><span class="sxs-lookup"><span data-stu-id="fcd1b-129">Uses the global lock regardless of whether the listener is thread safe.</span></span> <span data-ttu-id="fcd1b-130">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="fcd1b-130">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fcd1b-131">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fcd1b-131">Child Elements</span></span>  
  
|<span data-ttu-id="fcd1b-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="fcd1b-132">Element</span></span>|<span data-ttu-id="fcd1b-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fcd1b-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fcd1b-134">\<dinleyicileri ></span><span class="sxs-lookup"><span data-stu-id="fcd1b-134">\<listeners></span></span>](listeners-element-for-trace.md)|<span data-ttu-id="fcd1b-135">İletileri toplayan, depolayan ve yönlendiren bir dinleyici belirtir.</span><span class="sxs-lookup"><span data-stu-id="fcd1b-135">Specifies a listener that collects, stores, and routes messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fcd1b-136">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fcd1b-136">Parent Elements</span></span>  
  
|<span data-ttu-id="fcd1b-137">Öğe</span><span class="sxs-lookup"><span data-stu-id="fcd1b-137">Element</span></span>|<span data-ttu-id="fcd1b-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fcd1b-138">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="fcd1b-139">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="fcd1b-139">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="fcd1b-140">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fcd1b-140">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fcd1b-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="fcd1b-141">Example</span></span>  
 <span data-ttu-id="fcd1b-142">Aşağıdaki örnek, `Listeners` koleksiyonuna dinleyici `MyListener` eklemek için `<trace>` öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fcd1b-142">The following example shows how to use the `<trace>` element to add the listener `MyListener` to the `Listeners` collection.</span></span> <span data-ttu-id="fcd1b-143">`MyListener`, `MyListener.log` adlı bir dosya oluşturur ve çıktıyı dosyaya yazar.</span><span class="sxs-lookup"><span data-stu-id="fcd1b-143">`MyListener` creates a file that is named `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="fcd1b-144">`useGlobalLock` özniteliği, izleme dinleyicisi iş parçacığı güvenli ise, genel kilidin kullanılmasına neden olan `false`olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="fcd1b-144">The `useGlobalLock` attribute is set to `false`, which causes the global lock not to be used if the trace listener is thread safe.</span></span> <span data-ttu-id="fcd1b-145">`autoflush` özniteliği `true`olarak ayarlanır, bu da İzleme dinleyicisinin <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> yönteminin çağrılmasının ne olursa olsun dosyaya yazmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="fcd1b-145">The `autoflush` attribute is set to `true`, which causes the trace listener to write to the file regardless of whether the <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> method is called.</span></span> <span data-ttu-id="fcd1b-146">`indentsize` özniteliği 0 (sıfır) olarak ayarlanır ve bu, <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> yöntemi çağrıldığında dinleyicinin sıfır boşluk girintilemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="fcd1b-146">The `indentsize` attribute is set to 0 (zero), which causes the listener to indent zero spaces when the <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> method is called.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fcd1b-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fcd1b-147">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [<span data-ttu-id="fcd1b-148">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="fcd1b-148">Trace and Debug Settings Schema</span></span>](index.md)
