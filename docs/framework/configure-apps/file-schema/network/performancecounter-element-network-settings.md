---
title: "&lt;performanceCounter&gt; öğesi (ağ ayarları)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounter element
- <performanceCounter> element
ms.assetid: 3afa1586-e1b8-473d-8985-c3fc90cf561b
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 669811b20fd9980b6876683ec7eff4c235a676ef
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltperformancecountergt-element-network-settings"></a><span data-ttu-id="07a0e-102">&lt;performanceCounter&gt; öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="07a0e-102">&lt;performanceCounter&gt; Element (Network Settings)</span></span>
<span data-ttu-id="07a0e-103">Etkinleştirir veya ağ performans sayaçları devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="07a0e-103">Enables or disables networking performance counters.</span></span>  
  
 <span data-ttu-id="07a0e-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="07a0e-104">\<configuration></span></span>  
<span data-ttu-id="07a0e-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="07a0e-105">\<system.net></span></span>  
<span data-ttu-id="07a0e-106">\<Ayarlar ></span><span class="sxs-lookup"><span data-stu-id="07a0e-106">\<settings></span></span>  
<span data-ttu-id="07a0e-107">\<performans sayaçları ></span><span class="sxs-lookup"><span data-stu-id="07a0e-107">\<performanceCounters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07a0e-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="07a0e-108">Syntax</span></span>  
  
```xml  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="07a0e-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="07a0e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="07a0e-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="07a0e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="07a0e-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="07a0e-111">Attributes</span></span>  
  
|<span data-ttu-id="07a0e-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="07a0e-112">Attribute</span></span>|<span data-ttu-id="07a0e-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07a0e-113">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="07a0e-114">Ağ performans sayaçlarını etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="07a0e-114">Specifies whether the networking performance counters are enabled.</span></span> <span data-ttu-id="07a0e-115">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="07a0e-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="07a0e-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="07a0e-116">Child Elements</span></span>  
 <span data-ttu-id="07a0e-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="07a0e-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="07a0e-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="07a0e-118">Parent Elements</span></span>  
  
|<span data-ttu-id="07a0e-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="07a0e-119">Element</span></span>|<span data-ttu-id="07a0e-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07a0e-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="07a0e-121">Ayarlar</span><span class="sxs-lookup"><span data-stu-id="07a0e-121">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="07a0e-122">Temel ağ seçeneklerini yapılandırır <xref:System.Net> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="07a0e-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="07a0e-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="07a0e-123">Remarks</span></span>  
 <span data-ttu-id="07a0e-124">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="07a0e-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="07a0e-125">Ağ performans sayaçları yapılandırma dosyasında kullanılacak etkinleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="07a0e-125">Networking performance counters need to be enabled in the configuration file to be used.</span></span> <span data-ttu-id="07a0e-126">Tüm ağ performans sayaçlarını etkin veya yapılandırma dosyasında tek bir ayar ile devre dışı.</span><span class="sxs-lookup"><span data-stu-id="07a0e-126">All networking performance counters are enabled or disabled with a single setting in the configuration file.</span></span> <span data-ttu-id="07a0e-127">Performans sayaçları ağ tek etkin veya devre dışı.</span><span class="sxs-lookup"><span data-stu-id="07a0e-127">Individual networking performance counters cannot be enabled or disabled.</span></span> <span data-ttu-id="07a0e-128">Belirli ağ performans sayaçları hakkında daha fazla bilgi için bkz: [ağ performans sayaçları](http://msdn.microsoft.com/en-us/d1860235-f643-46ae-846c-ff0ed8b0e3cd).</span><span class="sxs-lookup"><span data-stu-id="07a0e-128">For more information on the specific networking performance counters, see [Networking Performance Counters](http://msdn.microsoft.com/en-us/d1860235-f643-46ae-846c-ff0ed8b0e3cd).</span></span>  
  
 <span data-ttu-id="07a0e-129">Ağ performans sayaçları devre dışı bırakıldı varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="07a0e-129">The default value is that networking performance counters are disabled.</span></span>  
  
 <span data-ttu-id="07a0e-130"><xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> Özelliği, geçerli değerini almak için kullanılabilir **etkin** geçerli yapılandırma dosyalarını özniteliği.</span><span class="sxs-lookup"><span data-stu-id="07a0e-130">The <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> property can be used to get the current value of the **enabled** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07a0e-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="07a0e-131">Example</span></span>  
 <span data-ttu-id="07a0e-132">Aşağıdaki örnekte nasıl yapılandırılacağını gösterir <xref:System.Net> ve ilgili ağ performans sayaçlarını etkinleştirmek için ad alanları.</span><span class="sxs-lookup"><span data-stu-id="07a0e-132">The following example shows how to configure the <xref:System.Net> and related namespaces to enable networking performance counters.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="07a0e-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="07a0e-133">See Also</span></span>  
 <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="07a0e-134">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="07a0e-134">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)  
 [<span data-ttu-id="07a0e-135">Ağ performans sayaçları</span><span class="sxs-lookup"><span data-stu-id="07a0e-135">Networking Performance Counters</span></span>](http://msdn.microsoft.com/en-us/d1860235-f643-46ae-846c-ff0ed8b0e3cd)
