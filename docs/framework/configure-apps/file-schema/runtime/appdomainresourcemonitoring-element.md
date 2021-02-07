---
description: 'Daha fazla bilgi edinin: <appDomainResourceMonitoring> öğesi'
title: <appDomainResourceMonitoring> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
ms.openlocfilehash: aee85386e6d0af2ca4fd30c0ad8fe69bae240315
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719298"
---
# <a name="appdomainresourcemonitoring-element"></a><span data-ttu-id="070cf-103">\<appDomainResourceMonitoring> Öğesi</span><span class="sxs-lookup"><span data-stu-id="070cf-103">\<appDomainResourceMonitoring> Element</span></span>

<span data-ttu-id="070cf-104">Çalışma zamanına, işlemin ömrü boyunca işlemdeki tüm uygulama etki alanlarında istatistikler toplamasını söyler.</span><span class="sxs-lookup"><span data-stu-id="070cf-104">Instructs the runtime to collect statistics on all application domains in the process for the life of the process.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainResourceMonitoring>**  
  
## <a name="syntax"></a><span data-ttu-id="070cf-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="070cf-105">Syntax</span></span>  
  
```xml  
<appDomainResourceMonitoring
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="070cf-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="070cf-106">Attributes and Elements</span></span>  

 <span data-ttu-id="070cf-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="070cf-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="070cf-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="070cf-108">Attributes</span></span>  
  
|<span data-ttu-id="070cf-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="070cf-109">Attribute</span></span>|<span data-ttu-id="070cf-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="070cf-110">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="070cf-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="070cf-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="070cf-112">Çalışma zamanının uygulama etki alanı kaynak izleme istatistiklerini toplayıp toplamadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="070cf-112">Specifies whether the runtime collects statistics for application domain resource monitoring.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="070cf-113">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="070cf-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="070cf-114">Değer</span><span class="sxs-lookup"><span data-stu-id="070cf-114">Value</span></span>|<span data-ttu-id="070cf-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="070cf-115">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="070cf-116">Uygulama etki alanı kaynak izleme istatistikleri toplanır.</span><span class="sxs-lookup"><span data-stu-id="070cf-116">Statistics for application domain resource monitoring are collected.</span></span>|  
|`false`|<span data-ttu-id="070cf-117">Uygulama etki alanı kaynak izleme istatistikleri toplanmadı.</span><span class="sxs-lookup"><span data-stu-id="070cf-117">Statistics for application domain resource monitoring are not collected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="070cf-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="070cf-118">Child Elements</span></span>  

 <span data-ttu-id="070cf-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="070cf-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="070cf-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="070cf-120">Parent Elements</span></span>  
  
|<span data-ttu-id="070cf-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="070cf-121">Element</span></span>|<span data-ttu-id="070cf-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="070cf-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="070cf-123">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="070cf-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="070cf-124">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="070cf-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="070cf-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="070cf-125">Remarks</span></span>  

 <span data-ttu-id="070cf-126">Uygulama etki alanı kaynak izleme, yönetilen uygulama etki alanı sınıfı, barındırma [ıclartppdomainresourcemonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) arabirimi ve Windows için olay Izleme (ETW) ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="070cf-126">Application domain resource monitoring is available through the managed application domain class, the hosting [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface, and event tracing for Windows (ETW).</span></span> <span data-ttu-id="070cf-127">İzleme etkinleştirildiğinde, işlem süresince işlemdeki tüm uygulama etki alanları için istatistikler toplanır.</span><span class="sxs-lookup"><span data-stu-id="070cf-127">When monitoring is enabled, statistics are collected for all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="070cf-128">Yönetilen koddan izlemeyi etkinleştirmek için <xref:System.AppDomain.MonitoringIsEnabled%2A> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="070cf-128">To enable monitoring from managed code, use the <xref:System.AppDomain.MonitoringIsEnabled%2A> property.</span></span>  
  
 <span data-ttu-id="070cf-129">Bu yapılandırma öğesi yalnızca .NET Framework 4 ve üzeri sürümlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="070cf-129">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="070cf-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="070cf-130">Example</span></span>  

 <span data-ttu-id="070cf-131">Aşağıdaki örnekte, uygulama etki alanı kaynak izlemenin nasıl etkinleştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="070cf-131">The following example shows how to enable application domain resource monitoring.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="070cf-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="070cf-132">See also</span></span>

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="070cf-133">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="070cf-133">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="070cf-134">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="070cf-134">Configuration File Schema</span></span>](../index.md)
