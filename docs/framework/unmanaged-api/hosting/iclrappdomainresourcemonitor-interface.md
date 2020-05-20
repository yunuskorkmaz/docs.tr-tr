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
ms.openlocfilehash: 08dc0f0891d960cb7b402b30455e606aaff7bcea
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616014"
---
# <a name="iclrappdomainresourcemonitor-interface"></a><span data-ttu-id="772fc-102">ICLRAppDomainResourceMonitor Arabirimi</span><span class="sxs-lookup"><span data-stu-id="772fc-102">ICLRAppDomainResourceMonitor Interface</span></span>
<span data-ttu-id="772fc-103">Bir uygulama etki alanının belleğini ve CPU kullanımını denetleyen yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="772fc-103">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="772fc-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="772fc-104">Methods</span></span>  
  
|<span data-ttu-id="772fc-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="772fc-105">Method</span></span>|<span data-ttu-id="772fc-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="772fc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="772fc-107">GetCurrentAllocated Yöntemi</span><span class="sxs-lookup"><span data-stu-id="772fc-107">GetCurrentAllocated Method</span></span>](iclrappdomainresourcemonitor-getcurrentallocated-method.md)|<span data-ttu-id="772fc-108">, Atık olarak toplanmış olan belleği çıkarmadan, uygulama etki alanı tarafından yapılan tüm bellek ayırmalarının bayt cinsinden toplam boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="772fc-108">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>|  
|[<span data-ttu-id="772fc-109">GetCurrentSurvived Yöntemi</span><span class="sxs-lookup"><span data-stu-id="772fc-109">GetCurrentSurvived Method</span></span>](iclrappdomainresourcemonitor-getcurrentsurvived-method.md)|<span data-ttu-id="772fc-110">Son tam ve çöp toplamayı engelleyen ve geçerli uygulama etki alanı tarafından başvurulan bayt sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="772fc-110">Gets the number of bytes that survived the last full, blocking garbage collection and that are referenced by the current application domain.</span></span>|  
|[<span data-ttu-id="772fc-111">GetCurrentCpuTime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="772fc-111">GetCurrentCpuTime Method</span></span>](iclrappdomainresourcemonitor-getcurrentcputime-method.md)|<span data-ttu-id="772fc-112">Uygulama etki alanı oluşturulduğundan bu yana geçerli uygulama etki alanında yürütme sırasında tüm iş parçacıkları tarafından kullanılan toplam işlemci süresini alır.</span><span class="sxs-lookup"><span data-stu-id="772fc-112">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="772fc-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="772fc-113">Remarks</span></span>  
 <span data-ttu-id="772fc-114">`ICLRAppDomainResourceMonitor`Arabirimi, aşağıdaki yönetilen özelliklere benzer işlevler sağlar:</span><span class="sxs-lookup"><span data-stu-id="772fc-114">The `ICLRAppDomainResourceMonitor` interface provides functionality that is similar to the following managed properties:</span></span>  
  
- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType>  
  
## <a name="requirements"></a><span data-ttu-id="772fc-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="772fc-115">Requirements</span></span>  
 <span data-ttu-id="772fc-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="772fc-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="772fc-117">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="772fc-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="772fc-118">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="772fc-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="772fc-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="772fc-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="772fc-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="772fc-120">See also</span></span>

- [<span data-ttu-id="772fc-121">\<appDomainResourceMonitoring> öğesi</span><span class="sxs-lookup"><span data-stu-id="772fc-121">\<appDomainResourceMonitoring> Element</span></span>](../../configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)
- [<span data-ttu-id="772fc-122">Uygulama etki alanı kaynak Izleme</span><span class="sxs-lookup"><span data-stu-id="772fc-122">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="772fc-123">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="772fc-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="772fc-124">Barındırma</span><span class="sxs-lookup"><span data-stu-id="772fc-124">Hosting</span></span>](index.md)
