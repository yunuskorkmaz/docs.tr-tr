---
title: "&lt;ekleme&gt; öğesi için &lt;anahtarları&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: 4406caa4da1375bea9809843ca96774e24421d5d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-element-for-ltswitchesgt"></a><span data-ttu-id="f77c3-102">&lt;ekleme&gt; öğesi için &lt;anahtarları&gt;</span><span class="sxs-lookup"><span data-stu-id="f77c3-102">&lt;add&gt; Element for &lt;switches&gt;</span></span>
<span data-ttu-id="f77c3-103">İzleme anahtarı ayarlandığı düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f77c3-103">Specifies the level where a trace switch is set.</span></span>  
  
 <span data-ttu-id="f77c3-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="f77c3-104">\<configuration></span></span>  
<span data-ttu-id="f77c3-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="f77c3-105">\<system.diagnostics></span></span>  
<span data-ttu-id="f77c3-106">\<anahtarları ></span><span class="sxs-lookup"><span data-stu-id="f77c3-106">\<switches></span></span>  
<span data-ttu-id="f77c3-107">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="f77c3-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f77c3-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f77c3-108">Syntax</span></span>  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f77c3-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f77c3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f77c3-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f77c3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f77c3-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f77c3-111">Attributes</span></span>  
  
|<span data-ttu-id="f77c3-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f77c3-112">Attribute</span></span>|<span data-ttu-id="f77c3-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f77c3-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f77c3-114">**adı**</span><span class="sxs-lookup"><span data-stu-id="f77c3-114">**name**</span></span>|<span data-ttu-id="f77c3-115">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="f77c3-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="f77c3-116">Anahtar adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f77c3-116">Specifies the name of the switch.</span></span> <span data-ttu-id="f77c3-117">Bu özniteliğin değeri karşılık gelen *displayName* Oluşturucusu geçiş yapmak için geçirilen parametre.</span><span class="sxs-lookup"><span data-stu-id="f77c3-117">The value of this attribute corresponds to the *displayName* parameter that is passed to switch constructor.</span></span>|  
|<span data-ttu-id="f77c3-118">**value**</span><span class="sxs-lookup"><span data-stu-id="f77c3-118">**value**</span></span>|<span data-ttu-id="f77c3-119">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="f77c3-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="f77c3-120">Anahtar düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f77c3-120">Specifies the level of the switch.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f77c3-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f77c3-121">Child Elements</span></span>  
 <span data-ttu-id="f77c3-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="f77c3-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f77c3-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f77c3-123">Parent Elements</span></span>  
  
|<span data-ttu-id="f77c3-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="f77c3-124">Element</span></span>|<span data-ttu-id="f77c3-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f77c3-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f77c3-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="f77c3-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`switches`|<span data-ttu-id="f77c3-127">İzleme anahtarları ve izleme anahtarları belirlendiği düzeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="f77c3-127">Contains trace switches and the level where the trace switches are set.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="f77c3-128">Toplamak, depolamak ve iletileri ve izleme anahtarı ayarlandığı düzeyi rota izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f77c3-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f77c3-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f77c3-129">Remarks</span></span>  
 <span data-ttu-id="f77c3-130">Bir yapılandırma dosyasında koyarak izleme anahtarı düzeyini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f77c3-130">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="f77c3-131">Anahtar ise bir <xref:System.Diagnostics.BooleanSwitch>açıp kapatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f77c3-131">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="f77c3-132">Anahtar ise bir <xref:System.Diagnostics.TraceSwitch>, izleme türlerini belirtmek için farklı düzeyleri atayabilir veya hata ayıklama iletileri uygulama çıkarır.</span><span class="sxs-lookup"><span data-stu-id="f77c3-132">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f77c3-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="f77c3-133">Example</span></span>  
 <span data-ttu-id="f77c3-134">Aşağıdaki örnekte nasıl kullanılacağını gösterir  **\<Ekle >** ayarlamak için öğenin `General` izleme anahtara <xref:System.Diagnostics.TraceLevel> düzey ve etkinleştirme `Data` Boolean izleme anahtarı.</span><span class="sxs-lookup"><span data-stu-id="f77c3-134">The following example shows how to use the **\<add>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f77c3-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f77c3-135">See Also</span></span>  
 <xref:System.Diagnostics.Switch>  
 <xref:System.Diagnostics.TraceSwitch>  
 <xref:System.Diagnostics.BooleanSwitch>  
 [<span data-ttu-id="f77c3-136">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="f77c3-136">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
