---
title: "&lt;Kaynakları&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources
- http://schemas.microsoft.com/.NetConfiguration/v2.0#sources
helpviewer_keywords:
- sources element
- trace sources
- <sources> element
ms.assetid: c727b2e2-423a-4463-a223-013f40ff16a3
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 58e9ff8787916132406a7e63aff511c9fb221b73
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltsourcesgt-element"></a><span data-ttu-id="7c758-102">&lt;Kaynakları&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="7c758-102">&lt;sources&gt; Element</span></span>
<span data-ttu-id="7c758-103">İzleme iletileri başlatmak izleme kaynakları belirtir.</span><span class="sxs-lookup"><span data-stu-id="7c758-103">Specifies trace sources that initiate tracing messages.</span></span>  
  
 <span data-ttu-id="7c758-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="7c758-104">\<configuration></span></span>  
<span data-ttu-id="7c758-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="7c758-105">\<system.diagnostics></span></span>  
<span data-ttu-id="7c758-106">\<Kaynakları ></span><span class="sxs-lookup"><span data-stu-id="7c758-106">\<sources></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c758-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7c758-107">Syntax</span></span>  
  
```xml  
<sources>  
   <source>...</source>  
</sources>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7c758-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7c758-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7c758-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7c758-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7c758-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7c758-110">Attributes</span></span>  
 <span data-ttu-id="7c758-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="7c758-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7c758-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7c758-112">Child Elements</span></span>  
  
|<span data-ttu-id="7c758-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="7c758-113">Element</span></span>|<span data-ttu-id="7c758-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7c758-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7c758-115">\<Kaynak ></span><span class="sxs-lookup"><span data-stu-id="7c758-115">\<source></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)|<span data-ttu-id="7c758-116">Gerekli öğe.</span><span class="sxs-lookup"><span data-stu-id="7c758-116">Required element.</span></span><br /><br /> <span data-ttu-id="7c758-117">İzleme iletileri başlatan bir izleme kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7c758-117">Specifies a trace source that initiates tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7c758-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7c758-118">Parent Elements</span></span>  
  
|<span data-ttu-id="7c758-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="7c758-119">Element</span></span>|<span data-ttu-id="7c758-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7c758-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7c758-121">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="7c758-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="7c758-122">Toplamak, depolamak ve iletileri ve izleme anahtarı ayarlandığı düzeyi rota izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7c758-122">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c758-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7c758-123">Remarks</span></span>  
 <span data-ttu-id="7c758-124">Bu öğe makine yapılandırma dosyası (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7c758-124">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c758-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="7c758-125">Example</span></span>  
 <span data-ttu-id="7c758-126">Aşağıdaki örnekte nasıl kullanılacağını gösterir `<sources>` izleme kaynağı eklemek için öğesi `mySource` ve kaynak anahtarı düzeyini ayarlamak için adlandırılmış `sourceSwitch`.</span><span class="sxs-lookup"><span data-stu-id="7c758-126">The following example shows how to use the `<sources>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="7c758-127">Bir konsol İzleme dinleyicisi, izleme bilgilerini konsola eklenir.</span><span class="sxs-lookup"><span data-stu-id="7c758-127">A console trace listener is added that writes trace information to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7c758-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7c758-128">See Also</span></span>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.ConsoleTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 <xref:System.Diagnostics.XmlWriterTraceListener>  
 [<span data-ttu-id="7c758-129">İzleme ve hata ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="7c758-129">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="7c758-130">\<Kaynak ></span><span class="sxs-lookup"><span data-stu-id="7c758-130">\<source></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)
