---
description: 'Şu konuda daha fazla bilgi edinin: IHostSyncManager arabirimi'
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
ms.openlocfilehash: c3bd2928315567605d320c772de8ff824ad3cd09
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784736"
---
# <a name="ihostsyncmanager-interface"></a><span data-ttu-id="c4413-103">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c4413-103">IHostSyncManager Interface</span></span>

<span data-ttu-id="c4413-104">Ortak dil çalışma zamanının (CLR) Win32 eşitleme işlevlerini kullanmak yerine Konağı çağırarak eşitleme temelleri oluşturmasına izin veren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c4413-104">Provides methods that allow the common language runtime (CLR) to create synchronization primitives by calling the host instead of using the Win32 synchronization functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c4413-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c4413-105">Methods</span></span>  
  
|<span data-ttu-id="c4413-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c4413-106">Method</span></span>|<span data-ttu-id="c4413-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c4413-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c4413-108">CreateAutoEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c4413-108">CreateAutoEvent Method</span></span>](ihostsyncmanager-createautoevent-method.md)|<span data-ttu-id="c4413-109">Otomatik sıfırlama olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c4413-109">Creates an auto-reset event object.</span></span>|  
|[<span data-ttu-id="c4413-110">CreateCrst Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c4413-110">CreateCrst Method</span></span>](ihostsyncmanager-createcrst-method.md)|<span data-ttu-id="c4413-111">Eşitleme için bir kritik bölüm nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c4413-111">Creates a critical section object for synchronization.</span></span>|  
|[<span data-ttu-id="c4413-112">CreateCrstWithSpinCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c4413-112">CreateCrstWithSpinCount Method</span></span>](ihostsyncmanager-createcrstwithspincount-method.md)|<span data-ttu-id="c4413-113">Eşitleme için döngü sayısı olan bir kritik bölüm nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c4413-113">Creates a critical section object with spin count for synchronization.</span></span>|  
|[<span data-ttu-id="c4413-114">CreateManualEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c4413-114">CreateManualEvent Method</span></span>](ihostsyncmanager-createmanualevent-method.md)|<span data-ttu-id="c4413-115">El ile sıfırlama olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c4413-115">Creates a manual-reset event object.</span></span>|  
|[<span data-ttu-id="c4413-116">CreateMonitorEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c4413-116">CreateMonitorEvent Method</span></span>](ihostsyncmanager-createmonitorevent-method.md)|<span data-ttu-id="c4413-117">İzlenen otomatik sıfırlama olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c4413-117">Creates a monitored auto-reset event object.</span></span>|  
|[<span data-ttu-id="c4413-118">CreateRWLockReaderEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c4413-118">CreateRWLockReaderEvent Method</span></span>](ihostsyncmanager-createrwlockreaderevent-method.md)|<span data-ttu-id="c4413-119">Bir okuyucu kilidinin uygulanması için el ile sıfırlama olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c4413-119">Creates a manual-reset event object for the implementation of a reader lock.</span></span>|  
|[<span data-ttu-id="c4413-120">CreateRWLockWriterEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c4413-120">CreateRWLockWriterEvent Method</span></span>](ihostsyncmanager-createrwlockwriterevent-method.md)|<span data-ttu-id="c4413-121">Bir yazıcı kilidinin uygulanması için otomatik sıfırlama olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c4413-121">Creates an auto-reset event object for the implementation of a writer lock.</span></span>|  
|[<span data-ttu-id="c4413-122">CreateSemaphore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c4413-122">CreateSemaphore Method</span></span>](ihostsyncmanager-createsemaphore-method.md)|<span data-ttu-id="c4413-123">CLR için, bekleme olayları için semafor olarak kullanılacak bir [ıhostsemafor](ihostsemaphore-interface.md) nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c4413-123">Creates an [IHostSemaphore](ihostsemaphore-interface.md) object for the CLR to use as a semaphore for wait events.</span></span>|  
|[<span data-ttu-id="c4413-124">SetCLRSyncManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c4413-124">SetCLRSyncManager Method</span></span>](ihostsyncmanager-setclrsyncmanager-method.md)|<span data-ttu-id="c4413-125">[ICLRSyncManager](iclrsyncmanager-interface.md) örneğini geçerli örnekle ilişkilendirilecek şekilde ayarlar `IHostSyncManager` .</span><span class="sxs-lookup"><span data-stu-id="c4413-125">Sets the [ICLRSyncManager](iclrsyncmanager-interface.md) instance to associate with the current `IHostSyncManager` instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4413-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c4413-126">Remarks</span></span>  

 <span data-ttu-id="c4413-127">CLR, `IHostSyncManager` IID_IHostSyncManager Ile [IHostControl:: GetHostManager](ihostcontrol-gethostmanager-method.md) metodunu çağırarak konağın uygulamasını bulur `IID` .</span><span class="sxs-lookup"><span data-stu-id="c4413-127">The CLR discovers the host's implementation of `IHostSyncManager` by calling the [IHostControl::GetHostManager](ihostcontrol-gethostmanager-method.md) method with an `IID` of IID_IHostSyncManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4413-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c4413-128">Requirements</span></span>  

 <span data-ttu-id="c4413-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4413-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4413-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c4413-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c4413-131">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="c4413-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c4413-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4413-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4413-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4413-133">See also</span></span>

- [<span data-ttu-id="c4413-134">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c4413-134">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="c4413-135">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c4413-135">Hosting Interfaces</span></span>](hosting-interfaces.md)
