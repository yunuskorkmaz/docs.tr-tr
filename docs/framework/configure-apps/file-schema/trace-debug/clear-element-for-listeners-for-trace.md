---
title: <clear>İçin için öğesi <listeners><trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 2d301d588e33b0eea4164a6bf62dedd7b0c450ec
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149276"
---
# <a name="clear-element-for-listeners-for-trace"></a><span data-ttu-id="4e768-102">\<clear>İçin için öğesi \<listeners>\<trace></span><span class="sxs-lookup"><span data-stu-id="4e768-102">\<clear> Element for \<listeners> for \<trace></span></span>

<span data-ttu-id="4e768-103">`Listeners`İzleme için koleksiyonu temizler.</span><span class="sxs-lookup"><span data-stu-id="4e768-103">Clears the `Listeners` collection for trace.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="4e768-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="4e768-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4e768-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4e768-105">Attributes and Elements</span></span>  

 <span data-ttu-id="4e768-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4e768-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4e768-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4e768-107">Attributes</span></span>  

 <span data-ttu-id="4e768-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="4e768-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4e768-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4e768-109">Child Elements</span></span>  

 <span data-ttu-id="4e768-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="4e768-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4e768-111">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4e768-111">Parent Elements</span></span>  
  
|<span data-ttu-id="4e768-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="4e768-112">Element</span></span>|<span data-ttu-id="4e768-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4e768-113">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4e768-114">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="4e768-114">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="4e768-115">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4e768-115">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="4e768-116">İzleme iletilerini toplayıp depolayan, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="4e768-116">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="4e768-117">İletileri toplayacak, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="4e768-117">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="4e768-118">Dinleyiciler izleme çıkışını uygun bir hedefe yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="4e768-118">Listeners direct the tracing output to an appropriate target.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e768-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4e768-119">Remarks</span></span>  

 <span data-ttu-id="4e768-120">`<clear>`Öğesi, `Listeners` izleme için koleksiyondaki tüm dinleyicileri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="4e768-120">The `<clear>` element removes all listeners from the `Listeners` collection for trace.</span></span> <span data-ttu-id="4e768-121">`<clear>` `<add>` Koleksiyonda başka hiçbir etkin dinleyici bulunmadığından emin olmak için öğesini kullanmadan önce öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e768-121">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
 <span data-ttu-id="4e768-122">`Listeners` <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> Özelliği () üzerinde yöntemini çağırarak koleksiyonu programlı bir şekilde temizleyebilirsiniz <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> `System.Diagnostics.Trace.Listeners.Clear()` .</span><span class="sxs-lookup"><span data-stu-id="4e768-122">You can clear the `Listeners` collection programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> method on the <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> property (`System.Diagnostics.Trace.Listeners.Clear()`).</span></span>  
  
 <span data-ttu-id="4e768-123">Bu öğe makine yapılandırma dosyasında (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4e768-123">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4e768-124">Öğesi,,, `<clear>` <xref:System.Diagnostics.DefaultTraceListener> `Listeners` <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType> ve yöntemlerinin davranışını değiştirerek koleksiyonundan kaldırır <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="4e768-124">The `<clear>` element removes the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection, altering the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="4e768-125">Bir `Assert` veya `Fail` yöntemini çağırmak normalde bir ileti kutusunun görüntüsüne neden olur.</span><span class="sxs-lookup"><span data-stu-id="4e768-125">Calling an `Assert` or `Fail` method normally results in the display of a message box.</span></span> <span data-ttu-id="4e768-126">Ancak, koleksiyonda değilse ileti kutusu görüntülenmez <xref:System.Diagnostics.DefaultTraceListener> `Listeners` .</span><span class="sxs-lookup"><span data-stu-id="4e768-126">However, the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e768-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="4e768-127">Example</span></span>  

 <span data-ttu-id="4e768-128">Aşağıdaki örnek, öğesini `<clear>` `<add>` `console` izleme için koleksiyona eklemek üzere öğesini kullanmadan önce öğesinin nasıl kullanılacağını gösterir `Listeners` .</span><span class="sxs-lookup"><span data-stu-id="4e768-128">The following example shows how to use the `<clear>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for trace.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4e768-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e768-129">See also</span></span>

- <xref:System.Diagnostics.Trace.Listeners%2A>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="4e768-130">İzleme ve hata ayıklama ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="4e768-130">Trace and Debug Settings Schema</span></span>](index.md)
- [\<remove>](remove-element-for-listeners-for-trace.md)
- [<span data-ttu-id="4e768-131">İz Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="4e768-131">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
