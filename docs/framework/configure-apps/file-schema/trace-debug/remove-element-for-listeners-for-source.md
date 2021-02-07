---
description: 'Hakkında daha fazla bilgi edinin: için <remove> öğesi <listeners><source>'
title: <remove>İçin için öğesi <listeners><source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
ms.openlocfilehash: 2f7a815fe97fda95d71bc2a5a1b8fdda7bc2a0ed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750630"
---
# <a name="remove-element-for-listeners-for-source"></a><span data-ttu-id="0b175-103">\<remove>İçin için öğesi \<listeners>\<source></span><span class="sxs-lookup"><span data-stu-id="0b175-103">\<remove> Element for \<listeners> for \<source></span></span>

<span data-ttu-id="0b175-104">`Listeners`İzleme kaynağı için koleksiyondan bir dinleyiciyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="0b175-104">Removes a listener from the `Listeners` collection for a trace source.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="0b175-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0b175-105">Syntax</span></span>  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0b175-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0b175-106">Attributes and Elements</span></span>  

 <span data-ttu-id="0b175-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0b175-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0b175-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0b175-108">Attributes</span></span>  
  
|<span data-ttu-id="0b175-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0b175-109">Attribute</span></span>|<span data-ttu-id="0b175-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b175-110">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="0b175-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0b175-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="0b175-112">Koleksiyondan kaldırılacak dinleyicinin adı `Listeners` .</span><span class="sxs-lookup"><span data-stu-id="0b175-112">The name of the listener to remove from the `Listeners` collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0b175-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0b175-113">Child Elements</span></span>  

 <span data-ttu-id="0b175-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="0b175-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0b175-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0b175-115">Parent Elements</span></span>  
  
|<span data-ttu-id="0b175-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="0b175-116">Element</span></span>|<span data-ttu-id="0b175-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b175-117">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0b175-118">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="0b175-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="0b175-119">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0b175-119">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="0b175-120">İzleme iletilerini Başlatan izleme kaynaklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="0b175-120">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="0b175-121">İzleme iletilerini Başlatan bir izleme kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0b175-121">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="0b175-122">İletileri toplayacak, depolayan ve yönlendiren dinleyicileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="0b175-122">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b175-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0b175-123">Remarks</span></span>  

 <span data-ttu-id="0b175-124">`<remove>`Öğesi, `Listeners` bir izleme kaynağı için belirtilen dinleyiciyi koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="0b175-124">The `<remove>` element removes a specified listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="0b175-125">`Listeners` <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> Örnek özelliği üzerinde yöntemini çağırarak bir izleme kaynağı için koleksiyondan bir öğeyi programlı bir şekilde kaldırabilirsiniz <xref:System.Diagnostics.TraceSource.Listeners%2A> <xref:System.Diagnostics.TraceSource> .</span><span class="sxs-lookup"><span data-stu-id="0b175-125">You can remove an element from the `Listeners` collection for a trace source programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> method on the <xref:System.Diagnostics.TraceSource.Listeners%2A> property of the <xref:System.Diagnostics.TraceSource> instance.</span></span>  
  
 <span data-ttu-id="0b175-126">Bu öğe makine yapılandırma dosyasında (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0b175-126">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b175-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="0b175-127">Example</span></span>  

 <span data-ttu-id="0b175-128">Aşağıdaki örnek, öğesini `<remove>` `<add>` `console` `Listeners` izleme kaynağı koleksiyonuna eklemek için öğesini kullanmadan önce öğesinin nasıl kullanılacağını gösterir `TraceSourceApp` .</span><span class="sxs-lookup"><span data-stu-id="0b175-128">The following example shows how to use the `<remove>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"
         switchType="System.Diagnostics.SourceSwitch" >  
         <listeners>  
           <remove name="Default"/>  
           <add name="console"
             type="System.Diagnostics.ConsoleTraceListener" />  
         </listeners>  
      </source>  
    </sources>  
  </system.diagnostics>  
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="0b175-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b175-129">See also</span></span>

- <xref:System.Diagnostics.TraceSource.Listeners%2A>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="0b175-130">İzleme ve hata ayıklama ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="0b175-130">Trace and Debug Settings Schema</span></span>](index.md)
- [\<clear>](clear-element-for-listeners-for-source.md)
- [<span data-ttu-id="0b175-131">İz Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="0b175-131">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
