---
title: <appDomainResourceMonitoring> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
ms.openlocfilehash: 3c6092b6c34bb13c0ad0e66df2d3b7e65ac3de7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154382"
---
# <a name="appdomainresourcemonitoring-element"></a><span data-ttu-id="ee03a-102">\<appDomainResourceMonitoring> Elemanı</span><span class="sxs-lookup"><span data-stu-id="ee03a-102">\<appDomainResourceMonitoring> Element</span></span>
<span data-ttu-id="ee03a-103">Çalışma zamanının, işlemin ömrü boyunca işlemdeki tüm uygulama etki alanlarının istatistiklerini toplamasını bildirir.</span><span class="sxs-lookup"><span data-stu-id="ee03a-103">Instructs the runtime to collect statistics on all application domains in the process for the life of the process.</span></span>  
  
<span data-ttu-id="ee03a-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ee03a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ee03a-105">&nbsp;&nbsp;[**\<çalışma zamanı>**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="ee03a-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="ee03a-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainResourceMonitoring>**</span><span class="sxs-lookup"><span data-stu-id="ee03a-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainResourceMonitoring>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee03a-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ee03a-107">Syntax</span></span>  
  
```xml  
<appDomainResourceMonitoring
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ee03a-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ee03a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ee03a-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ee03a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ee03a-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ee03a-110">Attributes</span></span>  
  
|<span data-ttu-id="ee03a-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ee03a-111">Attribute</span></span>|<span data-ttu-id="ee03a-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ee03a-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="ee03a-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="ee03a-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="ee03a-114">Çalışma zamanının uygulama etki alanı kaynak izleme istatistikleritoplayıp toplayıp toplamadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ee03a-114">Specifies whether the runtime collects statistics for application domain resource monitoring.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="ee03a-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ee03a-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="ee03a-116">Değer</span><span class="sxs-lookup"><span data-stu-id="ee03a-116">Value</span></span>|<span data-ttu-id="ee03a-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ee03a-117">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="ee03a-118">Uygulama etki alanı kaynak izleme istatistikleri toplanır.</span><span class="sxs-lookup"><span data-stu-id="ee03a-118">Statistics for application domain resource monitoring are collected.</span></span>|  
|`false`|<span data-ttu-id="ee03a-119">Uygulama etki alanı kaynak izleme istatistikleri toplanmaz.</span><span class="sxs-lookup"><span data-stu-id="ee03a-119">Statistics for application domain resource monitoring are not collected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ee03a-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ee03a-120">Child Elements</span></span>  
 <span data-ttu-id="ee03a-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="ee03a-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ee03a-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ee03a-122">Parent Elements</span></span>  
  
|<span data-ttu-id="ee03a-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="ee03a-123">Element</span></span>|<span data-ttu-id="ee03a-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ee03a-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ee03a-125">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="ee03a-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ee03a-126">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="ee03a-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee03a-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ee03a-127">Remarks</span></span>  
 <span data-ttu-id="ee03a-128">Uygulama etki alanı kaynak izleme yönetilen uygulama etki alanı sınıfı, barındırma [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) arayüzü ve Windows (ETW) için olay izleme üzerinden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ee03a-128">Application domain resource monitoring is available through the managed application domain class, the hosting [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface, and event tracing for Windows (ETW).</span></span> <span data-ttu-id="ee03a-129">İzleme etkinleştirildiğinde, işlem sürecindeki tüm uygulama etki alanları için istatistikler toplanır.</span><span class="sxs-lookup"><span data-stu-id="ee03a-129">When monitoring is enabled, statistics are collected for all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="ee03a-130">Yönetilen koddan izleme sağlamak için <xref:System.AppDomain.MonitoringIsEnabled%2A> özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="ee03a-130">To enable monitoring from managed code, use the <xref:System.AppDomain.MonitoringIsEnabled%2A> property.</span></span>  
  
 <span data-ttu-id="ee03a-131">Bu yapılandırma öğesi yalnızca .NET Framework 4 ve sonraki yerlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ee03a-131">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee03a-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="ee03a-132">Example</span></span>  
 <span data-ttu-id="ee03a-133">Aşağıdaki örnek, uygulama etki alanı kaynak izleme etkinleştirmek için nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="ee03a-133">The following example shows how to enable application domain resource monitoring.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ee03a-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee03a-134">See also</span></span>

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="ee03a-135">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="ee03a-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ee03a-136">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="ee03a-136">Configuration File Schema</span></span>](../index.md)
