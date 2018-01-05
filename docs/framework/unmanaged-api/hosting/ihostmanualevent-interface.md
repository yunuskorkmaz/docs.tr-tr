---
title: IHostManualEvent Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostManualEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostManualEvent
helpviewer_keywords: IHostManualEvent interface [.NET Framework hosting]
ms.assetid: 300c2661-b7d1-4c39-b080-9ebdef0fd523
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0d55500efbe808b2fce16e869422e727b8ed0b93
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmanualevent-interface"></a><span data-ttu-id="9d399-102">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d399-102">IHostManualEvent Interface</span></span>
<span data-ttu-id="9d399-103">Ana bilgisayarın uygulamasını elle sıfırlama olayı bir gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="9d399-103">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9d399-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9d399-104">Methods</span></span>  
  
|<span data-ttu-id="9d399-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="9d399-105">Method</span></span>|<span data-ttu-id="9d399-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9d399-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9d399-107">Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9d399-107">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md)|<span data-ttu-id="9d399-108">Geçerli sıfırlar `IHostManualEvent` işaret olmayan bir duruma örneği.</span><span class="sxs-lookup"><span data-stu-id="9d399-108">Resets the current `IHostManualEvent` instance to a non-signaled state.</span></span>|  
|[<span data-ttu-id="9d399-109">Set Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9d399-109">Set Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-set-method.md)|<span data-ttu-id="9d399-110">Geçerli ayarlar `IHostManualEvent` iş durumuna örneği.</span><span class="sxs-lookup"><span data-stu-id="9d399-110">Sets the current `IHostManualEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="9d399-111">Wait Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9d399-111">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-wait-method.md)|<span data-ttu-id="9d399-112">Geçerli neden `IHostManualEvent` örneği ait kadar bekleyin veya belirli bir süre geçtikten miktarını.</span><span class="sxs-lookup"><span data-stu-id="9d399-112">Causes the current `IHostManualEvent` instance to wait until it is owned, or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9d399-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9d399-113">Requirements</span></span>  
 <span data-ttu-id="9d399-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d399-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d399-115">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9d399-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9d399-116">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="9d399-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9d399-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d399-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d399-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9d399-118">See Also</span></span>  
 [<span data-ttu-id="9d399-119">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d399-119">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="9d399-120">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d399-120">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="9d399-121">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d399-121">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="9d399-122">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d399-122">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="9d399-123">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9d399-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
