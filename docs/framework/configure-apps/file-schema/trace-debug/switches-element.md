---
title: '&lt;anahtarları&gt; öğesi'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches
- http://schemas.microsoft.com/.NetConfiguration/v2.0#switches
helpviewer_keywords:
- <switches> element
- switches element
- trace switches, <switches> element
ms.assetid: 4cf36786-b89a-40e2-a0f1-86bb9b783343
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 7ca375935c1dfcdb406257ece1a9dfd18851dddf
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47232636"
---
# <a name="ltswitchesgt-element"></a><span data-ttu-id="d63c6-102">&lt;anahtarları&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="d63c6-102">&lt;switches&gt; Element</span></span>
<span data-ttu-id="d63c6-103">İzleme anahtarları ve izleme anahtarları ayarlandığı düzeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="d63c6-103">Contains trace switches and the level where the trace switches are set.</span></span>  
  
 <span data-ttu-id="d63c6-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="d63c6-104">\<configuration></span></span>  
<span data-ttu-id="d63c6-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="d63c6-105">\<system.diagnostics></span></span>  
<span data-ttu-id="d63c6-106">\<anahtarlar ></span><span class="sxs-lookup"><span data-stu-id="d63c6-106">\<switches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d63c6-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d63c6-107">Syntax</span></span>  
  
```xml  
      <switches>   
</switches>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d63c6-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d63c6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d63c6-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d63c6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d63c6-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d63c6-110">Attributes</span></span>  
 <span data-ttu-id="d63c6-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="d63c6-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d63c6-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d63c6-112">Child Elements</span></span>  
  
|<span data-ttu-id="d63c6-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="d63c6-113">Element</span></span>|<span data-ttu-id="d63c6-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d63c6-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d63c6-115">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="d63c6-115">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-switches.md)|<span data-ttu-id="d63c6-116">Bir izleme anahtarı ayarlandığı düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d63c6-116">Specifies the level where a trace switch is set.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d63c6-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d63c6-117">Parent Elements</span></span>  
  
|<span data-ttu-id="d63c6-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="d63c6-118">Element</span></span>|<span data-ttu-id="d63c6-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d63c6-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d63c6-120">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="d63c6-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.diagnostics`|<span data-ttu-id="d63c6-121">Toplamak, depolamak ve iletileri ve bir izleme anahtarı ayarlandığı düzeyi izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d63c6-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d63c6-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d63c6-122">Remarks</span></span>  
 <span data-ttu-id="d63c6-123">Bir yapılandırma dosyasına koyarak, bir izleme anahtarı düzeyini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d63c6-123">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="d63c6-124">Anahtar ise bir <xref:System.Diagnostics.BooleanSwitch>açıp kapatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d63c6-124">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="d63c6-125">Anahtar ise bir <xref:System.Diagnostics.TraceSwitch>hata ayıklama iletileri uygulama çıkışları veya izleme türlerini belirtmek için farklı düzeylerde atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d63c6-125">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d63c6-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="d63c6-126">Example</span></span>  
 <span data-ttu-id="d63c6-127">Aşağıdaki örnek nasıl kullanılacağını gösterir  **\<geçiş >** ayarlanacak öğenin `General` izleme anahtarı <xref:System.Diagnostics.TraceLevel> düzeyi ve etkinleştirme `Data` Boole izleme anahtarı.</span><span class="sxs-lookup"><span data-stu-id="d63c6-127">The following example shows how to use the **\<switch>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
         <add name="Data" value="1" />  
      </switches>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d63c6-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d63c6-128">See Also</span></span>  
 <xref:System.Diagnostics.Switch>  
 <xref:System.Diagnostics.TraceSwitch>  
 <xref:System.Diagnostics.BooleanSwitch>  
 [<span data-ttu-id="d63c6-129">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="d63c6-129">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
