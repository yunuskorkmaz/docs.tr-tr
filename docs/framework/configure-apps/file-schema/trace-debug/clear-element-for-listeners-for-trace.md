---
title: <clear><listeners> Için element<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 905dad8274fede80f4809ff3c7a014049f9df450
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153548"
---
# <a name="clear-element-for-listeners-for-trace"></a><span data-ttu-id="d2a61-102">\<izleme> \<için> \<dinleyiciler için açık> Element</span><span class="sxs-lookup"><span data-stu-id="d2a61-102">\<clear> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="d2a61-103">İzleme için `Listeners` koleksiyonu temizler.</span><span class="sxs-lookup"><span data-stu-id="d2a61-103">Clears the `Listeners` collection for trace.</span></span>  

<span data-ttu-id="d2a61-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d2a61-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d2a61-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="d2a61-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="d2a61-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<izleme>**](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="d2a61-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>\
<span data-ttu-id="d2a61-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dinleyici ler>**](listeners-element-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="d2a61-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)</span></span>\
<span data-ttu-id="d2a61-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<açık>**</span><span class="sxs-lookup"><span data-stu-id="d2a61-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="d2a61-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d2a61-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d2a61-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d2a61-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d2a61-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d2a61-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d2a61-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d2a61-112">Attributes</span></span>  
 <span data-ttu-id="d2a61-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="d2a61-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d2a61-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d2a61-114">Child Elements</span></span>  
 <span data-ttu-id="d2a61-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="d2a61-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d2a61-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d2a61-116">Parent Elements</span></span>  
  
|<span data-ttu-id="d2a61-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="d2a61-117">Element</span></span>|<span data-ttu-id="d2a61-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d2a61-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d2a61-119">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="d2a61-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="d2a61-120">İletileri toplayan, depolayan ve yönlendiren izleme dinleyicilerini ve izleme anahtarının ayarlandığı düzeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2a61-120">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="d2a61-121">İletileri toplayan, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="d2a61-121">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="d2a61-122">İletileri toplayan, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="d2a61-122">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="d2a61-123">Dinleyiciler izleme çıktısını uygun bir hedefe yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="d2a61-123">Listeners direct the tracing output to an appropriate target.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2a61-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d2a61-124">Remarks</span></span>  
 <span data-ttu-id="d2a61-125">Öğe `<clear>` izleme için `Listeners` koleksiyondaki tüm dinleyicileri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d2a61-125">The `<clear>` element removes all listeners from the `Listeners` collection for trace.</span></span> <span data-ttu-id="d2a61-126">Koleksiyonda başka `<clear>` etkin dinleyici `<add>` olmadığından emin olmak için öğeyi kullanmadan önce öğeyi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2a61-126">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
 <span data-ttu-id="d2a61-127">Toplamayı, `Listeners` <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> özellikteki yöntemi arayarak programlı olarak`System.Diagnostics.Trace.Listeners.Clear()`temizleyebilirsiniz ( ).</span><span class="sxs-lookup"><span data-stu-id="d2a61-127">You can clear the `Listeners` collection programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> method on the <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> property (`System.Diagnostics.Trace.Listeners.Clear()`).</span></span>  
  
 <span data-ttu-id="d2a61-128">Bu öğe makine yapılandırma dosyasında (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d2a61-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d2a61-129">`Listeners` Öğe, `<clear>` , <xref:System.Diagnostics.DefaultTraceListener> <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, ve <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> yöntemleri davranışını değiştirerek, koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d2a61-129">The `<clear>` element removes the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection, altering the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="d2a61-130">Bir `Assert` veya `Fail` yöntemin çağrılmak normalde bir ileti kutusunun görüntülenmesine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="d2a61-130">Calling an `Assert` or `Fail` method normally results in the display of a message box.</span></span> <span data-ttu-id="d2a61-131">Ancak, `Listeners` koleksiyonda yoksa ileti <xref:System.Diagnostics.DefaultTraceListener> kutusu görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="d2a61-131">However, the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2a61-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="d2a61-132">Example</span></span>  
 <span data-ttu-id="d2a61-133">`<clear>` Aşağıdaki örnek, dinleyiciyi `<add>` `console` izleme için koleksiyona eklemek için öğeyi kullanmadan önce öğenin nasıl kullanılacağını `Listeners` gösterir.</span><span class="sxs-lookup"><span data-stu-id="d2a61-133">The following example shows how to use the `<clear>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for trace.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <clear/>  
        <add name="console"
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"
            initializeData="Error" />  
        </add>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="d2a61-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2a61-134">See also</span></span>

- <xref:System.Diagnostics.Trace.Listeners%2A>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="d2a61-135">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="d2a61-135">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d2a61-136">\<>kaldırmak</span><span class="sxs-lookup"><span data-stu-id="d2a61-136">\<remove></span></span>](remove-element-for-listeners-for-trace.md)
- [<span data-ttu-id="d2a61-137">İz Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="d2a61-137">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
