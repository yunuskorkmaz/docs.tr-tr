---
title: "&lt;ekleme&gt; öğesi için &lt;anahtarları&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: de1acb37f3236598e9d8a74a188033d18b65ac8e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-element-for-ltswitchesgt"></a><span data-ttu-id="36940-102">&lt;ekleme&gt; öğesi için &lt;anahtarları&gt;</span><span class="sxs-lookup"><span data-stu-id="36940-102">&lt;add&gt; Element for &lt;switches&gt;</span></span>
<span data-ttu-id="36940-103">İzleme anahtarı ayarlandığı düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="36940-103">Specifies the level where a trace switch is set.</span></span>  
  
 <span data-ttu-id="36940-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="36940-104">\<configuration></span></span>  
<span data-ttu-id="36940-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="36940-105">\<system.diagnostics></span></span>  
<span data-ttu-id="36940-106">\<anahtarları ></span><span class="sxs-lookup"><span data-stu-id="36940-106">\<switches></span></span>  
<span data-ttu-id="36940-107">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="36940-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36940-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="36940-108">Syntax</span></span>  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="36940-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="36940-109">Attributes and Elements</span></span>  
 <span data-ttu-id="36940-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="36940-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="36940-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="36940-111">Attributes</span></span>  
  
|<span data-ttu-id="36940-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="36940-112">Attribute</span></span>|<span data-ttu-id="36940-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="36940-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="36940-114">**adı**</span><span class="sxs-lookup"><span data-stu-id="36940-114">**name**</span></span>|<span data-ttu-id="36940-115">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="36940-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="36940-116">Anahtar adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="36940-116">Specifies the name of the switch.</span></span> <span data-ttu-id="36940-117">Bu özniteliğin değeri karşılık gelen *displayName* Oluşturucusu geçiş yapmak için geçirilen parametre.</span><span class="sxs-lookup"><span data-stu-id="36940-117">The value of this attribute corresponds to the *displayName* parameter that is passed to switch constructor.</span></span>|  
|<span data-ttu-id="36940-118">**değer**</span><span class="sxs-lookup"><span data-stu-id="36940-118">**value**</span></span>|<span data-ttu-id="36940-119">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="36940-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="36940-120">Anahtar düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="36940-120">Specifies the level of the switch.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="36940-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="36940-121">Child Elements</span></span>  
 <span data-ttu-id="36940-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="36940-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="36940-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="36940-123">Parent Elements</span></span>  
  
|<span data-ttu-id="36940-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="36940-124">Element</span></span>|<span data-ttu-id="36940-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="36940-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="36940-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="36940-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`switches`|<span data-ttu-id="36940-127">İzleme anahtarları ve izleme anahtarları belirlendiği düzeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="36940-127">Contains trace switches and the level where the trace switches are set.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="36940-128">Toplamak, depolamak ve iletileri ve izleme anahtarı ayarlandığı düzeyi rota izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="36940-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36940-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="36940-129">Remarks</span></span>  
 <span data-ttu-id="36940-130">Bir yapılandırma dosyasında koyarak izleme anahtarı düzeyini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36940-130">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="36940-131">Anahtar ise bir <xref:System.Diagnostics.BooleanSwitch>açıp kapatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36940-131">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="36940-132">Anahtar ise bir <xref:System.Diagnostics.TraceSwitch>, izleme türlerini belirtmek için farklı düzeyleri atayabilir veya hata ayıklama iletileri uygulama çıkarır.</span><span class="sxs-lookup"><span data-stu-id="36940-132">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36940-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="36940-133">Example</span></span>  
 <span data-ttu-id="36940-134">Aşağıdaki örnekte nasıl kullanılacağını gösterir  **\<Ekle >** ayarlamak için öğenin `General` izleme anahtara <xref:System.Diagnostics.TraceLevel> düzey ve etkinleştirme `Data` Boolean izleme anahtarı.</span><span class="sxs-lookup"><span data-stu-id="36940-134">The following example shows how to use the **\<add>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="36940-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="36940-135">See Also</span></span>  
 <xref:System.Diagnostics.Switch>  
 <xref:System.Diagnostics.TraceSwitch>  
 <xref:System.Diagnostics.BooleanSwitch>  
 [<span data-ttu-id="36940-136">İzleme ve hata ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="36940-136">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
