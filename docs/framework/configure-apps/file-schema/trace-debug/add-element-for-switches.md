---
title: '&lt;ekleme&gt; öğesi için &lt;anahtarları&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: e0dc425327f6577606e1205a23fdaffcc39f6e01
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747460"
---
# <a name="ltaddgt-element-for-ltswitchesgt"></a><span data-ttu-id="369f6-102">&lt;ekleme&gt; öğesi için &lt;anahtarları&gt;</span><span class="sxs-lookup"><span data-stu-id="369f6-102">&lt;add&gt; Element for &lt;switches&gt;</span></span>
<span data-ttu-id="369f6-103">İzleme anahtarı ayarlandığı düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="369f6-103">Specifies the level where a trace switch is set.</span></span>  
  
 <span data-ttu-id="369f6-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="369f6-104">\<configuration></span></span>  
<span data-ttu-id="369f6-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="369f6-105">\<system.diagnostics></span></span>  
<span data-ttu-id="369f6-106">\<anahtarları ></span><span class="sxs-lookup"><span data-stu-id="369f6-106">\<switches></span></span>  
<span data-ttu-id="369f6-107">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="369f6-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="369f6-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="369f6-108">Syntax</span></span>  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="369f6-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="369f6-109">Attributes and Elements</span></span>  
 <span data-ttu-id="369f6-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="369f6-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="369f6-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="369f6-111">Attributes</span></span>  
  
|<span data-ttu-id="369f6-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="369f6-112">Attribute</span></span>|<span data-ttu-id="369f6-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="369f6-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="369f6-114">**Adı**</span><span class="sxs-lookup"><span data-stu-id="369f6-114">**name**</span></span>|<span data-ttu-id="369f6-115">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="369f6-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="369f6-116">Anahtar adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="369f6-116">Specifies the name of the switch.</span></span> <span data-ttu-id="369f6-117">Bu özniteliğin değeri karşılık gelen *displayName* Oluşturucusu geçiş yapmak için geçirilen parametre.</span><span class="sxs-lookup"><span data-stu-id="369f6-117">The value of this attribute corresponds to the *displayName* parameter that is passed to switch constructor.</span></span>|  
|<span data-ttu-id="369f6-118">**value**</span><span class="sxs-lookup"><span data-stu-id="369f6-118">**value**</span></span>|<span data-ttu-id="369f6-119">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="369f6-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="369f6-120">Anahtar düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="369f6-120">Specifies the level of the switch.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="369f6-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="369f6-121">Child Elements</span></span>  
 <span data-ttu-id="369f6-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="369f6-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="369f6-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="369f6-123">Parent Elements</span></span>  
  
|<span data-ttu-id="369f6-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="369f6-124">Element</span></span>|<span data-ttu-id="369f6-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="369f6-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="369f6-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="369f6-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`switches`|<span data-ttu-id="369f6-127">İzleme anahtarları ve izleme anahtarları belirlendiği düzeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="369f6-127">Contains trace switches and the level where the trace switches are set.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="369f6-128">Toplamak, depolamak ve iletileri ve izleme anahtarı ayarlandığı düzeyi rota izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="369f6-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="369f6-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="369f6-129">Remarks</span></span>  
 <span data-ttu-id="369f6-130">Bir yapılandırma dosyasında koyarak izleme anahtarı düzeyini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="369f6-130">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="369f6-131">Anahtar ise bir <xref:System.Diagnostics.BooleanSwitch>açıp kapatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="369f6-131">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="369f6-132">Anahtar ise bir <xref:System.Diagnostics.TraceSwitch>, izleme türlerini belirtmek için farklı düzeyleri atayabilir veya hata ayıklama iletileri uygulama çıkarır.</span><span class="sxs-lookup"><span data-stu-id="369f6-132">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="369f6-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="369f6-133">Example</span></span>  
 <span data-ttu-id="369f6-134">Aşağıdaki örnekte nasıl kullanılacağını gösterir  **\<Ekle >** ayarlamak için öğenin `General` izleme anahtara <xref:System.Diagnostics.TraceLevel> düzey ve etkinleştirme `Data` Boolean izleme anahtarı.</span><span class="sxs-lookup"><span data-stu-id="369f6-134">The following example shows how to use the **\<add>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="369f6-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="369f6-135">See Also</span></span>  
 <xref:System.Diagnostics.Switch>  
 <xref:System.Diagnostics.TraceSwitch>  
 <xref:System.Diagnostics.BooleanSwitch>  
 [<span data-ttu-id="369f6-136">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="369f6-136">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
