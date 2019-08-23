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
ms.openlocfilehash: 597381c8ab31e86a02f870a24f165676d200b66e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965022"
---
# <a name="iclrappdomainresourcemonitor-interface"></a><span data-ttu-id="47022-102">ICLRAppDomainResourceMonitor Arabirimi</span><span class="sxs-lookup"><span data-stu-id="47022-102">ICLRAppDomainResourceMonitor Interface</span></span>
<span data-ttu-id="47022-103">Bir uygulama etki alanının belleğini ve CPU kullanımını denetleyen yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="47022-103">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="47022-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="47022-104">Methods</span></span>  
  
|<span data-ttu-id="47022-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="47022-105">Method</span></span>|<span data-ttu-id="47022-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="47022-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="47022-107">GetCurrentAllocated Yöntemi</span><span class="sxs-lookup"><span data-stu-id="47022-107">GetCurrentAllocated Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentallocated-method.md)|<span data-ttu-id="47022-108">, Atık olarak toplanmış olan belleği çıkarmadan, uygulama etki alanı tarafından yapılan tüm bellek ayırmalarının bayt cinsinden toplam boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="47022-108">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>|  
|[<span data-ttu-id="47022-109">GetCurrentSurvived Yöntemi</span><span class="sxs-lookup"><span data-stu-id="47022-109">GetCurrentSurvived Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md)|<span data-ttu-id="47022-110">Son tam ve çöp toplamayı engelleyen ve geçerli uygulama etki alanı tarafından başvurulan bayt sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="47022-110">Gets the number of bytes that survived the last full, blocking garbage collection and that are referenced by the current application domain.</span></span>|  
|[<span data-ttu-id="47022-111">GetCurrentCpuTime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="47022-111">GetCurrentCpuTime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentcputime-method.md)|<span data-ttu-id="47022-112">Uygulama etki alanı oluşturulduğundan bu yana geçerli uygulama etki alanında yürütme sırasında tüm iş parçacıkları tarafından kullanılan toplam işlemci süresini alır.</span><span class="sxs-lookup"><span data-stu-id="47022-112">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47022-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="47022-113">Remarks</span></span>  
 <span data-ttu-id="47022-114">`ICLRAppDomainResourceMonitor` Arabirimi, aşağıdaki yönetilen özelliklere benzer işlevler sağlar:</span><span class="sxs-lookup"><span data-stu-id="47022-114">The `ICLRAppDomainResourceMonitor` interface provides functionality that is similar to the following managed properties:</span></span>  
  
- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType>  
  
## <a name="requirements"></a><span data-ttu-id="47022-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="47022-115">Requirements</span></span>  
 <span data-ttu-id="47022-116">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47022-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47022-117">**Üst bilgi** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="47022-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="47022-118">**Kitaplığı** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="47022-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="47022-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47022-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47022-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47022-120">See also</span></span>

- [<span data-ttu-id="47022-121">\<appDomainResourceMonitoring > öğesi</span><span class="sxs-lookup"><span data-stu-id="47022-121">\<appDomainResourceMonitoring> Element</span></span>](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)
- [<span data-ttu-id="47022-122">Uygulama Etki Alanı Kaynak İzleme</span><span class="sxs-lookup"><span data-stu-id="47022-122">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="47022-123">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="47022-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="47022-124">Barındırma</span><span class="sxs-lookup"><span data-stu-id="47022-124">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
