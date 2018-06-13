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
manager: markl
ms.openlocfilehash: 73fe0fb13c191843516a2218c708851abc1851b0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752708"
---
# <a name="ltsourcesgt-element"></a><span data-ttu-id="fd15f-102">&lt;Kaynakları&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="fd15f-102">&lt;sources&gt; Element</span></span>
<span data-ttu-id="fd15f-103">İzleme iletileri başlatmak izleme kaynakları belirtir.</span><span class="sxs-lookup"><span data-stu-id="fd15f-103">Specifies trace sources that initiate tracing messages.</span></span>  
  
 <span data-ttu-id="fd15f-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="fd15f-104">\<configuration></span></span>  
<span data-ttu-id="fd15f-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="fd15f-105">\<system.diagnostics></span></span>  
<span data-ttu-id="fd15f-106">\<Kaynakları ></span><span class="sxs-lookup"><span data-stu-id="fd15f-106">\<sources></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd15f-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fd15f-107">Syntax</span></span>  
  
```xml  
<sources>  
   <source>...</source>  
</sources>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd15f-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fd15f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="fd15f-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fd15f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd15f-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fd15f-110">Attributes</span></span>  
 <span data-ttu-id="fd15f-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="fd15f-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fd15f-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fd15f-112">Child Elements</span></span>  
  
|<span data-ttu-id="fd15f-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="fd15f-113">Element</span></span>|<span data-ttu-id="fd15f-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd15f-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fd15f-115">\<Kaynak ></span><span class="sxs-lookup"><span data-stu-id="fd15f-115">\<source></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)|<span data-ttu-id="fd15f-116">Gerekli öğe.</span><span class="sxs-lookup"><span data-stu-id="fd15f-116">Required element.</span></span><br /><br /> <span data-ttu-id="fd15f-117">İzleme iletileri başlatan bir izleme kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fd15f-117">Specifies a trace source that initiates tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fd15f-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fd15f-118">Parent Elements</span></span>  
  
|<span data-ttu-id="fd15f-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="fd15f-119">Element</span></span>|<span data-ttu-id="fd15f-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd15f-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="fd15f-121">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="fd15f-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="fd15f-122">Toplamak, depolamak ve iletileri ve izleme anahtarı ayarlandığı düzeyi rota izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fd15f-122">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd15f-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fd15f-123">Remarks</span></span>  
 <span data-ttu-id="fd15f-124">Bu öğe makine yapılandırma dosyası (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fd15f-124">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd15f-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="fd15f-125">Example</span></span>  
 <span data-ttu-id="fd15f-126">Aşağıdaki örnekte nasıl kullanılacağını gösterir `<sources>` izleme kaynağı eklemek için öğesi `mySource` ve kaynak anahtarı düzeyini ayarlamak için adlandırılmış `sourceSwitch`.</span><span class="sxs-lookup"><span data-stu-id="fd15f-126">The following example shows how to use the `<sources>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="fd15f-127">Bir konsol İzleme dinleyicisi, izleme bilgilerini konsola eklenir.</span><span class="sxs-lookup"><span data-stu-id="fd15f-127">A console trace listener is added that writes trace information to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fd15f-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fd15f-128">See Also</span></span>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.ConsoleTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 <xref:System.Diagnostics.XmlWriterTraceListener>  
 [<span data-ttu-id="fd15f-129">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="fd15f-129">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="fd15f-130">\<Kaynak ></span><span class="sxs-lookup"><span data-stu-id="fd15f-130">\<source></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)
