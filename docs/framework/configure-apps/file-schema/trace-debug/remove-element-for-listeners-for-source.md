---
title: <source> için <listeners> <remove> öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
ms.openlocfilehash: 75db45d4e868ce88e030ec6a43c8bdaf788a1102
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088847"
---
# <a name="remove-element-for-listeners-for-source"></a><span data-ttu-id="7a875-102">\<kaynak için \<dinleyicileri > > öğesi \<kaldırın ></span><span class="sxs-lookup"><span data-stu-id="7a875-102">\<remove> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="7a875-103">Bir izleme kaynağı için `Listeners` koleksiyonundan bir dinleyiciyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="7a875-103">Removes a listener from the `Listeners` collection for a trace source.</span></span>  

<span data-ttu-id="7a875-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="7a875-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7a875-105">[**System. diagnostics\<** ](system-diagnostics-element.md) &nbsp;&nbsp;</span><span class="sxs-lookup"><span data-stu-id="7a875-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="7a875-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<kaynakları >** ](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="7a875-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>\
<span data-ttu-id="7a875-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<kaynak >** ](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="7a875-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>\
<span data-ttu-id="7a875-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**dinleyicileri >** ](listeners-element-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="7a875-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)</span></span>\
<span data-ttu-id="7a875-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<kaldır >**</span><span class="sxs-lookup"><span data-stu-id="7a875-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="7a875-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7a875-110">Syntax</span></span>  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7a875-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7a875-111">Attributes and Elements</span></span>  
 <span data-ttu-id="7a875-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7a875-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7a875-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7a875-113">Attributes</span></span>  
  
|<span data-ttu-id="7a875-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7a875-114">Attribute</span></span>|<span data-ttu-id="7a875-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7a875-115">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="7a875-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="7a875-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="7a875-117">`Listeners` koleksiyonundan kaldırılacak dinleyicinin adı.</span><span class="sxs-lookup"><span data-stu-id="7a875-117">The name of the listener to remove from the `Listeners` collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7a875-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7a875-118">Child Elements</span></span>  
 <span data-ttu-id="7a875-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="7a875-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7a875-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7a875-120">Parent Elements</span></span>  
  
|<span data-ttu-id="7a875-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="7a875-121">Element</span></span>|<span data-ttu-id="7a875-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7a875-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7a875-123">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="7a875-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="7a875-124">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7a875-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="7a875-125">İzleme iletilerini Başlatan izleme kaynaklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="7a875-125">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="7a875-126">İzleme iletilerini Başlatan bir izleme kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7a875-126">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="7a875-127">İletileri toplayacak, depolayan ve yönlendiren dinleyicileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="7a875-127">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a875-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7a875-128">Remarks</span></span>  
 <span data-ttu-id="7a875-129">`<remove>` öğesi, bir izleme kaynağı için `Listeners` koleksiyonundan belirtilen dinleyiciyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="7a875-129">The `<remove>` element removes a specified listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="7a875-130"><xref:System.Diagnostics.TraceSource> örneğinin <xref:System.Diagnostics.TraceSource.Listeners%2A> özelliğinde <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> metodunu çağırarak, bir izleme kaynağı için `Listeners` koleksiyonundan bir öğeyi kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7a875-130">You can remove an element from the `Listeners` collection for a trace source programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> method on the <xref:System.Diagnostics.TraceSource.Listeners%2A> property of the <xref:System.Diagnostics.TraceSource> instance.</span></span>  
  
 <span data-ttu-id="7a875-131">Bu öğe makine yapılandırma dosyasında (Machine. config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7a875-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a875-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="7a875-132">Example</span></span>  
 <span data-ttu-id="7a875-133">Aşağıdaki örnek, izleme kaynağı `TraceSourceApp`için `Listeners` koleksiyonuna dinleyici `console` eklemek için `<add>` öğesini kullanmadan önce `<remove>` öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7a875-133">The following example shows how to use the `<remove>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7a875-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a875-134">See also</span></span>

- <xref:System.Diagnostics.TraceSource.Listeners%2A>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="7a875-135">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="7a875-135">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="7a875-136">\<Temizle ></span><span class="sxs-lookup"><span data-stu-id="7a875-136">\<clear></span></span>](clear-element-for-listeners-for-source.md)
- [<span data-ttu-id="7a875-137">İzleme Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="7a875-137">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
