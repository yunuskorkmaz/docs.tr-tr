---
title: <source> için <listeners> <clear> öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/clear
helpviewer_keywords:
- <clear> element for <listeners> for <source>
- clear element for <listeners> for <source>
ms.assetid: 76796bb2-9c0b-4526-8135-8bf18b16d8d9
ms.openlocfilehash: 4567f236397435e89371ca4c80730ff964fddd21
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088927"
---
# <a name="clear-element-for-listeners-for-source"></a><span data-ttu-id="d91a8-102">\<kaynak için \<dinleyicileri > için \<> öğesi Temizle ></span><span class="sxs-lookup"><span data-stu-id="d91a8-102">\<clear> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="d91a8-103">İzleme kaynağı için `Listeners` koleksiyonunu temizler.</span><span class="sxs-lookup"><span data-stu-id="d91a8-103">Clears the `Listeners` collection for a trace source.</span></span>  

<span data-ttu-id="d91a8-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="d91a8-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d91a8-105">[**System. diagnostics\<** ](system-diagnostics-element.md) &nbsp;&nbsp;</span><span class="sxs-lookup"><span data-stu-id="d91a8-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="d91a8-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<kaynakları >** ](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="d91a8-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>\
<span data-ttu-id="d91a8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<kaynak >** ](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="d91a8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>\
<span data-ttu-id="d91a8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**dinleyicileri >** ](listeners-element-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="d91a8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)</span></span>\
<span data-ttu-id="d91a8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<clear >**</span><span class="sxs-lookup"><span data-stu-id="d91a8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="d91a8-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d91a8-110">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d91a8-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d91a8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d91a8-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d91a8-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d91a8-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d91a8-113">Attributes</span></span>  
 <span data-ttu-id="d91a8-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="d91a8-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d91a8-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d91a8-115">Child Elements</span></span>  
 <span data-ttu-id="d91a8-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="d91a8-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d91a8-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d91a8-117">Parent Elements</span></span>  
  
|<span data-ttu-id="d91a8-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="d91a8-118">Element</span></span>|<span data-ttu-id="d91a8-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d91a8-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d91a8-120">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="d91a8-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="d91a8-121">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d91a8-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="d91a8-122">İzleme iletilerini Başlatan izleme kaynaklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="d91a8-122">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="d91a8-123">İzleme iletilerini Başlatan bir izleme kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d91a8-123">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="d91a8-124">İletileri toplayacak, depolayan ve yönlendiren dinleyicileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="d91a8-124">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d91a8-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d91a8-125">Remarks</span></span>  
 <span data-ttu-id="d91a8-126">`<clear>` öğesi, <xref:System.Diagnostics.DefaultTraceListener>dahil olmak üzere bir izleme kaynağı için `Listeners` koleksiyonundan tüm dinleyicileri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d91a8-126">The `<clear>` element removes all listeners from the `Listeners` collection for a trace source, including the <xref:System.Diagnostics.DefaultTraceListener>.</span></span> <span data-ttu-id="d91a8-127">Koleksiyonda başka hiçbir etkin dinleyici bulunmadığından emin olmak için `<add>` öğesini kullanmadan önce `<clear>` öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d91a8-127">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="d91a8-128">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="d91a8-128">Configuration File</span></span>  
 <span data-ttu-id="d91a8-129">Bu öğe makine yapılandırma dosyasında (Machine. config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d91a8-129">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d91a8-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="d91a8-130">Example</span></span>  
 <span data-ttu-id="d91a8-131">Aşağıdaki örnek, `<add>` öğelerini kullanarak `console` ve izleme kaynak `Listeners` için `TraceSourceApp`koleksiyonuna `textListener` eklemek için `<clear>` öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d91a8-131">The following example shows how to use the `<clear>` element before using the `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d91a8-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d91a8-132">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="d91a8-133">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="d91a8-133">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d91a8-134">İzleme Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="d91a8-134">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
