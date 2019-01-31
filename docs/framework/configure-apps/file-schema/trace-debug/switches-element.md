---
title: <switches> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches
- http://schemas.microsoft.com/.NetConfiguration/v2.0#switches
helpviewer_keywords:
- <switches> element
- switches element
- trace switches, <switches> element
ms.assetid: 4cf36786-b89a-40e2-a0f1-86bb9b783343
ms.openlocfilehash: afd0e955698dfc7ff3d5c843dd8db10f648265b8
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254671"
---
# <a name="switches-element"></a><span data-ttu-id="db9b2-102">\<anahtarlar > öğesi</span><span class="sxs-lookup"><span data-stu-id="db9b2-102">\<switches> Element</span></span>
<span data-ttu-id="db9b2-103">İzleme anahtarları ve izleme anahtarları ayarlandığı düzeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="db9b2-103">Contains trace switches and the level where the trace switches are set.</span></span>  
  
 <span data-ttu-id="db9b2-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="db9b2-104">\<configuration></span></span>  
<span data-ttu-id="db9b2-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="db9b2-105">\<system.diagnostics></span></span>  
<span data-ttu-id="db9b2-106">\<anahtarlar ></span><span class="sxs-lookup"><span data-stu-id="db9b2-106">\<switches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db9b2-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="db9b2-107">Syntax</span></span>  
  
```xml  
      <switches>   
</switches>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="db9b2-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="db9b2-108">Attributes and Elements</span></span>  
 <span data-ttu-id="db9b2-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="db9b2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="db9b2-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="db9b2-110">Attributes</span></span>  
 <span data-ttu-id="db9b2-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="db9b2-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="db9b2-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="db9b2-112">Child Elements</span></span>  
  
|<span data-ttu-id="db9b2-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="db9b2-113">Element</span></span>|<span data-ttu-id="db9b2-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="db9b2-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="db9b2-115">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="db9b2-115">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-switches.md)|<span data-ttu-id="db9b2-116">Bir izleme anahtarı ayarlandığı düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="db9b2-116">Specifies the level where a trace switch is set.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="db9b2-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="db9b2-117">Parent Elements</span></span>  
  
|<span data-ttu-id="db9b2-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="db9b2-118">Element</span></span>|<span data-ttu-id="db9b2-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="db9b2-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="db9b2-120">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="db9b2-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.diagnostics`|<span data-ttu-id="db9b2-121">Toplamak, depolamak ve iletileri ve bir izleme anahtarı ayarlandığı düzeyi izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="db9b2-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db9b2-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="db9b2-122">Remarks</span></span>  
 <span data-ttu-id="db9b2-123">Bir yapılandırma dosyasına koyarak, bir izleme anahtarı düzeyini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db9b2-123">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="db9b2-124">Anahtar ise bir <xref:System.Diagnostics.BooleanSwitch>açıp kapatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db9b2-124">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="db9b2-125">Anahtar ise bir <xref:System.Diagnostics.TraceSwitch>hata ayıklama iletileri uygulama çıkışları veya izleme türlerini belirtmek için farklı düzeylerde atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db9b2-125">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db9b2-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="db9b2-126">Example</span></span>  
 <span data-ttu-id="db9b2-127">Aşağıdaki örnek nasıl kullanılacağını gösterir  **\<geçiş >** ayarlanacak öğenin `General` izleme anahtarı <xref:System.Diagnostics.TraceLevel> düzeyi ve etkinleştirme `Data` Boole izleme anahtarı.</span><span class="sxs-lookup"><span data-stu-id="db9b2-127">The following example shows how to use the **\<switch>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="db9b2-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db9b2-128">See also</span></span>
- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="db9b2-129">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="db9b2-129">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
