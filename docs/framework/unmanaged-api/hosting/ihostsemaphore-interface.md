---
title: IHostSemaphore Arabirimi
ms.date: 03/30/2017
api_name:
- IHostSemaphore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSemaphore
helpviewer_keywords:
- IHostSemaphore interface [.NET Framework hosting]
ms.assetid: c0765321-656c-441e-bab5-58176292be1e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d7d4a295832a958fb6a8fe2e6c43a09135500d3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182292"
---
# <a name="ihostsemaphore-interface"></a><span data-ttu-id="ac1d5-102">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ac1d5-102">IHostSemaphore Interface</span></span>
<span data-ttu-id="ac1d5-103">İş parçacığı için semafor konağın uygulamasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ac1d5-103">Represents the host's implementation of a semaphore for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ac1d5-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ac1d5-104">Methods</span></span>  
  
|<span data-ttu-id="ac1d5-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ac1d5-105">Method</span></span>|<span data-ttu-id="ac1d5-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ac1d5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ac1d5-107">ReleaseSemaphore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ac1d5-107">ReleaseSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)|<span data-ttu-id="ac1d5-108">Geçerli sayısını artırır `IHostSemaphore` örneği tarafından belirtilen süre.</span><span class="sxs-lookup"><span data-stu-id="ac1d5-108">Increases the count of the current `IHostSemaphore` instance by the specified amount.</span></span>|  
|[<span data-ttu-id="ac1d5-109">Wait Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ac1d5-109">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md)|<span data-ttu-id="ac1d5-110">Geçerli neden `IHostSemaphore` örneğin ait kadar bekleyin veya zaman geçtikçe belirtilen miktarı.</span><span class="sxs-lookup"><span data-stu-id="ac1d5-110">Causes the current `IHostSemaphore` instance to wait until it is owned or the specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ac1d5-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ac1d5-111">Requirements</span></span>  
 <span data-ttu-id="ac1d5-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac1d5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac1d5-113">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ac1d5-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ac1d5-114">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="ac1d5-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ac1d5-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac1d5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac1d5-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac1d5-116">See also</span></span>

- [<span data-ttu-id="ac1d5-117">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ac1d5-117">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="ac1d5-118">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ac1d5-118">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="ac1d5-119">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ac1d5-119">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="ac1d5-120">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ac1d5-120">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="ac1d5-121">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ac1d5-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
