---
title: '&lt;Kaynak&gt; öğesi'
ms.date: 09/29/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 818324077322fffb40a192c9197efde6e8ff7591
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47088951"
---
# <a name="ltsourcegt-element"></a><span data-ttu-id="b4cad-102">&lt;Kaynak&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="b4cad-102">&lt;source&gt; Element</span></span>
<span data-ttu-id="b4cad-103">İzleme iletileri başlatan bir izleme kaynağı belirtir.</span><span class="sxs-lookup"><span data-stu-id="b4cad-103">Specifies a trace source that initiates tracing messages.</span></span>  
  
 <span data-ttu-id="b4cad-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="b4cad-104">\<configuration></span></span>  
<span data-ttu-id="b4cad-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="b4cad-105">\<system.diagnostics></span></span>  
<span data-ttu-id="b4cad-106">\<Kaynakları ></span><span class="sxs-lookup"><span data-stu-id="b4cad-106">\<sources></span></span>  
<span data-ttu-id="b4cad-107">\<Kaynak ></span><span class="sxs-lookup"><span data-stu-id="b4cad-107">\<source></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4cad-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b4cad-108">Syntax</span></span>  
  
```xml  
<source>   
  <listeners>...</listeners>  
</source>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b4cad-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b4cad-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b4cad-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b4cad-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b4cad-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b4cad-111">Attributes</span></span>  
  
|<span data-ttu-id="b4cad-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b4cad-112">Attribute</span></span>|<span data-ttu-id="b4cad-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b4cad-113">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="b4cad-114">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b4cad-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="b4cad-115">İzleme kaynağı adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b4cad-115">Specifies the name of the trace source.</span></span>|  
|`switchName`|<span data-ttu-id="b4cad-116">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b4cad-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="b4cad-117">Uygulamada bir izleme anahtarı örneğinin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b4cad-117">Specifies the name of a trace switch instance in the application.</span></span> <span data-ttu-id="b4cad-118">İçindeki anahtar tanımlanmamışsa bir `<switches>` öğesi, değeri anahtar düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b4cad-118">If the switch is not identified in a `<switches>` element, the value specifies the level for the switch.</span></span>|  
|`switchType`|<span data-ttu-id="b4cad-119">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b4cad-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="b4cad-120">İzleme anahtarı türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="b4cad-120">Specifies the type of the trace switch.</span></span> <span data-ttu-id="b4cad-121">Varsa, türü geçerli bir sınıf adı olmalı ve boş bir dize olamaz.</span><span class="sxs-lookup"><span data-stu-id="b4cad-121">If present, the type must be a valid class name and cannot be an empty string.</span></span>|  
|`extraAttribute`|<span data-ttu-id="b4cad-122">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b4cad-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="b4cad-123">Tarafından tanımlanan bir izleme kaynağı özel özniteliğinin değeri belirtir <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> yöntemi için bu izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="b4cad-123">Specifies the value for a trace source-specific attribute identified by the <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> method for that trace source.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b4cad-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b4cad-124">Child Elements</span></span>  
  
|<span data-ttu-id="b4cad-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="b4cad-125">Element</span></span>|<span data-ttu-id="b4cad-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b4cad-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b4cad-127">\<dinleyicileri ></span><span class="sxs-lookup"><span data-stu-id="b4cad-127">\<listeners></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-source.md)|<span data-ttu-id="b4cad-128">Toplamak, depolamak ve iletileri yönlendirmek dinleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="b4cad-128">Contains listeners that collect, store, and route messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b4cad-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b4cad-129">Parent Elements</span></span>  
  
|<span data-ttu-id="b4cad-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="b4cad-130">Element</span></span>|<span data-ttu-id="b4cad-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b4cad-131">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b4cad-132">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="b4cad-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="b4cad-133">Toplamak, depolamak ve iletileri ve bir izleme anahtarı ayarlandığı düzeyi izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b4cad-133">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="b4cad-134">İzleme iletileri başlatmak iz kaynakları içerir.</span><span class="sxs-lookup"><span data-stu-id="b4cad-134">Contains trace sources that initiate tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4cad-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b4cad-135">Remarks</span></span>  
 <span data-ttu-id="b4cad-136">Bu öğe, makine yapılandırma dosyası (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b4cad-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4cad-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="b4cad-137">Example</span></span>  
 <span data-ttu-id="b4cad-138">Aşağıdaki örnek nasıl kullanılacağını gösterir `<source>` iz eklenecek öğe `mySource` ve kaynak anahtarı düzeyini ayarlamak için adlı `sourceSwitch`.</span><span class="sxs-lookup"><span data-stu-id="b4cad-138">The following example shows how to use the `<source>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="b4cad-139">Bir konsol iz dinleyicisi, izleme bilgileri konsola yazar eklenir.</span><span class="sxs-lookup"><span data-stu-id="b4cad-139">A console trace listener is added that writes trace information to the console.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch" switchType="System.Diagnostics.SourceSwitch"  >  
        <listeners>  
          <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
            <filter type="System.Diagnostics.EventTypeFilter" initializeData="Error" />  
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
  
## <a name="see-also"></a><span data-ttu-id="b4cad-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b4cad-140">See Also</span></span>  
 [<span data-ttu-id="b4cad-141">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="b4cad-141">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="b4cad-142">İzleme Anahtarları</span><span class="sxs-lookup"><span data-stu-id="b4cad-142">Trace Switches</span></span>](../../../../../docs/framework/debug-trace-profile/trace-switches.md)
