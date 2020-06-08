---
title: IHostSyncManager Arabirimi
ms.date: 03/30/2017
api_name:
- IHostSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager
helpviewer_keywords:
- IHostSyncManager interface [.NET Framework hosting]
ms.assetid: 2e081a37-6a28-4c93-b7ab-1c96a464637c
topic_type:
- apiref
ms.openlocfilehash: fd3c941d89fbd93f30fc1af235f6310b23758973
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501462"
---
# <a name="ihostsyncmanager-interface"></a><span data-ttu-id="46c3e-102">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46c3e-102">IHostSyncManager Interface</span></span>
<span data-ttu-id="46c3e-103">Ortak dil çalışma zamanının (CLR) Win32 eşitleme işlevlerini kullanmak yerine Konağı çağırarak eşitleme temelleri oluşturmasına izin veren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="46c3e-103">Provides methods that allow the common language runtime (CLR) to create synchronization primitives by calling the host instead of using the Win32 synchronization functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="46c3e-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="46c3e-104">Methods</span></span>  
  
|<span data-ttu-id="46c3e-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="46c3e-105">Method</span></span>|<span data-ttu-id="46c3e-106">Description</span><span class="sxs-lookup"><span data-stu-id="46c3e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="46c3e-107">CreateAutoEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="46c3e-107">CreateAutoEvent Method</span></span>](ihostsyncmanager-createautoevent-method.md)|<span data-ttu-id="46c3e-108">Otomatik sıfırlama olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="46c3e-108">Creates an auto-reset event object.</span></span>|  
|[<span data-ttu-id="46c3e-109">CreateCrst Yöntemi</span><span class="sxs-lookup"><span data-stu-id="46c3e-109">CreateCrst Method</span></span>](ihostsyncmanager-createcrst-method.md)|<span data-ttu-id="46c3e-110">Eşitleme için bir kritik bölüm nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="46c3e-110">Creates a critical section object for synchronization.</span></span>|  
|[<span data-ttu-id="46c3e-111">CreateCrstWithSpinCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="46c3e-111">CreateCrstWithSpinCount Method</span></span>](ihostsyncmanager-createcrstwithspincount-method.md)|<span data-ttu-id="46c3e-112">Eşitleme için döngü sayısı olan bir kritik bölüm nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="46c3e-112">Creates a critical section object with spin count for synchronization.</span></span>|  
|[<span data-ttu-id="46c3e-113">CreateManualEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="46c3e-113">CreateManualEvent Method</span></span>](ihostsyncmanager-createmanualevent-method.md)|<span data-ttu-id="46c3e-114">El ile sıfırlama olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="46c3e-114">Creates a manual-reset event object.</span></span>|  
|[<span data-ttu-id="46c3e-115">CreateMonitorEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="46c3e-115">CreateMonitorEvent Method</span></span>](ihostsyncmanager-createmonitorevent-method.md)|<span data-ttu-id="46c3e-116">İzlenen otomatik sıfırlama olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="46c3e-116">Creates a monitored auto-reset event object.</span></span>|  
|[<span data-ttu-id="46c3e-117">CreateRWLockReaderEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="46c3e-117">CreateRWLockReaderEvent Method</span></span>](ihostsyncmanager-createrwlockreaderevent-method.md)|<span data-ttu-id="46c3e-118">Bir okuyucu kilidinin uygulanması için el ile sıfırlama olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="46c3e-118">Creates a manual-reset event object for the implementation of a reader lock.</span></span>|  
|[<span data-ttu-id="46c3e-119">CreateRWLockWriterEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="46c3e-119">CreateRWLockWriterEvent Method</span></span>](ihostsyncmanager-createrwlockwriterevent-method.md)|<span data-ttu-id="46c3e-120">Bir yazıcı kilidinin uygulanması için otomatik sıfırlama olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="46c3e-120">Creates an auto-reset event object for the implementation of a writer lock.</span></span>|  
|[<span data-ttu-id="46c3e-121">CreateSemaphore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="46c3e-121">CreateSemaphore Method</span></span>](ihostsyncmanager-createsemaphore-method.md)|<span data-ttu-id="46c3e-122">CLR için, bekleme olayları için semafor olarak kullanılacak bir [ıhostsemafor](ihostsemaphore-interface.md) nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="46c3e-122">Creates an [IHostSemaphore](ihostsemaphore-interface.md) object for the CLR to use as a semaphore for wait events.</span></span>|  
|[<span data-ttu-id="46c3e-123">SetCLRSyncManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="46c3e-123">SetCLRSyncManager Method</span></span>](ihostsyncmanager-setclrsyncmanager-method.md)|<span data-ttu-id="46c3e-124">[ICLRSyncManager](iclrsyncmanager-interface.md) örneğini geçerli örnekle ilişkilendirilecek şekilde ayarlar `IHostSyncManager` .</span><span class="sxs-lookup"><span data-stu-id="46c3e-124">Sets the [ICLRSyncManager](iclrsyncmanager-interface.md) instance to associate with the current `IHostSyncManager` instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46c3e-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="46c3e-125">Remarks</span></span>  
 <span data-ttu-id="46c3e-126">CLR, `IHostSyncManager` IID_IHostSyncManager Ile [IHostControl:: GetHostManager](ihostcontrol-gethostmanager-method.md) metodunu çağırarak konağın uygulamasını bulur `IID` .</span><span class="sxs-lookup"><span data-stu-id="46c3e-126">The CLR discovers the host's implementation of `IHostSyncManager` by calling the [IHostControl::GetHostManager](ihostcontrol-gethostmanager-method.md) method with an `IID` of IID_IHostSyncManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46c3e-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="46c3e-127">Requirements</span></span>  
 <span data-ttu-id="46c3e-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46c3e-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46c3e-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="46c3e-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="46c3e-130">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="46c3e-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="46c3e-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46c3e-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46c3e-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46c3e-132">See also</span></span>

- [<span data-ttu-id="46c3e-133">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46c3e-133">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="46c3e-134">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="46c3e-134">Hosting Interfaces</span></span>](hosting-interfaces.md)
