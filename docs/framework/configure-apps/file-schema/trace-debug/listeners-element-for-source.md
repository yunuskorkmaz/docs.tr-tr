---
description: 'İçin: öğesi hakkında daha fazla bilgi <listeners><source>'
title: <source> için <listeners> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners
helpviewer_keywords:
- listeners element for <source>
- <listeners> element for <source>
ms.assetid: a2991f43-b4d3-4614-a8e7-da392de9697f
ms.openlocfilehash: 6b857d4b114366d268eec1859afc7f33cc5b04a2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639658"
---
# <a name="listeners-element-for-source"></a><span data-ttu-id="16581-103">\<source> için \<listeners> Öğesi</span><span class="sxs-lookup"><span data-stu-id="16581-103">\<listeners> Element for \<source></span></span>

<span data-ttu-id="16581-104">İçin koleksiyonuna dinleyici ekler veya kaldırır <xref:System.Diagnostics.TraceSource.Listeners%2A> <xref:System.Diagnostics.TraceSource> .</span><span class="sxs-lookup"><span data-stu-id="16581-104">Adds or removes listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A> collection for a <xref:System.Diagnostics.TraceSource>.</span></span> <span data-ttu-id="16581-105">Dinleyici, izleme çıkışını günlük, pencere veya metin dosyası gibi uygun bir hedefe yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="16581-105">A listener directs the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<listeners>**  
  
## <a name="syntax"></a><span data-ttu-id="16581-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="16581-106">Syntax</span></span>  
  
```xml  
<listeners>
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="16581-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="16581-107">Attributes and Elements</span></span>  

 <span data-ttu-id="16581-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="16581-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="16581-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="16581-109">Attributes</span></span>  

 <span data-ttu-id="16581-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="16581-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="16581-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="16581-111">Child Elements</span></span>  
  
|<span data-ttu-id="16581-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="16581-112">Element</span></span>|<span data-ttu-id="16581-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="16581-113">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-source.md)|<span data-ttu-id="16581-114">Koleksiyona bir dinleyici ekler `Listeners` .</span><span class="sxs-lookup"><span data-stu-id="16581-114">Adds a listener to the `Listeners` collection.</span></span>|  
|[\<remove>](remove-element-for-listeners-for-source.md)|<span data-ttu-id="16581-115">Koleksiyondan bir dinleyiciyi kaldırır `Listeners` .</span><span class="sxs-lookup"><span data-stu-id="16581-115">Removes a listener from the `Listeners` collection.</span></span>|  
|[\<clear>](clear-element-for-listeners-for-source.md)|<span data-ttu-id="16581-116">`Listeners`İzleme kaynağı için koleksiyonu temizler.</span><span class="sxs-lookup"><span data-stu-id="16581-116">Clears the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="16581-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="16581-117">Parent Elements</span></span>  
  
|<span data-ttu-id="16581-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="16581-118">Element</span></span>|<span data-ttu-id="16581-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="16581-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="16581-120">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="16581-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="16581-121">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="16581-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="16581-122">İzleme iletilerini Başlatan izleme kaynaklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="16581-122">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="16581-123">İzleme iletilerini Başlatan bir izleme kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="16581-123">Specifies a trace source that initiates tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16581-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="16581-124">Remarks</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="16581-125">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="16581-125">Configuration File</span></span>  

 <span data-ttu-id="16581-126">Bu öğe makine yapılandırma dosyasında (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="16581-126">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16581-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="16581-127">Example</span></span>  

 <span data-ttu-id="16581-128">Aşağıdaki örnek, `<listeners>` bir konsol izleme dinleyicisini `mySource` kaynağa eklemek ve varsayılan izleme dinleyicisini kaldırmak için öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="16581-128">The following example shows how to use the `<listeners>` element to add a console trace listener to the `mySource` source and to remove the default trace listener.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="16581-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16581-129">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="16581-130">İzleme ve hata ayıklama ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="16581-130">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="16581-131">İz Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="16581-131">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
