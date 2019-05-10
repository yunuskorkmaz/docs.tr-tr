---
title: ICLRAppDomainResourceMonitor Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor
helpviewer_keywords:
- ICLRAppDomainResourceMonitor interface [.NET Framework hosting]
ms.assetid: 72fa83a1-8997-41d7-b355-ab177a24a303
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f336ac45e4bf5894c667412ff89acde4b9524c80
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64666062"
---
# <a name="iclrappdomainresourcemonitor-interface"></a><span data-ttu-id="cc0fe-102">ICLRAppDomainResourceMonitor Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cc0fe-102">ICLRAppDomainResourceMonitor Interface</span></span>
<span data-ttu-id="cc0fe-103">Bir uygulama etki alanının bellek ve CPU kullanımını denetlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="cc0fe-103">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cc0fe-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cc0fe-104">Methods</span></span>  
  
|<span data-ttu-id="cc0fe-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="cc0fe-105">Method</span></span>|<span data-ttu-id="cc0fe-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cc0fe-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cc0fe-107">GetCurrentAllocated Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cc0fe-107">GetCurrentAllocated Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentallocated-method.md)|<span data-ttu-id="cc0fe-108">Toplam boyutu bayt cinsinden, atık olarak toplanmış bellek çıkararak olmadan oluşturulduktan sonra uygulama etki alanı tarafından yapılan tüm bellek ayırmaları alır.</span><span class="sxs-lookup"><span data-stu-id="cc0fe-108">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>|  
|[<span data-ttu-id="cc0fe-109">GetCurrentSurvived Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cc0fe-109">GetCurrentSurvived Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md)|<span data-ttu-id="cc0fe-110">Atık toplamayı engelleme son tam kurtulan ve geçerli uygulama etki alanı tarafından başvurulan bayt sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="cc0fe-110">Gets the number of bytes that survived the last full, blocking garbage collection and that are referenced by the current application domain.</span></span>|  
|[<span data-ttu-id="cc0fe-111">GetCurrentCpuTime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cc0fe-111">GetCurrentCpuTime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentcputime-method.md)|<span data-ttu-id="cc0fe-112">Geçerli uygulama etki alanında, uygulama etki alanı oluşturulmasından bu yana yürütülürken tüm iş parçacıkları tarafından kullanılmış olan toplam işlemci zamanı alır.</span><span class="sxs-lookup"><span data-stu-id="cc0fe-112">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc0fe-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cc0fe-113">Remarks</span></span>  
 <span data-ttu-id="cc0fe-114">`ICLRAppDomainResourceMonitor` Arabirimi aşağıdaki yönetilen özelliklerine benzer işlevsellik sağlar:</span><span class="sxs-lookup"><span data-stu-id="cc0fe-114">The `ICLRAppDomainResourceMonitor` interface provides functionality that is similar to the following managed properties:</span></span>  
  
- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType>  
  
## <a name="requirements"></a><span data-ttu-id="cc0fe-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cc0fe-115">Requirements</span></span>  
 <span data-ttu-id="cc0fe-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc0fe-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc0fe-117">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="cc0fe-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="cc0fe-118">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="cc0fe-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cc0fe-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc0fe-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc0fe-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc0fe-120">See also</span></span>

- [<span data-ttu-id="cc0fe-121">\<appDomainResourceMonitoring > öğesi</span><span class="sxs-lookup"><span data-stu-id="cc0fe-121">\<appDomainResourceMonitoring> Element</span></span>](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)
- [<span data-ttu-id="cc0fe-122">Uygulama Etki Alanı Kaynak İzleme</span><span class="sxs-lookup"><span data-stu-id="cc0fe-122">Application Domain Resource Monitoring</span></span>](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="cc0fe-123">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cc0fe-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="cc0fe-124">Barındırma</span><span class="sxs-lookup"><span data-stu-id="cc0fe-124">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
