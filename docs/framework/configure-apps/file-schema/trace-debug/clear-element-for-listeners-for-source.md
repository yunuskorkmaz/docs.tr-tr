---
title: <clear><listeners> Için element<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/clear
helpviewer_keywords:
- <clear> element for <listeners> for <source>
- clear element for <listeners> for <source>
ms.assetid: 76796bb2-9c0b-4526-8135-8bf18b16d8d9
ms.openlocfilehash: 7f9ddd93d27c3619119702c82c9e8752dab1af7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153587"
---
# <a name="clear-element-for-listeners-for-source"></a><span data-ttu-id="525cc-102">\<kaynak> \<için> \<dinleyiciler için açık> Element</span><span class="sxs-lookup"><span data-stu-id="525cc-102">\<clear> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="525cc-103">Bir izleme `Listeners` kaynağı için koleksiyonu temizler.</span><span class="sxs-lookup"><span data-stu-id="525cc-103">Clears the `Listeners` collection for a trace source.</span></span>  

<span data-ttu-id="525cc-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="525cc-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="525cc-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="525cc-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="525cc-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<kaynaklar>**](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="525cc-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>\
<span data-ttu-id="525cc-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<kaynak>**](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="525cc-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>\
<span data-ttu-id="525cc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dinleyici ler>**](listeners-element-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="525cc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)</span></span>\
<span data-ttu-id="525cc-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<açık>**</span><span class="sxs-lookup"><span data-stu-id="525cc-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="525cc-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="525cc-110">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="525cc-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="525cc-111">Attributes and Elements</span></span>  
 <span data-ttu-id="525cc-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="525cc-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="525cc-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="525cc-113">Attributes</span></span>  
 <span data-ttu-id="525cc-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="525cc-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="525cc-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="525cc-115">Child Elements</span></span>  
 <span data-ttu-id="525cc-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="525cc-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="525cc-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="525cc-117">Parent Elements</span></span>  
  
|<span data-ttu-id="525cc-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="525cc-118">Element</span></span>|<span data-ttu-id="525cc-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="525cc-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="525cc-120">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="525cc-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="525cc-121">İletileri toplayan, depolayan ve yönlendiren izleme dinleyicilerini ve izleme anahtarının ayarlandığı düzeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="525cc-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="525cc-122">İletileri izlemeyi başlatan izleme kaynakları içerir.</span><span class="sxs-lookup"><span data-stu-id="525cc-122">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="525cc-123">İletilerin izlenmesini başlatan bir izleme kaynağı belirtir.</span><span class="sxs-lookup"><span data-stu-id="525cc-123">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="525cc-124">İletileri toplayan, depolayan ve yönlendiren dinleyicileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="525cc-124">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="525cc-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="525cc-125">Remarks</span></span>  
 <span data-ttu-id="525cc-126">Öğe, `<clear>` bir izleme kaynağı `Listeners` için koleksiyondaki tüm dinleyicileri <xref:System.Diagnostics.DefaultTraceListener>kaldırır.</span><span class="sxs-lookup"><span data-stu-id="525cc-126">The `<clear>` element removes all listeners from the `Listeners` collection for a trace source, including the <xref:System.Diagnostics.DefaultTraceListener>.</span></span> <span data-ttu-id="525cc-127">Koleksiyonda başka `<clear>` etkin dinleyici `<add>` olmadığından emin olmak için öğeyi kullanmadan önce öğeyi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="525cc-127">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="525cc-128">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="525cc-128">Configuration File</span></span>  
 <span data-ttu-id="525cc-129">Bu öğe makine yapılandırma dosyasında (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="525cc-129">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="525cc-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="525cc-130">Example</span></span>  
 <span data-ttu-id="525cc-131">Aşağıdaki `<clear>` örnek, dinleyicileri `<add>` `console` eklemek için öğeleri kullanmadan önce `textListener` öğenin `Listeners` nasıl kullanılacağını `TraceSourceApp`ve izleme kaynağının koleksiyonuna nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="525cc-131">The following example shows how to use the `<clear>` element before using the `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="525cc-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="525cc-132">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="525cc-133">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="525cc-133">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="525cc-134">İz Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="525cc-134">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
