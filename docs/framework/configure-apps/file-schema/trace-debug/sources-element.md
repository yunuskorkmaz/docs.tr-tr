---
title: '&lt;Kaynakları&gt; öğesi'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources
- http://schemas.microsoft.com/.NetConfiguration/v2.0#sources
helpviewer_keywords:
- sources element
- trace sources
- <sources> element
ms.assetid: c727b2e2-423a-4463-a223-013f40ff16a3
author: mcleblanc
ms.author: markl
ms.openlocfilehash: a9c5c5529e349eca2ba089ed6fb71da4bd48430a
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47203335"
---
# <a name="ltsourcesgt-element"></a><span data-ttu-id="e6ceb-102">&lt;Kaynakları&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="e6ceb-102">&lt;sources&gt; Element</span></span>
<span data-ttu-id="e6ceb-103">İzleme iletileri başlatmak iz kaynakları belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6ceb-103">Specifies trace sources that initiate tracing messages.</span></span>  
  
 <span data-ttu-id="e6ceb-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="e6ceb-104">\<configuration></span></span>  
<span data-ttu-id="e6ceb-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="e6ceb-105">\<system.diagnostics></span></span>  
<span data-ttu-id="e6ceb-106">\<Kaynakları ></span><span class="sxs-lookup"><span data-stu-id="e6ceb-106">\<sources></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6ceb-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e6ceb-107">Syntax</span></span>  
  
```xml  
<sources>  
   <source>...</source>  
</sources>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6ceb-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e6ceb-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e6ceb-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e6ceb-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6ceb-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e6ceb-110">Attributes</span></span>  
 <span data-ttu-id="e6ceb-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="e6ceb-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e6ceb-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e6ceb-112">Child Elements</span></span>  
  
|<span data-ttu-id="e6ceb-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="e6ceb-113">Element</span></span>|<span data-ttu-id="e6ceb-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e6ceb-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e6ceb-115">\<Kaynak ></span><span class="sxs-lookup"><span data-stu-id="e6ceb-115">\<source></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)|<span data-ttu-id="e6ceb-116">Gerekli öğe.</span><span class="sxs-lookup"><span data-stu-id="e6ceb-116">Required element.</span></span><br /><br /> <span data-ttu-id="e6ceb-117">İzleme iletileri başlatan bir izleme kaynağı belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6ceb-117">Specifies a trace source that initiates tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e6ceb-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e6ceb-118">Parent Elements</span></span>  
  
|<span data-ttu-id="e6ceb-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="e6ceb-119">Element</span></span>|<span data-ttu-id="e6ceb-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e6ceb-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e6ceb-121">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="e6ceb-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="e6ceb-122">Toplamak, depolamak ve iletileri ve bir izleme anahtarı ayarlandığı düzeyi izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6ceb-122">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6ceb-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e6ceb-123">Remarks</span></span>  
 <span data-ttu-id="e6ceb-124">Bu öğe, makine yapılandırma dosyası (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e6ceb-124">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6ceb-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="e6ceb-125">Example</span></span>  
 <span data-ttu-id="e6ceb-126">Aşağıdaki örnek nasıl kullanılacağını gösterir `<sources>` iz eklenecek öğe `mySource` ve kaynak anahtarı düzeyini ayarlamak için adlı `sourceSwitch`.</span><span class="sxs-lookup"><span data-stu-id="e6ceb-126">The following example shows how to use the `<sources>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="e6ceb-127">Bir konsol iz dinleyicisi, izleme bilgileri konsola yazar eklenir.</span><span class="sxs-lookup"><span data-stu-id="e6ceb-127">A console trace listener is added that writes trace information to the console.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <sources>  
         <source name="mySource" switchName="sourceSwitch"   
            switchType="System.Diagnostics.SourceSwitch"  >  
            <listeners>  
               <add name="console"   
                  type="System.Diagnostics.ConsoleTraceListener" >  
                  <filter type="System.Diagnostics.EventTypeFilter"   
                     initializeData="Error" />  
               </add>  
               <remove name="Default" />  
            </listeners>  
         </source>  
      </sources>  
      <switches>  
         <add name="sourceSwitch" value="Warning" />  
      </switches>    
   </system.diagnostics>   
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e6ceb-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e6ceb-128">See Also</span></span>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.ConsoleTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 <xref:System.Diagnostics.XmlWriterTraceListener>  
 [<span data-ttu-id="e6ceb-129">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="e6ceb-129">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="e6ceb-130">\<Kaynak ></span><span class="sxs-lookup"><span data-stu-id="e6ceb-130">\<source></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)
