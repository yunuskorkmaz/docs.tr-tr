---
description: 'Daha fazla bilgi edinin: <sharedListeners> öğesi'
title: <sharedListeners> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#sharedListeners
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners
helpviewer_keywords:
- <sharedListeners> element
- listeners
- shared listeners
- trace listeners, <sharedListeners> element
- sharedListeners element
ms.assetid: de200534-19dd-4156-86cf-c50521802c4c
ms.openlocfilehash: 904648754c99464e1109a04a5a19b52ec1a1cace
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750565"
---
# <a name="sharedlisteners-element"></a><span data-ttu-id="3a0a4-103">\<sharedListeners> Öğesi</span><span class="sxs-lookup"><span data-stu-id="3a0a4-103">\<sharedListeners> Element</span></span>

<span data-ttu-id="3a0a4-104">Herhangi bir kaynak veya izleme öğesinin başvurmasına yönelik dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="3a0a4-104">Contains listeners that any source or trace element can reference.</span></span>  <span data-ttu-id="3a0a4-105">Bu dinleyiciler, varsayılan olarak herhangi bir izleme almaz ve çalışma zamanında bu dinleyicileri almak mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="3a0a4-105">These listeners do not receive any traces by default, and it is not possible to retrieve these listeners at run time.</span></span> <span data-ttu-id="3a0a4-106">Paylaşılan dinleyiciler ada göre kaynaklara veya izlemelere eklenebilir olarak tanımlanan dinleyiciler.</span><span class="sxs-lookup"><span data-stu-id="3a0a4-106">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<sharedListeners>**  
  
## <a name="syntax"></a><span data-ttu-id="3a0a4-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="3a0a4-107">Syntax</span></span>  
  
```xml  
<sharedListeners>
  <add>...</add>  
</sharedListeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3a0a4-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3a0a4-108">Attributes and Elements</span></span>  

 <span data-ttu-id="3a0a4-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3a0a4-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3a0a4-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3a0a4-110">Attributes</span></span>  

 <span data-ttu-id="3a0a4-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="3a0a4-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3a0a4-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3a0a4-112">Child Elements</span></span>  
  
|<span data-ttu-id="3a0a4-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="3a0a4-113">Element</span></span>|<span data-ttu-id="3a0a4-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3a0a4-114">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="3a0a4-115">Koleksiyona bir dinleyici ekler `sharedListeners` .</span><span class="sxs-lookup"><span data-stu-id="3a0a4-115">Adds a listener to the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3a0a4-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3a0a4-116">Parent Elements</span></span>  
  
|<span data-ttu-id="3a0a4-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="3a0a4-117">Element</span></span>|<span data-ttu-id="3a0a4-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3a0a4-118">Description</span></span>|  
|-------------|-----------------|  
|`Configuration`|<span data-ttu-id="3a0a4-119">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="3a0a4-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="3a0a4-120">ASP.NET yapılandırma bölümünün kök öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3a0a4-120">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a0a4-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3a0a4-121">Remarks</span></span>  

 <span data-ttu-id="3a0a4-122">Paylaşılan dinleyiciler koleksiyonuna dinleyici eklemek, etkin bir dinleyici yapmaz.</span><span class="sxs-lookup"><span data-stu-id="3a0a4-122">Adding a listener to the shared listeners collection does not make it an active listener.</span></span> <span data-ttu-id="3a0a4-123">Yine de `Listeners` Bu izleme öğesi için koleksiyona ekleyerek bir izleme kaynağına veya bir izlemeye eklenmeli.</span><span class="sxs-lookup"><span data-stu-id="3a0a4-123">It must still be added to a trace source or a trace by adding it to the `Listeners` collection for that trace element.</span></span> <span data-ttu-id="3a0a4-124">.NET Framework dinleyici sınıfları <xref:System.Diagnostics.TraceListener> sınıfından türetilir.</span><span class="sxs-lookup"><span data-stu-id="3a0a4-124">The listener classes in the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="3a0a4-125">Bu öğe makine yapılandırma dosyasında (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3a0a4-125">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a0a4-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="3a0a4-126">Example</span></span>  

 <span data-ttu-id="3a0a4-127">Aşağıdaki örnek, `<sharedListeners>` `console` `Listeners` ve sınıflarının her ikisi için de dinleyiciyi koleksiyona eklemek için öğesinin nasıl kullanılacağını gösterir <xref:System.Diagnostics.TraceSource> <xref:System.Diagnostics.Trace> .</span><span class="sxs-lookup"><span data-stu-id="3a0a4-127">The following example shows how to use the `<sharedListeners>` element to add the listener `console` to the `Listeners` collection for both the <xref:System.Diagnostics.TraceSource> and <xref:System.Diagnostics.Trace> classes.</span></span> <span data-ttu-id="3a0a4-128">Konsol izleme dinleyicisi, veya çağrıları aracılığıyla konsola izleme bilgilerini yazar <xref:System.Diagnostics.TraceSource> <xref:System.Diagnostics.Trace> .</span><span class="sxs-lookup"><span data-stu-id="3a0a4-128">The console trace listener writes trace information to the console through calls to either <xref:System.Diagnostics.TraceSource> or <xref:System.Diagnostics.Trace>.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sharedListeners>  
      <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"  
          initializeData="Warning" />  
      </add>  
    </sharedListeners>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"  >  
        <listeners>  
          <add name="console" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Verbose"/>  
    </switches>  
    <trace>  
      <listeners>  
        <add name="console" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="3a0a4-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3a0a4-129">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="3a0a4-130">İzleme ve hata ayıklama ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="3a0a4-130">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="3a0a4-131">İz Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="3a0a4-131">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
