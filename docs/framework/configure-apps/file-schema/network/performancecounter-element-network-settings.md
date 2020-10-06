---
title: <performanceCounters> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounters element
ms.assetid: 3afa1586-e1b8-473d-8985-c3fc90cf561b
ms.openlocfilehash: 584bdafbbd60303401cbc6ad96b8654fe11c7077
ms.sourcegitcommit: a8a205034eeffc7c3e1bdd6f506a75b0f7099ebf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91756266"
---
# <a name="performancecounters-element-network-settings"></a><span data-ttu-id="10f6d-102">\<performanceCounters> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="10f6d-102">\<performanceCounters> Element (Network Settings)</span></span>

<span data-ttu-id="10f6d-103">Ağ performans sayaçlarını etkinleştirilir veya devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="10f6d-103">Enables or disables networking performance counters.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<performanceCounters>**

## <a name="syntax"></a><span data-ttu-id="10f6d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="10f6d-104">Syntax</span></span>  
  
```xml  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="10f6d-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="10f6d-105">Attributes and Elements</span></span>  

 <span data-ttu-id="10f6d-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="10f6d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="10f6d-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="10f6d-107">Attributes</span></span>  
  
|<span data-ttu-id="10f6d-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="10f6d-108">Attribute</span></span>|<span data-ttu-id="10f6d-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10f6d-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="10f6d-110">Ağ performans sayaçlarının etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="10f6d-110">Specifies whether the networking performance counters are enabled.</span></span> <span data-ttu-id="10f6d-111">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="10f6d-111">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="10f6d-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="10f6d-112">Child Elements</span></span>  

 <span data-ttu-id="10f6d-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="10f6d-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="10f6d-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="10f6d-114">Parent Elements</span></span>  
  
|<span data-ttu-id="10f6d-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="10f6d-115">Element</span></span>|<span data-ttu-id="10f6d-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10f6d-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="10f6d-117">ayarlar</span><span class="sxs-lookup"><span data-stu-id="10f6d-117">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="10f6d-118">Ad alanı için temel ağ seçeneklerini yapılandırır <xref:System.Net> .</span><span class="sxs-lookup"><span data-stu-id="10f6d-118">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10f6d-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="10f6d-119">Remarks</span></span>  

 <span data-ttu-id="10f6d-120">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="10f6d-120">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="10f6d-121">Ağ performans sayaçlarının kullanılacak yapılandırma dosyasında etkinleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="10f6d-121">Networking performance counters need to be enabled in the configuration file to be used.</span></span> <span data-ttu-id="10f6d-122">Tüm ağ performans sayaçları, yapılandırma dosyasında tek bir ayarla etkin veya devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="10f6d-122">All networking performance counters are enabled or disabled with a single setting in the configuration file.</span></span> <span data-ttu-id="10f6d-123">Bireysel ağ performans sayaçları etkinleştirilemez veya devre dışı bırakılamaz.</span><span class="sxs-lookup"><span data-stu-id="10f6d-123">Individual networking performance counters cannot be enabled or disabled.</span></span> <span data-ttu-id="10f6d-124">Belirli ağ performans sayaçları hakkında daha fazla bilgi için bkz. [ağ performans sayaçları](../../../debug-trace-profile/performance-counters.md#networking-performance-counters).</span><span class="sxs-lookup"><span data-stu-id="10f6d-124">For more information on the specific networking performance counters, see [Networking performance counters](../../../debug-trace-profile/performance-counters.md#networking-performance-counters).</span></span>  
  
 <span data-ttu-id="10f6d-125">Varsayılan değer ağ performans sayaçlarının devre dışı bırakıldığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="10f6d-125">The default value is that networking performance counters are disabled.</span></span>  
  
 <span data-ttu-id="10f6d-126"><xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>Özelliği, geçerli yapılandırma dosyalarından **etkin** özniteliğin geçerli değerini almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="10f6d-126">The <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> property can be used to get the current value of the **enabled** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10f6d-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="10f6d-127">Example</span></span>  

 <span data-ttu-id="10f6d-128">Aşağıdaki örnek, <xref:System.Net> ağ performans sayaçlarını etkinleştirmek için ve ilgili ad alanlarının nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="10f6d-128">The following example shows how to configure the <xref:System.Net> and related namespaces to enable networking performance counters.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="10f6d-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10f6d-129">See also</span></span>

- <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="10f6d-130">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="10f6d-130">Network Settings Schema</span></span>](index.md)
- [<span data-ttu-id="10f6d-131">Ağ performans sayaçları</span><span class="sxs-lookup"><span data-stu-id="10f6d-131">Networking Performance Counters</span></span>](../../../debug-trace-profile/performance-counters.md#networking-performance-counters)
