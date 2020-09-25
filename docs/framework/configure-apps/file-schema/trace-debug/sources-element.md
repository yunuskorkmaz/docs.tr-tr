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
ms.openlocfilehash: 670fb359f892d83feac56c849361c4b980d9a922
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173815"
---
# <a name="sources-element"></a><span data-ttu-id="6f094-102">\<sources> Öğesi</span><span class="sxs-lookup"><span data-stu-id="6f094-102">\<sources> Element</span></span>

<span data-ttu-id="6f094-103">İzleme iletilerini Başlatan izleme kaynaklarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f094-103">Specifies trace sources that initiate tracing messages.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<sources>**

## <a name="syntax"></a><span data-ttu-id="6f094-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="6f094-104">Syntax</span></span>  
  
```xml  
<sources>  
   <source>...</source>  
</sources>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6f094-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6f094-105">Attributes and Elements</span></span>  

 <span data-ttu-id="6f094-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6f094-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6f094-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6f094-107">Attributes</span></span>  

 <span data-ttu-id="6f094-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="6f094-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6f094-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6f094-109">Child Elements</span></span>  
  
|<span data-ttu-id="6f094-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="6f094-110">Element</span></span>|<span data-ttu-id="6f094-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f094-111">Description</span></span>|  
|-------------|-----------------|  
|[\<source>](source-element.md)|<span data-ttu-id="6f094-112">Gerekli öğe.</span><span class="sxs-lookup"><span data-stu-id="6f094-112">Required element.</span></span><br /><br /> <span data-ttu-id="6f094-113">İzleme iletilerini Başlatan bir izleme kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f094-113">Specifies a trace source that initiates tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6f094-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6f094-114">Parent Elements</span></span>  
  
|<span data-ttu-id="6f094-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="6f094-115">Element</span></span>|<span data-ttu-id="6f094-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f094-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6f094-117">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="6f094-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="6f094-118">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f094-118">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f094-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6f094-119">Remarks</span></span>  

 <span data-ttu-id="6f094-120">Bu öğe makine yapılandırma dosyasında (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6f094-120">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f094-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="6f094-121">Example</span></span>  

 <span data-ttu-id="6f094-122">Aşağıdaki örnek, `<sources>` izleme kaynağını eklemek `mySource` ve adlı kaynak anahtarın düzeyini ayarlamak için öğesinin nasıl kullanılacağını gösterir `sourceSwitch` .</span><span class="sxs-lookup"><span data-stu-id="6f094-122">The following example shows how to use the `<sources>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="6f094-123">İzleme bilgilerini konsola yazan bir konsol izleme dinleyicisi eklenir.</span><span class="sxs-lookup"><span data-stu-id="6f094-123">A console trace listener is added that writes trace information to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6f094-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f094-124">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- [<span data-ttu-id="6f094-125">İzleme ve hata ayıklama ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="6f094-125">Trace and Debug Settings Schema</span></span>](index.md)
- [\<source>](source-element.md)
