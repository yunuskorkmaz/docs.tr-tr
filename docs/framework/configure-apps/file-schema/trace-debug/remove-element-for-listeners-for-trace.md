---
title: '&lt;kaldırma&gt; öğesi için &lt;dinleyicileri&gt; için &lt;izleme&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/remove
helpviewer_keywords:
- remove element
- <remove> element
ms.assetid: 9a5cd1b5-be1a-485f-8f0c-2890ad3ef3e0
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 54fd529c571c8e8cf43c5dabe2398ae4a6cf4f11
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47088964"
---
# <a name="ltremovegt-element-for-ltlistenersgt-for-lttracegt"></a><span data-ttu-id="da810-102">&lt;kaldırma&gt; öğesi için &lt;dinleyicileri&gt; için &lt;izleme&gt;</span><span class="sxs-lookup"><span data-stu-id="da810-102">&lt;remove&gt; Element for &lt;listeners&gt; for &lt;trace&gt;</span></span>
<span data-ttu-id="da810-103">Bir dinleyicisinden kaldırır **dinleyicileri** koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="da810-103">Removes a listener from the **Listeners** collection.</span></span>  
  
 <span data-ttu-id="da810-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="da810-104">\<configuration></span></span>  
<span data-ttu-id="da810-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="da810-105">\<system.diagnostics></span></span>  
<span data-ttu-id="da810-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="da810-106">\<trace></span></span>  
<span data-ttu-id="da810-107">\<dinleyicileri ></span><span class="sxs-lookup"><span data-stu-id="da810-107">\<listeners></span></span>  
<span data-ttu-id="da810-108">\<kaldırma ></span><span class="sxs-lookup"><span data-stu-id="da810-108">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da810-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="da810-109">Syntax</span></span>  
  
```xml  
<remove name="listener name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="da810-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="da810-110">Attributes and Elements</span></span>  
 <span data-ttu-id="da810-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="da810-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="da810-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="da810-112">Attributes</span></span>  
  
|<span data-ttu-id="da810-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="da810-113">Attribute</span></span>|<span data-ttu-id="da810-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="da810-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="da810-115">**Adı**</span><span class="sxs-lookup"><span data-stu-id="da810-115">**name**</span></span>|<span data-ttu-id="da810-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="da810-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="da810-117">Dinleyiciyi kaldırmak için adını **dinleyicileri** koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="da810-117">The name of the listener to remove from the **Listeners** collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="da810-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="da810-118">Child Elements</span></span>  
 <span data-ttu-id="da810-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="da810-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="da810-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="da810-120">Parent Elements</span></span>  
  
|<span data-ttu-id="da810-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="da810-121">Element</span></span>|<span data-ttu-id="da810-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="da810-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="da810-123">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="da810-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="da810-124">Toplar, depolar, bir dinleyici belirtir ve iletileri yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="da810-124">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="da810-125">Dinleyicileri bir uygun hedef izleme çıkışa doğrudan.</span><span class="sxs-lookup"><span data-stu-id="da810-125">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="da810-126">Toplamak, depolamak ve iletileri ve bir izleme anahtarı ayarlandığı düzeyi izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="da810-126">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="da810-127">ASP.NET izleme hizmetini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="da810-127">Configures the ASP.NET trace service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da810-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="da810-128">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da810-129">Kaldırma <xref:System.Diagnostics.DefaultTraceListener> gelen `Listeners` koleksiyon davranışını değiştiren <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, ve <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="da810-129">Removing the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection alters the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="da810-130">Çağırma bir `Assert` veya `Fail` yöntemi ileti kutusu görüntülenmez ancak görüntülenen bir ileti kutusu normalde sonuçlanır <xref:System.Diagnostics.DefaultTraceListener> kullanımda olmayan `Listeners` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="da810-130">Calling an `Assert` or `Fail` method normally results in the display of a message box, however the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da810-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="da810-131">Example</span></span>  
 <span data-ttu-id="da810-132">Aşağıdaki örnek, varsayılan izleme Dinleyicide izlemesinden kaldırmak gösterilmektedir **dinleyicileri** koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="da810-132">The following example shows how to remove the default trace listener from the trace **Listeners** collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="da810-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="da810-133">See Also</span></span>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 [<span data-ttu-id="da810-134">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="da810-134">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
