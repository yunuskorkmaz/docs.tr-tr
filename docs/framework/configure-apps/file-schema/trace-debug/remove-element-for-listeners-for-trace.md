---
title: <remove> Öğe için <listeners> için <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/remove
helpviewer_keywords:
- remove element
- <remove> element
ms.assetid: 9a5cd1b5-be1a-485f-8f0c-2890ad3ef3e0
ms.openlocfilehash: adf00394bc0bfe808836e74214003cd2078204e4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59164261"
---
# <a name="remove-element-for-listeners-for-trace"></a><span data-ttu-id="d8fb4-102">\<kaldırma > öğesi için \<dinleyicileri > için \<İzleme ></span><span class="sxs-lookup"><span data-stu-id="d8fb4-102">\<remove> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="d8fb4-103">Bir dinleyicisinden kaldırır **dinleyicileri** koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d8fb4-103">Removes a listener from the **Listeners** collection.</span></span>  
  
 <span data-ttu-id="d8fb4-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="d8fb4-104">\<configuration></span></span>  
<span data-ttu-id="d8fb4-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="d8fb4-105">\<system.diagnostics></span></span>  
<span data-ttu-id="d8fb4-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="d8fb4-106">\<trace></span></span>  
<span data-ttu-id="d8fb4-107">\<dinleyicileri ></span><span class="sxs-lookup"><span data-stu-id="d8fb4-107">\<listeners></span></span>  
<span data-ttu-id="d8fb4-108">\<kaldırma ></span><span class="sxs-lookup"><span data-stu-id="d8fb4-108">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8fb4-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8fb4-109">Syntax</span></span>  
  
```xml  
<remove name="listener name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d8fb4-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d8fb4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d8fb4-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d8fb4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d8fb4-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d8fb4-112">Attributes</span></span>  
  
|<span data-ttu-id="d8fb4-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d8fb4-113">Attribute</span></span>|<span data-ttu-id="d8fb4-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d8fb4-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d8fb4-115">**Adı**</span><span class="sxs-lookup"><span data-stu-id="d8fb4-115">**name**</span></span>|<span data-ttu-id="d8fb4-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d8fb4-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="d8fb4-117">Dinleyiciyi kaldırmak için adını **dinleyicileri** koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d8fb4-117">The name of the listener to remove from the **Listeners** collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d8fb4-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d8fb4-118">Child Elements</span></span>  
 <span data-ttu-id="d8fb4-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="d8fb4-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d8fb4-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d8fb4-120">Parent Elements</span></span>  
  
|<span data-ttu-id="d8fb4-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="d8fb4-121">Element</span></span>|<span data-ttu-id="d8fb4-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d8fb4-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d8fb4-123">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="d8fb4-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="d8fb4-124">Toplar, depolar, bir dinleyici belirtir ve iletileri yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="d8fb4-124">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="d8fb4-125">Dinleyicileri bir uygun hedef izleme çıkışa doğrudan.</span><span class="sxs-lookup"><span data-stu-id="d8fb4-125">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="d8fb4-126">Toplamak, depolamak ve iletileri ve bir izleme anahtarı ayarlandığı düzeyi izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d8fb4-126">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="d8fb4-127">ASP.NET izleme hizmetini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="d8fb4-127">Configures the ASP.NET trace service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8fb4-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8fb4-128">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d8fb4-129">Kaldırma <xref:System.Diagnostics.DefaultTraceListener> gelen `Listeners` koleksiyon davranışını değiştiren <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, ve <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="d8fb4-129">Removing the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection alters the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="d8fb4-130">Çağırma bir `Assert` veya `Fail` yöntemi ileti kutusu görüntülenmez ancak görüntülenen bir ileti kutusu normalde sonuçlanır <xref:System.Diagnostics.DefaultTraceListener> kullanımda olmayan `Listeners` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d8fb4-130">Calling an `Assert` or `Fail` method normally results in the display of a message box, however the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8fb4-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="d8fb4-131">Example</span></span>  
 <span data-ttu-id="d8fb4-132">Aşağıdaki örnek, varsayılan izleme Dinleyicide izlemesinden kaldırmak gösterilmektedir **dinleyicileri** koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d8fb4-132">The following example shows how to remove the default trace listener from the trace **Listeners** collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d8fb4-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8fb4-133">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [<span data-ttu-id="d8fb4-134">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="d8fb4-134">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
