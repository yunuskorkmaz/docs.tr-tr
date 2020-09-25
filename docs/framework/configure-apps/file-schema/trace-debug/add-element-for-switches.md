---
title: <switches> için <add> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
ms.openlocfilehash: 5be39425363cb6d2a0eca6a0fa3f4154ce857bb5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173945"
---
# <a name="add-element-for-switches"></a><span data-ttu-id="2766d-102">\<switches> için \<add> Öğesi</span><span class="sxs-lookup"><span data-stu-id="2766d-102">\<add> Element for \<switches></span></span>

<span data-ttu-id="2766d-103">Bir izleme anahtarının ayarlandığı düzeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="2766d-103">Specifies the level where a trace switch is set.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<switches>**](switches-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="2766d-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="2766d-104">Syntax</span></span>  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2766d-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2766d-105">Attributes and Elements</span></span>  

 <span data-ttu-id="2766d-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2766d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2766d-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2766d-107">Attributes</span></span>  
  
|<span data-ttu-id="2766d-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2766d-108">Attribute</span></span>|<span data-ttu-id="2766d-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2766d-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2766d-110">**ada**</span><span class="sxs-lookup"><span data-stu-id="2766d-110">**name**</span></span>|<span data-ttu-id="2766d-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="2766d-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="2766d-112">Anahtarın adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2766d-112">Specifies the name of the switch.</span></span> <span data-ttu-id="2766d-113">Bu özniteliğin değeri, Switch yapıcısına geçirilen *DisplayName* parametresine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="2766d-113">The value of this attribute corresponds to the *displayName* parameter that is passed to switch constructor.</span></span>|  
|<span data-ttu-id="2766d-114">**deeri**</span><span class="sxs-lookup"><span data-stu-id="2766d-114">**value**</span></span>|<span data-ttu-id="2766d-115">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="2766d-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="2766d-116">Anahtar düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2766d-116">Specifies the level of the switch.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2766d-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2766d-117">Child Elements</span></span>  

 <span data-ttu-id="2766d-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="2766d-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2766d-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2766d-119">Parent Elements</span></span>  
  
|<span data-ttu-id="2766d-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="2766d-120">Element</span></span>|<span data-ttu-id="2766d-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2766d-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2766d-122">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="2766d-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`switches`|<span data-ttu-id="2766d-123">İzleme anahtarlarını ve izleme anahtarlarının ayarlandığı düzeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="2766d-123">Contains trace switches and the level where the trace switches are set.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="2766d-124">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2766d-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2766d-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2766d-125">Remarks</span></span>  

 <span data-ttu-id="2766d-126">Bir izleme anahtarı düzeyini bir yapılandırma dosyasına yerleştirerek değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2766d-126">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="2766d-127">Anahtar bir ise <xref:System.Diagnostics.BooleanSwitch> , açıp kapatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2766d-127">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="2766d-128">Anahtar bir ise <xref:System.Diagnostics.TraceSwitch> , uygulamanın çıkışları için izleme veya hata ayıklama iletilerinin türlerini belirtmek üzere buna farklı düzeyler atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2766d-128">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2766d-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="2766d-129">Example</span></span>  

 <span data-ttu-id="2766d-130">Aşağıdaki örnek, **\<add>** izleme anahtarını düzeye ayarlamak için öğesinin nasıl kullanılacağını gösterir `General` <xref:System.Diagnostics.TraceLevel> ve `Data` Boole izleme anahtarını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="2766d-130">The following example shows how to use the **\<add>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2766d-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2766d-131">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="2766d-132">İzleme ve hata ayıklama ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="2766d-132">Trace and Debug Settings Schema</span></span>](index.md)
