---
title: <switches> için <add> öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
ms.openlocfilehash: 2edc890049d62913d693ad61d8d814d012c0f482
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697190"
---
# <a name="add-element-for-switches"></a><span data-ttu-id="0bc0d-102">\<\<anahtarlar için > öğesi ekleyin ></span><span class="sxs-lookup"><span data-stu-id="0bc0d-102">\<add> Element for \<switches></span></span>
<span data-ttu-id="0bc0d-103">Bir izleme anahtarının ayarlandığı düzeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="0bc0d-103">Specifies the level where a trace switch is set.</span></span>  
  
[<span data-ttu-id="0bc0d-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="0bc0d-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="0bc0d-105">&nbsp; @ no__t-1[ **\<system. Diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="0bc0d-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="0bc0d-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<switches >** ](switches-element.md)</span><span class="sxs-lookup"><span data-stu-id="0bc0d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<switches>**](switches-element.md)</span></span>  
<span data-ttu-id="0bc0d-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<add >**</span><span class="sxs-lookup"><span data-stu-id="0bc0d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bc0d-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0bc0d-108">Syntax</span></span>  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0bc0d-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0bc0d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0bc0d-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0bc0d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0bc0d-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0bc0d-111">Attributes</span></span>  
  
|<span data-ttu-id="0bc0d-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0bc0d-112">Attribute</span></span>|<span data-ttu-id="0bc0d-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0bc0d-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0bc0d-114">**ada**</span><span class="sxs-lookup"><span data-stu-id="0bc0d-114">**name**</span></span>|<span data-ttu-id="0bc0d-115">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0bc0d-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="0bc0d-116">Anahtarın adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0bc0d-116">Specifies the name of the switch.</span></span> <span data-ttu-id="0bc0d-117">Bu özniteliğin değeri, Switch yapıcısına geçirilen *DisplayName* parametresine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="0bc0d-117">The value of this attribute corresponds to the *displayName* parameter that is passed to switch constructor.</span></span>|  
|<span data-ttu-id="0bc0d-118">**value**</span><span class="sxs-lookup"><span data-stu-id="0bc0d-118">**value**</span></span>|<span data-ttu-id="0bc0d-119">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0bc0d-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="0bc0d-120">Anahtar düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0bc0d-120">Specifies the level of the switch.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0bc0d-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0bc0d-121">Child Elements</span></span>  
 <span data-ttu-id="0bc0d-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="0bc0d-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0bc0d-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0bc0d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="0bc0d-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="0bc0d-124">Element</span></span>|<span data-ttu-id="0bc0d-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0bc0d-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0bc0d-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="0bc0d-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`switches`|<span data-ttu-id="0bc0d-127">İzleme anahtarlarını ve izleme anahtarlarının ayarlandığı düzeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="0bc0d-127">Contains trace switches and the level where the trace switches are set.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="0bc0d-128">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0bc0d-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0bc0d-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0bc0d-129">Remarks</span></span>  
 <span data-ttu-id="0bc0d-130">Bir izleme anahtarı düzeyini bir yapılandırma dosyasına yerleştirerek değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0bc0d-130">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="0bc0d-131">Anahtar bir <xref:System.Diagnostics.BooleanSwitch> ise, açıp kapatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0bc0d-131">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="0bc0d-132">Anahtar bir <xref:System.Diagnostics.TraceSwitch> ise, uygulamanın çıkışları için izleme veya hata ayıklama iletilerinin türlerini belirtmek üzere buna farklı düzeyler atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0bc0d-132">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bc0d-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="0bc0d-133">Example</span></span>  
 <span data-ttu-id="0bc0d-134">Aşağıdaki örnek, `General` izleme anahtarını <xref:System.Diagnostics.TraceLevel> düzeyine ayarlamak için **\<add >** öğesinin nasıl kullanılacağını gösterir ve `Data` Boole izleme anahtarını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="0bc0d-134">The following example shows how to use the **\<add>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0bc0d-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0bc0d-135">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="0bc0d-136">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="0bc0d-136">Trace and Debug Settings Schema</span></span>](index.md)
