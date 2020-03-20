---
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
ms.openlocfilehash: 69f15cc9583b397017ac30a0c567914495867c18
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153327"
---
# <a name="sharedlisteners-element"></a><span data-ttu-id="ceffe-102">\<sharedListeners> Element</span><span class="sxs-lookup"><span data-stu-id="ceffe-102">\<sharedListeners> Element</span></span>
<span data-ttu-id="ceffe-103">Herhangi bir kaynak veya izleme öğesinin başvuruedebileceği dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="ceffe-103">Contains listeners that any source or trace element can reference.</span></span>  <span data-ttu-id="ceffe-104">Bu dinleyiciler varsayılan olarak herhangi bir iz almazlar ve bu dinleyicileri çalışma zamanında almak mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="ceffe-104">These listeners do not receive any traces by default, and it is not possible to retrieve these listeners at run time.</span></span> <span data-ttu-id="ceffe-105">Paylaşılan dinleyici olarak tanımlanan dinleyiciler kaynaklara veya izadile eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="ceffe-105">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>  
  
[<span data-ttu-id="ceffe-106">**\<yapılandırma>**</span><span class="sxs-lookup"><span data-stu-id="ceffe-106">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="ceffe-107">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="ceffe-107">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="ceffe-108">&nbsp;&nbsp;&nbsp;&nbsp;**\<paylaşılanDinleyiciler>**</span><span class="sxs-lookup"><span data-stu-id="ceffe-108">&nbsp;&nbsp;&nbsp;&nbsp;**\<sharedListeners>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ceffe-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ceffe-109">Syntax</span></span>  
  
```xml  
<sharedListeners>
  <add>...</add>  
</sharedListeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ceffe-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ceffe-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ceffe-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ceffe-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ceffe-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ceffe-112">Attributes</span></span>  
 <span data-ttu-id="ceffe-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="ceffe-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ceffe-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ceffe-114">Child Elements</span></span>  
  
|<span data-ttu-id="ceffe-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="ceffe-115">Element</span></span>|<span data-ttu-id="ceffe-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ceffe-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ceffe-117">\<>ekleyin</span><span class="sxs-lookup"><span data-stu-id="ceffe-117">\<add></span></span>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="ceffe-118">`sharedListeners` Koleksiyona bir dinleyici ekler.</span><span class="sxs-lookup"><span data-stu-id="ceffe-118">Adds a listener to the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ceffe-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ceffe-119">Parent Elements</span></span>  
  
|<span data-ttu-id="ceffe-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="ceffe-120">Element</span></span>|<span data-ttu-id="ceffe-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ceffe-121">Description</span></span>|  
|-------------|-----------------|  
|`Configuration`|<span data-ttu-id="ceffe-122">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="ceffe-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="ceffe-123">ASP.NET yapılandırma bölümünün kök öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ceffe-123">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ceffe-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ceffe-124">Remarks</span></span>  
 <span data-ttu-id="ceffe-125">Paylaşılan dinleyici koleksiyonuna dinleyici eklemek onu etkin bir dinleyici yapmaz.</span><span class="sxs-lookup"><span data-stu-id="ceffe-125">Adding a listener to the shared listeners collection does not make it an active listener.</span></span> <span data-ttu-id="ceffe-126">Yine de bir izleme kaynağına veya bir izleme `Listeners` için bu izleme öğesi için koleksiyona ekleyerek eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="ceffe-126">It must still be added to a trace source or a trace by adding it to the `Listeners` collection for that trace element.</span></span> <span data-ttu-id="ceffe-127">.NET Framework'deki dinleyici sınıfları sınıftan <xref:System.Diagnostics.TraceListener> türetilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ceffe-127">The listener classes in the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="ceffe-128">Bu öğe makine yapılandırma dosyasında (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ceffe-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ceffe-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="ceffe-129">Example</span></span>  
 <span data-ttu-id="ceffe-130">Aşağıdaki örnek, dinleyiciyi `<sharedListeners>` `Listeners` hem sınıflar hem `console` de <xref:System.Diagnostics.Trace> sınıflar için <xref:System.Diagnostics.TraceSource> koleksiyona eklemek için öğenin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ceffe-130">The following example shows how to use the `<sharedListeners>` element to add the listener `console` to the `Listeners` collection for both the <xref:System.Diagnostics.TraceSource> and <xref:System.Diagnostics.Trace> classes.</span></span> <span data-ttu-id="ceffe-131">Konsol izleme dinleyicisi ya da <xref:System.Diagnostics.TraceSource> <xref:System.Diagnostics.Trace>aramalar yoluyla konsola izleme bilgileri yazar.</span><span class="sxs-lookup"><span data-stu-id="ceffe-131">The console trace listener writes trace information to the console through calls to either <xref:System.Diagnostics.TraceSource> or <xref:System.Diagnostics.Trace>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ceffe-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ceffe-132">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="ceffe-133">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="ceffe-133">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ceffe-134">İz Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="ceffe-134">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
