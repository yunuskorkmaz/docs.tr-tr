---
title: <trace> için <listeners> <remove> öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/remove
helpviewer_keywords:
- remove element
- <remove> element
ms.assetid: 9a5cd1b5-be1a-485f-8f0c-2890ad3ef3e0
ms.openlocfilehash: 56d1e56514aed98d5f3b9f7363e461af6ac68a8c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697213"
---
# <a name="remove-element-for-listeners-for-trace"></a><span data-ttu-id="ff032-102">\<trace için \<listeners > için \<> öğesini kaldırın ></span><span class="sxs-lookup"><span data-stu-id="ff032-102">\<remove> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="ff032-103">**Dinleyicileri** koleksiyondan bir dinleyiciyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ff032-103">Removes a listener from the **Listeners** collection.</span></span>  
  
[<span data-ttu-id="ff032-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="ff032-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="ff032-105">&nbsp; @ no__t-1[ **\<system. Diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="ff032-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="ff032-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<trace >** ](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="ff032-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>  
<span data-ttu-id="ff032-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<listeners >** ](listeners-element-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="ff032-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)</span></span>  
<span data-ttu-id="ff032-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 **\<remove >**</span><span class="sxs-lookup"><span data-stu-id="ff032-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff032-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ff032-109">Syntax</span></span>  
  
```xml  
<remove name="listener name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ff032-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ff032-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ff032-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ff032-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ff032-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ff032-112">Attributes</span></span>  
  
|<span data-ttu-id="ff032-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ff032-113">Attribute</span></span>|<span data-ttu-id="ff032-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ff032-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ff032-115">**ada**</span><span class="sxs-lookup"><span data-stu-id="ff032-115">**name**</span></span>|<span data-ttu-id="ff032-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="ff032-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="ff032-117">**Dinleyici koleksiyonundan kaldırılacak** dinleyicinin adı.</span><span class="sxs-lookup"><span data-stu-id="ff032-117">The name of the listener to remove from the **Listeners** collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ff032-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ff032-118">Child Elements</span></span>  
 <span data-ttu-id="ff032-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="ff032-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ff032-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ff032-120">Parent Elements</span></span>  
  
|<span data-ttu-id="ff032-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="ff032-121">Element</span></span>|<span data-ttu-id="ff032-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ff032-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ff032-123">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="ff032-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="ff032-124">İletileri toplayan, depolayan ve yönlendiren bir dinleyici belirtir.</span><span class="sxs-lookup"><span data-stu-id="ff032-124">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="ff032-125">Dinleyiciler izleme çıkışını uygun bir hedefe yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="ff032-125">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="ff032-126">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ff032-126">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="ff032-127">ASP.NET izleme hizmetini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="ff032-127">Configures the ASP.NET trace service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff032-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ff032-128">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ff032-129">@No__t-1 koleksiyonundan <xref:System.Diagnostics.DefaultTraceListener> ' ı kaldırmak, <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType> ve <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> yöntemlerinin davranışını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="ff032-129">Removing the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection alters the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="ff032-130">@No__t-0 veya `Fail` yönteminin çağrılması normalde bir ileti kutusunun görüntülenmesine neden olur, ancak <xref:System.Diagnostics.DefaultTraceListener> `Listeners` koleksiyonunda değilse ileti kutusu görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="ff032-130">Calling an `Assert` or `Fail` method normally results in the display of a message box, however the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff032-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="ff032-131">Example</span></span>  
 <span data-ttu-id="ff032-132">Aşağıdaki örnek, izleme **dinleyicileri** koleksiyonundan varsayılan izleme dinleyicisinin nasıl kaldırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ff032-132">The following example shows how to remove the default trace listener from the trace **Listeners** collection.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace autoflush="true" indentsize="0">  
         <listeners>  
            <remove name="Default" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ff032-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff032-133">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [<span data-ttu-id="ff032-134">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="ff032-134">Trace and Debug Settings Schema</span></span>](index.md)
