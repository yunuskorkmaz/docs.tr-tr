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
ms.openlocfilehash: 02a59b8ef63f7e866e419db4e3232da7eec19558
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132623"
---
# <a name="ihostsyncmanager-interface"></a><span data-ttu-id="684f5-102">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="684f5-102">IHostSyncManager Interface</span></span>
<span data-ttu-id="684f5-103">Ortak dil çalışma zamanının (CLR) Win32 eşitleme işlevlerini kullanmak yerine Konağı çağırarak eşitleme temelleri oluşturmasına izin veren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="684f5-103">Provides methods that allow the common language runtime (CLR) to create synchronization primitives by calling the host instead of using the Win32 synchronization functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="684f5-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="684f5-104">Methods</span></span>  
  
|<span data-ttu-id="684f5-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="684f5-105">Method</span></span>|<span data-ttu-id="684f5-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="684f5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="684f5-107">CreateAutoEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="684f5-107">CreateAutoEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createautoevent-method.md)|<span data-ttu-id="684f5-108">Otomatik sıfırlama olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="684f5-108">Creates an auto-reset event object.</span></span>|  
|[<span data-ttu-id="684f5-109">CreateCrst Yöntemi</span><span class="sxs-lookup"><span data-stu-id="684f5-109">CreateCrst Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrst-method.md)|<span data-ttu-id="684f5-110">Eşitleme için bir kritik bölüm nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="684f5-110">Creates a critical section object for synchronization.</span></span>|  
|[<span data-ttu-id="684f5-111">CreateCrstWithSpinCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="684f5-111">CreateCrstWithSpinCount Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrstwithspincount-method.md)|<span data-ttu-id="684f5-112">Eşitleme için döngü sayısı olan bir kritik bölüm nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="684f5-112">Creates a critical section object with spin count for synchronization.</span></span>|  
|[<span data-ttu-id="684f5-113">CreateManualEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="684f5-113">CreateManualEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmanualevent-method.md)|<span data-ttu-id="684f5-114">El ile sıfırlama olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="684f5-114">Creates a manual-reset event object.</span></span>|  
|[<span data-ttu-id="684f5-115">CreateMonitorEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="684f5-115">CreateMonitorEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md)|<span data-ttu-id="684f5-116">İzlenen otomatik sıfırlama olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="684f5-116">Creates a monitored auto-reset event object.</span></span>|  
|[<span data-ttu-id="684f5-117">CreateRWLockReaderEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="684f5-117">CreateRWLockReaderEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockreaderevent-method.md)|<span data-ttu-id="684f5-118">Bir okuyucu kilidinin uygulanması için el ile sıfırlama olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="684f5-118">Creates a manual-reset event object for the implementation of a reader lock.</span></span>|  
|[<span data-ttu-id="684f5-119">CreateRWLockWriterEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="684f5-119">CreateRWLockWriterEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockwriterevent-method.md)|<span data-ttu-id="684f5-120">Bir yazıcı kilidinin uygulanması için otomatik sıfırlama olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="684f5-120">Creates an auto-reset event object for the implementation of a writer lock.</span></span>|  
|[<span data-ttu-id="684f5-121">CreateSemaphore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="684f5-121">CreateSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createsemaphore-method.md)|<span data-ttu-id="684f5-122">CLR için, bekleme olayları için semafor olarak kullanılacak bir [ıhostsemafor](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="684f5-122">Creates an [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) object for the CLR to use as a semaphore for wait events.</span></span>|  
|[<span data-ttu-id="684f5-123">SetCLRSyncManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="684f5-123">SetCLRSyncManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-setclrsyncmanager-method.md)|<span data-ttu-id="684f5-124">[ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) örneğini geçerli `IHostSyncManager` örneğiyle ilişkilendirilecek şekilde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="684f5-124">Sets the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instance to associate with the current `IHostSyncManager` instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="684f5-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="684f5-125">Remarks</span></span>  
 <span data-ttu-id="684f5-126">CLR, IID_IHostSyncManager 'in bir `IID` ile [IHostControl:: GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) metodunu çağırarak konağın `IHostSyncManager` uygulanmasını bulur.</span><span class="sxs-lookup"><span data-stu-id="684f5-126">The CLR discovers the host's implementation of `IHostSyncManager` by calling the [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) method with an `IID` of IID_IHostSyncManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="684f5-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="684f5-127">Requirements</span></span>  
 <span data-ttu-id="684f5-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="684f5-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="684f5-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="684f5-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="684f5-130">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="684f5-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="684f5-131">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="684f5-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="684f5-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="684f5-132">See also</span></span>

- [<span data-ttu-id="684f5-133">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="684f5-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="684f5-134">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="684f5-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
