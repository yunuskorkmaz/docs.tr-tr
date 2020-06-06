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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153172"
---
# <a name="trace-element"></a><span data-ttu-id="aea4e-102">\<trace> Öğesi</span><span class="sxs-lookup"><span data-stu-id="aea4e-102">\<trace> Element</span></span>
<span data-ttu-id="aea4e-103">İzleme iletilerini toplayıp depolayan, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="aea4e-103">Contains listeners that collect, store, and route tracing messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<trace>**  
  
## <a name="syntax"></a><span data-ttu-id="aea4e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aea4e-104">Syntax</span></span>  
  
```xml  
<trace autoflush="true|false"
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aea4e-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="aea4e-105">Attributes and Elements</span></span>  
 <span data-ttu-id="aea4e-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="aea4e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aea4e-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="aea4e-107">Attributes</span></span>  
  
|<span data-ttu-id="aea4e-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="aea4e-108">Attribute</span></span>|<span data-ttu-id="aea4e-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aea4e-109">Description</span></span>|  
|---------------|-----------------|  
|`autoflush`|<span data-ttu-id="aea4e-110">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="aea4e-110">Optional attribute.</span></span><br /><br /> <span data-ttu-id="aea4e-111">İzleme dinleyicilerinin her yazma işleminden sonra çıktı arabelleğini otomatik olarak temizlemesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="aea4e-111">Specifies whether the trace listeners automatically flush the output buffer after every write operation.</span></span>|  
|`indentsize`|<span data-ttu-id="aea4e-112">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="aea4e-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="aea4e-113">Girintilendirmek için boşluk sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="aea4e-113">Specifies the number of spaces to indent.</span></span>|  
|`useGlobalLock`|<span data-ttu-id="aea4e-114">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="aea4e-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="aea4e-115">Genel kilidin kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="aea4e-115">Indicates whether the global lock should be used.</span></span>|  
  
## <a name="autoflush-attribute"></a><span data-ttu-id="aea4e-116">Oto Temizleme özniteliği</span><span class="sxs-lookup"><span data-stu-id="aea4e-116">autoflush Attribute</span></span>  
  
|<span data-ttu-id="aea4e-117">Değer</span><span class="sxs-lookup"><span data-stu-id="aea4e-117">Value</span></span>|<span data-ttu-id="aea4e-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aea4e-118">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="aea4e-119">, Çıkış arabelleğini otomatik olarak temizlemez.</span><span class="sxs-lookup"><span data-stu-id="aea4e-119">Does not automatically flush the output buffer.</span></span> <span data-ttu-id="aea4e-120">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="aea4e-120">This is the default.</span></span>|  
|`true`|<span data-ttu-id="aea4e-121">Çıktı arabelleğini otomatik olarak temizler.</span><span class="sxs-lookup"><span data-stu-id="aea4e-121">Automatically flushes the output buffer.</span></span>|  
  
## <a name="usegloballock-attribute"></a><span data-ttu-id="aea4e-122">useGlobalLock özniteliği</span><span class="sxs-lookup"><span data-stu-id="aea4e-122">useGlobalLock Attribute</span></span>  
  
|<span data-ttu-id="aea4e-123">Değer</span><span class="sxs-lookup"><span data-stu-id="aea4e-123">Value</span></span>|<span data-ttu-id="aea4e-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aea4e-124">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="aea4e-125">Dinleyicisi iş parçacığı güvenli ise, genel kilidi kullanmaz; Aksi takdirde, genel kilidi kullanır.</span><span class="sxs-lookup"><span data-stu-id="aea4e-125">Does not use the global lock if the listener is thread safe; otherwise, uses the global lock.</span></span>|  
|`true`|<span data-ttu-id="aea4e-126">Dinleyicinin iş parçacığı güvenli olup olmamasına bakılmaksızın genel kilidi kullanır.</span><span class="sxs-lookup"><span data-stu-id="aea4e-126">Uses the global lock regardless of whether the listener is thread safe.</span></span> <span data-ttu-id="aea4e-127">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="aea4e-127">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aea4e-128">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="aea4e-128">Child Elements</span></span>  
  
|<span data-ttu-id="aea4e-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="aea4e-129">Element</span></span>|<span data-ttu-id="aea4e-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aea4e-130">Description</span></span>|  
|-------------|-----------------|  
|[\<listeners>](listeners-element-for-trace.md)|<span data-ttu-id="aea4e-131">İletileri toplayan, depolayan ve yönlendiren bir dinleyici belirtir.</span><span class="sxs-lookup"><span data-stu-id="aea4e-131">Specifies a listener that collects, stores, and routes messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="aea4e-132">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="aea4e-132">Parent Elements</span></span>  
  
|<span data-ttu-id="aea4e-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="aea4e-133">Element</span></span>|<span data-ttu-id="aea4e-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aea4e-134">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="aea4e-135">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="aea4e-135">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="aea4e-136">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="aea4e-136">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="aea4e-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="aea4e-137">Example</span></span>  
 <span data-ttu-id="aea4e-138">Aşağıdaki örnek, bir `<trace>` dinleyicinin koleksiyona eklemek için öğesinin nasıl kullanılacağını gösterir `MyListener` `Listeners` .</span><span class="sxs-lookup"><span data-stu-id="aea4e-138">The following example shows how to use the `<trace>` element to add the listener `MyListener` to the `Listeners` collection.</span></span> <span data-ttu-id="aea4e-139">`MyListener`adlı bir dosya oluşturur `MyListener.log` ve çıktıyı dosyaya yazar.</span><span class="sxs-lookup"><span data-stu-id="aea4e-139">`MyListener` creates a file that is named `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="aea4e-140">`useGlobalLock`Özniteliği olarak ayarlanır `false` ; Bu, izleme dinleyicisi iş parçacığı güvenli ise genel kilidin kullanılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="aea4e-140">The `useGlobalLock` attribute is set to `false`, which causes the global lock not to be used if the trace listener is thread safe.</span></span> <span data-ttu-id="aea4e-141">`autoflush`Özniteliği olarak ayarlanır `true` ; Bu, İzleme dinleyicisinin, yöntemin çağrılmasının ne olursa olsun dosyaya yazmasına neden olur <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="aea4e-141">The `autoflush` attribute is set to `true`, which causes the trace listener to write to the file regardless of whether the <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> method is called.</span></span> <span data-ttu-id="aea4e-142">`indentsize`Öznitelik 0 (sıfır) olarak ayarlanır, bu da yöntem çağrıldığında dinleyicinin sıfır boşluk girintilemesini sağlar <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="aea4e-142">The `indentsize` attribute is set to 0 (zero), which causes the listener to indent zero spaces when the <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> method is called.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="aea4e-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aea4e-143">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [<span data-ttu-id="aea4e-144">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="aea4e-144">Trace and Debug Settings Schema</span></span>](index.md)
