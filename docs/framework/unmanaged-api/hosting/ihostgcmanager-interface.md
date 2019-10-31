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
ms.openlocfilehash: 6f7158bcac7ad22647104e2041da959285d2be8f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130488"
---
# <a name="ihostgcmanager-interface"></a><span data-ttu-id="0b037-102">IHostGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b037-102">IHostGCManager Interface</span></span>
<span data-ttu-id="0b037-103">Ortak dil çalışma zamanı (CLR) tarafından uygulanan çöp toplama mekanizmasında olayların ana bilgisayarına bildirimde bulunan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0b037-103">Provides methods that notify the host of events in the garbage collection mechanism implemented by the common language runtime (CLR).</span></span>  
  
## <a name="members"></a><span data-ttu-id="0b037-104">Üyeler</span><span class="sxs-lookup"><span data-stu-id="0b037-104">Members</span></span>  
  
|<span data-ttu-id="0b037-105">Üye</span><span class="sxs-lookup"><span data-stu-id="0b037-105">Member</span></span>|<span data-ttu-id="0b037-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b037-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0b037-107">SuspensionEnding Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0b037-107">SuspensionEnding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md)|<span data-ttu-id="0b037-108">Konağa CLR 'nin bir çöp toplama işlemi için askıya alınmış iş parçacıklarında görevlerin yürütülmesini sürdürmesinin sürdürüyor olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="0b037-108">Notifies the host that the CLR is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>|  
|[<span data-ttu-id="0b037-109">SuspensionStarting Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0b037-109">SuspensionStarting Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md)|<span data-ttu-id="0b037-110">Bir atık toplama işlemi gerçekleştirmek için, CLR 'nin görevlerin yürütülmesini askıya aldığı konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="0b037-110">Notifies the host that the CLR is suspending execution of tasks, to perform a garbage collection.</span></span>|  
|[<span data-ttu-id="0b037-111">ThreadIsBlockingForSuspension Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0b037-111">ThreadIsBlockingForSuspension Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md)|<span data-ttu-id="0b037-112">Ana bilgisayara, yöntem çağrısının yaptığı iş parçacığının çöp toplama için engellemek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="0b037-112">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0b037-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0b037-113">Requirements</span></span>  
 <span data-ttu-id="0b037-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b037-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b037-115">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0b037-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0b037-116">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="0b037-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0b037-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b037-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b037-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b037-118">See also</span></span>

- [<span data-ttu-id="0b037-119">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b037-119">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="0b037-120">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b037-120">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="0b037-121">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b037-121">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="0b037-122">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b037-122">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="0b037-123">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0b037-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
