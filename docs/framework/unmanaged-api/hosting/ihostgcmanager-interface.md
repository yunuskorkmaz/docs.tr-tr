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
ms.openlocfilehash: 428e4cf8997713b08e40d9376c34ae5eee8cfa32
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804851"
---
# <a name="ihostgcmanager-interface"></a><span data-ttu-id="4adc0-102">IHostGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4adc0-102">IHostGCManager Interface</span></span>
<span data-ttu-id="4adc0-103">Ortak dil çalışma zamanı (CLR) tarafından uygulanan çöp toplama mekanizmasında olayların ana bilgisayarına bildirimde bulunan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="4adc0-103">Provides methods that notify the host of events in the garbage collection mechanism implemented by the common language runtime (CLR).</span></span>  
  
## <a name="members"></a><span data-ttu-id="4adc0-104">Üyeler</span><span class="sxs-lookup"><span data-stu-id="4adc0-104">Members</span></span>  
  
|<span data-ttu-id="4adc0-105">Üye</span><span class="sxs-lookup"><span data-stu-id="4adc0-105">Member</span></span>|<span data-ttu-id="4adc0-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4adc0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4adc0-107">SuspensionEnding Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4adc0-107">SuspensionEnding Method</span></span>](ihostgcmanager-suspensionending-method.md)|<span data-ttu-id="4adc0-108">Konağa CLR 'nin bir çöp toplama işlemi için askıya alınmış iş parçacıklarında görevlerin yürütülmesini sürdürmesinin sürdürüyor olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="4adc0-108">Notifies the host that the CLR is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>|  
|[<span data-ttu-id="4adc0-109">SuspensionStarting Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4adc0-109">SuspensionStarting Method</span></span>](ihostgcmanager-suspensionstarting-method.md)|<span data-ttu-id="4adc0-110">Bir atık toplama işlemi gerçekleştirmek için, CLR 'nin görevlerin yürütülmesini askıya aldığı konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="4adc0-110">Notifies the host that the CLR is suspending execution of tasks, to perform a garbage collection.</span></span>|  
|[<span data-ttu-id="4adc0-111">ThreadIsBlockingForSuspension Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4adc0-111">ThreadIsBlockingForSuspension Method</span></span>](ihostgcmanager-threadisblockingforsuspension-method.md)|<span data-ttu-id="4adc0-112">Ana bilgisayara, yöntem çağrısının yaptığı iş parçacığının çöp toplama için engellemek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="4adc0-112">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4adc0-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4adc0-113">Requirements</span></span>  
 <span data-ttu-id="4adc0-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4adc0-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4adc0-115">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4adc0-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4adc0-116">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="4adc0-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4adc0-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4adc0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4adc0-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4adc0-118">See also</span></span>

- [<span data-ttu-id="4adc0-119">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4adc0-119">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="4adc0-120">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4adc0-120">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="4adc0-121">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4adc0-121">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="4adc0-122">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4adc0-122">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="4adc0-123">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4adc0-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
