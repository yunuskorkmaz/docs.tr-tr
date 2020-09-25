---
title: <appDomainResourceMonitoring> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
ms.openlocfilehash: 9ecf2e382b5d483377df871835793219b3f74760
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91170278"
---
# <a name="appdomainresourcemonitoring-element"></a><span data-ttu-id="9b6f1-102">\<appDomainResourceMonitoring> Öğesi</span><span class="sxs-lookup"><span data-stu-id="9b6f1-102">\<appDomainResourceMonitoring> Element</span></span>

<span data-ttu-id="9b6f1-103">Çalışma zamanına, işlemin ömrü boyunca işlemdeki tüm uygulama etki alanlarında istatistikler toplamasını söyler.</span><span class="sxs-lookup"><span data-stu-id="9b6f1-103">Instructs the runtime to collect statistics on all application domains in the process for the life of the process.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainResourceMonitoring>**  
  
## <a name="syntax"></a><span data-ttu-id="9b6f1-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="9b6f1-104">Syntax</span></span>  
  
```xml  
<appDomainResourceMonitoring
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9b6f1-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9b6f1-105">Attributes and Elements</span></span>  

 <span data-ttu-id="9b6f1-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9b6f1-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9b6f1-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9b6f1-107">Attributes</span></span>  
  
|<span data-ttu-id="9b6f1-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9b6f1-108">Attribute</span></span>|<span data-ttu-id="9b6f1-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9b6f1-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="9b6f1-110">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="9b6f1-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="9b6f1-111">Çalışma zamanının uygulama etki alanı kaynak izleme istatistiklerini toplayıp toplamadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9b6f1-111">Specifies whether the runtime collects statistics for application domain resource monitoring.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="9b6f1-112">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9b6f1-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="9b6f1-113">Değer</span><span class="sxs-lookup"><span data-stu-id="9b6f1-113">Value</span></span>|<span data-ttu-id="9b6f1-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9b6f1-114">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="9b6f1-115">Uygulama etki alanı kaynak izleme istatistikleri toplanır.</span><span class="sxs-lookup"><span data-stu-id="9b6f1-115">Statistics for application domain resource monitoring are collected.</span></span>|  
|`false`|<span data-ttu-id="9b6f1-116">Uygulama etki alanı kaynak izleme istatistikleri toplanmadı.</span><span class="sxs-lookup"><span data-stu-id="9b6f1-116">Statistics for application domain resource monitoring are not collected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9b6f1-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9b6f1-117">Child Elements</span></span>  

 <span data-ttu-id="9b6f1-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="9b6f1-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9b6f1-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9b6f1-119">Parent Elements</span></span>  
  
|<span data-ttu-id="9b6f1-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="9b6f1-120">Element</span></span>|<span data-ttu-id="9b6f1-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9b6f1-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9b6f1-122">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="9b6f1-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="9b6f1-123">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="9b6f1-123">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9b6f1-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9b6f1-124">Remarks</span></span>  

 <span data-ttu-id="9b6f1-125">Uygulama etki alanı kaynak izleme, yönetilen uygulama etki alanı sınıfı, barındırma [ıclartppdomainresourcemonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) arabirimi ve Windows için olay Izleme (ETW) ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9b6f1-125">Application domain resource monitoring is available through the managed application domain class, the hosting [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface, and event tracing for Windows (ETW).</span></span> <span data-ttu-id="9b6f1-126">İzleme etkinleştirildiğinde, işlem süresince işlemdeki tüm uygulama etki alanları için istatistikler toplanır.</span><span class="sxs-lookup"><span data-stu-id="9b6f1-126">When monitoring is enabled, statistics are collected for all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="9b6f1-127">Yönetilen koddan izlemeyi etkinleştirmek için <xref:System.AppDomain.MonitoringIsEnabled%2A> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="9b6f1-127">To enable monitoring from managed code, use the <xref:System.AppDomain.MonitoringIsEnabled%2A> property.</span></span>  
  
 <span data-ttu-id="9b6f1-128">Bu yapılandırma öğesi yalnızca .NET Framework 4 ve üzeri sürümlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9b6f1-128">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b6f1-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="9b6f1-129">Example</span></span>  

 <span data-ttu-id="9b6f1-130">Aşağıdaki örnekte, uygulama etki alanı kaynak izlemenin nasıl etkinleştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9b6f1-130">The following example shows how to enable application domain resource monitoring.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9b6f1-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9b6f1-131">See also</span></span>

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="9b6f1-132">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="9b6f1-132">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="9b6f1-133">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="9b6f1-133">Configuration File Schema</span></span>](../index.md)
