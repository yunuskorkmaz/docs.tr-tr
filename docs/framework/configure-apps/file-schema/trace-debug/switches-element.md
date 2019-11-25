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
ms.openlocfilehash: 4aeb3cb0cd75f0fb27e3b359b86da61a77b491c7
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088799"
---
# <a name="switches-element"></a><span data-ttu-id="cbd59-102">\<anahtarlar > öğesi</span><span class="sxs-lookup"><span data-stu-id="cbd59-102">\<switches> Element</span></span>
<span data-ttu-id="cbd59-103">İzleme anahtarlarını ve izleme anahtarlarının ayarlandığı düzeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="cbd59-103">Contains trace switches and the level where the trace switches are set.</span></span>  

<span data-ttu-id="cbd59-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="cbd59-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="cbd59-105">[**System. diagnostics\<** ](system-diagnostics-element.md) &nbsp;&nbsp;</span><span class="sxs-lookup"><span data-stu-id="cbd59-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="cbd59-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<anahtarlar >**</span><span class="sxs-lookup"><span data-stu-id="cbd59-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<switches>**</span></span>

## <a name="syntax"></a><span data-ttu-id="cbd59-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cbd59-107">Syntax</span></span>  
  
```xml  
      <switches>   
</switches>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cbd59-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cbd59-108">Attributes and Elements</span></span>  
 <span data-ttu-id="cbd59-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cbd59-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cbd59-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cbd59-110">Attributes</span></span>  
 <span data-ttu-id="cbd59-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="cbd59-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cbd59-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cbd59-112">Child Elements</span></span>  
  
|<span data-ttu-id="cbd59-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="cbd59-113">Element</span></span>|<span data-ttu-id="cbd59-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cbd59-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cbd59-115">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="cbd59-115">\<add></span></span>](add-element-for-switches.md)|<span data-ttu-id="cbd59-116">Bir izleme anahtarının ayarlandığı düzeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="cbd59-116">Specifies the level where a trace switch is set.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cbd59-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cbd59-117">Parent Elements</span></span>  
  
|<span data-ttu-id="cbd59-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="cbd59-118">Element</span></span>|<span data-ttu-id="cbd59-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cbd59-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="cbd59-120">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="cbd59-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.diagnostics`|<span data-ttu-id="cbd59-121">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="cbd59-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cbd59-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cbd59-122">Remarks</span></span>  
 <span data-ttu-id="cbd59-123">Bir izleme anahtarı düzeyini bir yapılandırma dosyasına yerleştirerek değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cbd59-123">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="cbd59-124">Anahtar bir <xref:System.Diagnostics.BooleanSwitch>, açıp kapatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cbd59-124">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="cbd59-125">Anahtar bir <xref:System.Diagnostics.TraceSwitch>ise, uygulamanın çıkışları için izleme veya hata ayıklama iletilerinin türlerini belirtmek üzere buna farklı düzeyler atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cbd59-125">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cbd59-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="cbd59-126">Example</span></span>  
 <span data-ttu-id="cbd59-127">Aşağıdaki örnek, `General` izleme anahtarını <xref:System.Diagnostics.TraceLevel> düzeyine ayarlamak ve `Data` Boole izleme anahtarını etkinleştirmek için **\<anahtar >** öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cbd59-127">The following example shows how to use the **\<switch>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cbd59-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cbd59-128">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="cbd59-129">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="cbd59-129">Trace and Debug Settings Schema</span></span>](index.md)
