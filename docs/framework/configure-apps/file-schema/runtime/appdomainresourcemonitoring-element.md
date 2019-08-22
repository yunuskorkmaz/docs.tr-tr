---
title: <appDomainResourceMonitoring> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b82be30c18cde361aa412ee1b631c8368c8de1b3
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663925"
---
# <a name="appdomainresourcemonitoring-element"></a><span data-ttu-id="c6d94-102">\<appDomainResourceMonitoring > öğesi</span><span class="sxs-lookup"><span data-stu-id="c6d94-102">\<appDomainResourceMonitoring> Element</span></span>
<span data-ttu-id="c6d94-103">Çalışma zamanına, işlemin ömrü boyunca işlemdeki tüm uygulama etki alanlarında istatistikler toplamasını söyler.</span><span class="sxs-lookup"><span data-stu-id="c6d94-103">Instructs the runtime to collect statistics on all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="c6d94-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="c6d94-104">\<configuration></span></span>  
<span data-ttu-id="c6d94-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="c6d94-105">\<runtime></span></span>  
<span data-ttu-id="c6d94-106">\<appDomainResourceMonitoring ></span><span class="sxs-lookup"><span data-stu-id="c6d94-106">\<appDomainResourceMonitoring></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6d94-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c6d94-107">Syntax</span></span>  
  
```xml  
<appDomainResourceMonitoring    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c6d94-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c6d94-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c6d94-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c6d94-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c6d94-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c6d94-110">Attributes</span></span>  
  
|<span data-ttu-id="c6d94-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c6d94-111">Attribute</span></span>|<span data-ttu-id="c6d94-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6d94-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="c6d94-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="c6d94-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="c6d94-114">Çalışma zamanının uygulama etki alanı kaynak izleme istatistiklerini toplayıp toplamadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c6d94-114">Specifies whether the runtime collects statistics for application domain resource monitoring.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="c6d94-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c6d94-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="c6d94-116">Değer</span><span class="sxs-lookup"><span data-stu-id="c6d94-116">Value</span></span>|<span data-ttu-id="c6d94-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6d94-117">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="c6d94-118">Uygulama etki alanı kaynak izleme istatistikleri toplanır.</span><span class="sxs-lookup"><span data-stu-id="c6d94-118">Statistics for application domain resource monitoring are collected.</span></span>|  
|`false`|<span data-ttu-id="c6d94-119">Uygulama etki alanı kaynak izleme istatistikleri toplanmadı.</span><span class="sxs-lookup"><span data-stu-id="c6d94-119">Statistics for application domain resource monitoring are not collected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c6d94-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c6d94-120">Child Elements</span></span>  
 <span data-ttu-id="c6d94-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="c6d94-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c6d94-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c6d94-122">Parent Elements</span></span>  
  
|<span data-ttu-id="c6d94-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="c6d94-123">Element</span></span>|<span data-ttu-id="c6d94-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6d94-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c6d94-125">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="c6d94-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="c6d94-126">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="c6d94-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6d94-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c6d94-127">Remarks</span></span>  
 <span data-ttu-id="c6d94-128">Uygulama etki alanı kaynak izleme, yönetilen uygulama etki alanı sınıfı, barındırma [ıclartppdomainresourcemonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) arabirimi ve Windows için olay Izleme (ETW) ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c6d94-128">Application domain resource monitoring is available through the managed application domain class, the hosting [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface, and event tracing for Windows (ETW).</span></span> <span data-ttu-id="c6d94-129">İzleme etkinleştirildiğinde, işlem süresince işlemdeki tüm uygulama etki alanları için istatistikler toplanır.</span><span class="sxs-lookup"><span data-stu-id="c6d94-129">When monitoring is enabled, statistics are collected for all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="c6d94-130">Yönetilen koddan izlemeyi etkinleştirmek için <xref:System.AppDomain.MonitoringIsEnabled%2A> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c6d94-130">To enable monitoring from managed code, use the <xref:System.AppDomain.MonitoringIsEnabled%2A> property.</span></span>  
  
 <span data-ttu-id="c6d94-131">Bu yapılandırma öğesi yalnızca .NET Framework 4 ve üzeri sürümlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c6d94-131">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6d94-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="c6d94-132">Example</span></span>  
 <span data-ttu-id="c6d94-133">Aşağıdaki örnekte, uygulama etki alanı kaynak izlemenin nasıl etkinleştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c6d94-133">The following example shows how to enable application domain resource monitoring.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c6d94-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6d94-134">See also</span></span>

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="c6d94-135">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="c6d94-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c6d94-136">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="c6d94-136">Configuration File Schema</span></span>](../index.md)
