---
title: <source> için <listeners> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners
helpviewer_keywords:
- listeners element for <source>
- <listeners> element for <source>
ms.assetid: a2991f43-b4d3-4614-a8e7-da392de9697f
ms.openlocfilehash: 853bc94978218fd4d426e6070b3a36e20435cd6d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920486"
---
# <a name="listeners-element-for-source"></a><span data-ttu-id="c9793-102">\<Kaynak > için \<dinleyiciler > öğesi</span><span class="sxs-lookup"><span data-stu-id="c9793-102">\<listeners> Element for \<source></span></span>
<span data-ttu-id="c9793-103">İçin koleksiyonuna<xref:System.Diagnostics.TraceSource.Listeners%2A> dinleyici ekler veya kaldırır. <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="c9793-103">Adds or removes listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A> collection for a <xref:System.Diagnostics.TraceSource>.</span></span> <span data-ttu-id="c9793-104">Dinleyici, izleme çıkışını günlük, pencere veya metin dosyası gibi uygun bir hedefe yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="c9793-104">A listener directs the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
 <span data-ttu-id="c9793-105">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="c9793-105">\<configuration></span></span>  
<span data-ttu-id="c9793-106">\<System. Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="c9793-106">\<system.diagnostics></span></span>  
<span data-ttu-id="c9793-107">\<Kaynaklar ></span><span class="sxs-lookup"><span data-stu-id="c9793-107">\<sources></span></span>  
<span data-ttu-id="c9793-108">\<Kaynak ></span><span class="sxs-lookup"><span data-stu-id="c9793-108">\<source></span></span>  
<span data-ttu-id="c9793-109">\<dinleyiciler > öğesi</span><span class="sxs-lookup"><span data-stu-id="c9793-109">\<listeners> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9793-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c9793-110">Syntax</span></span>  
  
```xml  
<listeners>   
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9793-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c9793-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c9793-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c9793-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c9793-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c9793-113">Attributes</span></span>  
 <span data-ttu-id="c9793-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="c9793-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c9793-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c9793-115">Child Elements</span></span>  
  
|<span data-ttu-id="c9793-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="c9793-116">Element</span></span>|<span data-ttu-id="c9793-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9793-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c9793-118">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="c9793-118">\<add></span></span>](add-element-for-listeners-for-source.md)|<span data-ttu-id="c9793-119">`Listeners` Koleksiyona bir dinleyici ekler.</span><span class="sxs-lookup"><span data-stu-id="c9793-119">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="c9793-120">\<> Kaldır</span><span class="sxs-lookup"><span data-stu-id="c9793-120">\<remove></span></span>](remove-element-for-listeners-for-source.md)|<span data-ttu-id="c9793-121">`Listeners` Koleksiyondan bir dinleyiciyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c9793-121">Removes a listener from the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="c9793-122">\<> Temizle</span><span class="sxs-lookup"><span data-stu-id="c9793-122">\<clear></span></span>](clear-element-for-listeners-for-source.md)|<span data-ttu-id="c9793-123">İzleme kaynağı için koleksiyonu temizler. `Listeners`</span><span class="sxs-lookup"><span data-stu-id="c9793-123">Clears the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c9793-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c9793-124">Parent Elements</span></span>  
  
|<span data-ttu-id="c9793-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="c9793-125">Element</span></span>|<span data-ttu-id="c9793-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9793-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c9793-127">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="c9793-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="c9793-128">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c9793-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="c9793-129">İzleme iletilerini Başlatan izleme kaynaklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="c9793-129">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="c9793-130">İzleme iletilerini Başlatan bir izleme kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c9793-130">Specifies a trace source that initiates tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9793-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c9793-131">Remarks</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="c9793-132">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="c9793-132">Configuration File</span></span>  
 <span data-ttu-id="c9793-133">Bu öğe makine yapılandırma dosyasında (Machine. config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c9793-133">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9793-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="c9793-134">Example</span></span>  
 <span data-ttu-id="c9793-135">Aşağıdaki örnek, bir konsol izleme dinleyicisini `<listeners>` `mySource` kaynağa eklemek ve varsayılan izleme dinleyicisini kaldırmak için öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c9793-135">The following example shows how to use the `<listeners>` element to add a console trace listener to the `mySource` source and to remove the default trace listener.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c9793-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9793-136">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="c9793-137">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="c9793-137">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c9793-138">İzleme Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="c9793-138">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
