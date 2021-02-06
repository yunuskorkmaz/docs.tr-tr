---
description: 'Hakkında daha fazla bilgi edinin: için <clear> öğesi <listeners><source>'
title: <clear>İçin için öğesi <listeners><source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/clear
helpviewer_keywords:
- <clear> element for <listeners> for <source>
- clear element for <listeners> for <source>
ms.assetid: 76796bb2-9c0b-4526-8135-8bf18b16d8d9
ms.openlocfilehash: 731c23c73b6d149bd37672e91eca1d70431b2789
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639711"
---
# <a name="clear-element-for-listeners-for-source"></a><span data-ttu-id="cdd08-103">\<clear>İçin için öğesi \<listeners>\<source></span><span class="sxs-lookup"><span data-stu-id="cdd08-103">\<clear> Element for \<listeners> for \<source></span></span>

<span data-ttu-id="cdd08-104">`Listeners`İzleme kaynağı için koleksiyonu temizler.</span><span class="sxs-lookup"><span data-stu-id="cdd08-104">Clears the `Listeners` collection for a trace source.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="cdd08-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="cdd08-105">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cdd08-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cdd08-106">Attributes and Elements</span></span>  

 <span data-ttu-id="cdd08-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cdd08-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cdd08-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cdd08-108">Attributes</span></span>  

 <span data-ttu-id="cdd08-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="cdd08-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cdd08-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cdd08-110">Child Elements</span></span>  

 <span data-ttu-id="cdd08-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="cdd08-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cdd08-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cdd08-112">Parent Elements</span></span>  
  
|<span data-ttu-id="cdd08-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="cdd08-113">Element</span></span>|<span data-ttu-id="cdd08-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cdd08-114">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="cdd08-115">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="cdd08-115">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="cdd08-116">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="cdd08-116">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="cdd08-117">İzleme iletilerini Başlatan izleme kaynaklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="cdd08-117">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="cdd08-118">İzleme iletilerini Başlatan bir izleme kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="cdd08-118">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="cdd08-119">İletileri toplayacak, depolayan ve yönlendiren dinleyicileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="cdd08-119">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cdd08-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cdd08-120">Remarks</span></span>  

 <span data-ttu-id="cdd08-121">`<clear>`Öğesi, `Listeners` dahil olmak üzere bir izleme kaynağı için koleksiyondan tüm dinleyicileri kaldırır <xref:System.Diagnostics.DefaultTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="cdd08-121">The `<clear>` element removes all listeners from the `Listeners` collection for a trace source, including the <xref:System.Diagnostics.DefaultTraceListener>.</span></span> <span data-ttu-id="cdd08-122">`<clear>` `<add>` Koleksiyonda başka hiçbir etkin dinleyici bulunmadığından emin olmak için öğesini kullanmadan önce öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cdd08-122">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="cdd08-123">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="cdd08-123">Configuration File</span></span>  

 <span data-ttu-id="cdd08-124">Bu öğe makine yapılandırma dosyasında (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cdd08-124">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cdd08-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="cdd08-125">Example</span></span>  

 <span data-ttu-id="cdd08-126">Aşağıdaki örnek, `<clear>` öğeleri kullanarak, `<add>` dinleyicileri `console` ve `textListener` `Listeners` izleme kaynağı koleksiyonuna eklemek için öğesinin nasıl kullanılacağını gösterir `TraceSourceApp` .</span><span class="sxs-lookup"><span data-stu-id="cdd08-126">The following example shows how to use the `<clear>` element before using the `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cdd08-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cdd08-127">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="cdd08-128">İzleme ve hata ayıklama ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="cdd08-128">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="cdd08-129">İz Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="cdd08-129">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
