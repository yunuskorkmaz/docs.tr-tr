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
ms.openlocfilehash: 2a76816ee73f516b3c7544877a77531acaa8e09c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153275"
---
# <a name="sources-element"></a><span data-ttu-id="bd9f1-102">\<sources> Öğesi</span><span class="sxs-lookup"><span data-stu-id="bd9f1-102">\<sources> Element</span></span>
<span data-ttu-id="bd9f1-103">İzleme iletilerini Başlatan izleme kaynaklarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bd9f1-103">Specifies trace sources that initiate tracing messages.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<sources>**

## <a name="syntax"></a><span data-ttu-id="bd9f1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bd9f1-104">Syntax</span></span>  
  
```xml  
<sources>  
   <source>...</source>  
</sources>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bd9f1-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bd9f1-105">Attributes and Elements</span></span>  
 <span data-ttu-id="bd9f1-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bd9f1-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bd9f1-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bd9f1-107">Attributes</span></span>  
 <span data-ttu-id="bd9f1-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="bd9f1-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bd9f1-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bd9f1-109">Child Elements</span></span>  
  
|<span data-ttu-id="bd9f1-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="bd9f1-110">Element</span></span>|<span data-ttu-id="bd9f1-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bd9f1-111">Description</span></span>|  
|-------------|-----------------|  
|[\<source>](source-element.md)|<span data-ttu-id="bd9f1-112">Gerekli öğe.</span><span class="sxs-lookup"><span data-stu-id="bd9f1-112">Required element.</span></span><br /><br /> <span data-ttu-id="bd9f1-113">İzleme iletilerini Başlatan bir izleme kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bd9f1-113">Specifies a trace source that initiates tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bd9f1-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bd9f1-114">Parent Elements</span></span>  
  
|<span data-ttu-id="bd9f1-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="bd9f1-115">Element</span></span>|<span data-ttu-id="bd9f1-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bd9f1-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="bd9f1-117">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="bd9f1-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="bd9f1-118">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bd9f1-118">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd9f1-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bd9f1-119">Remarks</span></span>  
 <span data-ttu-id="bd9f1-120">Bu öğe makine yapılandırma dosyasında (Machine. config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bd9f1-120">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd9f1-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="bd9f1-121">Example</span></span>  
 <span data-ttu-id="bd9f1-122">Aşağıdaki örnek, `<sources>` izleme kaynağını eklemek `mySource` ve adlı kaynak anahtarın düzeyini ayarlamak için öğesinin nasıl kullanılacağını gösterir `sourceSwitch` .</span><span class="sxs-lookup"><span data-stu-id="bd9f1-122">The following example shows how to use the `<sources>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="bd9f1-123">İzleme bilgilerini konsola yazan bir konsol izleme dinleyicisi eklenir.</span><span class="sxs-lookup"><span data-stu-id="bd9f1-123">A console trace listener is added that writes trace information to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bd9f1-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd9f1-124">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- [<span data-ttu-id="bd9f1-125">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="bd9f1-125">Trace and Debug Settings Schema</span></span>](index.md)
- [\<source>](source-element.md)
