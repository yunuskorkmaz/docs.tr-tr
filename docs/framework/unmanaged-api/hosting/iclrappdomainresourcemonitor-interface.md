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
ms.openlocfilehash: 84c53f0666d0e04b898e28c1d8e146eab566ca1b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674703"
---
# <a name="iclrappdomainresourcemonitor-interface"></a><span data-ttu-id="1d0bc-102">ICLRAppDomainResourceMonitor Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1d0bc-102">ICLRAppDomainResourceMonitor Interface</span></span>

<span data-ttu-id="1d0bc-103">Bir uygulama etki alanının belleğini ve CPU kullanımını denetleyen yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="1d0bc-103">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1d0bc-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1d0bc-104">Methods</span></span>  
  
|<span data-ttu-id="1d0bc-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1d0bc-105">Method</span></span>|<span data-ttu-id="1d0bc-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1d0bc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1d0bc-107">GetCurrentAllocated Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1d0bc-107">GetCurrentAllocated Method</span></span>](iclrappdomainresourcemonitor-getcurrentallocated-method.md)|<span data-ttu-id="1d0bc-108">, Atık olarak toplanmış olan belleği çıkarmadan, uygulama etki alanı tarafından yapılan tüm bellek ayırmalarının bayt cinsinden toplam boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="1d0bc-108">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>|  
|[<span data-ttu-id="1d0bc-109">GetCurrentSurvived Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1d0bc-109">GetCurrentSurvived Method</span></span>](iclrappdomainresourcemonitor-getcurrentsurvived-method.md)|<span data-ttu-id="1d0bc-110">Son tam ve çöp toplamayı engelleyen ve geçerli uygulama etki alanı tarafından başvurulan bayt sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="1d0bc-110">Gets the number of bytes that survived the last full, blocking garbage collection and that are referenced by the current application domain.</span></span>|  
|[<span data-ttu-id="1d0bc-111">GetCurrentCpuTime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1d0bc-111">GetCurrentCpuTime Method</span></span>](iclrappdomainresourcemonitor-getcurrentcputime-method.md)|<span data-ttu-id="1d0bc-112">Uygulama etki alanı oluşturulduğundan bu yana geçerli uygulama etki alanında yürütme sırasında tüm iş parçacıkları tarafından kullanılan toplam işlemci süresini alır.</span><span class="sxs-lookup"><span data-stu-id="1d0bc-112">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d0bc-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1d0bc-113">Remarks</span></span>  

 <span data-ttu-id="1d0bc-114">`ICLRAppDomainResourceMonitor`Arabirimi, aşağıdaki yönetilen özelliklere benzer işlevler sağlar:</span><span class="sxs-lookup"><span data-stu-id="1d0bc-114">The `ICLRAppDomainResourceMonitor` interface provides functionality that is similar to the following managed properties:</span></span>  
  
- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType>  
  
## <a name="requirements"></a><span data-ttu-id="1d0bc-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1d0bc-115">Requirements</span></span>  

 <span data-ttu-id="1d0bc-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d0bc-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d0bc-117">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="1d0bc-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1d0bc-118">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="1d0bc-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1d0bc-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d0bc-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d0bc-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d0bc-120">See also</span></span>

- [<span data-ttu-id="1d0bc-121">\<appDomainResourceMonitoring> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="1d0bc-121">\<appDomainResourceMonitoring> Element</span></span>](../../configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)
- [<span data-ttu-id="1d0bc-122">Uygulama etki alanı kaynak Izleme</span><span class="sxs-lookup"><span data-stu-id="1d0bc-122">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="1d0bc-123">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1d0bc-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="1d0bc-124">Hosting</span><span class="sxs-lookup"><span data-stu-id="1d0bc-124">Hosting</span></span>](index.md)
