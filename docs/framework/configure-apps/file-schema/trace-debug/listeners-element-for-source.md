---
title: <source> için <listeners> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners
helpviewer_keywords:
- listeners element for <source>
- <listeners> element for <source>
ms.assetid: a2991f43-b4d3-4614-a8e7-da392de9697f
ms.openlocfilehash: b7144b0a7004ba32b21cbc98513df574a5a9e1d9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195187"
---
# <a name="listeners-element-for-source"></a><span data-ttu-id="7529b-102">\<source> için \<listeners> Öğesi</span><span class="sxs-lookup"><span data-stu-id="7529b-102">\<listeners> Element for \<source></span></span>

<span data-ttu-id="7529b-103">İçin koleksiyonuna dinleyici ekler veya kaldırır <xref:System.Diagnostics.TraceSource.Listeners%2A> <xref:System.Diagnostics.TraceSource> .</span><span class="sxs-lookup"><span data-stu-id="7529b-103">Adds or removes listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A> collection for a <xref:System.Diagnostics.TraceSource>.</span></span> <span data-ttu-id="7529b-104">Dinleyici, izleme çıkışını günlük, pencere veya metin dosyası gibi uygun bir hedefe yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="7529b-104">A listener directs the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<listeners>**  
  
## <a name="syntax"></a><span data-ttu-id="7529b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7529b-105">Syntax</span></span>  
  
```xml  
<listeners>
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7529b-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7529b-106">Attributes and Elements</span></span>  

 <span data-ttu-id="7529b-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7529b-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7529b-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7529b-108">Attributes</span></span>  

 <span data-ttu-id="7529b-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="7529b-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7529b-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7529b-110">Child Elements</span></span>  
  
|<span data-ttu-id="7529b-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="7529b-111">Element</span></span>|<span data-ttu-id="7529b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7529b-112">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-source.md)|<span data-ttu-id="7529b-113">Koleksiyona bir dinleyici ekler `Listeners` .</span><span class="sxs-lookup"><span data-stu-id="7529b-113">Adds a listener to the `Listeners` collection.</span></span>|  
|[\<remove>](remove-element-for-listeners-for-source.md)|<span data-ttu-id="7529b-114">Koleksiyondan bir dinleyiciyi kaldırır `Listeners` .</span><span class="sxs-lookup"><span data-stu-id="7529b-114">Removes a listener from the `Listeners` collection.</span></span>|  
|[\<clear>](clear-element-for-listeners-for-source.md)|<span data-ttu-id="7529b-115">`Listeners`İzleme kaynağı için koleksiyonu temizler.</span><span class="sxs-lookup"><span data-stu-id="7529b-115">Clears the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7529b-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7529b-116">Parent Elements</span></span>  
  
|<span data-ttu-id="7529b-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="7529b-117">Element</span></span>|<span data-ttu-id="7529b-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7529b-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7529b-119">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="7529b-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="7529b-120">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7529b-120">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="7529b-121">İzleme iletilerini Başlatan izleme kaynaklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="7529b-121">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="7529b-122">İzleme iletilerini Başlatan bir izleme kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7529b-122">Specifies a trace source that initiates tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7529b-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7529b-123">Remarks</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="7529b-124">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="7529b-124">Configuration File</span></span>  

 <span data-ttu-id="7529b-125">Bu öğe makine yapılandırma dosyasında (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7529b-125">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7529b-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="7529b-126">Example</span></span>  

 <span data-ttu-id="7529b-127">Aşağıdaki örnek, `<listeners>` bir konsol izleme dinleyicisini `mySource` kaynağa eklemek ve varsayılan izleme dinleyicisini kaldırmak için öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7529b-127">The following example shows how to use the `<listeners>` element to add a console trace listener to the `mySource` source and to remove the default trace listener.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7529b-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7529b-128">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="7529b-129">İzleme ve hata ayıklama ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="7529b-129">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="7529b-130">İz Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="7529b-130">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
