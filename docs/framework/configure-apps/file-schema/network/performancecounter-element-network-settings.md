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
ms.openlocfilehash: 3fe6b19d0055aafad859b55960800d9786d7fa08
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697996"
---
# <a name="performancecounter-element-network-settings"></a><span data-ttu-id="6d6bd-102">\<performanceCounter > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="6d6bd-102">\<performanceCounter> Element (Network Settings)</span></span>
<span data-ttu-id="6d6bd-103">Ağ performans sayaçlarını etkinleştirilir veya devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="6d6bd-103">Enables or disables networking performance counters.</span></span>  
  
[<span data-ttu-id="6d6bd-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="6d6bd-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="6d6bd-105">&nbsp; @ no__t-1[ **@no__t -4system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="6d6bd-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="6d6bd-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<settings >** ](settings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="6d6bd-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)</span></span>  
<span data-ttu-id="6d6bd-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<performanceCounters >**</span><span class="sxs-lookup"><span data-stu-id="6d6bd-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<performanceCounters>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d6bd-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6d6bd-108">Syntax</span></span>  
  
```xml  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6d6bd-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6d6bd-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6d6bd-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6d6bd-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6d6bd-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6d6bd-111">Attributes</span></span>  
  
|<span data-ttu-id="6d6bd-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6d6bd-112">Attribute</span></span>|<span data-ttu-id="6d6bd-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6d6bd-113">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="6d6bd-114">Ağ performans sayaçlarının etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6d6bd-114">Specifies whether the networking performance counters are enabled.</span></span> <span data-ttu-id="6d6bd-115">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6d6bd-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6d6bd-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6d6bd-116">Child Elements</span></span>  
 <span data-ttu-id="6d6bd-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="6d6bd-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6d6bd-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6d6bd-118">Parent Elements</span></span>  
  
|<span data-ttu-id="6d6bd-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="6d6bd-119">Element</span></span>|<span data-ttu-id="6d6bd-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6d6bd-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6d6bd-121">Ayarlar</span><span class="sxs-lookup"><span data-stu-id="6d6bd-121">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="6d6bd-122">@No__t-0 ad alanı için temel ağ seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="6d6bd-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d6bd-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6d6bd-123">Remarks</span></span>  
 <span data-ttu-id="6d6bd-124">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6d6bd-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="6d6bd-125">Ağ performans sayaçlarının kullanılacak yapılandırma dosyasında etkinleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="6d6bd-125">Networking performance counters need to be enabled in the configuration file to be used.</span></span> <span data-ttu-id="6d6bd-126">Tüm ağ performans sayaçları, yapılandırma dosyasında tek bir ayarla etkin veya devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="6d6bd-126">All networking performance counters are enabled or disabled with a single setting in the configuration file.</span></span> <span data-ttu-id="6d6bd-127">Bireysel ağ performans sayaçları etkinleştirilemez veya devre dışı bırakılamaz.</span><span class="sxs-lookup"><span data-stu-id="6d6bd-127">Individual networking performance counters cannot be enabled or disabled.</span></span> <span data-ttu-id="6d6bd-128">Belirli ağ performans sayaçları hakkında daha fazla bilgi için bkz. [ağ performans sayaçları](../../../debug-trace-profile/performance-counters.md#networking).</span><span class="sxs-lookup"><span data-stu-id="6d6bd-128">For more information on the specific networking performance counters, see [Networking Performance Counters](../../../debug-trace-profile/performance-counters.md#networking).</span></span>  
  
 <span data-ttu-id="6d6bd-129">Varsayılan değer ağ performans sayaçlarının devre dışı bırakıldığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6d6bd-129">The default value is that networking performance counters are disabled.</span></span>  
  
 <span data-ttu-id="6d6bd-130">@No__t-0 özelliği, geçerli yapılandırma dosyalarından **etkin** özniteliğin geçerli değerini almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6d6bd-130">The <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> property can be used to get the current value of the **enabled** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d6bd-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="6d6bd-131">Example</span></span>  
 <span data-ttu-id="6d6bd-132">Aşağıdaki örnek, ağ performans sayaçlarını etkinleştirmek üzere <xref:System.Net> ve ilgili ad alanlarının nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6d6bd-132">The following example shows how to configure the <xref:System.Net> and related namespaces to enable networking performance counters.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6d6bd-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d6bd-133">See also</span></span>

- <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="6d6bd-134">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="6d6bd-134">Network Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6d6bd-135">Ağ performans sayaçları</span><span class="sxs-lookup"><span data-stu-id="6d6bd-135">Networking Performance Counters</span></span>](../../../debug-trace-profile/performance-counters.md#networking)
