---
title: <source> için <listeners> öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners
helpviewer_keywords:
- listeners element for <source>
- <listeners> element for <source>
ms.assetid: a2991f43-b4d3-4614-a8e7-da392de9697f
ms.openlocfilehash: d7641611e5d8257b49bc6a6abd0a2fadfde66e91
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697298"
---
# <a name="listeners-element-for-source"></a><span data-ttu-id="96e3b-102">\<kaynak > için \<listeners > öğesi</span><span class="sxs-lookup"><span data-stu-id="96e3b-102">\<listeners> Element for \<source></span></span>
<span data-ttu-id="96e3b-103">@No__t-1 için <xref:System.Diagnostics.TraceSource.Listeners%2A> koleksiyonundaki dinleyicileri ekler veya kaldırır.</span><span class="sxs-lookup"><span data-stu-id="96e3b-103">Adds or removes listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A> collection for a <xref:System.Diagnostics.TraceSource>.</span></span> <span data-ttu-id="96e3b-104">Dinleyici, izleme çıkışını günlük, pencere veya metin dosyası gibi uygun bir hedefe yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="96e3b-104">A listener directs the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
[<span data-ttu-id="96e3b-105"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="96e3b-105">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="96e3b-106">&nbsp; @ no__t-1[ **\<system. Diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="96e3b-106">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="96e3b-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<sources >** ](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="96e3b-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>  
<span data-ttu-id="96e3b-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<source >** ](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="96e3b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>  
<span data-ttu-id="96e3b-109">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 **\<listeners >**</span><span class="sxs-lookup"><span data-stu-id="96e3b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<listeners>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96e3b-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="96e3b-110">Syntax</span></span>  
  
```xml  
<listeners>   
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="96e3b-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="96e3b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="96e3b-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="96e3b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="96e3b-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="96e3b-113">Attributes</span></span>  
 <span data-ttu-id="96e3b-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="96e3b-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="96e3b-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="96e3b-115">Child Elements</span></span>  
  
|<span data-ttu-id="96e3b-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="96e3b-116">Element</span></span>|<span data-ttu-id="96e3b-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="96e3b-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="96e3b-118">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="96e3b-118">\<add></span></span>](add-element-for-listeners-for-source.md)|<span data-ttu-id="96e3b-119">@No__t-0 koleksiyonuna bir dinleyici ekler.</span><span class="sxs-lookup"><span data-stu-id="96e3b-119">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="96e3b-120">\<remove ></span><span class="sxs-lookup"><span data-stu-id="96e3b-120">\<remove></span></span>](remove-element-for-listeners-for-source.md)|<span data-ttu-id="96e3b-121">@No__t-0 koleksiyonundan bir dinleyiciyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="96e3b-121">Removes a listener from the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="96e3b-122">\<clear ></span><span class="sxs-lookup"><span data-stu-id="96e3b-122">\<clear></span></span>](clear-element-for-listeners-for-source.md)|<span data-ttu-id="96e3b-123">Bir izleme kaynağı için `Listeners` koleksiyonunu temizler.</span><span class="sxs-lookup"><span data-stu-id="96e3b-123">Clears the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="96e3b-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="96e3b-124">Parent Elements</span></span>  
  
|<span data-ttu-id="96e3b-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="96e3b-125">Element</span></span>|<span data-ttu-id="96e3b-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="96e3b-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="96e3b-127">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="96e3b-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="96e3b-128">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="96e3b-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="96e3b-129">İzleme iletilerini Başlatan izleme kaynaklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="96e3b-129">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="96e3b-130">İzleme iletilerini Başlatan bir izleme kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="96e3b-130">Specifies a trace source that initiates tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96e3b-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="96e3b-131">Remarks</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="96e3b-132">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="96e3b-132">Configuration File</span></span>  
 <span data-ttu-id="96e3b-133">Bu öğe makine yapılandırma dosyasında (Machine. config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="96e3b-133">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96e3b-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="96e3b-134">Example</span></span>  
 <span data-ttu-id="96e3b-135">Aşağıdaki örnek, `mySource` kaynağına bir konsol izleme dinleyicisi eklemek ve varsayılan izleme dinleyicisini kaldırmak için `<listeners>` öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="96e3b-135">The following example shows how to use the `<listeners>` element to add a console trace listener to the `mySource` source and to remove the default trace listener.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"   
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener">  
            <filter type="System.Diagnostics.EventTypeFilter"   
              initializeData="Error"/>  
          </add>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="96e3b-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96e3b-136">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="96e3b-137">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="96e3b-137">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="96e3b-138">İzleme Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="96e3b-138">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
