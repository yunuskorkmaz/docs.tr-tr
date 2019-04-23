---
title: <appDomainResourceMonitoring> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71cc69eba17de8465cc7999f334c724e4ec14e7d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59224383"
---
# <a name="appdomainresourcemonitoring-element"></a><span data-ttu-id="9fbd1-102">\<appDomainResourceMonitoring > öğesi</span><span class="sxs-lookup"><span data-stu-id="9fbd1-102">\<appDomainResourceMonitoring> Element</span></span>
<span data-ttu-id="9fbd1-103">Ömür işlemin işlemdeki tüm uygulama etki alanlarında istatistikleri toplamak için çalışma zamanı bildirir.</span><span class="sxs-lookup"><span data-stu-id="9fbd1-103">Instructs the runtime to collect statistics on all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="9fbd1-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="9fbd1-104">\<configuration></span></span>  
<span data-ttu-id="9fbd1-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="9fbd1-105">\<runtime></span></span>  
<span data-ttu-id="9fbd1-106">\<appDomainResourceMonitoring ></span><span class="sxs-lookup"><span data-stu-id="9fbd1-106">\<appDomainResourceMonitoring></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fbd1-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9fbd1-107">Syntax</span></span>  
  
```xml  
<appDomainResourceMonitoring    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9fbd1-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9fbd1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9fbd1-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9fbd1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9fbd1-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9fbd1-110">Attributes</span></span>  
  
|<span data-ttu-id="9fbd1-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9fbd1-111">Attribute</span></span>|<span data-ttu-id="9fbd1-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9fbd1-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="9fbd1-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="9fbd1-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="9fbd1-114">Çalışma zamanı istatistikleri uygulama etki alanı kaynak izleme toplayıp toplamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9fbd1-114">Specifies whether the runtime collects statistics for application domain resource monitoring.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="9fbd1-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9fbd1-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="9fbd1-116">Değer</span><span class="sxs-lookup"><span data-stu-id="9fbd1-116">Value</span></span>|<span data-ttu-id="9fbd1-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9fbd1-117">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="9fbd1-118">Uygulama etki alanı kaynak izleme için İstatistikler toplanır.</span><span class="sxs-lookup"><span data-stu-id="9fbd1-118">Statistics for application domain resource monitoring are collected.</span></span>|  
|`false`|<span data-ttu-id="9fbd1-119">Uygulama etki alanı kaynak izleme istatistiklerini toplanmadı.</span><span class="sxs-lookup"><span data-stu-id="9fbd1-119">Statistics for application domain resource monitoring are not collected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9fbd1-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9fbd1-120">Child Elements</span></span>  
 <span data-ttu-id="9fbd1-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="9fbd1-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9fbd1-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9fbd1-122">Parent Elements</span></span>  
  
|<span data-ttu-id="9fbd1-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="9fbd1-123">Element</span></span>|<span data-ttu-id="9fbd1-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9fbd1-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9fbd1-125">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="9fbd1-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="9fbd1-126">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="9fbd1-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9fbd1-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9fbd1-127">Remarks</span></span>  
 <span data-ttu-id="9fbd1-128">Uygulama etki alanı kaynak izleme, barındırma yönetilen uygulama etki alanı sınıfı kullanılabilir [Iclrappdomainresourcemonitor](../../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) arabirimi ve olay izleme için Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="9fbd1-128">Application domain resource monitoring is available through the managed application domain class, the hosting [ICLRAppDomainResourceMonitor](../../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface, and event tracing for Windows (ETW).</span></span> <span data-ttu-id="9fbd1-129">İzleme etkin olduğunda istatistikleri ömrü işlemin işlemdeki tüm uygulama etki alanları için toplanır.</span><span class="sxs-lookup"><span data-stu-id="9fbd1-129">When monitoring is enabled, statistics are collected for all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="9fbd1-130">Yönetilen koddan izlemeyi etkinleştirmek için <xref:System.AppDomain.MonitoringIsEnabled%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="9fbd1-130">To enable monitoring from managed code, use the <xref:System.AppDomain.MonitoringIsEnabled%2A> property.</span></span>  
  
 <span data-ttu-id="9fbd1-131">Bu yapılandırma öğesi yalnızca [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] ve daha sonra.</span><span class="sxs-lookup"><span data-stu-id="9fbd1-131">This configuration element is available only in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9fbd1-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="9fbd1-132">Example</span></span>  
 <span data-ttu-id="9fbd1-133">Aşağıdaki örnek, uygulama etki alanı kaynak izleme etkinleştirmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9fbd1-133">The following example shows how to enable application domain resource monitoring.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9fbd1-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9fbd1-134">See also</span></span>

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="9fbd1-135">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="9fbd1-135">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="9fbd1-136">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="9fbd1-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
