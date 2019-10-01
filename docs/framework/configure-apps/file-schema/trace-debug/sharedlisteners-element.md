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
ms.openlocfilehash: b419ecf451b79808e545525c7b8761175f390200
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699297"
---
# <a name="sharedlisteners-element"></a><span data-ttu-id="a114f-102">\<sharedListeners > öğesi</span><span class="sxs-lookup"><span data-stu-id="a114f-102">\<sharedListeners> Element</span></span>
<span data-ttu-id="a114f-103">Herhangi bir kaynak veya izleme öğesinin başvurmasına yönelik dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="a114f-103">Contains listeners that any source or trace element can reference.</span></span>  <span data-ttu-id="a114f-104">Bu dinleyiciler, varsayılan olarak herhangi bir izleme almaz ve çalışma zamanında bu dinleyicileri almak mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="a114f-104">These listeners do not receive any traces by default, and it is not possible to retrieve these listeners at run time.</span></span> <span data-ttu-id="a114f-105">Paylaşılan dinleyiciler ada göre kaynaklara veya izlemelere eklenebilir olarak tanımlanan dinleyiciler.</span><span class="sxs-lookup"><span data-stu-id="a114f-105">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>  
  
[<span data-ttu-id="a114f-106"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="a114f-106">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="a114f-107">&nbsp; @ no__t-1[ **\<system. Diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="a114f-107">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="a114f-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<sharedListeners >**</span><span class="sxs-lookup"><span data-stu-id="a114f-108">&nbsp;&nbsp;&nbsp;&nbsp;**\<sharedListeners>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a114f-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a114f-109">Syntax</span></span>  
  
```xml  
<sharedListeners>   
  <add>...</add>  
</sharedListeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a114f-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a114f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a114f-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a114f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a114f-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a114f-112">Attributes</span></span>  
 <span data-ttu-id="a114f-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="a114f-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a114f-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a114f-114">Child Elements</span></span>  
  
|<span data-ttu-id="a114f-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="a114f-115">Element</span></span>|<span data-ttu-id="a114f-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a114f-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a114f-117">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="a114f-117">\<add></span></span>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="a114f-118">@No__t-0 koleksiyonuna bir dinleyici ekler.</span><span class="sxs-lookup"><span data-stu-id="a114f-118">Adds a listener to the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a114f-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a114f-119">Parent Elements</span></span>  
  
|<span data-ttu-id="a114f-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="a114f-120">Element</span></span>|<span data-ttu-id="a114f-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a114f-121">Description</span></span>|  
|-------------|-----------------|  
|`Configuration`|<span data-ttu-id="a114f-122">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="a114f-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="a114f-123">ASP.NET yapılandırma bölümünün kök öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a114f-123">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a114f-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a114f-124">Remarks</span></span>  
 <span data-ttu-id="a114f-125">Paylaşılan dinleyiciler koleksiyonuna dinleyici eklemek, etkin bir dinleyici yapmaz.</span><span class="sxs-lookup"><span data-stu-id="a114f-125">Adding a listener to the shared listeners collection does not make it an active listener.</span></span> <span data-ttu-id="a114f-126">Yine de bu izleme öğesi için `Listeners` koleksiyonuna ekleyerek bir izleme kaynağına veya bir izlemeye eklenmeli.</span><span class="sxs-lookup"><span data-stu-id="a114f-126">It must still be added to a trace source or a trace by adding it to the `Listeners` collection for that trace element.</span></span> <span data-ttu-id="a114f-127">.NET Framework dinleyici sınıfları <xref:System.Diagnostics.TraceListener> sınıfından türetilir.</span><span class="sxs-lookup"><span data-stu-id="a114f-127">The listener classes in the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="a114f-128">Bu öğe makine yapılandırma dosyasında (Machine. config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a114f-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a114f-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="a114f-129">Example</span></span>  
 <span data-ttu-id="a114f-130">Aşağıdaki örnek, <xref:System.Diagnostics.TraceSource> ve <xref:System.Diagnostics.Trace> sınıfları için `console` dinleyicisini `Listeners` koleksiyonuna eklemek için `<sharedListeners>` öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a114f-130">The following example shows how to use the `<sharedListeners>` element to add the listener `console` to the `Listeners` collection for both the <xref:System.Diagnostics.TraceSource> and <xref:System.Diagnostics.Trace> classes.</span></span> <span data-ttu-id="a114f-131">Konsol izleme dinleyicisi, <xref:System.Diagnostics.TraceSource> ya da <xref:System.Diagnostics.Trace> ' e yapılan çağrılar aracılığıyla izleme bilgilerini konsola yazar.</span><span class="sxs-lookup"><span data-stu-id="a114f-131">The console trace listener writes trace information to the console through calls to either <xref:System.Diagnostics.TraceSource> or <xref:System.Diagnostics.Trace>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a114f-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a114f-132">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="a114f-133">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="a114f-133">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a114f-134">İzleme Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="a114f-134">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
