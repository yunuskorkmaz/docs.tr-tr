---
description: 'Daha fazla bilgi edinin: <performanceCounters> öğesi (ağ ayarları)'
title: <performanceCounters> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounters element
ms.assetid: 3afa1586-e1b8-473d-8985-c3fc90cf561b
ms.openlocfilehash: a923ba2420bd15e33f4564a196854fdf9e130e12
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99804120"
---
# <a name="performancecounters-element-network-settings"></a><span data-ttu-id="dfc54-103">\<performanceCounters> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="dfc54-103">\<performanceCounters> Element (Network Settings)</span></span>

<span data-ttu-id="dfc54-104">Ağ performans sayaçlarını etkinleştirilir veya devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="dfc54-104">Enables or disables networking performance counters.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<performanceCounters>**

## <a name="syntax"></a><span data-ttu-id="dfc54-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="dfc54-105">Syntax</span></span>  
  
```xml  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dfc54-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="dfc54-106">Attributes and Elements</span></span>  

 <span data-ttu-id="dfc54-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dfc54-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dfc54-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="dfc54-108">Attributes</span></span>  
  
|<span data-ttu-id="dfc54-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="dfc54-109">Attribute</span></span>|<span data-ttu-id="dfc54-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dfc54-110">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="dfc54-111">Ağ performans sayaçlarının etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="dfc54-111">Specifies whether the networking performance counters are enabled.</span></span> <span data-ttu-id="dfc54-112">`false` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="dfc54-112">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dfc54-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="dfc54-113">Child Elements</span></span>  

 <span data-ttu-id="dfc54-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="dfc54-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dfc54-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="dfc54-115">Parent Elements</span></span>  
  
|<span data-ttu-id="dfc54-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="dfc54-116">Element</span></span>|<span data-ttu-id="dfc54-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dfc54-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dfc54-118">ayarlar</span><span class="sxs-lookup"><span data-stu-id="dfc54-118">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="dfc54-119">Ad alanı için temel ağ seçeneklerini yapılandırır <xref:System.Net> .</span><span class="sxs-lookup"><span data-stu-id="dfc54-119">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dfc54-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dfc54-120">Remarks</span></span>  

 <span data-ttu-id="dfc54-121">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dfc54-121">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="dfc54-122">Ağ performans sayaçlarının kullanılacak yapılandırma dosyasında etkinleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="dfc54-122">Networking performance counters need to be enabled in the configuration file to be used.</span></span> <span data-ttu-id="dfc54-123">Tüm ağ performans sayaçları, yapılandırma dosyasında tek bir ayarla etkin veya devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="dfc54-123">All networking performance counters are enabled or disabled with a single setting in the configuration file.</span></span> <span data-ttu-id="dfc54-124">Bireysel ağ performans sayaçları etkinleştirilemez veya devre dışı bırakılamaz.</span><span class="sxs-lookup"><span data-stu-id="dfc54-124">Individual networking performance counters cannot be enabled or disabled.</span></span> <span data-ttu-id="dfc54-125">Belirli ağ performans sayaçları hakkında daha fazla bilgi için bkz. [ağ performans sayaçları](../../../debug-trace-profile/performance-counters.md#networking-performance-counters).</span><span class="sxs-lookup"><span data-stu-id="dfc54-125">For more information on the specific networking performance counters, see [Networking performance counters](../../../debug-trace-profile/performance-counters.md#networking-performance-counters).</span></span>  
  
 <span data-ttu-id="dfc54-126">Varsayılan değer ağ performans sayaçlarının devre dışı bırakıldığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="dfc54-126">The default value is that networking performance counters are disabled.</span></span>  
  
 <span data-ttu-id="dfc54-127"><xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>Özelliği, geçerli yapılandırma dosyalarından **etkin** özniteliğin geçerli değerini almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dfc54-127">The <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> property can be used to get the current value of the **enabled** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dfc54-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="dfc54-128">Example</span></span>  

 <span data-ttu-id="dfc54-129">Aşağıdaki örnek, <xref:System.Net> ağ performans sayaçlarını etkinleştirmek için ve ilgili ad alanlarının nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="dfc54-129">The following example shows how to configure the <xref:System.Net> and related namespaces to enable networking performance counters.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <performanceCounters  
        enabled="true"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dfc54-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dfc54-130">See also</span></span>

- <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="dfc54-131">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="dfc54-131">Network Settings Schema</span></span>](index.md)
- [<span data-ttu-id="dfc54-132">Ağ performans sayaçları</span><span class="sxs-lookup"><span data-stu-id="dfc54-132">Networking Performance Counters</span></span>](../../../debug-trace-profile/performance-counters.md#networking-performance-counters)
