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
ms.openlocfilehash: 7d8a989219d84e8604e767456c84c0092bc73b22
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153172"
---
# <a name="trace-element"></a><span data-ttu-id="a0ef7-102">\<izleme> Öğesi</span><span class="sxs-lookup"><span data-stu-id="a0ef7-102">\<trace> Element</span></span>
<span data-ttu-id="a0ef7-103">İletileri toplayan, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="a0ef7-103">Contains listeners that collect, store, and route tracing messages.</span></span>  
  
[<span data-ttu-id="a0ef7-104">**\<yapılandırma>**</span><span class="sxs-lookup"><span data-stu-id="a0ef7-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="a0ef7-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="a0ef7-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="a0ef7-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<izleme>**</span><span class="sxs-lookup"><span data-stu-id="a0ef7-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<trace>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0ef7-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a0ef7-107">Syntax</span></span>  
  
```xml  
<trace autoflush="true|false"
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a0ef7-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a0ef7-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a0ef7-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a0ef7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a0ef7-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a0ef7-110">Attributes</span></span>  
  
|<span data-ttu-id="a0ef7-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a0ef7-111">Attribute</span></span>|<span data-ttu-id="a0ef7-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0ef7-112">Description</span></span>|  
|---------------|-----------------|  
|`autoflush`|<span data-ttu-id="a0ef7-113">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a0ef7-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a0ef7-114">İzleme dinleyicilerinin her yazma işleminden sonra çıktı arabelleği otomatik olarak sifonu çekip çıkarmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a0ef7-114">Specifies whether the trace listeners automatically flush the output buffer after every write operation.</span></span>|  
|`indentsize`|<span data-ttu-id="a0ef7-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a0ef7-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a0ef7-116">Girinecek alanların sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a0ef7-116">Specifies the number of spaces to indent.</span></span>|  
|`useGlobalLock`|<span data-ttu-id="a0ef7-117">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a0ef7-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a0ef7-118">Genel kilidin kullanılıp kullanılmayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a0ef7-118">Indicates whether the global lock should be used.</span></span>|  
  
## <a name="autoflush-attribute"></a><span data-ttu-id="a0ef7-119">autoflush Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a0ef7-119">autoflush Attribute</span></span>  
  
|<span data-ttu-id="a0ef7-120">Değer</span><span class="sxs-lookup"><span data-stu-id="a0ef7-120">Value</span></span>|<span data-ttu-id="a0ef7-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0ef7-121">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="a0ef7-122">Çıktı arabelleği otomatik olarak sifonu çekmez.</span><span class="sxs-lookup"><span data-stu-id="a0ef7-122">Does not automatically flush the output buffer.</span></span> <span data-ttu-id="a0ef7-123">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="a0ef7-123">This is the default.</span></span>|  
|`true`|<span data-ttu-id="a0ef7-124">Çıkış arabelleği otomatik olarak temize çıkar.</span><span class="sxs-lookup"><span data-stu-id="a0ef7-124">Automatically flushes the output buffer.</span></span>|  
  
## <a name="usegloballock-attribute"></a><span data-ttu-id="a0ef7-125">globallock özniteliğini kullanma</span><span class="sxs-lookup"><span data-stu-id="a0ef7-125">useGlobalLock Attribute</span></span>  
  
|<span data-ttu-id="a0ef7-126">Değer</span><span class="sxs-lookup"><span data-stu-id="a0ef7-126">Value</span></span>|<span data-ttu-id="a0ef7-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0ef7-127">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="a0ef7-128">Dinleyici iş parçacığı güvenliyse genel kilidi kullanmaz; aksi takdirde, genel kilidi kullanır.</span><span class="sxs-lookup"><span data-stu-id="a0ef7-128">Does not use the global lock if the listener is thread safe; otherwise, uses the global lock.</span></span>|  
|`true`|<span data-ttu-id="a0ef7-129">Dinleyicinin iş parçacığı nın güvenli olup olmadığına bakılmaksızın genel kilidi kullanır.</span><span class="sxs-lookup"><span data-stu-id="a0ef7-129">Uses the global lock regardless of whether the listener is thread safe.</span></span> <span data-ttu-id="a0ef7-130">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="a0ef7-130">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a0ef7-131">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a0ef7-131">Child Elements</span></span>  
  
|<span data-ttu-id="a0ef7-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="a0ef7-132">Element</span></span>|<span data-ttu-id="a0ef7-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0ef7-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a0ef7-134">\<dinleyici ler></span><span class="sxs-lookup"><span data-stu-id="a0ef7-134">\<listeners></span></span>](listeners-element-for-trace.md)|<span data-ttu-id="a0ef7-135">İletileri toplayan, depolayan ve gönderen bir dinleyici belirtir.</span><span class="sxs-lookup"><span data-stu-id="a0ef7-135">Specifies a listener that collects, stores, and routes messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a0ef7-136">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a0ef7-136">Parent Elements</span></span>  
  
|<span data-ttu-id="a0ef7-137">Öğe</span><span class="sxs-lookup"><span data-stu-id="a0ef7-137">Element</span></span>|<span data-ttu-id="a0ef7-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0ef7-138">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a0ef7-139">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="a0ef7-139">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="a0ef7-140">İletileri toplayan, depolayan ve yönlendiren izleme dinleyicilerini ve izleme anahtarının ayarlandığı düzeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="a0ef7-140">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a0ef7-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="a0ef7-141">Example</span></span>  
 <span data-ttu-id="a0ef7-142">Aşağıdaki örnek, dinleyiciyi `<trace>` `MyListener` koleksiyona eklemek için öğenin nasıl kullanılacağını `Listeners` gösterir.</span><span class="sxs-lookup"><span data-stu-id="a0ef7-142">The following example shows how to use the `<trace>` element to add the listener `MyListener` to the `Listeners` collection.</span></span> <span data-ttu-id="a0ef7-143">`MyListener`adlı `MyListener.log` bir dosya oluşturur ve çıktıyı dosyaya yazar.</span><span class="sxs-lookup"><span data-stu-id="a0ef7-143">`MyListener` creates a file that is named `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="a0ef7-144">Öznitelik, `useGlobalLock` izleme `false`dinleyicisi iş parçacığı güvenliyse, genel kilidin kullanılmaması için gereken enitelik olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="a0ef7-144">The `useGlobalLock` attribute is set to `false`, which causes the global lock not to be used if the trace listener is thread safe.</span></span> <span data-ttu-id="a0ef7-145">`true`Öznitelik, <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> `autoflush` izleme dinleyicisinin yöntemin çağrılıp çağrılmadığına bakılmaksızın dosyaya yazmasına neden olan olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="a0ef7-145">The `autoflush` attribute is set to `true`, which causes the trace listener to write to the file regardless of whether the <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> method is called.</span></span> <span data-ttu-id="a0ef7-146">Öznitelik `indentsize` 0 (sıfır) olarak ayarlanır ve bu da dinleyicinin <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> yöntem çağrıldığında girinal sıfır boşluklarına neden olur.</span><span class="sxs-lookup"><span data-stu-id="a0ef7-146">The `indentsize` attribute is set to 0 (zero), which causes the listener to indent zero spaces when the <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> method is called.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a0ef7-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0ef7-147">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [<span data-ttu-id="a0ef7-148">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="a0ef7-148">Trace and Debug Settings Schema</span></span>](index.md)
