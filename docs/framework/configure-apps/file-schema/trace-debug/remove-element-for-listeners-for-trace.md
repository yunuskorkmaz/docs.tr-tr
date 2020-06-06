---
title: <remove>İçin için öğesi <listeners><trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/remove
helpviewer_keywords:
- remove element
- <remove> element
ms.assetid: 9a5cd1b5-be1a-485f-8f0c-2890ad3ef3e0
ms.openlocfilehash: f06973ec30d5061e4a200d6bf7e68adcf6302018
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088844"
---
# <a name="remove-element-for-listeners-for-trace"></a><span data-ttu-id="e12be-102">\<remove>İçin için öğesi \<listeners>\<trace></span><span class="sxs-lookup"><span data-stu-id="e12be-102">\<remove> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="e12be-103">**Dinleyicileri** koleksiyondan bir dinleyiciyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e12be-103">Removes a listener from the **Listeners** collection.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="e12be-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e12be-104">Syntax</span></span>  
  
```xml  
<remove name="listener name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e12be-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e12be-105">Attributes and Elements</span></span>  
 <span data-ttu-id="e12be-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e12be-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e12be-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e12be-107">Attributes</span></span>  
  
|<span data-ttu-id="e12be-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e12be-108">Attribute</span></span>|<span data-ttu-id="e12be-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e12be-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e12be-110">**ada**</span><span class="sxs-lookup"><span data-stu-id="e12be-110">**name**</span></span>|<span data-ttu-id="e12be-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e12be-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="e12be-112">**Dinleyici koleksiyonundan kaldırılacak** dinleyicinin adı.</span><span class="sxs-lookup"><span data-stu-id="e12be-112">The name of the listener to remove from the **Listeners** collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e12be-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e12be-113">Child Elements</span></span>  
 <span data-ttu-id="e12be-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="e12be-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e12be-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e12be-115">Parent Elements</span></span>  
  
|<span data-ttu-id="e12be-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="e12be-116">Element</span></span>|<span data-ttu-id="e12be-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e12be-117">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e12be-118">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="e12be-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="e12be-119">İletileri toplayan, depolayan ve yönlendiren bir dinleyici belirtir.</span><span class="sxs-lookup"><span data-stu-id="e12be-119">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="e12be-120">Dinleyiciler izleme çıkışını uygun bir hedefe yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="e12be-120">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="e12be-121">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e12be-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="e12be-122">ASP.NET izleme hizmetini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="e12be-122">Configures the ASP.NET trace service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e12be-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e12be-123">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e12be-124">Koleksiyonundan kaldırma <xref:System.Diagnostics.DefaultTraceListener> ,,, `Listeners` <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType> ve <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> yöntemlerinin davranışını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="e12be-124">Removing the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection alters the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="e12be-125">`Assert`Ya da `Fail` yöntemini çağırmak normalde bir ileti kutusunun görüntülenmesine neden olur, ancak koleksiyonda değilse ileti kutusu görüntülenmez <xref:System.Diagnostics.DefaultTraceListener> `Listeners` .</span><span class="sxs-lookup"><span data-stu-id="e12be-125">Calling an `Assert` or `Fail` method normally results in the display of a message box, however the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e12be-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="e12be-126">Example</span></span>  
 <span data-ttu-id="e12be-127">Aşağıdaki örnek, izleme **dinleyicileri** koleksiyonundan varsayılan izleme dinleyicisinin nasıl kaldırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e12be-127">The following example shows how to remove the default trace listener from the trace **Listeners** collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e12be-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e12be-128">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [<span data-ttu-id="e12be-129">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="e12be-129">Trace and Debug Settings Schema</span></span>](index.md)
