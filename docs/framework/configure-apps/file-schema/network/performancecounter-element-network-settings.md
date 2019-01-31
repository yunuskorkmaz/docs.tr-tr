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
ms.openlocfilehash: 4603a942788d31a049196fb699d07a13551fa443
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55279766"
---
# <a name="performancecounter-element-network-settings"></a><span data-ttu-id="34c9a-102">\<performanceCounter > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="34c9a-102">\<performanceCounter> Element (Network Settings)</span></span>
<span data-ttu-id="34c9a-103">Etkinleştirir veya ağ performans sayaçları devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="34c9a-103">Enables or disables networking performance counters.</span></span>  
  
 <span data-ttu-id="34c9a-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="34c9a-104">\<configuration></span></span>  
<span data-ttu-id="34c9a-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="34c9a-105">\<system.net></span></span>  
<span data-ttu-id="34c9a-106">\<Ayarlar ></span><span class="sxs-lookup"><span data-stu-id="34c9a-106">\<settings></span></span>  
<span data-ttu-id="34c9a-107">\<performanceCounters ></span><span class="sxs-lookup"><span data-stu-id="34c9a-107">\<performanceCounters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34c9a-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="34c9a-108">Syntax</span></span>  
  
```xml  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="34c9a-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="34c9a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="34c9a-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="34c9a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="34c9a-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="34c9a-111">Attributes</span></span>  
  
|<span data-ttu-id="34c9a-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="34c9a-112">Attribute</span></span>|<span data-ttu-id="34c9a-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34c9a-113">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="34c9a-114">Ağ performans sayaçlarının etkin olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="34c9a-114">Specifies whether the networking performance counters are enabled.</span></span> <span data-ttu-id="34c9a-115">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="34c9a-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="34c9a-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="34c9a-116">Child Elements</span></span>  
 <span data-ttu-id="34c9a-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="34c9a-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="34c9a-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="34c9a-118">Parent Elements</span></span>  
  
|<span data-ttu-id="34c9a-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="34c9a-119">Element</span></span>|<span data-ttu-id="34c9a-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34c9a-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="34c9a-121">Ayarlar</span><span class="sxs-lookup"><span data-stu-id="34c9a-121">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="34c9a-122">Temel ağ seçeneklerini yapılandırır <xref:System.Net> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="34c9a-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34c9a-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="34c9a-123">Remarks</span></span>  
 <span data-ttu-id="34c9a-124">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="34c9a-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="34c9a-125">Ağ performans sayaçları yapılandırma dosyasında kullanılacak etkinleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="34c9a-125">Networking performance counters need to be enabled in the configuration file to be used.</span></span> <span data-ttu-id="34c9a-126">Tüm ağ performans sayaçları etkin veya yapılandırma dosyasında tek bir ayarı ile devre dışı.</span><span class="sxs-lookup"><span data-stu-id="34c9a-126">All networking performance counters are enabled or disabled with a single setting in the configuration file.</span></span> <span data-ttu-id="34c9a-127">Ağ performans sayaçları tek etkin veya devre dışı.</span><span class="sxs-lookup"><span data-stu-id="34c9a-127">Individual networking performance counters cannot be enabled or disabled.</span></span> <span data-ttu-id="34c9a-128">Belirli ağ performans sayaçları hakkında daha fazla bilgi için bkz. [ağ performans sayaçları](../../../../../docs/framework/debug-trace-profile/performance-counters.md#networking).</span><span class="sxs-lookup"><span data-stu-id="34c9a-128">For more information on the specific networking performance counters, see [Networking Performance Counters](../../../../../docs/framework/debug-trace-profile/performance-counters.md#networking).</span></span>  
  
 <span data-ttu-id="34c9a-129">Ağ performans sayaçları devre dışı bırakıldı varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="34c9a-129">The default value is that networking performance counters are disabled.</span></span>  
  
 <span data-ttu-id="34c9a-130"><xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> Özelliği, geçerli değerini almak için kullanılabilir **etkin** ilgili yapılandırma dosyaları özniteliği.</span><span class="sxs-lookup"><span data-stu-id="34c9a-130">The <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> property can be used to get the current value of the **enabled** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34c9a-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="34c9a-131">Example</span></span>  
 <span data-ttu-id="34c9a-132">Aşağıdaki örnek nasıl yapılandırılacağı gösterilmektedir <xref:System.Net> ve ilgili ağ performans sayaçları etkinleştirmek için ad alanları.</span><span class="sxs-lookup"><span data-stu-id="34c9a-132">The following example shows how to configure the <xref:System.Net> and related namespaces to enable networking performance counters.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="34c9a-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34c9a-133">See also</span></span>
- <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="34c9a-134">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="34c9a-134">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
- [<span data-ttu-id="34c9a-135">Ağ performans sayaçları</span><span class="sxs-lookup"><span data-stu-id="34c9a-135">Networking Performance Counters</span></span>](../../../../../docs/framework/debug-trace-profile/performance-counters.md#networking)
