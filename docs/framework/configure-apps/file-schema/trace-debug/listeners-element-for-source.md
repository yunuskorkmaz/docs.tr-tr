---
title: <listeners> için <source> Öğesi
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
# <a name="listeners-element-for-source"></a><span data-ttu-id="e5177-102">\<kaynak > için \<dinleyicileri > öğesi</span><span class="sxs-lookup"><span data-stu-id="e5177-102">\<listeners> Element for \<source></span></span>
<span data-ttu-id="e5177-103"><xref:System.Diagnostics.TraceSource>için <xref:System.Diagnostics.TraceSource.Listeners%2A> koleksiyonuna dinleyici ekler veya kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e5177-103">Adds or removes listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A> collection for a <xref:System.Diagnostics.TraceSource>.</span></span> <span data-ttu-id="e5177-104">Dinleyici, izleme çıkışını günlük, pencere veya metin dosyası gibi uygun bir hedefe yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="e5177-104">A listener directs the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
[<span data-ttu-id="e5177-105"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="e5177-105">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="e5177-106">[ **System. diagnostics\<** &nbsp;&nbsp;>](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="e5177-106">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="e5177-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<kaynakları >** ](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="e5177-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>  
<span data-ttu-id="e5177-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<kaynak >** ](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="e5177-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>  
<span data-ttu-id="e5177-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**dinleyicileri >**</span><span class="sxs-lookup"><span data-stu-id="e5177-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<listeners>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5177-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e5177-110">Syntax</span></span>  
  
```xml  
<listeners>   
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e5177-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e5177-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e5177-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e5177-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e5177-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e5177-113">Attributes</span></span>  
 <span data-ttu-id="e5177-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="e5177-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e5177-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e5177-115">Child Elements</span></span>  
  
|<span data-ttu-id="e5177-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="e5177-116">Element</span></span>|<span data-ttu-id="e5177-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5177-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e5177-118">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="e5177-118">\<add></span></span>](add-element-for-listeners-for-source.md)|<span data-ttu-id="e5177-119">`Listeners` koleksiyonuna bir dinleyici ekler.</span><span class="sxs-lookup"><span data-stu-id="e5177-119">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="e5177-120">\<> Kaldır</span><span class="sxs-lookup"><span data-stu-id="e5177-120">\<remove></span></span>](remove-element-for-listeners-for-source.md)|<span data-ttu-id="e5177-121">`Listeners` koleksiyonundan bir dinleyiciyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e5177-121">Removes a listener from the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="e5177-122">\<Temizle ></span><span class="sxs-lookup"><span data-stu-id="e5177-122">\<clear></span></span>](clear-element-for-listeners-for-source.md)|<span data-ttu-id="e5177-123">İzleme kaynağı için `Listeners` koleksiyonunu temizler.</span><span class="sxs-lookup"><span data-stu-id="e5177-123">Clears the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e5177-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e5177-124">Parent Elements</span></span>  
  
|<span data-ttu-id="e5177-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="e5177-125">Element</span></span>|<span data-ttu-id="e5177-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5177-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e5177-127">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="e5177-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="e5177-128">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5177-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="e5177-129">İzleme iletilerini Başlatan izleme kaynaklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="e5177-129">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="e5177-130">İzleme iletilerini Başlatan bir izleme kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5177-130">Specifies a trace source that initiates tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5177-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e5177-131">Remarks</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="e5177-132">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="e5177-132">Configuration File</span></span>  
 <span data-ttu-id="e5177-133">Bu öğe makine yapılandırma dosyasında (Machine. config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e5177-133">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5177-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="e5177-134">Example</span></span>  
 <span data-ttu-id="e5177-135">Aşağıdaki örnek, `mySource` kaynağına bir konsol izleme dinleyicisi eklemek ve varsayılan izleme dinleyicisini kaldırmak için `<listeners>` öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e5177-135">The following example shows how to use the `<listeners>` element to add a console trace listener to the `mySource` source and to remove the default trace listener.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e5177-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5177-136">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="e5177-137">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="e5177-137">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e5177-138">İzleme Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="e5177-138">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
