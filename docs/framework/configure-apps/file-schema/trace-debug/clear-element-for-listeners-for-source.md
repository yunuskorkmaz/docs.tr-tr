---
title: <clear>İçin için <listeners> öğesi<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/clear
helpviewer_keywords:
- <clear> element for <listeners> for <source>
- clear element for <listeners> for <source>
ms.assetid: 76796bb2-9c0b-4526-8135-8bf18b16d8d9
ms.openlocfilehash: 768d51a74b4c31d1250d2f5d6517f760f886e0a0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920547"
---
# <a name="clear-element-for-listeners-for-source"></a><span data-ttu-id="1f741-102">\<Kaynak > için \< \<dinleyiciler > > öğeyi temizle</span><span class="sxs-lookup"><span data-stu-id="1f741-102">\<clear> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="1f741-103">İzleme kaynağı için koleksiyonu temizler. `Listeners`</span><span class="sxs-lookup"><span data-stu-id="1f741-103">Clears the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="1f741-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="1f741-104">\<configuration></span></span>  
<span data-ttu-id="1f741-105">\<System. Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="1f741-105">\<system.diagnostics></span></span>  
<span data-ttu-id="1f741-106">\<Kaynaklar ></span><span class="sxs-lookup"><span data-stu-id="1f741-106">\<sources></span></span>  
<span data-ttu-id="1f741-107">\<Kaynak ></span><span class="sxs-lookup"><span data-stu-id="1f741-107">\<source></span></span>  
<span data-ttu-id="1f741-108">\<dinleyiciler ></span><span class="sxs-lookup"><span data-stu-id="1f741-108">\<listeners></span></span>  
<span data-ttu-id="1f741-109">\<> Temizle</span><span class="sxs-lookup"><span data-stu-id="1f741-109">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f741-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1f741-110">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1f741-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1f741-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1f741-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1f741-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1f741-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1f741-113">Attributes</span></span>  
 <span data-ttu-id="1f741-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="1f741-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1f741-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1f741-115">Child Elements</span></span>  
 <span data-ttu-id="1f741-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="1f741-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1f741-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1f741-117">Parent Elements</span></span>  
  
|<span data-ttu-id="1f741-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="1f741-118">Element</span></span>|<span data-ttu-id="1f741-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f741-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1f741-120">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="1f741-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="1f741-121">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1f741-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="1f741-122">İzleme iletilerini Başlatan izleme kaynaklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="1f741-122">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="1f741-123">İzleme iletilerini Başlatan bir izleme kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1f741-123">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="1f741-124">İletileri toplayacak, depolayan ve yönlendiren dinleyicileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="1f741-124">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f741-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1f741-125">Remarks</span></span>  
 <span data-ttu-id="1f741-126">Öğesi, dahil olmak üzere bir <xref:System.Diagnostics.DefaultTraceListener>izleme `Listeners` kaynağı için koleksiyondan tüm dinleyicileri kaldırır. `<clear>`</span><span class="sxs-lookup"><span data-stu-id="1f741-126">The `<clear>` element removes all listeners from the `Listeners` collection for a trace source, including the <xref:System.Diagnostics.DefaultTraceListener>.</span></span> <span data-ttu-id="1f741-127">Koleksiyonda başka hiçbir etkin `<clear>` dinleyici bulunmadığından emin olmak `<add>` için öğesini kullanmadan önce öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f741-127">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="1f741-128">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="1f741-128">Configuration File</span></span>  
 <span data-ttu-id="1f741-129">Bu öğe makine yapılandırma dosyasında (Machine. config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1f741-129">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f741-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="1f741-130">Example</span></span>  
 <span data-ttu-id="1f741-131">Aşağıdaki örnek, `<add>` öğeleri kullanarak, dinleyicileri `console` ve `<clear>` `textListener` `Listeners` izleme kaynağı`TraceSourceApp`koleksiyonuna eklemek için öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1f741-131">The following example shows how to use the `<clear>` element before using the `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
       <source name="TraceSourceApp" switchName="sourceSwitch"   
         switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <clear/>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"   
        type="System.Diagnostics.TextWriterTraceListener"   
        initializeData="myListener.log"/>  
    </sharedListeners>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a><span data-ttu-id="1f741-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f741-132">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="1f741-133">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="1f741-133">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="1f741-134">İzleme Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="1f741-134">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
