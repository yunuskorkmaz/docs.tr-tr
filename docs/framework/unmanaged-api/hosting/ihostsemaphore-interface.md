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
ms.openlocfilehash: 67b3225186f74fceadfb3104145743823ef82fc2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsemaphore-interface"></a><span data-ttu-id="aeb1c-102">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aeb1c-102">IHostSemaphore Interface</span></span>
<span data-ttu-id="aeb1c-103">İş parçacığı oluşturma için semafor ana bilgisayarın uygulamasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="aeb1c-103">Represents the host's implementation of a semaphore for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="aeb1c-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="aeb1c-104">Methods</span></span>  
  
|<span data-ttu-id="aeb1c-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="aeb1c-105">Method</span></span>|<span data-ttu-id="aeb1c-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aeb1c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="aeb1c-107">ReleaseSemaphore yöntemi</span><span class="sxs-lookup"><span data-stu-id="aeb1c-107">ReleaseSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)|<span data-ttu-id="aeb1c-108">Geçerli sayısını azaltır `IHostSemaphore` örneği tarafından belirtilen tutar.</span><span class="sxs-lookup"><span data-stu-id="aeb1c-108">Increases the count of the current `IHostSemaphore` instance by the specified amount.</span></span>|  
|[<span data-ttu-id="aeb1c-109">Wait yöntemi</span><span class="sxs-lookup"><span data-stu-id="aeb1c-109">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md)|<span data-ttu-id="aeb1c-110">Geçerli neden `IHostSemaphore` örneği ait kadar bekleyin veya geçtiğinde belirtilen miktarı.</span><span class="sxs-lookup"><span data-stu-id="aeb1c-110">Causes the current `IHostSemaphore` instance to wait until it is owned or the specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="aeb1c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aeb1c-111">Requirements</span></span>  
 <span data-ttu-id="aeb1c-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aeb1c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aeb1c-113">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="aeb1c-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aeb1c-114">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="aeb1c-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aeb1c-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aeb1c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aeb1c-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aeb1c-116">See Also</span></span>  
 [<span data-ttu-id="aeb1c-117">Iclrsyncmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="aeb1c-117">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="aeb1c-118">Ihostautoevent arabirimi</span><span class="sxs-lookup"><span data-stu-id="aeb1c-118">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="aeb1c-119">Ihostmanualevent arabirimi</span><span class="sxs-lookup"><span data-stu-id="aeb1c-119">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="aeb1c-120">Ihostsyncmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="aeb1c-120">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="aeb1c-121">Barındırma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="aeb1c-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
