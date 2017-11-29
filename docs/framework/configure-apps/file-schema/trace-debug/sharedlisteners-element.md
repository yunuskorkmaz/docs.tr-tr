---
title: "&lt;sharedListeners&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 7ab96ad43248517dca99bff176be7edfab8d3ced
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltsharedlistenersgt-element"></a><span data-ttu-id="1e4e6-102">&lt;sharedListeners&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="1e4e6-102">&lt;sharedListeners&gt; Element</span></span>
<span data-ttu-id="1e4e6-103">Herhangi bir kaynak veya trace ögesi başvurabilir dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="1e4e6-103">Contains listeners that any source or trace element can reference.</span></span>  <span data-ttu-id="1e4e6-104">Bu dinleyicileri varsayılan olarak tüm izlemeleri almaz ve bu dinleyicileri çalışma zamanında almak mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="1e4e6-104">These listeners do not receive any traces by default, and it is not possible to retrieve these listeners at run time.</span></span> <span data-ttu-id="1e4e6-105">Paylaşılan dinleyiciler tanımlanan dinleyicileri kaynakları veya izlemeleri adıyla eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="1e4e6-105">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>  
  
 <span data-ttu-id="1e4e6-106">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="1e4e6-106">\<configuration></span></span>  
<span data-ttu-id="1e4e6-107">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="1e4e6-107">\<system.diagnostics></span></span>  
<span data-ttu-id="1e4e6-108">\<sharedListeners ></span><span class="sxs-lookup"><span data-stu-id="1e4e6-108">\<sharedListeners></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e4e6-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1e4e6-109">Syntax</span></span>  
  
```xml  
<sharedListeners>   
  <add>...</add>  
</sharedListeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1e4e6-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1e4e6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1e4e6-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1e4e6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1e4e6-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1e4e6-112">Attributes</span></span>  
 <span data-ttu-id="1e4e6-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="1e4e6-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1e4e6-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1e4e6-114">Child Elements</span></span>  
  
|<span data-ttu-id="1e4e6-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="1e4e6-115">Element</span></span>|<span data-ttu-id="1e4e6-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1e4e6-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1e4e6-117">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="1e4e6-117">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|<span data-ttu-id="1e4e6-118">Bir dinleyici ekler `sharedListeners` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="1e4e6-118">Adds a listener to the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1e4e6-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1e4e6-119">Parent Elements</span></span>  
  
|<span data-ttu-id="1e4e6-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="1e4e6-120">Element</span></span>|<span data-ttu-id="1e4e6-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1e4e6-121">Description</span></span>|  
|-------------|-----------------|  
|`Configuration`|<span data-ttu-id="1e4e6-122">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="1e4e6-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="1e4e6-123">ASP.NET yapılandırma bölümü için kök öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="1e4e6-123">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e4e6-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1e4e6-124">Remarks</span></span>  
 <span data-ttu-id="1e4e6-125">Paylaşılan dinleyiciler koleksiyona bir dinleyici ekleme etkin olan bir dinleyici yapmaz.</span><span class="sxs-lookup"><span data-stu-id="1e4e6-125">Adding a listener to the shared listeners collection does not make it an active listener.</span></span> <span data-ttu-id="1e4e6-126">Bunu hala bir izleme kaynağı veya bir izleme ekleyerek eklenmelidir `Listeners` söz konusu izleme öğenin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="1e4e6-126">It must still be added to a trace source or a trace by adding it to the `Listeners` collection for that trace element.</span></span> <span data-ttu-id="1e4e6-127">.NET Framework dinleyicisi sınıflarda türetin <xref:System.Diagnostics.TraceListener> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1e4e6-127">The listener classes in the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="1e4e6-128">Bu öğe makine yapılandırma dosyası (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1e4e6-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e4e6-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="1e4e6-129">Example</span></span>  
 <span data-ttu-id="1e4e6-130">Aşağıdaki örnekte nasıl kullanılacağını gösterir `<sharedListeners>` dinleyicisi eklemek için öğesi `console` için `Listeners` koleksiyonu her ikisi için de <xref:System.Diagnostics.TraceSource> ve <xref:System.Diagnostics.Trace> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="1e4e6-130">The following example shows how to use the `<sharedListeners>` element to add the listener `console` to the `Listeners` collection for both the <xref:System.Diagnostics.TraceSource> and <xref:System.Diagnostics.Trace> classes.</span></span> <span data-ttu-id="1e4e6-131">Konsol İzleme dinleyicisi izleme bilgilerini ya da çağrıları aracılığıyla konsola yazar <xref:System.Diagnostics.TraceSource> veya <xref:System.Diagnostics.Trace>.</span><span class="sxs-lookup"><span data-stu-id="1e4e6-131">The console trace listener writes trace information to the console through calls to either <xref:System.Diagnostics.TraceSource> or <xref:System.Diagnostics.Trace>.</span></span>  
  
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
</configuration></system.diagnostics>   
```  
  
## <a name="see-also"></a><span data-ttu-id="1e4e6-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1e4e6-132">See Also</span></span>  
 <xref:System.Diagnostics.TraceListener>  
 [<span data-ttu-id="1e4e6-133">İzleme ve hata ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="1e4e6-133">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="1e4e6-134">İzleme dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="1e4e6-134">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
