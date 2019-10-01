---
title: <trace> için <listeners> <clear> öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 0361580724351f8f42d058d5e20354e3335bac2f
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699376"
---
# <a name="clear-element-for-listeners-for-trace"></a><span data-ttu-id="4080c-102">\<trace için \<listeners > için \<clear > öğesi ></span><span class="sxs-lookup"><span data-stu-id="4080c-102">\<clear> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="4080c-103">İzleme için `Listeners` koleksiyonunu temizler.</span><span class="sxs-lookup"><span data-stu-id="4080c-103">Clears the `Listeners` collection for trace.</span></span>  
  
[<span data-ttu-id="4080c-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="4080c-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="4080c-105">&nbsp; @ no__t-1[ **\<system. Diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="4080c-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="4080c-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<trace >** ](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="4080c-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>  
<span data-ttu-id="4080c-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<listeners >** ](listeners-element-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="4080c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)</span></span>  
<span data-ttu-id="4080c-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 **\<clear >**</span><span class="sxs-lookup"><span data-stu-id="4080c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4080c-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4080c-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4080c-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4080c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4080c-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4080c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4080c-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4080c-112">Attributes</span></span>  
 <span data-ttu-id="4080c-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="4080c-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4080c-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4080c-114">Child Elements</span></span>  
 <span data-ttu-id="4080c-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="4080c-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4080c-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4080c-116">Parent Elements</span></span>  
  
|<span data-ttu-id="4080c-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="4080c-117">Element</span></span>|<span data-ttu-id="4080c-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4080c-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4080c-119">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="4080c-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="4080c-120">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4080c-120">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="4080c-121">İzleme iletilerini toplayıp depolayan, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="4080c-121">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="4080c-122">İletileri toplayacak, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="4080c-122">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="4080c-123">Dinleyiciler izleme çıkışını uygun bir hedefe yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="4080c-123">Listeners direct the tracing output to an appropriate target.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4080c-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4080c-124">Remarks</span></span>  
 <span data-ttu-id="4080c-125">@No__t-0 öğesi, izleme için `Listeners` koleksiyonundan tüm dinleyicileri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="4080c-125">The `<clear>` element removes all listeners from the `Listeners` collection for trace.</span></span> <span data-ttu-id="4080c-126">Koleksiyonda başka hiçbir etkin dinleyici bulunmadığından emin olmak için `<add>` öğesini kullanmadan önce `<clear>` öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4080c-126">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
 <span data-ttu-id="4080c-127">@No__t-0 koleksiyonunu <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> özelliği (`System.Diagnostics.Trace.Listeners.Clear()`) üzerinde <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> yöntemini çağırarak programlı bir şekilde temizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4080c-127">You can clear the `Listeners` collection programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> method on the <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> property (`System.Diagnostics.Trace.Listeners.Clear()`).</span></span>  
  
 <span data-ttu-id="4080c-128">Bu öğe makine yapılandırma dosyasında (Machine. config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4080c-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4080c-129">@No__t-0 öğesi, <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType> ve <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> yöntemlerinin davranışını değiştirerek `Listeners` koleksiyonundan <xref:System.Diagnostics.DefaultTraceListener> ' i kaldırır.</span><span class="sxs-lookup"><span data-stu-id="4080c-129">The `<clear>` element removes the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection, altering the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="4080c-130">@No__t-0 veya `Fail` yöntemini çağırmak normalde bir ileti kutusunun görüntüsüne neden olur.</span><span class="sxs-lookup"><span data-stu-id="4080c-130">Calling an `Assert` or `Fail` method normally results in the display of a message box.</span></span> <span data-ttu-id="4080c-131">Ancak, <xref:System.Diagnostics.DefaultTraceListener> `Listeners` koleksiyonunda değilse ileti kutusu görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="4080c-131">However, the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4080c-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="4080c-132">Example</span></span>  
 <span data-ttu-id="4080c-133">Aşağıdaki örnek, izleme için `Listeners` koleksiyonuna `console` dinleyicisini eklemek üzere `<add>` öğesi kullanılmadan önce `<clear>` öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4080c-133">The following example shows how to use the `<clear>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for trace.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4080c-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4080c-134">See also</span></span>

- <xref:System.Diagnostics.Trace.Listeners%2A>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="4080c-135">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="4080c-135">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="4080c-136">\<remove ></span><span class="sxs-lookup"><span data-stu-id="4080c-136">\<remove></span></span>](remove-element-for-listeners-for-trace.md)
- [<span data-ttu-id="4080c-137">İzleme Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="4080c-137">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
