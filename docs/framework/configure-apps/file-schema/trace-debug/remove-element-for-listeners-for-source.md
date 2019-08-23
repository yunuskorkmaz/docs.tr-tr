---
title: <remove>İçin için <listeners> öğesi<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
ms.openlocfilehash: edd27dd262004aead7db4d81db8ecab0e831dac1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926987"
---
# <a name="remove-element-for-listeners-for-source"></a><span data-ttu-id="46d2d-102">\<Kaynak > için \<> \<dinleyicileri > öğesini kaldır</span><span class="sxs-lookup"><span data-stu-id="46d2d-102">\<remove> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="46d2d-103">İzleme kaynağı için `Listeners` koleksiyondan bir dinleyiciyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="46d2d-103">Removes a listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="46d2d-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="46d2d-104">\<configuration></span></span>  
<span data-ttu-id="46d2d-105">\<System. Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="46d2d-105">\<system.diagnostics></span></span>  
<span data-ttu-id="46d2d-106">\<Kaynaklar ></span><span class="sxs-lookup"><span data-stu-id="46d2d-106">\<sources></span></span>  
<span data-ttu-id="46d2d-107">\<Kaynak ></span><span class="sxs-lookup"><span data-stu-id="46d2d-107">\<source></span></span>  
<span data-ttu-id="46d2d-108">\<dinleyiciler ></span><span class="sxs-lookup"><span data-stu-id="46d2d-108">\<listeners></span></span>  
<span data-ttu-id="46d2d-109">\<> Kaldır</span><span class="sxs-lookup"><span data-stu-id="46d2d-109">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46d2d-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="46d2d-110">Syntax</span></span>  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="46d2d-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="46d2d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="46d2d-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="46d2d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="46d2d-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="46d2d-113">Attributes</span></span>  
  
|<span data-ttu-id="46d2d-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="46d2d-114">Attribute</span></span>|<span data-ttu-id="46d2d-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="46d2d-115">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="46d2d-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="46d2d-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="46d2d-117">`Listeners` Koleksiyondan kaldırılacak dinleyicinin adı.</span><span class="sxs-lookup"><span data-stu-id="46d2d-117">The name of the listener to remove from the `Listeners` collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="46d2d-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="46d2d-118">Child Elements</span></span>  
 <span data-ttu-id="46d2d-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="46d2d-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="46d2d-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="46d2d-120">Parent Elements</span></span>  
  
|<span data-ttu-id="46d2d-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="46d2d-121">Element</span></span>|<span data-ttu-id="46d2d-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="46d2d-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="46d2d-123">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="46d2d-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="46d2d-124">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="46d2d-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="46d2d-125">İzleme iletilerini Başlatan izleme kaynaklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="46d2d-125">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="46d2d-126">İzleme iletilerini Başlatan bir izleme kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="46d2d-126">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="46d2d-127">İletileri toplayacak, depolayan ve yönlendiren dinleyicileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="46d2d-127">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46d2d-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="46d2d-128">Remarks</span></span>  
 <span data-ttu-id="46d2d-129">Öğesi `<remove>` , bir izleme kaynağı için belirtilen dinleyiciyi `Listeners` koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="46d2d-129">The `<remove>` element removes a specified listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="46d2d-130">Örnek<xref:System.Diagnostics.TraceSource> `Listeners` özelliği<xref:System.Diagnostics.TraceSource.Listeners%2A> üzerinde <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> yöntemini çağırarak bir izleme kaynağı için koleksiyondan bir öğeyi programlı bir şekilde kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46d2d-130">You can remove an element from the `Listeners` collection for a trace source programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> method on the <xref:System.Diagnostics.TraceSource.Listeners%2A> property of the <xref:System.Diagnostics.TraceSource> instance.</span></span>  
  
 <span data-ttu-id="46d2d-131">Bu öğe makine yapılandırma dosyasında (Machine. config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="46d2d-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46d2d-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="46d2d-132">Example</span></span>  
 <span data-ttu-id="46d2d-133">Aşağıdaki örnek, öğesini izleme kaynağı `<remove>` `console` `Listeners` `<add>` koleksiyonuna`TraceSourceApp`eklemek için öğesini kullanmadan önce öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="46d2d-133">The following example shows how to use the `<remove>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="46d2d-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46d2d-134">See also</span></span>

- <xref:System.Diagnostics.TraceSource.Listeners%2A>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="46d2d-135">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="46d2d-135">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="46d2d-136">\<> Temizle</span><span class="sxs-lookup"><span data-stu-id="46d2d-136">\<clear></span></span>](clear-element-for-listeners-for-source.md)
- [<span data-ttu-id="46d2d-137">İzleme Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="46d2d-137">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
