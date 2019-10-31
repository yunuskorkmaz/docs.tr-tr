---
title: <appDomainResourceMonitoring> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
ms.openlocfilehash: 991833500cae4d96e9c28f7e94ca366e9b976a9d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73118250"
---
# <a name="appdomainresourcemonitoring-element"></a><span data-ttu-id="d9ee5-102">\<appDomainResourceMonitoring > öğesi</span><span class="sxs-lookup"><span data-stu-id="d9ee5-102">\<appDomainResourceMonitoring> Element</span></span>
<span data-ttu-id="d9ee5-103">Çalışma zamanına, işlemin ömrü boyunca işlemdeki tüm uygulama etki alanlarında istatistikler toplamasını söyler.</span><span class="sxs-lookup"><span data-stu-id="d9ee5-103">Instructs the runtime to collect statistics on all application domains in the process for the life of the process.</span></span>  
  
<span data-ttu-id="d9ee5-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="d9ee5-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d9ee5-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="d9ee5-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="d9ee5-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<appDomainResourceMonitoring >**</span><span class="sxs-lookup"><span data-stu-id="d9ee5-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainResourceMonitoring>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9ee5-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d9ee5-107">Syntax</span></span>  
  
```xml  
<appDomainResourceMonitoring    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d9ee5-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d9ee5-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d9ee5-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d9ee5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d9ee5-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d9ee5-110">Attributes</span></span>  
  
|<span data-ttu-id="d9ee5-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d9ee5-111">Attribute</span></span>|<span data-ttu-id="d9ee5-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d9ee5-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="d9ee5-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d9ee5-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="d9ee5-114">Çalışma zamanının uygulama etki alanı kaynak izleme istatistiklerini toplayıp toplamadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d9ee5-114">Specifies whether the runtime collects statistics for application domain resource monitoring.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="d9ee5-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d9ee5-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="d9ee5-116">Değer</span><span class="sxs-lookup"><span data-stu-id="d9ee5-116">Value</span></span>|<span data-ttu-id="d9ee5-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d9ee5-117">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="d9ee5-118">Uygulama etki alanı kaynak izleme istatistikleri toplanır.</span><span class="sxs-lookup"><span data-stu-id="d9ee5-118">Statistics for application domain resource monitoring are collected.</span></span>|  
|`false`|<span data-ttu-id="d9ee5-119">Uygulama etki alanı kaynak izleme istatistikleri toplanmadı.</span><span class="sxs-lookup"><span data-stu-id="d9ee5-119">Statistics for application domain resource monitoring are not collected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d9ee5-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d9ee5-120">Child Elements</span></span>  
 <span data-ttu-id="d9ee5-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="d9ee5-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d9ee5-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d9ee5-122">Parent Elements</span></span>  
  
|<span data-ttu-id="d9ee5-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="d9ee5-123">Element</span></span>|<span data-ttu-id="d9ee5-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d9ee5-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d9ee5-125">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="d9ee5-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d9ee5-126">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="d9ee5-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9ee5-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d9ee5-127">Remarks</span></span>  
 <span data-ttu-id="d9ee5-128">Uygulama etki alanı kaynak izleme, yönetilen uygulama etki alanı sınıfı, barındırma [ıclartppdomainresourcemonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) arabirimi ve Windows için olay Izleme (ETW) ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d9ee5-128">Application domain resource monitoring is available through the managed application domain class, the hosting [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface, and event tracing for Windows (ETW).</span></span> <span data-ttu-id="d9ee5-129">İzleme etkinleştirildiğinde, işlem süresince işlemdeki tüm uygulama etki alanları için istatistikler toplanır.</span><span class="sxs-lookup"><span data-stu-id="d9ee5-129">When monitoring is enabled, statistics are collected for all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="d9ee5-130">Yönetilen koddan izlemeyi etkinleştirmek için <xref:System.AppDomain.MonitoringIsEnabled%2A> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d9ee5-130">To enable monitoring from managed code, use the <xref:System.AppDomain.MonitoringIsEnabled%2A> property.</span></span>  
  
 <span data-ttu-id="d9ee5-131">Bu yapılandırma öğesi yalnızca .NET Framework 4 ve üzeri sürümlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d9ee5-131">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9ee5-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="d9ee5-132">Example</span></span>  
 <span data-ttu-id="d9ee5-133">Aşağıdaki örnekte, uygulama etki alanı kaynak izlemenin nasıl etkinleştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d9ee5-133">The following example shows how to enable application domain resource monitoring.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d9ee5-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9ee5-134">See also</span></span>

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="d9ee5-135">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="d9ee5-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d9ee5-136">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="d9ee5-136">Configuration File Schema</span></span>](../index.md)
