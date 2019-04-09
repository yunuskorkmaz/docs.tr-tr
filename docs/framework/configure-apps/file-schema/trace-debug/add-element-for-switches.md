---
title: <add> öğe için <switches>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
ms.openlocfilehash: d7500620aed1165ff365fee8529230ba252dbc4b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120100"
---
# <a name="add-element-for-switches"></a><span data-ttu-id="d4ac5-102">\<Ekle > öğesi için \<anahtarlar ></span><span class="sxs-lookup"><span data-stu-id="d4ac5-102">\<add> Element for \<switches></span></span>
<span data-ttu-id="d4ac5-103">Bir izleme anahtarı ayarlandığı düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d4ac5-103">Specifies the level where a trace switch is set.</span></span>  
  
 <span data-ttu-id="d4ac5-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="d4ac5-104">\<configuration></span></span>  
<span data-ttu-id="d4ac5-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="d4ac5-105">\<system.diagnostics></span></span>  
<span data-ttu-id="d4ac5-106">\<anahtarlar ></span><span class="sxs-lookup"><span data-stu-id="d4ac5-106">\<switches></span></span>  
<span data-ttu-id="d4ac5-107">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="d4ac5-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4ac5-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d4ac5-108">Syntax</span></span>  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d4ac5-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d4ac5-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d4ac5-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d4ac5-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d4ac5-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d4ac5-111">Attributes</span></span>  
  
|<span data-ttu-id="d4ac5-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d4ac5-112">Attribute</span></span>|<span data-ttu-id="d4ac5-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d4ac5-113">Description</span></span>|  
|---------------|-----------------|  
|**<span data-ttu-id="d4ac5-114">name</span><span class="sxs-lookup"><span data-stu-id="d4ac5-114">name</span></span>**|<span data-ttu-id="d4ac5-115">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d4ac5-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="d4ac5-116">Anahtar adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d4ac5-116">Specifies the name of the switch.</span></span> <span data-ttu-id="d4ac5-117">Bu özniteliğin değeri karşılık gelen *displayName* Oluşturucusu geçiş yapmak için geçirilen parametre.</span><span class="sxs-lookup"><span data-stu-id="d4ac5-117">The value of this attribute corresponds to the *displayName* parameter that is passed to switch constructor.</span></span>|  
|**<span data-ttu-id="d4ac5-118">value</span><span class="sxs-lookup"><span data-stu-id="d4ac5-118">value</span></span>**|<span data-ttu-id="d4ac5-119">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d4ac5-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="d4ac5-120">Anahtar düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d4ac5-120">Specifies the level of the switch.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d4ac5-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d4ac5-121">Child Elements</span></span>  
 <span data-ttu-id="d4ac5-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="d4ac5-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d4ac5-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d4ac5-123">Parent Elements</span></span>  
  
|<span data-ttu-id="d4ac5-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="d4ac5-124">Element</span></span>|<span data-ttu-id="d4ac5-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d4ac5-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d4ac5-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="d4ac5-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`switches`|<span data-ttu-id="d4ac5-127">İzleme anahtarları ve izleme anahtarları ayarlandığı düzeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="d4ac5-127">Contains trace switches and the level where the trace switches are set.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="d4ac5-128">Toplamak, depolamak ve iletileri ve bir izleme anahtarı ayarlandığı düzeyi izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d4ac5-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4ac5-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d4ac5-129">Remarks</span></span>  
 <span data-ttu-id="d4ac5-130">Bir yapılandırma dosyasına koyarak, bir izleme anahtarı düzeyini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4ac5-130">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="d4ac5-131">Anahtar ise bir <xref:System.Diagnostics.BooleanSwitch>açıp kapatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4ac5-131">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="d4ac5-132">Anahtar ise bir <xref:System.Diagnostics.TraceSwitch>hata ayıklama iletileri uygulama çıkışları veya izleme türlerini belirtmek için farklı düzeylerde atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4ac5-132">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4ac5-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="d4ac5-133">Example</span></span>  
 <span data-ttu-id="d4ac5-134">Aşağıdaki örnek nasıl kullanılacağını gösterir  **\<Ekle >** ayarlanacak öğenin `General` izleme anahtarı <xref:System.Diagnostics.TraceLevel> düzeyi ve etkinleştirme `Data` Boole izleme anahtarı.</span><span class="sxs-lookup"><span data-stu-id="d4ac5-134">The following example shows how to use the **\<add>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d4ac5-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4ac5-135">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="d4ac5-136">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="d4ac5-136">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
