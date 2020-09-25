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
ms.openlocfilehash: 7e249e59423740b36e42f59fae8854412d01a0cc
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173854"
---
# <a name="sharedlisteners-element"></a><span data-ttu-id="c6203-102">\<sharedListeners> Öğesi</span><span class="sxs-lookup"><span data-stu-id="c6203-102">\<sharedListeners> Element</span></span>

<span data-ttu-id="c6203-103">Herhangi bir kaynak veya izleme öğesinin başvurmasına yönelik dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="c6203-103">Contains listeners that any source or trace element can reference.</span></span>  <span data-ttu-id="c6203-104">Bu dinleyiciler, varsayılan olarak herhangi bir izleme almaz ve çalışma zamanında bu dinleyicileri almak mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="c6203-104">These listeners do not receive any traces by default, and it is not possible to retrieve these listeners at run time.</span></span> <span data-ttu-id="c6203-105">Paylaşılan dinleyiciler ada göre kaynaklara veya izlemelere eklenebilir olarak tanımlanan dinleyiciler.</span><span class="sxs-lookup"><span data-stu-id="c6203-105">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<sharedListeners>**  
  
## <a name="syntax"></a><span data-ttu-id="c6203-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="c6203-106">Syntax</span></span>  
  
```xml  
<sharedListeners>
  <add>...</add>  
</sharedListeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c6203-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c6203-107">Attributes and Elements</span></span>  

 <span data-ttu-id="c6203-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c6203-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c6203-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c6203-109">Attributes</span></span>  

 <span data-ttu-id="c6203-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="c6203-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c6203-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c6203-111">Child Elements</span></span>  
  
|<span data-ttu-id="c6203-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="c6203-112">Element</span></span>|<span data-ttu-id="c6203-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6203-113">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="c6203-114">Koleksiyona bir dinleyici ekler `sharedListeners` .</span><span class="sxs-lookup"><span data-stu-id="c6203-114">Adds a listener to the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c6203-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c6203-115">Parent Elements</span></span>  
  
|<span data-ttu-id="c6203-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="c6203-116">Element</span></span>|<span data-ttu-id="c6203-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6203-117">Description</span></span>|  
|-------------|-----------------|  
|`Configuration`|<span data-ttu-id="c6203-118">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="c6203-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="c6203-119">ASP.NET yapılandırma bölümünün kök öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c6203-119">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6203-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c6203-120">Remarks</span></span>  

 <span data-ttu-id="c6203-121">Paylaşılan dinleyiciler koleksiyonuna dinleyici eklemek, etkin bir dinleyici yapmaz.</span><span class="sxs-lookup"><span data-stu-id="c6203-121">Adding a listener to the shared listeners collection does not make it an active listener.</span></span> <span data-ttu-id="c6203-122">Yine de `Listeners` Bu izleme öğesi için koleksiyona ekleyerek bir izleme kaynağına veya bir izlemeye eklenmeli.</span><span class="sxs-lookup"><span data-stu-id="c6203-122">It must still be added to a trace source or a trace by adding it to the `Listeners` collection for that trace element.</span></span> <span data-ttu-id="c6203-123">.NET Framework dinleyici sınıfları <xref:System.Diagnostics.TraceListener> sınıfından türetilir.</span><span class="sxs-lookup"><span data-stu-id="c6203-123">The listener classes in the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="c6203-124">Bu öğe makine yapılandırma dosyasında (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c6203-124">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6203-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="c6203-125">Example</span></span>  

 <span data-ttu-id="c6203-126">Aşağıdaki örnek, `<sharedListeners>` `console` `Listeners` ve sınıflarının her ikisi için de dinleyiciyi koleksiyona eklemek için öğesinin nasıl kullanılacağını gösterir <xref:System.Diagnostics.TraceSource> <xref:System.Diagnostics.Trace> .</span><span class="sxs-lookup"><span data-stu-id="c6203-126">The following example shows how to use the `<sharedListeners>` element to add the listener `console` to the `Listeners` collection for both the <xref:System.Diagnostics.TraceSource> and <xref:System.Diagnostics.Trace> classes.</span></span> <span data-ttu-id="c6203-127">Konsol izleme dinleyicisi, veya çağrıları aracılığıyla konsola izleme bilgilerini yazar <xref:System.Diagnostics.TraceSource> <xref:System.Diagnostics.Trace> .</span><span class="sxs-lookup"><span data-stu-id="c6203-127">The console trace listener writes trace information to the console through calls to either <xref:System.Diagnostics.TraceSource> or <xref:System.Diagnostics.Trace>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c6203-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6203-128">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="c6203-129">İzleme ve hata ayıklama ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="c6203-129">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c6203-130">İz Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="c6203-130">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
