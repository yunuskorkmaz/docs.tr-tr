---
description: 'Hakkında daha fazla bilgi edinin: için <clear> öğesi <listeners><trace>'
title: <clear>İçin için öğesi <listeners><trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 3c1b3816f4ccd0ceb9e9bc0fc6acfd9b6e8ade85
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725980"
---
# <a name="clear-element-for-listeners-for-trace"></a><span data-ttu-id="583ce-103">\<clear>İçin için öğesi \<listeners>\<trace></span><span class="sxs-lookup"><span data-stu-id="583ce-103">\<clear> Element for \<listeners> for \<trace></span></span>

<span data-ttu-id="583ce-104">`Listeners`İzleme için koleksiyonu temizler.</span><span class="sxs-lookup"><span data-stu-id="583ce-104">Clears the `Listeners` collection for trace.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="583ce-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="583ce-105">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="583ce-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="583ce-106">Attributes and Elements</span></span>  

 <span data-ttu-id="583ce-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="583ce-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="583ce-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="583ce-108">Attributes</span></span>  

 <span data-ttu-id="583ce-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="583ce-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="583ce-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="583ce-110">Child Elements</span></span>  

 <span data-ttu-id="583ce-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="583ce-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="583ce-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="583ce-112">Parent Elements</span></span>  
  
|<span data-ttu-id="583ce-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="583ce-113">Element</span></span>|<span data-ttu-id="583ce-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="583ce-114">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="583ce-115">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="583ce-115">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="583ce-116">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="583ce-116">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="583ce-117">İzleme iletilerini toplayıp depolayan, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="583ce-117">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="583ce-118">İletileri toplayacak, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="583ce-118">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="583ce-119">Dinleyiciler izleme çıkışını uygun bir hedefe yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="583ce-119">Listeners direct the tracing output to an appropriate target.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="583ce-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="583ce-120">Remarks</span></span>  

 <span data-ttu-id="583ce-121">`<clear>`Öğesi, `Listeners` izleme için koleksiyondaki tüm dinleyicileri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="583ce-121">The `<clear>` element removes all listeners from the `Listeners` collection for trace.</span></span> <span data-ttu-id="583ce-122">`<clear>` `<add>` Koleksiyonda başka hiçbir etkin dinleyici bulunmadığından emin olmak için öğesini kullanmadan önce öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="583ce-122">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
 <span data-ttu-id="583ce-123">`Listeners` <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> Özelliği () üzerinde yöntemini çağırarak koleksiyonu programlı bir şekilde temizleyebilirsiniz <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> `System.Diagnostics.Trace.Listeners.Clear()` .</span><span class="sxs-lookup"><span data-stu-id="583ce-123">You can clear the `Listeners` collection programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> method on the <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> property (`System.Diagnostics.Trace.Listeners.Clear()`).</span></span>  
  
 <span data-ttu-id="583ce-124">Bu öğe makine yapılandırma dosyasında (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="583ce-124">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="583ce-125">Öğesi,,, `<clear>` <xref:System.Diagnostics.DefaultTraceListener> `Listeners` <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType> ve yöntemlerinin davranışını değiştirerek koleksiyonundan kaldırır <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="583ce-125">The `<clear>` element removes the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection, altering the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="583ce-126">Bir `Assert` veya `Fail` yöntemini çağırmak normalde bir ileti kutusunun görüntüsüne neden olur.</span><span class="sxs-lookup"><span data-stu-id="583ce-126">Calling an `Assert` or `Fail` method normally results in the display of a message box.</span></span> <span data-ttu-id="583ce-127">Ancak, koleksiyonda değilse ileti kutusu görüntülenmez <xref:System.Diagnostics.DefaultTraceListener> `Listeners` .</span><span class="sxs-lookup"><span data-stu-id="583ce-127">However, the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="583ce-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="583ce-128">Example</span></span>  

 <span data-ttu-id="583ce-129">Aşağıdaki örnek, öğesini `<clear>` `<add>` `console` izleme için koleksiyona eklemek üzere öğesini kullanmadan önce öğesinin nasıl kullanılacağını gösterir `Listeners` .</span><span class="sxs-lookup"><span data-stu-id="583ce-129">The following example shows how to use the `<clear>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for trace.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="583ce-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="583ce-130">See also</span></span>

- <xref:System.Diagnostics.Trace.Listeners%2A>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="583ce-131">İzleme ve hata ayıklama ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="583ce-131">Trace and Debug Settings Schema</span></span>](index.md)
- [\<remove>](remove-element-for-listeners-for-trace.md)
- [<span data-ttu-id="583ce-132">İz Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="583ce-132">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
