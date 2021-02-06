---
description: 'İçin: öğesi hakkında daha fazla bilgi <add><switches>'
title: <switches> için <add> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
ms.openlocfilehash: fc47a8518aca1e4e6390d9d7eba97d5fb7a7664e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639724"
---
# <a name="add-element-for-switches"></a><span data-ttu-id="158ac-103">\<switches> için \<add> Öğesi</span><span class="sxs-lookup"><span data-stu-id="158ac-103">\<add> Element for \<switches></span></span>

<span data-ttu-id="158ac-104">Bir izleme anahtarının ayarlandığı düzeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="158ac-104">Specifies the level where a trace switch is set.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<switches>**](switches-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="158ac-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="158ac-105">Syntax</span></span>  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="158ac-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="158ac-106">Attributes and Elements</span></span>  

 <span data-ttu-id="158ac-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="158ac-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="158ac-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="158ac-108">Attributes</span></span>  
  
|<span data-ttu-id="158ac-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="158ac-109">Attribute</span></span>|<span data-ttu-id="158ac-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="158ac-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="158ac-111">**ada**</span><span class="sxs-lookup"><span data-stu-id="158ac-111">**name**</span></span>|<span data-ttu-id="158ac-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="158ac-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="158ac-113">Anahtarın adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="158ac-113">Specifies the name of the switch.</span></span> <span data-ttu-id="158ac-114">Bu özniteliğin değeri, Switch yapıcısına geçirilen *DisplayName* parametresine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="158ac-114">The value of this attribute corresponds to the *displayName* parameter that is passed to switch constructor.</span></span>|  
|<span data-ttu-id="158ac-115">**değer**</span><span class="sxs-lookup"><span data-stu-id="158ac-115">**value**</span></span>|<span data-ttu-id="158ac-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="158ac-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="158ac-117">Anahtar düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="158ac-117">Specifies the level of the switch.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="158ac-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="158ac-118">Child Elements</span></span>  

 <span data-ttu-id="158ac-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="158ac-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="158ac-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="158ac-120">Parent Elements</span></span>  
  
|<span data-ttu-id="158ac-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="158ac-121">Element</span></span>|<span data-ttu-id="158ac-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="158ac-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="158ac-123">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="158ac-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`switches`|<span data-ttu-id="158ac-124">İzleme anahtarlarını ve izleme anahtarlarının ayarlandığı düzeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="158ac-124">Contains trace switches and the level where the trace switches are set.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="158ac-125">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="158ac-125">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="158ac-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="158ac-126">Remarks</span></span>  

 <span data-ttu-id="158ac-127">Bir izleme anahtarı düzeyini bir yapılandırma dosyasına yerleştirerek değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="158ac-127">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="158ac-128">Anahtar bir ise <xref:System.Diagnostics.BooleanSwitch> , açıp kapatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="158ac-128">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="158ac-129">Anahtar bir ise <xref:System.Diagnostics.TraceSwitch> , uygulamanın çıkışları için izleme veya hata ayıklama iletilerinin türlerini belirtmek üzere buna farklı düzeyler atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="158ac-129">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="158ac-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="158ac-130">Example</span></span>  

 <span data-ttu-id="158ac-131">Aşağıdaki örnek, **\<add>** izleme anahtarını düzeye ayarlamak için öğesinin nasıl kullanılacağını gösterir `General` <xref:System.Diagnostics.TraceLevel> ve `Data` Boole izleme anahtarını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="158ac-131">The following example shows how to use the **\<add>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="158ac-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="158ac-132">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="158ac-133">İzleme ve hata ayıklama ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="158ac-133">Trace and Debug Settings Schema</span></span>](index.md)
