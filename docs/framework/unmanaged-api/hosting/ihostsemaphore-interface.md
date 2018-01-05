---
title: IHostSemaphore Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSemaphore
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSemaphore
helpviewer_keywords: IHostSemaphore interface [.NET Framework hosting]
ms.assetid: c0765321-656c-441e-bab5-58176292be1e
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bcc6a9a7847932e9e469cdbffc9792e1d5860570
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsemaphore-interface"></a><span data-ttu-id="d3bda-102">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d3bda-102">IHostSemaphore Interface</span></span>
<span data-ttu-id="d3bda-103">İş parçacığı oluşturma için semafor ana bilgisayarın uygulamasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d3bda-103">Represents the host's implementation of a semaphore for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d3bda-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d3bda-104">Methods</span></span>  
  
|<span data-ttu-id="d3bda-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d3bda-105">Method</span></span>|<span data-ttu-id="d3bda-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3bda-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d3bda-107">ReleaseSemaphore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d3bda-107">ReleaseSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)|<span data-ttu-id="d3bda-108">Geçerli sayısını azaltır `IHostSemaphore` örneği tarafından belirtilen tutar.</span><span class="sxs-lookup"><span data-stu-id="d3bda-108">Increases the count of the current `IHostSemaphore` instance by the specified amount.</span></span>|  
|[<span data-ttu-id="d3bda-109">Wait Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d3bda-109">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md)|<span data-ttu-id="d3bda-110">Geçerli neden `IHostSemaphore` örneği ait kadar bekleyin veya geçtiğinde belirtilen miktarı.</span><span class="sxs-lookup"><span data-stu-id="d3bda-110">Causes the current `IHostSemaphore` instance to wait until it is owned or the specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d3bda-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d3bda-111">Requirements</span></span>  
 <span data-ttu-id="d3bda-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3bda-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3bda-113">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d3bda-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d3bda-114">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d3bda-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d3bda-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3bda-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3bda-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d3bda-116">See Also</span></span>  
 [<span data-ttu-id="d3bda-117">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d3bda-117">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="d3bda-118">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d3bda-118">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="d3bda-119">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d3bda-119">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="d3bda-120">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d3bda-120">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="d3bda-121">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d3bda-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
