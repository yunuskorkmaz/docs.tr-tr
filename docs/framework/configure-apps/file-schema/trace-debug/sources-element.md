---
title: <sources> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources
- http://schemas.microsoft.com/.NetConfiguration/v2.0#sources
helpviewer_keywords:
- sources element
- trace sources
- <sources> element
ms.assetid: c727b2e2-423a-4463-a223-013f40ff16a3
ms.openlocfilehash: a903d009f2056e65414c1792494fbbd20e224413
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088809"
---
# <a name="sources-element"></a><span data-ttu-id="0d84d-102">\<kaynak > öğesi</span><span class="sxs-lookup"><span data-stu-id="0d84d-102">\<sources> Element</span></span>
<span data-ttu-id="0d84d-103">İzleme iletilerini Başlatan izleme kaynaklarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0d84d-103">Specifies trace sources that initiate tracing messages.</span></span>  

<span data-ttu-id="0d84d-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="0d84d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0d84d-105">[**System. diagnostics\<** ](system-diagnostics-element.md) &nbsp;&nbsp;</span><span class="sxs-lookup"><span data-stu-id="0d84d-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="0d84d-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<kaynakları >**</span><span class="sxs-lookup"><span data-stu-id="0d84d-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sources>**</span></span>

## <a name="syntax"></a><span data-ttu-id="0d84d-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0d84d-107">Syntax</span></span>  
  
```xml  
<sources>  
   <source>...</source>  
</sources>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0d84d-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0d84d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0d84d-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0d84d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0d84d-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0d84d-110">Attributes</span></span>  
 <span data-ttu-id="0d84d-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="0d84d-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0d84d-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0d84d-112">Child Elements</span></span>  
  
|<span data-ttu-id="0d84d-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="0d84d-113">Element</span></span>|<span data-ttu-id="0d84d-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0d84d-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0d84d-115">Kaynak > \<</span><span class="sxs-lookup"><span data-stu-id="0d84d-115">\<source></span></span>](source-element.md)|<span data-ttu-id="0d84d-116">Gerekli öğe.</span><span class="sxs-lookup"><span data-stu-id="0d84d-116">Required element.</span></span><br /><br /> <span data-ttu-id="0d84d-117">İzleme iletilerini Başlatan bir izleme kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0d84d-117">Specifies a trace source that initiates tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0d84d-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0d84d-118">Parent Elements</span></span>  
  
|<span data-ttu-id="0d84d-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="0d84d-119">Element</span></span>|<span data-ttu-id="0d84d-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0d84d-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0d84d-121">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="0d84d-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="0d84d-122">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0d84d-122">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d84d-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0d84d-123">Remarks</span></span>  
 <span data-ttu-id="0d84d-124">Bu öğe makine yapılandırma dosyasında (Machine. config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0d84d-124">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d84d-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="0d84d-125">Example</span></span>  
 <span data-ttu-id="0d84d-126">Aşağıdaki örnek, izleme kaynağı `mySource` eklemek ve `sourceSwitch`adlı kaynak anahtarın düzeyini ayarlamak için `<sources>` öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0d84d-126">The following example shows how to use the `<sources>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="0d84d-127">İzleme bilgilerini konsola yazan bir konsol izleme dinleyicisi eklenir.</span><span class="sxs-lookup"><span data-stu-id="0d84d-127">A console trace listener is added that writes trace information to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0d84d-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d84d-128">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- [<span data-ttu-id="0d84d-129">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="0d84d-129">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="0d84d-130">Kaynak > \<</span><span class="sxs-lookup"><span data-stu-id="0d84d-130">\<source></span></span>](source-element.md)
