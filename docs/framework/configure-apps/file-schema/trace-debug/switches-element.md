---
description: 'Daha fazla bilgi edinin: <switches> öğesi'
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
ms.openlocfilehash: d0ffdf2bdc4dacd157d09d34c40063b687595e3d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750526"
---
# <a name="switches-element"></a><span data-ttu-id="0e7d0-103">\<switches> Öğesi</span><span class="sxs-lookup"><span data-stu-id="0e7d0-103">\<switches> Element</span></span>

<span data-ttu-id="0e7d0-104">İzleme anahtarlarını ve izleme anahtarlarının ayarlandığı düzeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="0e7d0-104">Contains trace switches and the level where the trace switches are set.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<switches>**

## <a name="syntax"></a><span data-ttu-id="0e7d0-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0e7d0-105">Syntax</span></span>  
  
```xml  
      <switches>
</switches>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0e7d0-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0e7d0-106">Attributes and Elements</span></span>  

 <span data-ttu-id="0e7d0-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0e7d0-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0e7d0-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0e7d0-108">Attributes</span></span>  

 <span data-ttu-id="0e7d0-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="0e7d0-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0e7d0-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0e7d0-110">Child Elements</span></span>  
  
|<span data-ttu-id="0e7d0-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="0e7d0-111">Element</span></span>|<span data-ttu-id="0e7d0-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e7d0-112">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-switches.md)|<span data-ttu-id="0e7d0-113">Bir izleme anahtarının ayarlandığı düzeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="0e7d0-113">Specifies the level where a trace switch is set.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0e7d0-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0e7d0-114">Parent Elements</span></span>  
  
|<span data-ttu-id="0e7d0-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="0e7d0-115">Element</span></span>|<span data-ttu-id="0e7d0-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e7d0-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0e7d0-117">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="0e7d0-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.diagnostics`|<span data-ttu-id="0e7d0-118">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0e7d0-118">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e7d0-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0e7d0-119">Remarks</span></span>  

 <span data-ttu-id="0e7d0-120">Bir izleme anahtarı düzeyini bir yapılandırma dosyasına yerleştirerek değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e7d0-120">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="0e7d0-121">Anahtar bir ise <xref:System.Diagnostics.BooleanSwitch> , açıp kapatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e7d0-121">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="0e7d0-122">Anahtar bir ise <xref:System.Diagnostics.TraceSwitch> , uygulamanın çıkışları için izleme veya hata ayıklama iletilerinin türlerini belirtmek üzere buna farklı düzeyler atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e7d0-122">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e7d0-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="0e7d0-123">Example</span></span>  

 <span data-ttu-id="0e7d0-124">Aşağıdaki örnek, **\<switch>** izleme anahtarını düzeye ayarlamak için öğesinin nasıl kullanılacağını gösterir `General` <xref:System.Diagnostics.TraceLevel> ve `Data` Boole izleme anahtarını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="0e7d0-124">The following example shows how to use the **\<switch>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0e7d0-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e7d0-125">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="0e7d0-126">İzleme ve hata ayıklama ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="0e7d0-126">Trace and Debug Settings Schema</span></span>](index.md)
