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
ms.openlocfilehash: eb7e52b5237d4341c27b8c167249dc2614168679
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729539"
---
# <a name="ihostgcmanager-interface"></a><span data-ttu-id="43127-102">IHostGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="43127-102">IHostGCManager Interface</span></span>

<span data-ttu-id="43127-103">Ortak dil çalışma zamanı (CLR) tarafından uygulanan çöp toplama mekanizmasında olayların ana bilgisayarına bildirimde bulunan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="43127-103">Provides methods that notify the host of events in the garbage collection mechanism implemented by the common language runtime (CLR).</span></span>  
  
## <a name="members"></a><span data-ttu-id="43127-104">Üyeler</span><span class="sxs-lookup"><span data-stu-id="43127-104">Members</span></span>  
  
|<span data-ttu-id="43127-105">Üye</span><span class="sxs-lookup"><span data-stu-id="43127-105">Member</span></span>|<span data-ttu-id="43127-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43127-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="43127-107">SuspensionEnding Yöntemi</span><span class="sxs-lookup"><span data-stu-id="43127-107">SuspensionEnding Method</span></span>](ihostgcmanager-suspensionending-method.md)|<span data-ttu-id="43127-108">Konağa CLR 'nin bir çöp toplama işlemi için askıya alınmış iş parçacıklarında görevlerin yürütülmesini sürdürmesinin sürdürüyor olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="43127-108">Notifies the host that the CLR is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>|  
|[<span data-ttu-id="43127-109">SuspensionStarting Yöntemi</span><span class="sxs-lookup"><span data-stu-id="43127-109">SuspensionStarting Method</span></span>](ihostgcmanager-suspensionstarting-method.md)|<span data-ttu-id="43127-110">Bir atık toplama işlemi gerçekleştirmek için, CLR 'nin görevlerin yürütülmesini askıya aldığı konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="43127-110">Notifies the host that the CLR is suspending execution of tasks, to perform a garbage collection.</span></span>|  
|[<span data-ttu-id="43127-111">ThreadIsBlockingForSuspension Yöntemi</span><span class="sxs-lookup"><span data-stu-id="43127-111">ThreadIsBlockingForSuspension Method</span></span>](ihostgcmanager-threadisblockingforsuspension-method.md)|<span data-ttu-id="43127-112">Ana bilgisayara, yöntem çağrısının yaptığı iş parçacığının çöp toplama için engellemek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="43127-112">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="43127-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="43127-113">Requirements</span></span>  

 <span data-ttu-id="43127-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43127-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43127-115">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="43127-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="43127-116">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="43127-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="43127-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43127-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43127-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43127-118">See also</span></span>

- [<span data-ttu-id="43127-119">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="43127-119">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="43127-120">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="43127-120">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="43127-121">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="43127-121">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="43127-122">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="43127-122">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="43127-123">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="43127-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
