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
ms.openlocfilehash: e96492270c403f93687245cee8b680dc16b3c787
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803119"
---
# <a name="ihostsyncmanager-interface"></a><span data-ttu-id="a5964-102">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a5964-102">IHostSyncManager Interface</span></span>
<span data-ttu-id="a5964-103">Ortak dil çalışma zamanının (CLR) Win32 eşitleme işlevlerini kullanmak yerine Konağı çağırarak eşitleme temelleri oluşturmasına izin veren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a5964-103">Provides methods that allow the common language runtime (CLR) to create synchronization primitives by calling the host instead of using the Win32 synchronization functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a5964-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a5964-104">Methods</span></span>  
  
|<span data-ttu-id="a5964-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a5964-105">Method</span></span>|<span data-ttu-id="a5964-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a5964-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a5964-107">CreateAutoEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a5964-107">CreateAutoEvent Method</span></span>](ihostsyncmanager-createautoevent-method.md)|<span data-ttu-id="a5964-108">Otomatik sıfırlama olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a5964-108">Creates an auto-reset event object.</span></span>|  
|[<span data-ttu-id="a5964-109">CreateCrst Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a5964-109">CreateCrst Method</span></span>](ihostsyncmanager-createcrst-method.md)|<span data-ttu-id="a5964-110">Eşitleme için bir kritik bölüm nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a5964-110">Creates a critical section object for synchronization.</span></span>|  
|[<span data-ttu-id="a5964-111">CreateCrstWithSpinCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a5964-111">CreateCrstWithSpinCount Method</span></span>](ihostsyncmanager-createcrstwithspincount-method.md)|<span data-ttu-id="a5964-112">Eşitleme için döngü sayısı olan bir kritik bölüm nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a5964-112">Creates a critical section object with spin count for synchronization.</span></span>|  
|[<span data-ttu-id="a5964-113">CreateManualEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a5964-113">CreateManualEvent Method</span></span>](ihostsyncmanager-createmanualevent-method.md)|<span data-ttu-id="a5964-114">El ile sıfırlama olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a5964-114">Creates a manual-reset event object.</span></span>|  
|[<span data-ttu-id="a5964-115">CreateMonitorEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a5964-115">CreateMonitorEvent Method</span></span>](ihostsyncmanager-createmonitorevent-method.md)|<span data-ttu-id="a5964-116">İzlenen otomatik sıfırlama olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a5964-116">Creates a monitored auto-reset event object.</span></span>|  
|[<span data-ttu-id="a5964-117">CreateRWLockReaderEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a5964-117">CreateRWLockReaderEvent Method</span></span>](ihostsyncmanager-createrwlockreaderevent-method.md)|<span data-ttu-id="a5964-118">Bir okuyucu kilidinin uygulanması için el ile sıfırlama olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a5964-118">Creates a manual-reset event object for the implementation of a reader lock.</span></span>|  
|[<span data-ttu-id="a5964-119">CreateRWLockWriterEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a5964-119">CreateRWLockWriterEvent Method</span></span>](ihostsyncmanager-createrwlockwriterevent-method.md)|<span data-ttu-id="a5964-120">Bir yazıcı kilidinin uygulanması için otomatik sıfırlama olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a5964-120">Creates an auto-reset event object for the implementation of a writer lock.</span></span>|  
|[<span data-ttu-id="a5964-121">CreateSemaphore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a5964-121">CreateSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createsemaphore-method.md)|<span data-ttu-id="a5964-122">CLR için, bekleme olayları için semafor olarak kullanılacak bir [ıhostsemafor](ihostsemaphore-interface.md) nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a5964-122">Creates an [IHostSemaphore](ihostsemaphore-interface.md) object for the CLR to use as a semaphore for wait events.</span></span>|  
|[<span data-ttu-id="a5964-123">SetCLRSyncManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a5964-123">SetCLRSyncManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-setclrsyncmanager-method.md)|<span data-ttu-id="a5964-124">[ICLRSyncManager](iclrsyncmanager-interface.md) örneğini geçerli örnekle ilişkilendirilecek şekilde ayarlar `IHostSyncManager` .</span><span class="sxs-lookup"><span data-stu-id="a5964-124">Sets the [ICLRSyncManager](iclrsyncmanager-interface.md) instance to associate with the current `IHostSyncManager` instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5964-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a5964-125">Remarks</span></span>  
 <span data-ttu-id="a5964-126">CLR, `IHostSyncManager` IID_IHostSyncManager Ile [IHostControl:: GetHostManager](ihostcontrol-gethostmanager-method.md) metodunu çağırarak konağın uygulamasını bulur `IID` .</span><span class="sxs-lookup"><span data-stu-id="a5964-126">The CLR discovers the host's implementation of `IHostSyncManager` by calling the [IHostControl::GetHostManager](ihostcontrol-gethostmanager-method.md) method with an `IID` of IID_IHostSyncManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5964-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a5964-127">Requirements</span></span>  
 <span data-ttu-id="a5964-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5964-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5964-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a5964-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a5964-130">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="a5964-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a5964-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5964-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5964-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a5964-132">See also</span></span>

- [<span data-ttu-id="a5964-133">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a5964-133">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="a5964-134">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a5964-134">Hosting Interfaces</span></span>](hosting-interfaces.md)
