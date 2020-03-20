---
title: <remove><listeners> Için element<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
ms.openlocfilehash: 657e6db2af9b99b3bbf03afc6aab02c58a830f2d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153341"
---
# <a name="remove-element-for-listeners-for-source"></a><span data-ttu-id="4e1af-102">\<kaynak> \<için> \<dinleyiciler için> Öğesi kaldırmak</span><span class="sxs-lookup"><span data-stu-id="4e1af-102">\<remove> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="4e1af-103">İzleme kaynağı için dinleyiciyi `Listeners` koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="4e1af-103">Removes a listener from the `Listeners` collection for a trace source.</span></span>  

<span data-ttu-id="4e1af-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4e1af-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4e1af-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="4e1af-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="4e1af-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<kaynaklar>**](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="4e1af-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>\
<span data-ttu-id="4e1af-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<kaynak>**](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="4e1af-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>\
<span data-ttu-id="4e1af-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dinleyici ler>**](listeners-element-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="4e1af-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)</span></span>\
<span data-ttu-id="4e1af-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>kaldırmak**</span><span class="sxs-lookup"><span data-stu-id="4e1af-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="4e1af-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4e1af-110">Syntax</span></span>  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4e1af-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4e1af-111">Attributes and Elements</span></span>  
 <span data-ttu-id="4e1af-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4e1af-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4e1af-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4e1af-113">Attributes</span></span>  
  
|<span data-ttu-id="4e1af-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4e1af-114">Attribute</span></span>|<span data-ttu-id="4e1af-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4e1af-115">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="4e1af-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="4e1af-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="4e1af-117">`Listeners` Koleksiyondan kaldırmak için dinleyicinin adı.</span><span class="sxs-lookup"><span data-stu-id="4e1af-117">The name of the listener to remove from the `Listeners` collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4e1af-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4e1af-118">Child Elements</span></span>  
 <span data-ttu-id="4e1af-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="4e1af-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4e1af-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4e1af-120">Parent Elements</span></span>  
  
|<span data-ttu-id="4e1af-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="4e1af-121">Element</span></span>|<span data-ttu-id="4e1af-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4e1af-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4e1af-123">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="4e1af-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="4e1af-124">İletileri toplayan, depolayan ve yönlendiren izleme dinleyicilerini ve izleme anahtarının ayarlandığı düzeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="4e1af-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="4e1af-125">İletileri izlemeyi başlatan izleme kaynakları içerir.</span><span class="sxs-lookup"><span data-stu-id="4e1af-125">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="4e1af-126">İletilerin izlenmesini başlatan bir izleme kaynağı belirtir.</span><span class="sxs-lookup"><span data-stu-id="4e1af-126">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="4e1af-127">İletileri toplayan, depolayan ve yönlendiren dinleyicileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="4e1af-127">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e1af-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4e1af-128">Remarks</span></span>  
 <span data-ttu-id="4e1af-129">Öğe, `<remove>` izleme kaynağı için `Listeners` koleksiyondan belirli bir dinleyiciyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="4e1af-129">The `<remove>` element removes a specified listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="4e1af-130">Bir izleme kaynağı için `Listeners` koleksiyondaki bir <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> <xref:System.Diagnostics.TraceSource.Listeners%2A> <xref:System.Diagnostics.TraceSource> öğeyi, örneğin özelliğindeki yöntemi çağırarak programlı olarak kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e1af-130">You can remove an element from the `Listeners` collection for a trace source programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> method on the <xref:System.Diagnostics.TraceSource.Listeners%2A> property of the <xref:System.Diagnostics.TraceSource> instance.</span></span>  
  
 <span data-ttu-id="4e1af-131">Bu öğe makine yapılandırma dosyasında (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4e1af-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e1af-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="4e1af-132">Example</span></span>  
 <span data-ttu-id="4e1af-133">Aşağıdaki örnek, dinleyiciyi `<remove>` izleme kaynağının `<add>` `console` `Listeners` `TraceSourceApp`koleksiyonuna eklemek için öğeyi kullanmadan önce öğenin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4e1af-133">The following example shows how to use the `<remove>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4e1af-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e1af-134">See also</span></span>

- <xref:System.Diagnostics.TraceSource.Listeners%2A>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="4e1af-135">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="4e1af-135">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="4e1af-136">\<açık></span><span class="sxs-lookup"><span data-stu-id="4e1af-136">\<clear></span></span>](clear-element-for-listeners-for-source.md)
- [<span data-ttu-id="4e1af-137">İz Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="4e1af-137">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
