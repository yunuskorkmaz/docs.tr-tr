---
title: <remove>İçin için öğesi <listeners><source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
ms.openlocfilehash: 53ba773ea1cb31955e59c1f57e1c0cc807227402
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173880"
---
# <a name="remove-element-for-listeners-for-source"></a><span data-ttu-id="e4391-102">\<remove>İçin için öğesi \<listeners>\<source></span><span class="sxs-lookup"><span data-stu-id="e4391-102">\<remove> Element for \<listeners> for \<source></span></span>

<span data-ttu-id="e4391-103">`Listeners`İzleme kaynağı için koleksiyondan bir dinleyiciyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e4391-103">Removes a listener from the `Listeners` collection for a trace source.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="e4391-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="e4391-104">Syntax</span></span>  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4391-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e4391-105">Attributes and Elements</span></span>  

 <span data-ttu-id="e4391-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e4391-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4391-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e4391-107">Attributes</span></span>  
  
|<span data-ttu-id="e4391-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e4391-108">Attribute</span></span>|<span data-ttu-id="e4391-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e4391-109">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="e4391-110">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e4391-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="e4391-111">Koleksiyondan kaldırılacak dinleyicinin adı `Listeners` .</span><span class="sxs-lookup"><span data-stu-id="e4391-111">The name of the listener to remove from the `Listeners` collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e4391-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e4391-112">Child Elements</span></span>  

 <span data-ttu-id="e4391-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="e4391-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e4391-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e4391-114">Parent Elements</span></span>  
  
|<span data-ttu-id="e4391-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="e4391-115">Element</span></span>|<span data-ttu-id="e4391-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e4391-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e4391-117">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="e4391-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="e4391-118">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e4391-118">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="e4391-119">İzleme iletilerini Başlatan izleme kaynaklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="e4391-119">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="e4391-120">İzleme iletilerini Başlatan bir izleme kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e4391-120">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="e4391-121">İletileri toplayacak, depolayan ve yönlendiren dinleyicileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="e4391-121">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4391-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e4391-122">Remarks</span></span>  

 <span data-ttu-id="e4391-123">`<remove>`Öğesi, `Listeners` bir izleme kaynağı için belirtilen dinleyiciyi koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e4391-123">The `<remove>` element removes a specified listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="e4391-124">`Listeners` <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> Örnek özelliği üzerinde yöntemini çağırarak bir izleme kaynağı için koleksiyondan bir öğeyi programlı bir şekilde kaldırabilirsiniz <xref:System.Diagnostics.TraceSource.Listeners%2A> <xref:System.Diagnostics.TraceSource> .</span><span class="sxs-lookup"><span data-stu-id="e4391-124">You can remove an element from the `Listeners` collection for a trace source programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> method on the <xref:System.Diagnostics.TraceSource.Listeners%2A> property of the <xref:System.Diagnostics.TraceSource> instance.</span></span>  
  
 <span data-ttu-id="e4391-125">Bu öğe makine yapılandırma dosyasında (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e4391-125">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4391-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="e4391-126">Example</span></span>  

 <span data-ttu-id="e4391-127">Aşağıdaki örnek, öğesini `<remove>` `<add>` `console` `Listeners` izleme kaynağı koleksiyonuna eklemek için öğesini kullanmadan önce öğesinin nasıl kullanılacağını gösterir `TraceSourceApp` .</span><span class="sxs-lookup"><span data-stu-id="e4391-127">The following example shows how to use the `<remove>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e4391-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4391-128">See also</span></span>

- <xref:System.Diagnostics.TraceSource.Listeners%2A>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="e4391-129">İzleme ve hata ayıklama ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="e4391-129">Trace and Debug Settings Schema</span></span>](index.md)
- [\<clear>](clear-element-for-listeners-for-source.md)
- [<span data-ttu-id="e4391-130">İz Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="e4391-130">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
