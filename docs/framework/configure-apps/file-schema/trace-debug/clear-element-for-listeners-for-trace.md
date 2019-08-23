---
title: <clear>İçin için <listeners> öğesi<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 9816ba0f8e4ddd4c38537eb4e014a4240ff20407
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927179"
---
# <a name="clear-element-for-listeners-for-trace"></a><span data-ttu-id="0bfa8-102">\<izleme için \< \<dinleyiciler > > öğeyi Temizle ></span><span class="sxs-lookup"><span data-stu-id="0bfa8-102">\<clear> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="0bfa8-103">İzleme için `Listeners` koleksiyonu temizler.</span><span class="sxs-lookup"><span data-stu-id="0bfa8-103">Clears the `Listeners` collection for trace.</span></span>  
  
 <span data-ttu-id="0bfa8-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="0bfa8-104">\<configuration></span></span>  
<span data-ttu-id="0bfa8-105">\<System. Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="0bfa8-105">\<system.diagnostics></span></span>  
<span data-ttu-id="0bfa8-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="0bfa8-106">\<trace></span></span>  
<span data-ttu-id="0bfa8-107">\<dinleyiciler ></span><span class="sxs-lookup"><span data-stu-id="0bfa8-107">\<listeners></span></span>  
<span data-ttu-id="0bfa8-108">\<> Temizle</span><span class="sxs-lookup"><span data-stu-id="0bfa8-108">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bfa8-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0bfa8-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0bfa8-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0bfa8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0bfa8-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0bfa8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0bfa8-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0bfa8-112">Attributes</span></span>  
 <span data-ttu-id="0bfa8-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="0bfa8-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0bfa8-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0bfa8-114">Child Elements</span></span>  
 <span data-ttu-id="0bfa8-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="0bfa8-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0bfa8-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0bfa8-116">Parent Elements</span></span>  
  
|<span data-ttu-id="0bfa8-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="0bfa8-117">Element</span></span>|<span data-ttu-id="0bfa8-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0bfa8-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0bfa8-119">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="0bfa8-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="0bfa8-120">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0bfa8-120">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="0bfa8-121">İzleme iletilerini toplayıp depolayan, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="0bfa8-121">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="0bfa8-122">İletileri toplayacak, depolayan ve yönlendiren dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="0bfa8-122">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="0bfa8-123">Dinleyiciler izleme çıkışını uygun bir hedefe yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="0bfa8-123">Listeners direct the tracing output to an appropriate target.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0bfa8-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0bfa8-124">Remarks</span></span>  
 <span data-ttu-id="0bfa8-125">Öğesi `<clear>` , izleme için `Listeners` koleksiyondaki tüm dinleyicileri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="0bfa8-125">The `<clear>` element removes all listeners from the `Listeners` collection for trace.</span></span> <span data-ttu-id="0bfa8-126">Koleksiyonda başka hiçbir etkin `<clear>` dinleyici bulunmadığından emin olmak `<add>` için öğesini kullanmadan önce öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0bfa8-126">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
 <span data-ttu-id="0bfa8-127">`Listeners` <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> Özelliği(`System.Diagnostics.Trace.Listeners.Clear()`) üzerinde yöntemini çağırarak koleksiyonu programlı bir şekilde temizleyebilirsiniz. <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="0bfa8-127">You can clear the `Listeners` collection programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> method on the <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> property (`System.Diagnostics.Trace.Listeners.Clear()`).</span></span>  
  
 <span data-ttu-id="0bfa8-128">Bu öğe makine yapılandırma dosyasında (Machine. config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0bfa8-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0bfa8-129"><xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.DefaultTraceListener> `Listeners` Öğesi,<xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>,, ve yöntemlerinindavranışını<xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>değiştirerek koleksiyonundan kaldırır. <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> `<clear>`</span><span class="sxs-lookup"><span data-stu-id="0bfa8-129">The `<clear>` element removes the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection, altering the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="0bfa8-130">Bir `Assert` veya`Fail` yöntemini çağırmak normalde bir ileti kutusunun görüntüsüne neden olur.</span><span class="sxs-lookup"><span data-stu-id="0bfa8-130">Calling an `Assert` or `Fail` method normally results in the display of a message box.</span></span> <span data-ttu-id="0bfa8-131">Ancak, <xref:System.Diagnostics.DefaultTraceListener> `Listeners` koleksiyonda değilse ileti kutusu görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="0bfa8-131">However, the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bfa8-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="0bfa8-132">Example</span></span>  
 <span data-ttu-id="0bfa8-133">Aşağıdaki örnek, öğesini `<clear>` izleme için `Listeners` koleksiyona eklemek `console` üzere `<add>` öğesini kullanmadan önce öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0bfa8-133">The following example shows how to use the `<clear>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for trace.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0bfa8-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0bfa8-134">See also</span></span>

- <xref:System.Diagnostics.Trace.Listeners%2A>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="0bfa8-135">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="0bfa8-135">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="0bfa8-136">\<> Kaldır</span><span class="sxs-lookup"><span data-stu-id="0bfa8-136">\<remove></span></span>](remove-element-for-listeners-for-trace.md)
- [<span data-ttu-id="0bfa8-137">İzleme Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="0bfa8-137">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
