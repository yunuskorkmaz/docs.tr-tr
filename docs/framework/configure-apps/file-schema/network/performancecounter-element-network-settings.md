---
title: <performanceCounter> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounter element
- <performanceCounter> element
ms.assetid: 3afa1586-e1b8-473d-8985-c3fc90cf561b
ms.openlocfilehash: 05aac6c1ed3c04bce263a45cafdb9bec906bd75b
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664058"
---
# <a name="performancecounter-element-network-settings"></a><span data-ttu-id="7155b-102">\<performanceCounter > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="7155b-102">\<performanceCounter> Element (Network Settings)</span></span>
<span data-ttu-id="7155b-103">Ağ performans sayaçlarını etkinleştirilir veya devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="7155b-103">Enables or disables networking performance counters.</span></span>  
  
 <span data-ttu-id="7155b-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="7155b-104">\<configuration></span></span>  
<span data-ttu-id="7155b-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="7155b-105">\<system.net></span></span>  
<span data-ttu-id="7155b-106">\<Ayarlar ></span><span class="sxs-lookup"><span data-stu-id="7155b-106">\<settings></span></span>  
<span data-ttu-id="7155b-107">\<performanceCounters ></span><span class="sxs-lookup"><span data-stu-id="7155b-107">\<performanceCounters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7155b-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7155b-108">Syntax</span></span>  
  
```xml  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7155b-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7155b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7155b-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7155b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7155b-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7155b-111">Attributes</span></span>  
  
|<span data-ttu-id="7155b-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7155b-112">Attribute</span></span>|<span data-ttu-id="7155b-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7155b-113">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="7155b-114">Ağ performans sayaçlarının etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7155b-114">Specifies whether the networking performance counters are enabled.</span></span> <span data-ttu-id="7155b-115">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="7155b-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7155b-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7155b-116">Child Elements</span></span>  
 <span data-ttu-id="7155b-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="7155b-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7155b-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7155b-118">Parent Elements</span></span>  
  
|<span data-ttu-id="7155b-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="7155b-119">Element</span></span>|<span data-ttu-id="7155b-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7155b-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7155b-121">Ayarlar</span><span class="sxs-lookup"><span data-stu-id="7155b-121">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="7155b-122"><xref:System.Net> Ad alanı için temel ağ seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="7155b-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7155b-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7155b-123">Remarks</span></span>  
 <span data-ttu-id="7155b-124">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7155b-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="7155b-125">Ağ performans sayaçlarının kullanılacak yapılandırma dosyasında etkinleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="7155b-125">Networking performance counters need to be enabled in the configuration file to be used.</span></span> <span data-ttu-id="7155b-126">Tüm ağ performans sayaçları, yapılandırma dosyasında tek bir ayarla etkin veya devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="7155b-126">All networking performance counters are enabled or disabled with a single setting in the configuration file.</span></span> <span data-ttu-id="7155b-127">Bireysel ağ performans sayaçları etkinleştirilemez veya devre dışı bırakılamaz.</span><span class="sxs-lookup"><span data-stu-id="7155b-127">Individual networking performance counters cannot be enabled or disabled.</span></span> <span data-ttu-id="7155b-128">Belirli ağ performans sayaçları hakkında daha fazla bilgi için bkz. [ağ performans sayaçları](../../../debug-trace-profile/performance-counters.md#networking).</span><span class="sxs-lookup"><span data-stu-id="7155b-128">For more information on the specific networking performance counters, see [Networking Performance Counters](../../../debug-trace-profile/performance-counters.md#networking).</span></span>  
  
 <span data-ttu-id="7155b-129">Varsayılan değer ağ performans sayaçlarının devre dışı bırakıldığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7155b-129">The default value is that networking performance counters are disabled.</span></span>  
  
 <span data-ttu-id="7155b-130">Özelliği <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> , geçerli yapılandırma dosyalarından **etkin** özniteliğin geçerli değerini almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7155b-130">The <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> property can be used to get the current value of the **enabled** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7155b-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="7155b-131">Example</span></span>  
 <span data-ttu-id="7155b-132">Aşağıdaki örnek, ağ performans sayaçlarını etkinleştirmek için <xref:System.Net> ve ilgili ad alanlarının nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7155b-132">The following example shows how to configure the <xref:System.Net> and related namespaces to enable networking performance counters.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7155b-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7155b-133">See also</span></span>

- <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="7155b-134">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="7155b-134">Network Settings Schema</span></span>](index.md)
- [<span data-ttu-id="7155b-135">Ağ performans sayaçları</span><span class="sxs-lookup"><span data-stu-id="7155b-135">Networking Performance Counters</span></span>](../../../debug-trace-profile/performance-counters.md#networking)
