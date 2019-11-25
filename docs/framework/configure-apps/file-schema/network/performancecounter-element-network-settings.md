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
ms.openlocfilehash: 58a2bf5118a3a2cd9c33301eca5dcc751c2351bf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283085"
---
# <a name="performancecounter-element-network-settings"></a><span data-ttu-id="6c1ff-102">\<performanceCounter > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="6c1ff-102">\<performanceCounter> Element (Network Settings)</span></span>
<span data-ttu-id="6c1ff-103">Ağ performans sayaçlarını etkinleştirilir veya devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="6c1ff-103">Enables or disables networking performance counters.</span></span>  

<span data-ttu-id="6c1ff-104">[ **\<yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6c1ff-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6c1ff-105">[**System. net >\<** ](system-net-element-network-settings.md) &nbsp;&nbsp;</span><span class="sxs-lookup"><span data-stu-id="6c1ff-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="6c1ff-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ayarları >** ](settings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="6c1ff-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)</span></span>\
<span data-ttu-id="6c1ff-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<performanceCounters >**</span><span class="sxs-lookup"><span data-stu-id="6c1ff-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<performanceCounters>**</span></span>

## <a name="syntax"></a><span data-ttu-id="6c1ff-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6c1ff-108">Syntax</span></span>  
  
```xml  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6c1ff-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6c1ff-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6c1ff-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6c1ff-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6c1ff-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6c1ff-111">Attributes</span></span>  
  
|<span data-ttu-id="6c1ff-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6c1ff-112">Attribute</span></span>|<span data-ttu-id="6c1ff-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c1ff-113">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="6c1ff-114">Ağ performans sayaçlarının etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c1ff-114">Specifies whether the networking performance counters are enabled.</span></span> <span data-ttu-id="6c1ff-115">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c1ff-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6c1ff-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6c1ff-116">Child Elements</span></span>  
 <span data-ttu-id="6c1ff-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="6c1ff-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6c1ff-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6c1ff-118">Parent Elements</span></span>  
  
|<span data-ttu-id="6c1ff-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="6c1ff-119">Element</span></span>|<span data-ttu-id="6c1ff-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c1ff-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6c1ff-121">Ayarlar</span><span class="sxs-lookup"><span data-stu-id="6c1ff-121">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="6c1ff-122"><xref:System.Net> ad alanı için temel ağ seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="6c1ff-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c1ff-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6c1ff-123">Remarks</span></span>  
 <span data-ttu-id="6c1ff-124">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6c1ff-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="6c1ff-125">Ağ performans sayaçlarının kullanılacak yapılandırma dosyasında etkinleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="6c1ff-125">Networking performance counters need to be enabled in the configuration file to be used.</span></span> <span data-ttu-id="6c1ff-126">Tüm ağ performans sayaçları, yapılandırma dosyasında tek bir ayarla etkin veya devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="6c1ff-126">All networking performance counters are enabled or disabled with a single setting in the configuration file.</span></span> <span data-ttu-id="6c1ff-127">Bireysel ağ performans sayaçları etkinleştirilemez veya devre dışı bırakılamaz.</span><span class="sxs-lookup"><span data-stu-id="6c1ff-127">Individual networking performance counters cannot be enabled or disabled.</span></span> <span data-ttu-id="6c1ff-128">Belirli ağ performans sayaçları hakkında daha fazla bilgi için bkz. [ağ performans sayaçları](../../../debug-trace-profile/performance-counters.md#networking-performance-counters).</span><span class="sxs-lookup"><span data-stu-id="6c1ff-128">For more information on the specific networking performance counters, see [Networking performance counters](../../../debug-trace-profile/performance-counters.md#networking-performance-counters).</span></span>  
  
 <span data-ttu-id="6c1ff-129">Varsayılan değer ağ performans sayaçlarının devre dışı bırakıldığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6c1ff-129">The default value is that networking performance counters are disabled.</span></span>  
  
 <span data-ttu-id="6c1ff-130"><xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> özelliği, geçerli yapılandırma dosyalarından **etkin** özniteliğin geçerli değerini almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6c1ff-130">The <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> property can be used to get the current value of the **enabled** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c1ff-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="6c1ff-131">Example</span></span>  
 <span data-ttu-id="6c1ff-132">Aşağıdaki örnek, ağ performans sayaçlarını etkinleştirmek üzere <xref:System.Net> ve ilgili ad alanlarının nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6c1ff-132">The following example shows how to configure the <xref:System.Net> and related namespaces to enable networking performance counters.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6c1ff-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c1ff-133">See also</span></span>

- <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="6c1ff-134">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="6c1ff-134">Network Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6c1ff-135">Ağ performans sayaçları</span><span class="sxs-lookup"><span data-stu-id="6c1ff-135">Networking Performance Counters</span></span>](../../../debug-trace-profile/performance-counters.md#networking-performance-counters)
