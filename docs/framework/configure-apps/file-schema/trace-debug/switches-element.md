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
ms.openlocfilehash: 92a1c8db43579048945d76082e3ebd2862efd7ed
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920438"
---
# <a name="switches-element"></a><span data-ttu-id="7571f-102">\<> öğe anahtarları</span><span class="sxs-lookup"><span data-stu-id="7571f-102">\<switches> Element</span></span>
<span data-ttu-id="7571f-103">İzleme anahtarlarını ve izleme anahtarlarının ayarlandığı düzeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="7571f-103">Contains trace switches and the level where the trace switches are set.</span></span>  
  
 <span data-ttu-id="7571f-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="7571f-104">\<configuration></span></span>  
<span data-ttu-id="7571f-105">\<System. Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="7571f-105">\<system.diagnostics></span></span>  
<span data-ttu-id="7571f-106">\<Anahtarlar ></span><span class="sxs-lookup"><span data-stu-id="7571f-106">\<switches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7571f-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7571f-107">Syntax</span></span>  
  
```xml  
      <switches>   
</switches>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7571f-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7571f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7571f-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7571f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7571f-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7571f-110">Attributes</span></span>  
 <span data-ttu-id="7571f-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="7571f-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7571f-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7571f-112">Child Elements</span></span>  
  
|<span data-ttu-id="7571f-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="7571f-113">Element</span></span>|<span data-ttu-id="7571f-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7571f-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7571f-115">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="7571f-115">\<add></span></span>](add-element-for-switches.md)|<span data-ttu-id="7571f-116">Bir izleme anahtarının ayarlandığı düzeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="7571f-116">Specifies the level where a trace switch is set.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7571f-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7571f-117">Parent Elements</span></span>  
  
|<span data-ttu-id="7571f-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="7571f-118">Element</span></span>|<span data-ttu-id="7571f-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7571f-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7571f-120">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="7571f-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.diagnostics`|<span data-ttu-id="7571f-121">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7571f-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7571f-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7571f-122">Remarks</span></span>  
 <span data-ttu-id="7571f-123">Bir izleme anahtarı düzeyini bir yapılandırma dosyasına yerleştirerek değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7571f-123">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="7571f-124">Anahtar bir <xref:System.Diagnostics.BooleanSwitch>ise, açıp kapatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7571f-124">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="7571f-125">Anahtar bir <xref:System.Diagnostics.TraceSwitch>ise, uygulamanın çıkışları için izleme veya hata ayıklama iletilerinin türlerini belirtmek üzere buna farklı düzeyler atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7571f-125">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7571f-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="7571f-126">Example</span></span>  
 <span data-ttu-id="7571f-127">Aşağıdaki örnek, `General` izleme `Data` anahtarını <xref:System.Diagnostics.TraceLevel> düzeye ayarlamak için  **\<anahtar >** öğesinin nasıl kullanılacağını gösterir ve Boole izleme anahtarını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="7571f-127">The following example shows how to use the **\<switch>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7571f-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7571f-128">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="7571f-129">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="7571f-129">Trace and Debug Settings Schema</span></span>](index.md)
