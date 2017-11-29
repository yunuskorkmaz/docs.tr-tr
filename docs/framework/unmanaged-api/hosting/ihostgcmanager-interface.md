---
title: IHostGCManager Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostGCManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostGCManager
helpviewer_keywords: IHostGCManager interface [.NET Framework hosting]
ms.assetid: 820330a4-244c-4f67-ab5e-f24b0b3c2080
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0927b236af094b964261a9b2a49a33d1ea2b9391
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostgcmanager-interface"></a><span data-ttu-id="cf296-102">IHostGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cf296-102">IHostGCManager Interface</span></span>
<span data-ttu-id="cf296-103">Ortak dil çalışma zamanı tarafından (CLR) uygulanan atık toplama mekanizması olayları ana bildir yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf296-103">Provides methods that notify the host of events in the garbage collection mechanism implemented by the common language runtime (CLR).</span></span>  
  
## <a name="members"></a><span data-ttu-id="cf296-104">Üyeler</span><span class="sxs-lookup"><span data-stu-id="cf296-104">Members</span></span>  
  
|<span data-ttu-id="cf296-105">Üye</span><span class="sxs-lookup"><span data-stu-id="cf296-105">Member</span></span>|<span data-ttu-id="cf296-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cf296-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cf296-107">SuspensionEnding yöntemi</span><span class="sxs-lookup"><span data-stu-id="cf296-107">SuspensionEnding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md)|<span data-ttu-id="cf296-108">Ana bilgisayar CLR görevler için bir atık toplama askıya iş parçacığı üzerinde yürütülmesi sürdürüyor bildirir.</span><span class="sxs-lookup"><span data-stu-id="cf296-108">Notifies the host that the CLR is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>|  
|[<span data-ttu-id="cf296-109">SuspensionStarting yöntemi</span><span class="sxs-lookup"><span data-stu-id="cf296-109">SuspensionStarting Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md)|<span data-ttu-id="cf296-110">Ana bilgisayar CLR çöp toplama gerçekleştirmek için görevlerini yürütülmesi askıya alma bildirir.</span><span class="sxs-lookup"><span data-stu-id="cf296-110">Notifies the host that the CLR is suspending execution of tasks, to perform a garbage collection.</span></span>|  
|[<span data-ttu-id="cf296-111">Threadısblockingforsuspension yöntemi</span><span class="sxs-lookup"><span data-stu-id="cf296-111">ThreadIsBlockingForSuspension Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md)|<span data-ttu-id="cf296-112">İçinden yöntem çağrısı yapıldı iş parçacığı konak bildirir atık toplama için engellemek üzere.</span><span class="sxs-lookup"><span data-stu-id="cf296-112">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cf296-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cf296-113">Requirements</span></span>  
 <span data-ttu-id="cf296-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf296-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf296-115">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cf296-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cf296-116">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="cf296-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cf296-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf296-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf296-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cf296-118">See Also</span></span>  
 [<span data-ttu-id="cf296-119">Iclrtask arabirimi</span><span class="sxs-lookup"><span data-stu-id="cf296-119">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="cf296-120">Iclrtaskmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="cf296-120">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="cf296-121">Ihosttask arabirimi</span><span class="sxs-lookup"><span data-stu-id="cf296-121">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="cf296-122">Ihosttaskmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="cf296-122">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="cf296-123">Barındırma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cf296-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
