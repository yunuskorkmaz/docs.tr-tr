---
title: '&lt;appDomainResourceMonitoring&gt; öğesi'
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 32ffe48e7a65ab4ca2250eee65d188c0c7270c11
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53611340"
---
# <a name="ltappdomainresourcemonitoringgt-element"></a><span data-ttu-id="d3eef-102">&lt;appDomainResourceMonitoring&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="d3eef-102">&lt;appDomainResourceMonitoring&gt; Element</span></span>
<span data-ttu-id="d3eef-103">Ömür işlemin işlemdeki tüm uygulama etki alanlarında istatistikleri toplamak için çalışma zamanı bildirir.</span><span class="sxs-lookup"><span data-stu-id="d3eef-103">Instructs the runtime to collect statistics on all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="d3eef-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="d3eef-104">\<configuration></span></span>  
<span data-ttu-id="d3eef-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="d3eef-105">\<runtime></span></span>  
<span data-ttu-id="d3eef-106">\<appDomainResourceMonitoring ></span><span class="sxs-lookup"><span data-stu-id="d3eef-106">\<appDomainResourceMonitoring></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3eef-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d3eef-107">Syntax</span></span>  
  
```xml  
<appDomainResourceMonitoring    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d3eef-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d3eef-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d3eef-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d3eef-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d3eef-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d3eef-110">Attributes</span></span>  
  
|<span data-ttu-id="d3eef-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d3eef-111">Attribute</span></span>|<span data-ttu-id="d3eef-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3eef-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="d3eef-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d3eef-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="d3eef-114">Çalışma zamanı istatistikleri uygulama etki alanı kaynak izleme toplayıp toplamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d3eef-114">Specifies whether the runtime collects statistics for application domain resource monitoring.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="d3eef-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d3eef-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="d3eef-116">Değer</span><span class="sxs-lookup"><span data-stu-id="d3eef-116">Value</span></span>|<span data-ttu-id="d3eef-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3eef-117">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="d3eef-118">Uygulama etki alanı kaynak izleme için İstatistikler toplanır.</span><span class="sxs-lookup"><span data-stu-id="d3eef-118">Statistics for application domain resource monitoring are collected.</span></span>|  
|`false`|<span data-ttu-id="d3eef-119">Uygulama etki alanı kaynak izleme istatistiklerini toplanmadı.</span><span class="sxs-lookup"><span data-stu-id="d3eef-119">Statistics for application domain resource monitoring are not collected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d3eef-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d3eef-120">Child Elements</span></span>  
 <span data-ttu-id="d3eef-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="d3eef-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d3eef-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d3eef-122">Parent Elements</span></span>  
  
|<span data-ttu-id="d3eef-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="d3eef-123">Element</span></span>|<span data-ttu-id="d3eef-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3eef-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d3eef-125">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="d3eef-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d3eef-126">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="d3eef-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3eef-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d3eef-127">Remarks</span></span>  
 <span data-ttu-id="d3eef-128">Uygulama etki alanı kaynak izleme, barındırma yönetilen uygulama etki alanı sınıfı kullanılabilir [Iclrappdomainresourcemonitor](../../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) arabirimi ve olay izleme için Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="d3eef-128">Application domain resource monitoring is available through the managed application domain class, the hosting [ICLRAppDomainResourceMonitor](../../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface, and event tracing for Windows (ETW).</span></span> <span data-ttu-id="d3eef-129">İzleme etkin olduğunda istatistikleri ömrü işlemin işlemdeki tüm uygulama etki alanları için toplanır.</span><span class="sxs-lookup"><span data-stu-id="d3eef-129">When monitoring is enabled, statistics are collected for all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="d3eef-130">Yönetilen koddan izlemeyi etkinleştirmek için <xref:System.AppDomain.MonitoringIsEnabled%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="d3eef-130">To enable monitoring from managed code, use the <xref:System.AppDomain.MonitoringIsEnabled%2A> property.</span></span>  
  
 <span data-ttu-id="d3eef-131">Bu yapılandırma öğesi yalnızca [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] ve daha sonra.</span><span class="sxs-lookup"><span data-stu-id="d3eef-131">This configuration element is available only in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3eef-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="d3eef-132">Example</span></span>  
 <span data-ttu-id="d3eef-133">Aşağıdaki örnek, uygulama etki alanı kaynak izleme etkinleştirmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d3eef-133">The following example shows how to enable application domain resource monitoring.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d3eef-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d3eef-134">See Also</span></span>  
- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="d3eef-135">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="d3eef-135">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [<span data-ttu-id="d3eef-136">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="d3eef-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
