---
title: <trace> için <listeners> <remove> öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/remove
helpviewer_keywords:
- remove element
- <remove> element
ms.assetid: 9a5cd1b5-be1a-485f-8f0c-2890ad3ef3e0
ms.openlocfilehash: f06973ec30d5061e4a200d6bf7e68adcf6302018
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088844"
---
# <a name="remove-element-for-listeners-for-trace"></a><span data-ttu-id="e75a8-102">\<Trace için \<Listeners > > öğesi \<kaldırın ></span><span class="sxs-lookup"><span data-stu-id="e75a8-102">\<remove> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="e75a8-103">**Dinleyicileri** koleksiyondan bir dinleyiciyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e75a8-103">Removes a listener from the **Listeners** collection.</span></span>  

<span data-ttu-id="e75a8-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="e75a8-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e75a8-105">[**System. diagnostics\<** ](system-diagnostics-element.md) &nbsp;&nbsp;</span><span class="sxs-lookup"><span data-stu-id="e75a8-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="e75a8-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<izleme >** ](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="e75a8-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>\
<span data-ttu-id="e75a8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dinleyicileri >** ](listeners-element-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="e75a8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)</span></span>\
<span data-ttu-id="e75a8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<kaldır >**</span><span class="sxs-lookup"><span data-stu-id="e75a8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="e75a8-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e75a8-109">Syntax</span></span>  
  
```xml  
<remove name="listener name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e75a8-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e75a8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e75a8-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e75a8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e75a8-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e75a8-112">Attributes</span></span>  
  
|<span data-ttu-id="e75a8-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e75a8-113">Attribute</span></span>|<span data-ttu-id="e75a8-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e75a8-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e75a8-115">**ada**</span><span class="sxs-lookup"><span data-stu-id="e75a8-115">**name**</span></span>|<span data-ttu-id="e75a8-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e75a8-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="e75a8-117">**Dinleyici koleksiyonundan kaldırılacak** dinleyicinin adı.</span><span class="sxs-lookup"><span data-stu-id="e75a8-117">The name of the listener to remove from the **Listeners** collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e75a8-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e75a8-118">Child Elements</span></span>  
 <span data-ttu-id="e75a8-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="e75a8-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e75a8-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e75a8-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e75a8-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="e75a8-121">Element</span></span>|<span data-ttu-id="e75a8-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e75a8-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e75a8-123">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="e75a8-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="e75a8-124">İletileri toplayan, depolayan ve yönlendiren bir dinleyici belirtir.</span><span class="sxs-lookup"><span data-stu-id="e75a8-124">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="e75a8-125">Dinleyiciler izleme çıkışını uygun bir hedefe yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="e75a8-125">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="e75a8-126">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e75a8-126">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="e75a8-127">ASP.NET izleme hizmetini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="e75a8-127">Configures the ASP.NET trace service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e75a8-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e75a8-128">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e75a8-129">`Listeners` koleksiyonundan <xref:System.Diagnostics.DefaultTraceListener> kaldırmak <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>ve <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> yöntemlerinin davranışını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="e75a8-129">Removing the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection alters the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="e75a8-130">Bir `Assert` veya `Fail` yöntemini çağırmak normalde bir ileti kutusunun görüntülenmesine neden olur, ancak <xref:System.Diagnostics.DefaultTraceListener> `Listeners` koleksiyonunda değilse ileti kutusu görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="e75a8-130">Calling an `Assert` or `Fail` method normally results in the display of a message box, however the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e75a8-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="e75a8-131">Example</span></span>  
 <span data-ttu-id="e75a8-132">Aşağıdaki örnek, izleme **dinleyicileri** koleksiyonundan varsayılan izleme dinleyicisinin nasıl kaldırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e75a8-132">The following example shows how to remove the default trace listener from the trace **Listeners** collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e75a8-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e75a8-133">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [<span data-ttu-id="e75a8-134">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="e75a8-134">Trace and Debug Settings Schema</span></span>](index.md)
