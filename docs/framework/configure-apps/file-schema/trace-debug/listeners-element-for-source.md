---
title: <source> için <listeners> öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners
helpviewer_keywords:
- listeners element for <source>
- <listeners> element for <source>
ms.assetid: a2991f43-b4d3-4614-a8e7-da392de9697f
ms.openlocfilehash: 0eee325e01b41a15a19e4f40f479596f9d70f73b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153418"
---
# <a name="listeners-element-for-source"></a><span data-ttu-id="fb12d-102">\<kaynak> için \<Element> dinleyici</span><span class="sxs-lookup"><span data-stu-id="fb12d-102">\<listeners> Element for \<source></span></span>
<span data-ttu-id="fb12d-103"><xref:System.Diagnostics.TraceSource.Listeners%2A> Koleksiyondaki dinleyicileri ekler veya kaldırır. <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="fb12d-103">Adds or removes listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A> collection for a <xref:System.Diagnostics.TraceSource>.</span></span> <span data-ttu-id="fb12d-104">Dinleyici, izleme çıktısını günlük, pencere veya metin dosyası gibi uygun bir hedefe yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="fb12d-104">A listener directs the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
[<span data-ttu-id="fb12d-105">**\<yapılandırma>**</span><span class="sxs-lookup"><span data-stu-id="fb12d-105">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="fb12d-106">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="fb12d-106">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="fb12d-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<kaynaklar>**](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="fb12d-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>  
<span data-ttu-id="fb12d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<kaynak>**](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="fb12d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>  
<span data-ttu-id="fb12d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dinleyici ler>**</span><span class="sxs-lookup"><span data-stu-id="fb12d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<listeners>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb12d-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fb12d-110">Syntax</span></span>  
  
```xml  
<listeners>
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fb12d-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fb12d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="fb12d-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fb12d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fb12d-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fb12d-113">Attributes</span></span>  
 <span data-ttu-id="fb12d-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="fb12d-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fb12d-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fb12d-115">Child Elements</span></span>  
  
|<span data-ttu-id="fb12d-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="fb12d-116">Element</span></span>|<span data-ttu-id="fb12d-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fb12d-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fb12d-118">\<>ekleyin</span><span class="sxs-lookup"><span data-stu-id="fb12d-118">\<add></span></span>](add-element-for-listeners-for-source.md)|<span data-ttu-id="fb12d-119">`Listeners` Koleksiyona bir dinleyici ekler.</span><span class="sxs-lookup"><span data-stu-id="fb12d-119">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="fb12d-120">\<>kaldırmak</span><span class="sxs-lookup"><span data-stu-id="fb12d-120">\<remove></span></span>](remove-element-for-listeners-for-source.md)|<span data-ttu-id="fb12d-121">Dinleyiciyi `Listeners` koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="fb12d-121">Removes a listener from the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="fb12d-122">\<açık></span><span class="sxs-lookup"><span data-stu-id="fb12d-122">\<clear></span></span>](clear-element-for-listeners-for-source.md)|<span data-ttu-id="fb12d-123">Bir izleme `Listeners` kaynağı için koleksiyonu temizler.</span><span class="sxs-lookup"><span data-stu-id="fb12d-123">Clears the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fb12d-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fb12d-124">Parent Elements</span></span>  
  
|<span data-ttu-id="fb12d-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="fb12d-125">Element</span></span>|<span data-ttu-id="fb12d-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fb12d-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="fb12d-127">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="fb12d-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="fb12d-128">İletileri toplayan, depolayan ve yönlendiren izleme dinleyicilerini ve izleme anahtarının ayarlandığı düzeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="fb12d-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="fb12d-129">İletileri izlemeyi başlatan izleme kaynakları içerir.</span><span class="sxs-lookup"><span data-stu-id="fb12d-129">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="fb12d-130">İletilerin izlenmesini başlatan bir izleme kaynağı belirtir.</span><span class="sxs-lookup"><span data-stu-id="fb12d-130">Specifies a trace source that initiates tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb12d-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fb12d-131">Remarks</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="fb12d-132">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="fb12d-132">Configuration File</span></span>  
 <span data-ttu-id="fb12d-133">Bu öğe makine yapılandırma dosyasında (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fb12d-133">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb12d-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="fb12d-134">Example</span></span>  
 <span data-ttu-id="fb12d-135">Aşağıdaki örnek, kaynağa `<listeners>` konsol izleme dinleyicisi eklemek `mySource` ve varsayılan izleme dinleyicisini kaldırmak için öğenin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fb12d-135">The following example shows how to use the `<listeners>` element to add a console trace listener to the `mySource` source and to remove the default trace listener.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fb12d-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb12d-136">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="fb12d-137">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="fb12d-137">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="fb12d-138">İz Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="fb12d-138">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
