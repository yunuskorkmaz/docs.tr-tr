---
title: '&lt;appDomainResourceMonitoring&gt; öğesi'
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 11e892d8ab9001d3670c801b43ba444aa24b2e41
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltappdomainresourcemonitoringgt-element"></a><span data-ttu-id="5dbaa-102">&lt;appDomainResourceMonitoring&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="5dbaa-102">&lt;appDomainResourceMonitoring&gt; Element</span></span>
<span data-ttu-id="5dbaa-103">İşlem ömrü için işlemdeki tüm uygulama etki alanları istatistikleri toplamak için çalışma zamanı bildirir.</span><span class="sxs-lookup"><span data-stu-id="5dbaa-103">Instructs the runtime to collect statistics on all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="5dbaa-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="5dbaa-104">\<configuration></span></span>  
<span data-ttu-id="5dbaa-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="5dbaa-105">\<runtime></span></span>  
<span data-ttu-id="5dbaa-106">\<appDomainResourceMonitoring ></span><span class="sxs-lookup"><span data-stu-id="5dbaa-106">\<appDomainResourceMonitoring></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5dbaa-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5dbaa-107">Syntax</span></span>  
  
```xml  
<appDomainResourceMonitoring    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5dbaa-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5dbaa-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5dbaa-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5dbaa-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5dbaa-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5dbaa-110">Attributes</span></span>  
  
|<span data-ttu-id="5dbaa-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5dbaa-111">Attribute</span></span>|<span data-ttu-id="5dbaa-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5dbaa-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="5dbaa-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="5dbaa-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="5dbaa-114">Çalışma zamanı uygulama etki alanı kaynak izleme istatistiklerini toplayıp toplamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5dbaa-114">Specifies whether the runtime collects statistics for application domain resource monitoring.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="5dbaa-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5dbaa-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="5dbaa-116">Değer</span><span class="sxs-lookup"><span data-stu-id="5dbaa-116">Value</span></span>|<span data-ttu-id="5dbaa-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5dbaa-117">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="5dbaa-118">Uygulama etki alanı kaynak izleme istatistiklerini toplanır.</span><span class="sxs-lookup"><span data-stu-id="5dbaa-118">Statistics for application domain resource monitoring are collected.</span></span>|  
|`false`|<span data-ttu-id="5dbaa-119">Uygulama etki alanı kaynak izleme istatistiklerini toplanmadı.</span><span class="sxs-lookup"><span data-stu-id="5dbaa-119">Statistics for application domain resource monitoring are not collected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5dbaa-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5dbaa-120">Child Elements</span></span>  
 <span data-ttu-id="5dbaa-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="5dbaa-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5dbaa-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5dbaa-122">Parent Elements</span></span>  
  
|<span data-ttu-id="5dbaa-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="5dbaa-123">Element</span></span>|<span data-ttu-id="5dbaa-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5dbaa-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5dbaa-125">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="5dbaa-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="5dbaa-126">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="5dbaa-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5dbaa-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5dbaa-127">Remarks</span></span>  
 <span data-ttu-id="5dbaa-128">Uygulama etki alanı kaynak izleme kullanılabilir barındırma yönetilen uygulama etki alanı sınıfı [Iclrappdomainresourcemonitor](../../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) arabirimi ve olay izleme için Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="5dbaa-128">Application domain resource monitoring is available through the managed application domain class, the hosting [ICLRAppDomainResourceMonitor](../../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface, and event tracing for Windows (ETW).</span></span> <span data-ttu-id="5dbaa-129">İzleme etkinleştirildiğinde, istatistikleri işlem ömrü için işlemdeki tüm uygulama etki alanları için toplanır.</span><span class="sxs-lookup"><span data-stu-id="5dbaa-129">When monitoring is enabled, statistics are collected for all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="5dbaa-130">Yönetilen koddan izlemeyi etkinleştirmek için kullanın <xref:System.AppDomain.MonitoringIsEnabled%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="5dbaa-130">To enable monitoring from managed code, use the <xref:System.AppDomain.MonitoringIsEnabled%2A> property.</span></span>  
  
 <span data-ttu-id="5dbaa-131">Bu yapılandırma öğesi yalnızca kullanılabilir [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] ve daha sonra.</span><span class="sxs-lookup"><span data-stu-id="5dbaa-131">This configuration element is available only in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5dbaa-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="5dbaa-132">Example</span></span>  
 <span data-ttu-id="5dbaa-133">Aşağıdaki örnek, uygulama etki alanı kaynak izleme etkinleştirmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5dbaa-133">The following example shows how to enable application domain resource monitoring.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5dbaa-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5dbaa-134">See Also</span></span>  
 <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="5dbaa-135">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="5dbaa-135">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="5dbaa-136">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="5dbaa-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
