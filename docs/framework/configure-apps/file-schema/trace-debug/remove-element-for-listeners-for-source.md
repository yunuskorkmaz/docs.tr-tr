---
title: <source> için <listeners> <remove> öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
ms.openlocfilehash: 4a11308278f755ec8271477352d91d8797d105c5
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699494"
---
# <a name="remove-element-for-listeners-for-source"></a><span data-ttu-id="be619-102">\<source > için \<listeners > için \<> öğesini kaldırın</span><span class="sxs-lookup"><span data-stu-id="be619-102">\<remove> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="be619-103">İzleme kaynağı için `Listeners` koleksiyonundan bir dinleyiciyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="be619-103">Removes a listener from the `Listeners` collection for a trace source.</span></span>  
  
[<span data-ttu-id="be619-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="be619-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="be619-105">&nbsp; @ no__t-1[ **\<system. Diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="be619-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="be619-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<sources >** ](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="be619-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>  
<span data-ttu-id="be619-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<source >** ](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="be619-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>  
<span data-ttu-id="be619-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7[ **&nbsp;0listeners >** ](listeners-element-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="be619-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)</span></span>  
<span data-ttu-id="be619-109">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 @ no__t-8 @ no__t-9 **&nbsp;1remove >**</span><span class="sxs-lookup"><span data-stu-id="be619-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be619-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="be619-110">Syntax</span></span>  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="be619-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="be619-111">Attributes and Elements</span></span>  
 <span data-ttu-id="be619-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="be619-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="be619-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="be619-113">Attributes</span></span>  
  
|<span data-ttu-id="be619-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="be619-114">Attribute</span></span>|<span data-ttu-id="be619-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="be619-115">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="be619-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="be619-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="be619-117">@No__t-0 koleksiyonundan kaldırılacak dinleyicinin adı.</span><span class="sxs-lookup"><span data-stu-id="be619-117">The name of the listener to remove from the `Listeners` collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="be619-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="be619-118">Child Elements</span></span>  
 <span data-ttu-id="be619-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="be619-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="be619-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="be619-120">Parent Elements</span></span>  
  
|<span data-ttu-id="be619-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="be619-121">Element</span></span>|<span data-ttu-id="be619-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="be619-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="be619-123">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="be619-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="be619-124">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="be619-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="be619-125">İzleme iletilerini Başlatan izleme kaynaklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="be619-125">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="be619-126">İzleme iletilerini Başlatan bir izleme kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="be619-126">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="be619-127">İletileri toplayacak, depolayan ve yönlendiren dinleyicileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="be619-127">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be619-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="be619-128">Remarks</span></span>  
 <span data-ttu-id="be619-129">@No__t-0 öğesi, izleme kaynağı için `Listeners` koleksiyonundan belirtilen dinleyiciyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="be619-129">The `<remove>` element removes a specified listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="be619-130">@No__t-3 örneğinin <xref:System.Diagnostics.TraceSource.Listeners%2A> özelliğinde <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> metodunu çağırarak, izleme kaynağı için `Listeners` koleksiyonundan bir öğeyi kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="be619-130">You can remove an element from the `Listeners` collection for a trace source programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> method on the <xref:System.Diagnostics.TraceSource.Listeners%2A> property of the <xref:System.Diagnostics.TraceSource> instance.</span></span>  
  
 <span data-ttu-id="be619-131">Bu öğe makine yapılandırma dosyasında (Machine. config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="be619-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="be619-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="be619-132">Example</span></span>  
 <span data-ttu-id="be619-133">Aşağıdaki örnek, `TraceSourceApp` ' ü izleme kaynağı için `Listeners` koleksiyonuna `console` dinleyicisini eklemek için `<add>` öğesini kullanmadan önce `<remove>` öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="be619-133">The following example shows how to use the `<remove>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="be619-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be619-134">See also</span></span>

- <xref:System.Diagnostics.TraceSource.Listeners%2A>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="be619-135">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="be619-135">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="be619-136">\<clear ></span><span class="sxs-lookup"><span data-stu-id="be619-136">\<clear></span></span>](clear-element-for-listeners-for-source.md)
- [<span data-ttu-id="be619-137">İzleme Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="be619-137">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
