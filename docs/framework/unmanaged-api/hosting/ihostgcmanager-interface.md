---
title: IHostGCManager Arabirimi
ms.date: 03/30/2017
api_name:
- IHostGCManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager
helpviewer_keywords:
- IHostGCManager interface [.NET Framework hosting]
ms.assetid: 820330a4-244c-4f67-ab5e-f24b0b3c2080
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 238b054d240437df64a83a9c4daad34d4bd5d36a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228893"
---
# <a name="ihostgcmanager-interface"></a><span data-ttu-id="a6ffc-102">IHostGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a6ffc-102">IHostGCManager Interface</span></span>
<span data-ttu-id="a6ffc-103">Ortak dil çalışma zamanı tarafından (CLR) uygulanan çöp toplama mekanizması olayların ana bilgisayara bildirmek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a6ffc-103">Provides methods that notify the host of events in the garbage collection mechanism implemented by the common language runtime (CLR).</span></span>  
  
## <a name="members"></a><span data-ttu-id="a6ffc-104">Üyeler</span><span class="sxs-lookup"><span data-stu-id="a6ffc-104">Members</span></span>  
  
|<span data-ttu-id="a6ffc-105">Üye</span><span class="sxs-lookup"><span data-stu-id="a6ffc-105">Member</span></span>|<span data-ttu-id="a6ffc-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a6ffc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a6ffc-107">SuspensionEnding Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a6ffc-107">SuspensionEnding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md)|<span data-ttu-id="a6ffc-108">Konak, CLR askıya alındığı için çöp toplama iş parçacığı üzerinde görevlerin yürütülmesi sürdürülmekte bildirir.</span><span class="sxs-lookup"><span data-stu-id="a6ffc-108">Notifies the host that the CLR is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>|  
|[<span data-ttu-id="a6ffc-109">SuspensionStarting Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a6ffc-109">SuspensionStarting Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md)|<span data-ttu-id="a6ffc-110">CLR çöp toplama için görevlerin yürütülmesi askıya alma konak bildirir.</span><span class="sxs-lookup"><span data-stu-id="a6ffc-110">Notifies the host that the CLR is suspending execution of tasks, to perform a garbage collection.</span></span>|  
|[<span data-ttu-id="a6ffc-111">ThreadIsBlockingForSuspension Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a6ffc-111">ThreadIsBlockingForSuspension Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md)|<span data-ttu-id="a6ffc-112">İş parçacığı içinden yöntem çağrısı yapıldı, konağa bildirir yönelik bir çöp toplamanın engellemek üzere.</span><span class="sxs-lookup"><span data-stu-id="a6ffc-112">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a6ffc-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a6ffc-113">Requirements</span></span>  
 <span data-ttu-id="a6ffc-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6ffc-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6ffc-115">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a6ffc-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a6ffc-116">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="a6ffc-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="a6ffc-117">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="a6ffc-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a6ffc-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6ffc-118">See also</span></span>

- [<span data-ttu-id="a6ffc-119">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a6ffc-119">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="a6ffc-120">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a6ffc-120">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="a6ffc-121">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a6ffc-121">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="a6ffc-122">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a6ffc-122">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="a6ffc-123">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a6ffc-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
