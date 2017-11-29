---
title: ICLRAppDomainResourceMonitor Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAppDomainResourceMonitor
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAppDomainResourceMonitor
helpviewer_keywords: ICLRAppDomainResourceMonitor interface [.NET Framework hosting]
ms.assetid: 72fa83a1-8997-41d7-b355-ab177a24a303
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f2cb7fd41e3f5b192974d61ddd9cf2b5845690ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrappdomainresourcemonitor-interface"></a><span data-ttu-id="187a8-102">ICLRAppDomainResourceMonitor Arabirimi</span><span class="sxs-lookup"><span data-stu-id="187a8-102">ICLRAppDomainResourceMonitor Interface</span></span>
<span data-ttu-id="187a8-103">Bir uygulama etki alanının bellek ve CPU kullanımını denetleme yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="187a8-103">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="187a8-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="187a8-104">Methods</span></span>  
  
|<span data-ttu-id="187a8-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="187a8-105">Method</span></span>|<span data-ttu-id="187a8-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="187a8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="187a8-107">GetCurrentAllocated yöntemi</span><span class="sxs-lookup"><span data-stu-id="187a8-107">GetCurrentAllocated Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentallocated-method.md)|<span data-ttu-id="187a8-108">Atık olarak toplanmış bellek çıkarılmasıyla olmadan oluşturulduktan sonra uygulama etki alanı tarafından yapılan tüm bellek ayırmaları bayt cinsinden toplam boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="187a8-108">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>|  
|[<span data-ttu-id="187a8-109">GetCurrentSurvived yöntemi</span><span class="sxs-lookup"><span data-stu-id="187a8-109">GetCurrentSurvived Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md)|<span data-ttu-id="187a8-110">Çöp toplama engelleme son tam, derdi bitti ve geçerli uygulama etki alanı tarafından başvurulan bayt sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="187a8-110">Gets the number of bytes that survived the last full, blocking garbage collection and that are referenced by the current application domain.</span></span>|  
|[<span data-ttu-id="187a8-111">GetCurrentCpuTime yöntemi</span><span class="sxs-lookup"><span data-stu-id="187a8-111">GetCurrentCpuTime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentcputime-method.md)|<span data-ttu-id="187a8-112">Uygulama etki alanı oluşturulduktan sonra geçerli uygulama etki alanında yürütülürken tüm iş parçacıkları tarafından kullanılmış olan toplam işlemci zamanı alır.</span><span class="sxs-lookup"><span data-stu-id="187a8-112">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="187a8-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="187a8-113">Remarks</span></span>  
 <span data-ttu-id="187a8-114">`ICLRAppDomainResourceMonitor` Arabirimi aşağıdaki yönetilen özelliklerine benzer işlevsellik sağlar:</span><span class="sxs-lookup"><span data-stu-id="187a8-114">The `ICLRAppDomainResourceMonitor` interface provides functionality that is similar to the following managed properties:</span></span>  
  
-   <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType>  
  
## <a name="requirements"></a><span data-ttu-id="187a8-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="187a8-115">Requirements</span></span>  
 <span data-ttu-id="187a8-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="187a8-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="187a8-117">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="187a8-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="187a8-118">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="187a8-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="187a8-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="187a8-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="187a8-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="187a8-120">See Also</span></span>  
 [<span data-ttu-id="187a8-121">\<appDomainResourceMonitoring > öğesi</span><span class="sxs-lookup"><span data-stu-id="187a8-121">\<appDomainResourceMonitoring> Element</span></span>](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)  
 [<span data-ttu-id="187a8-122">Uygulama etki alanı kaynak izleme</span><span class="sxs-lookup"><span data-stu-id="187a8-122">Application Domain Resource Monitoring</span></span>](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)  
 [<span data-ttu-id="187a8-123">Barındırma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="187a8-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="187a8-124">Barındırma</span><span class="sxs-lookup"><span data-stu-id="187a8-124">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
