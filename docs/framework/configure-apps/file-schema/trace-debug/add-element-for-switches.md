---
title: <switches> için <add> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
ms.openlocfilehash: db2de681227dfdb7420808963219b9f52381f8fe
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088955"
---
# <a name="add-element-for-switches"></a><span data-ttu-id="90839-102">\<switches> için \<add> Öğesi</span><span class="sxs-lookup"><span data-stu-id="90839-102">\<add> Element for \<switches></span></span>
<span data-ttu-id="90839-103">Bir izleme anahtarının ayarlandığı düzeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="90839-103">Specifies the level where a trace switch is set.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<switches>**](switches-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="90839-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="90839-104">Syntax</span></span>  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="90839-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="90839-105">Attributes and Elements</span></span>  
 <span data-ttu-id="90839-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="90839-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="90839-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="90839-107">Attributes</span></span>  
  
|<span data-ttu-id="90839-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="90839-108">Attribute</span></span>|<span data-ttu-id="90839-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="90839-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="90839-110">**ada**</span><span class="sxs-lookup"><span data-stu-id="90839-110">**name**</span></span>|<span data-ttu-id="90839-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="90839-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="90839-112">Anahtarın adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="90839-112">Specifies the name of the switch.</span></span> <span data-ttu-id="90839-113">Bu özniteliğin değeri, Switch yapıcısına geçirilen *DisplayName* parametresine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="90839-113">The value of this attribute corresponds to the *displayName* parameter that is passed to switch constructor.</span></span>|  
|<span data-ttu-id="90839-114">**deeri**</span><span class="sxs-lookup"><span data-stu-id="90839-114">**value**</span></span>|<span data-ttu-id="90839-115">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="90839-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="90839-116">Anahtar düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="90839-116">Specifies the level of the switch.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="90839-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="90839-117">Child Elements</span></span>  
 <span data-ttu-id="90839-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="90839-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="90839-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="90839-119">Parent Elements</span></span>  
  
|<span data-ttu-id="90839-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="90839-120">Element</span></span>|<span data-ttu-id="90839-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="90839-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="90839-122">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="90839-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`switches`|<span data-ttu-id="90839-123">İzleme anahtarlarını ve izleme anahtarlarının ayarlandığı düzeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="90839-123">Contains trace switches and the level where the trace switches are set.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="90839-124">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="90839-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90839-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="90839-125">Remarks</span></span>  
 <span data-ttu-id="90839-126">Bir izleme anahtarı düzeyini bir yapılandırma dosyasına yerleştirerek değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="90839-126">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="90839-127">Anahtar bir ise <xref:System.Diagnostics.BooleanSwitch> , açıp kapatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="90839-127">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="90839-128">Anahtar bir ise <xref:System.Diagnostics.TraceSwitch> , uygulamanın çıkışları için izleme veya hata ayıklama iletilerinin türlerini belirtmek üzere buna farklı düzeyler atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="90839-128">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="90839-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="90839-129">Example</span></span>  
 <span data-ttu-id="90839-130">Aşağıdaki örnek, **\<add>** izleme anahtarını düzeye ayarlamak için öğesinin nasıl kullanılacağını gösterir `General` <xref:System.Diagnostics.TraceLevel> ve `Data` Boole izleme anahtarını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="90839-130">The following example shows how to use the **\<add>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="90839-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="90839-131">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="90839-132">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="90839-132">Trace and Debug Settings Schema</span></span>](index.md)
