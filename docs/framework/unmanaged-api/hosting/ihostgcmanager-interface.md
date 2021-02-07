---
description: 'Daha fazla bilgi edinin: IHostGCManager Interface'
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
ms.openlocfilehash: da229c04eb5f5a27c34c133b5c88183d00f47c40
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708664"
---
# <a name="ihostgcmanager-interface"></a><span data-ttu-id="04aab-103">IHostGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="04aab-103">IHostGCManager Interface</span></span>

<span data-ttu-id="04aab-104">Ortak dil çalışma zamanı (CLR) tarafından uygulanan çöp toplama mekanizmasında olayların ana bilgisayarına bildirimde bulunan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="04aab-104">Provides methods that notify the host of events in the garbage collection mechanism implemented by the common language runtime (CLR).</span></span>  
  
## <a name="members"></a><span data-ttu-id="04aab-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="04aab-105">Members</span></span>  
  
|<span data-ttu-id="04aab-106">Üye</span><span class="sxs-lookup"><span data-stu-id="04aab-106">Member</span></span>|<span data-ttu-id="04aab-107">Description</span><span class="sxs-lookup"><span data-stu-id="04aab-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="04aab-108">SuspensionEnding Yöntemi</span><span class="sxs-lookup"><span data-stu-id="04aab-108">SuspensionEnding Method</span></span>](ihostgcmanager-suspensionending-method.md)|<span data-ttu-id="04aab-109">Konağa CLR 'nin bir çöp toplama işlemi için askıya alınmış iş parçacıklarında görevlerin yürütülmesini sürdürmesinin sürdürüyor olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="04aab-109">Notifies the host that the CLR is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>|  
|[<span data-ttu-id="04aab-110">SuspensionStarting Yöntemi</span><span class="sxs-lookup"><span data-stu-id="04aab-110">SuspensionStarting Method</span></span>](ihostgcmanager-suspensionstarting-method.md)|<span data-ttu-id="04aab-111">Bir atık toplama işlemi gerçekleştirmek için, CLR 'nin görevlerin yürütülmesini askıya aldığı konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="04aab-111">Notifies the host that the CLR is suspending execution of tasks, to perform a garbage collection.</span></span>|  
|[<span data-ttu-id="04aab-112">ThreadIsBlockingForSuspension Yöntemi</span><span class="sxs-lookup"><span data-stu-id="04aab-112">ThreadIsBlockingForSuspension Method</span></span>](ihostgcmanager-threadisblockingforsuspension-method.md)|<span data-ttu-id="04aab-113">Ana bilgisayara, yöntem çağrısının yaptığı iş parçacığının çöp toplama için engellemek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="04aab-113">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="04aab-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="04aab-114">Requirements</span></span>  

 <span data-ttu-id="04aab-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04aab-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04aab-116">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="04aab-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="04aab-117">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="04aab-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="04aab-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04aab-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04aab-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04aab-119">See also</span></span>

- [<span data-ttu-id="04aab-120">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="04aab-120">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="04aab-121">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="04aab-121">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="04aab-122">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="04aab-122">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="04aab-123">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="04aab-123">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="04aab-124">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="04aab-124">Hosting Interfaces</span></span>](hosting-interfaces.md)
