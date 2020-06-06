---
title: <clear>İçin için öğesi <listeners><source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/clear
helpviewer_keywords:
- <clear> element for <listeners> for <source>
- clear element for <listeners> for <source>
ms.assetid: 76796bb2-9c0b-4526-8135-8bf18b16d8d9
ms.openlocfilehash: 7f9ddd93d27c3619119702c82c9e8752dab1af7b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153587"
---
# <a name="clear-element-for-listeners-for-source"></a><span data-ttu-id="5a06a-102">\<clear>İçin için öğesi \<listeners>\<source></span><span class="sxs-lookup"><span data-stu-id="5a06a-102">\<clear> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="5a06a-103">`Listeners`İzleme kaynağı için koleksiyonu temizler.</span><span class="sxs-lookup"><span data-stu-id="5a06a-103">Clears the `Listeners` collection for a trace source.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="5a06a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5a06a-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a06a-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5a06a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="5a06a-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5a06a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a06a-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5a06a-107">Attributes</span></span>  
 <span data-ttu-id="5a06a-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="5a06a-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5a06a-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5a06a-109">Child Elements</span></span>  
 <span data-ttu-id="5a06a-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="5a06a-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5a06a-111">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5a06a-111">Parent Elements</span></span>  
  
|<span data-ttu-id="5a06a-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="5a06a-112">Element</span></span>|<span data-ttu-id="5a06a-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5a06a-113">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5a06a-114">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="5a06a-114">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="5a06a-115">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5a06a-115">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="5a06a-116">İzleme iletilerini Başlatan izleme kaynaklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="5a06a-116">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="5a06a-117">İzleme iletilerini Başlatan bir izleme kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5a06a-117">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="5a06a-118">İletileri toplayacak, depolayan ve yönlendiren dinleyicileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="5a06a-118">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a06a-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5a06a-119">Remarks</span></span>  
 <span data-ttu-id="5a06a-120">`<clear>`Öğesi, `Listeners` dahil olmak üzere bir izleme kaynağı için koleksiyondan tüm dinleyicileri kaldırır <xref:System.Diagnostics.DefaultTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="5a06a-120">The `<clear>` element removes all listeners from the `Listeners` collection for a trace source, including the <xref:System.Diagnostics.DefaultTraceListener>.</span></span> <span data-ttu-id="5a06a-121">`<clear>` `<add>` Koleksiyonda başka hiçbir etkin dinleyici bulunmadığından emin olmak için öğesini kullanmadan önce öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a06a-121">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="5a06a-122">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="5a06a-122">Configuration File</span></span>  
 <span data-ttu-id="5a06a-123">Bu öğe makine yapılandırma dosyasında (Machine. config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5a06a-123">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a06a-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="5a06a-124">Example</span></span>  
 <span data-ttu-id="5a06a-125">Aşağıdaki örnek, `<clear>` öğeleri kullanarak, `<add>` dinleyicileri `console` ve `textListener` `Listeners` izleme kaynağı koleksiyonuna eklemek için öğesinin nasıl kullanılacağını gösterir `TraceSourceApp` .</span><span class="sxs-lookup"><span data-stu-id="5a06a-125">The following example shows how to use the `<clear>` element before using the `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5a06a-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a06a-126">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="5a06a-127">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="5a06a-127">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="5a06a-128">İz Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="5a06a-128">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
