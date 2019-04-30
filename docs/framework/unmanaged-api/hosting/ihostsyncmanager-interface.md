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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 200da8b87b52a29c2b075d1e06929031d3f588b7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769635"
---
# <a name="ihostsyncmanager-interface"></a><span data-ttu-id="c6a81-102">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c6a81-102">IHostSyncManager Interface</span></span>
<span data-ttu-id="c6a81-103">Ortak dil çalışma zamanı (CLR) Win32 eşitleme işlevleri kullanmak yerine konak çağırarak eşitleme temellerine oluşturmaya olanak tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c6a81-103">Provides methods that allow the common language runtime (CLR) to create synchronization primitives by calling the host instead of using the Win32 synchronization functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c6a81-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c6a81-104">Methods</span></span>  
  
|<span data-ttu-id="c6a81-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c6a81-105">Method</span></span>|<span data-ttu-id="c6a81-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6a81-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c6a81-107">CreateAutoEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c6a81-107">CreateAutoEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createautoevent-method.md)|<span data-ttu-id="c6a81-108">Otomatik sıfırlama olayından nesne oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c6a81-108">Creates an auto-reset event object.</span></span>|  
|[<span data-ttu-id="c6a81-109">CreateCrst Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c6a81-109">CreateCrst Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrst-method.md)|<span data-ttu-id="c6a81-110">Eşitleme için kritik bölüm nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c6a81-110">Creates a critical section object for synchronization.</span></span>|  
|[<span data-ttu-id="c6a81-111">CreateCrstWithSpinCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c6a81-111">CreateCrstWithSpinCount Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrstwithspincount-method.md)|<span data-ttu-id="c6a81-112">Eşitleme döndürme sayısına sahip bir kritik bölüm nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c6a81-112">Creates a critical section object with spin count for synchronization.</span></span>|  
|[<span data-ttu-id="c6a81-113">CreateManualEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c6a81-113">CreateManualEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmanualevent-method.md)|<span data-ttu-id="c6a81-114">Elle sıfırlama olayı nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c6a81-114">Creates a manual-reset event object.</span></span>|  
|[<span data-ttu-id="c6a81-115">CreateMonitorEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c6a81-115">CreateMonitorEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md)|<span data-ttu-id="c6a81-116">İzlenen otomatik sıfırlama olayı nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c6a81-116">Creates a monitored auto-reset event object.</span></span>|  
|[<span data-ttu-id="c6a81-117">CreateRWLockReaderEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c6a81-117">CreateRWLockReaderEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockreaderevent-method.md)|<span data-ttu-id="c6a81-118">Bir okuyucu kilidi uygulanması için bir elle sıfırlama olayı nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c6a81-118">Creates a manual-reset event object for the implementation of a reader lock.</span></span>|  
|[<span data-ttu-id="c6a81-119">CreateRWLockWriterEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c6a81-119">CreateRWLockWriterEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockwriterevent-method.md)|<span data-ttu-id="c6a81-120">Bir yazıcı kilidi uygulanması için bir otomatik sıfırlama olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c6a81-120">Creates an auto-reset event object for the implementation of a writer lock.</span></span>|  
|[<span data-ttu-id="c6a81-121">CreateSemaphore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c6a81-121">CreateSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createsemaphore-method.md)|<span data-ttu-id="c6a81-122">Oluşturur bir [Ihostsemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) bekleme olayları için semafor kullanılacak bir CLR nesnesi.</span><span class="sxs-lookup"><span data-stu-id="c6a81-122">Creates an [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) object for the CLR to use as a semaphore for wait events.</span></span>|  
|[<span data-ttu-id="c6a81-123">SetCLRSyncManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c6a81-123">SetCLRSyncManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-setclrsyncmanager-method.md)|<span data-ttu-id="c6a81-124">Kümeleri [Iclrsyncmanager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) geçerli ile ilişkilendirilecek örneği `IHostSyncManager` örneği.</span><span class="sxs-lookup"><span data-stu-id="c6a81-124">Sets the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instance to associate with the current `IHostSyncManager` instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6a81-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c6a81-125">Remarks</span></span>  
 <span data-ttu-id="c6a81-126">Ana bilgisayarın uygulaması CLR bulur `IHostSyncManager` çağırarak [Ihostcontrol::gethostmanager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) yöntemi ile bir `IID` IID_IHostSyncManager biri.</span><span class="sxs-lookup"><span data-stu-id="c6a81-126">The CLR discovers the host's implementation of `IHostSyncManager` by calling the [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) method with an `IID` of IID_IHostSyncManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6a81-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c6a81-127">Requirements</span></span>  
 <span data-ttu-id="c6a81-128">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6a81-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6a81-129">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c6a81-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c6a81-130">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="c6a81-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c6a81-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6a81-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6a81-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6a81-132">See also</span></span>

- [<span data-ttu-id="c6a81-133">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c6a81-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="c6a81-134">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c6a81-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
