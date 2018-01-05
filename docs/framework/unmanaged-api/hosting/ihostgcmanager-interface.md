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
ms.workload: dotnet
ms.openlocfilehash: 7452f49df6970bf2ca49781f6a38874186bec64f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostgcmanager-interface"></a><span data-ttu-id="37734-102">IHostGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="37734-102">IHostGCManager Interface</span></span>
<span data-ttu-id="37734-103">Ortak dil çalışma zamanı tarafından (CLR) uygulanan atık toplama mekanizması olayları ana bildir yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="37734-103">Provides methods that notify the host of events in the garbage collection mechanism implemented by the common language runtime (CLR).</span></span>  
  
## <a name="members"></a><span data-ttu-id="37734-104">Üyeler</span><span class="sxs-lookup"><span data-stu-id="37734-104">Members</span></span>  
  
|<span data-ttu-id="37734-105">Üye</span><span class="sxs-lookup"><span data-stu-id="37734-105">Member</span></span>|<span data-ttu-id="37734-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="37734-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="37734-107">SuspensionEnding Yöntemi</span><span class="sxs-lookup"><span data-stu-id="37734-107">SuspensionEnding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md)|<span data-ttu-id="37734-108">Ana bilgisayar CLR görevler için bir atık toplama askıya iş parçacığı üzerinde yürütülmesi sürdürüyor bildirir.</span><span class="sxs-lookup"><span data-stu-id="37734-108">Notifies the host that the CLR is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>|  
|[<span data-ttu-id="37734-109">SuspensionStarting Yöntemi</span><span class="sxs-lookup"><span data-stu-id="37734-109">SuspensionStarting Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md)|<span data-ttu-id="37734-110">Ana bilgisayar CLR çöp toplama gerçekleştirmek için görevlerini yürütülmesi askıya alma bildirir.</span><span class="sxs-lookup"><span data-stu-id="37734-110">Notifies the host that the CLR is suspending execution of tasks, to perform a garbage collection.</span></span>|  
|[<span data-ttu-id="37734-111">ThreadIsBlockingForSuspension Yöntemi</span><span class="sxs-lookup"><span data-stu-id="37734-111">ThreadIsBlockingForSuspension Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md)|<span data-ttu-id="37734-112">İçinden yöntem çağrısı yapıldı iş parçacığı konak bildirir atık toplama için engellemek üzere.</span><span class="sxs-lookup"><span data-stu-id="37734-112">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="37734-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="37734-113">Requirements</span></span>  
 <span data-ttu-id="37734-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37734-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37734-115">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="37734-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="37734-116">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="37734-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="37734-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37734-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37734-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="37734-118">See Also</span></span>  
 [<span data-ttu-id="37734-119">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="37734-119">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="37734-120">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="37734-120">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="37734-121">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="37734-121">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="37734-122">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="37734-122">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="37734-123">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="37734-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
