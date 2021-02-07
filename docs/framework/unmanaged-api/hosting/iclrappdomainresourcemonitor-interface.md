---
description: ': Iclartppdomainresourcemonitor arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 85321eabedb6912efabe57553732f8c6a4063155
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753906"
---
# <a name="iclrappdomainresourcemonitor-interface"></a><span data-ttu-id="bcf26-103">ICLRAppDomainResourceMonitor Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bcf26-103">ICLRAppDomainResourceMonitor Interface</span></span>

<span data-ttu-id="bcf26-104">Bir uygulama etki alanının belleğini ve CPU kullanımını denetleyen yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="bcf26-104">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bcf26-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="bcf26-105">Methods</span></span>  
  
|<span data-ttu-id="bcf26-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="bcf26-106">Method</span></span>|<span data-ttu-id="bcf26-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bcf26-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bcf26-108">GetCurrentAllocated Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bcf26-108">GetCurrentAllocated Method</span></span>](iclrappdomainresourcemonitor-getcurrentallocated-method.md)|<span data-ttu-id="bcf26-109">, Atık olarak toplanmış olan belleği çıkarmadan, uygulama etki alanı tarafından yapılan tüm bellek ayırmalarının bayt cinsinden toplam boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="bcf26-109">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>|  
|[<span data-ttu-id="bcf26-110">GetCurrentSurvived Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bcf26-110">GetCurrentSurvived Method</span></span>](iclrappdomainresourcemonitor-getcurrentsurvived-method.md)|<span data-ttu-id="bcf26-111">Son tam ve çöp toplamayı engelleyen ve geçerli uygulama etki alanı tarafından başvurulan bayt sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="bcf26-111">Gets the number of bytes that survived the last full, blocking garbage collection and that are referenced by the current application domain.</span></span>|  
|[<span data-ttu-id="bcf26-112">GetCurrentCpuTime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bcf26-112">GetCurrentCpuTime Method</span></span>](iclrappdomainresourcemonitor-getcurrentcputime-method.md)|<span data-ttu-id="bcf26-113">Uygulama etki alanı oluşturulduğundan bu yana geçerli uygulama etki alanında yürütme sırasında tüm iş parçacıkları tarafından kullanılan toplam işlemci süresini alır.</span><span class="sxs-lookup"><span data-stu-id="bcf26-113">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bcf26-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bcf26-114">Remarks</span></span>  

 <span data-ttu-id="bcf26-115">`ICLRAppDomainResourceMonitor`Arabirimi, aşağıdaki yönetilen özelliklere benzer işlevler sağlar:</span><span class="sxs-lookup"><span data-stu-id="bcf26-115">The `ICLRAppDomainResourceMonitor` interface provides functionality that is similar to the following managed properties:</span></span>  
  
- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType>  
  
## <a name="requirements"></a><span data-ttu-id="bcf26-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bcf26-116">Requirements</span></span>  

 <span data-ttu-id="bcf26-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bcf26-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bcf26-118">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="bcf26-118">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="bcf26-119">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="bcf26-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bcf26-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bcf26-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcf26-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bcf26-121">See also</span></span>

- [<span data-ttu-id="bcf26-122">\<appDomainResourceMonitoring> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="bcf26-122">\<appDomainResourceMonitoring> Element</span></span>](../../configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)
- [<span data-ttu-id="bcf26-123">Uygulama etki alanı kaynak Izleme</span><span class="sxs-lookup"><span data-stu-id="bcf26-123">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="bcf26-124">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="bcf26-124">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="bcf26-125">Hosting</span><span class="sxs-lookup"><span data-stu-id="bcf26-125">Hosting</span></span>](index.md)
