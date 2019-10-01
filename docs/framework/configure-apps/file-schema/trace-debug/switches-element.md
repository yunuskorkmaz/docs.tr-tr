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
ms.openlocfilehash: c161f842192396101dcc6850f3b3da328958eac3
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697091"
---
# <a name="switches-element"></a><span data-ttu-id="bf085-102">\<switches > öğesi</span><span class="sxs-lookup"><span data-stu-id="bf085-102">\<switches> Element</span></span>
<span data-ttu-id="bf085-103">İzleme anahtarlarını ve izleme anahtarlarının ayarlandığı düzeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="bf085-103">Contains trace switches and the level where the trace switches are set.</span></span>  
  
[<span data-ttu-id="bf085-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="bf085-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="bf085-105">&nbsp; @ no__t-1[ **\<system. Diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="bf085-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="bf085-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\< anahtar >**</span><span class="sxs-lookup"><span data-stu-id="bf085-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<switches>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf085-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bf085-107">Syntax</span></span>  
  
```xml  
      <switches>   
</switches>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bf085-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bf085-108">Attributes and Elements</span></span>  
 <span data-ttu-id="bf085-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bf085-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bf085-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bf085-110">Attributes</span></span>  
 <span data-ttu-id="bf085-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="bf085-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bf085-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bf085-112">Child Elements</span></span>  
  
|<span data-ttu-id="bf085-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="bf085-113">Element</span></span>|<span data-ttu-id="bf085-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bf085-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bf085-115">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="bf085-115">\<add></span></span>](add-element-for-switches.md)|<span data-ttu-id="bf085-116">Bir izleme anahtarının ayarlandığı düzeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="bf085-116">Specifies the level where a trace switch is set.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bf085-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bf085-117">Parent Elements</span></span>  
  
|<span data-ttu-id="bf085-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="bf085-118">Element</span></span>|<span data-ttu-id="bf085-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bf085-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="bf085-120">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="bf085-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.diagnostics`|<span data-ttu-id="bf085-121">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bf085-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf085-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bf085-122">Remarks</span></span>  
 <span data-ttu-id="bf085-123">Bir izleme anahtarı düzeyini bir yapılandırma dosyasına yerleştirerek değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf085-123">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="bf085-124">Anahtar bir <xref:System.Diagnostics.BooleanSwitch> ise, açıp kapatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf085-124">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="bf085-125">Anahtar bir <xref:System.Diagnostics.TraceSwitch> ise, uygulamanın çıkışları için izleme veya hata ayıklama iletilerinin türlerini belirtmek üzere buna farklı düzeyler atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf085-125">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf085-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="bf085-126">Example</span></span>  
 <span data-ttu-id="bf085-127">Aşağıdaki örnek, `General` izleme anahtarını <xref:System.Diagnostics.TraceLevel> düzeyine ayarlamak ve `Data` Boole izleme anahtarını etkinleştirmek için **\<Anahtar >** öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bf085-127">The following example shows how to use the **\<switch>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bf085-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf085-128">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="bf085-129">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="bf085-129">Trace and Debug Settings Schema</span></span>](index.md)
 