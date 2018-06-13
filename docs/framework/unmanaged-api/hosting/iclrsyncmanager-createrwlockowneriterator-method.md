---
title: ICLRSyncManager::CreateRWLockOwnerIterator Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.CreateRWLockOwnerIterator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::CreateRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::CreateRWLockOwnerIterator method [.NET Framework hosting]
- CreateRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: b5535b87-9439-424e-b9b3-7d6fafb9819e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eda20543c28a7b97979463928ce307df9b830103
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436026"
---
# <a name="iclrsyncmanagercreaterwlockowneriterator-method"></a><span data-ttu-id="05f34-102">ICLRSyncManager::CreateRWLockOwnerIterator Yöntemi</span><span class="sxs-lookup"><span data-stu-id="05f34-102">ICLRSyncManager::CreateRWLockOwnerIterator Method</span></span>
<span data-ttu-id="05f34-103">Ortak dil çalışma zamanı (CLR) oluşturma yineleyici Okuyucu-Yazıcı kilit Bekleyen Görevler belirlemek için kullanılacak ana bilgisayar için istek sayısı.</span><span class="sxs-lookup"><span data-stu-id="05f34-103">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05f34-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="05f34-104">Syntax</span></span>  
  
```  
HRESULT CreateRWLockOwnerIterator (  
    [in]  SIZE_T    cookie,  
    [out] SIZE_T   *pIterator  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="05f34-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="05f34-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="05f34-106">[in] İstenen Okuyucu-Yazıcı kilidi ile ilişkili tanımlama.</span><span class="sxs-lookup"><span data-stu-id="05f34-106">[in] The cookie associated with the desired reader-writer lock.</span></span>  
  
 `pIterator`  
 <span data-ttu-id="05f34-107">[out] Bir işaretçi için geçirilen yineleyici [GetRWLockOwnerNext](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) ve [Deleterwlockownerıterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="05f34-107">[out] A pointer to an iterator that can be passed to the [GetRWLockOwnerNext](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) and [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) methods.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="05f34-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="05f34-108">Return Value</span></span>  
  
|<span data-ttu-id="05f34-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="05f34-109">HRESULT</span></span>|<span data-ttu-id="05f34-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="05f34-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="05f34-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="05f34-111">S_OK</span></span>|<span data-ttu-id="05f34-112">`CreateRWLockOwnerIterator` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="05f34-112">`CreateRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="05f34-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="05f34-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="05f34-114">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="05f34-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="05f34-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="05f34-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="05f34-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="05f34-116">The call timed out.</span></span>|  
|<span data-ttu-id="05f34-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="05f34-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="05f34-118">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="05f34-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="05f34-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="05f34-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="05f34-120">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="05f34-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="05f34-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="05f34-121">E_FAIL</span></span>|<span data-ttu-id="05f34-122">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="05f34-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="05f34-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="05f34-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="05f34-124">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="05f34-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="05f34-125">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="05f34-125">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="05f34-126">`CreateRWLockOwnerIterator` yönetilen kod şu anda çalışan bir iş parçacığında çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="05f34-126">`CreateRWLockOwnerIterator` was called on a thread that is currently running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05f34-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="05f34-127">Remarks</span></span>  
 <span data-ttu-id="05f34-128">Ana bilgisayarlar genellikle çağrısı `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`, ve `GetRWLockOwnerNext` kilitlenme algılama sırasında yöntemi.</span><span class="sxs-lookup"><span data-stu-id="05f34-128">Hosts typically call the `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`, and `GetRWLockOwnerNext` methods during deadlock detection.</span></span> <span data-ttu-id="05f34-129">Konak, CLR Okuyucu-Yazıcı kilit Canlı girişimi yaptığından Okuyucu-Yazıcı kilit hala geçerli olduğundan emin olmanın için sorumludur.</span><span class="sxs-lookup"><span data-stu-id="05f34-129">The host is responsible for ensuring that the reader-writer lock is still valid, because the CLR makes no attempt to keep the reader-writer lock alive.</span></span> <span data-ttu-id="05f34-130">Birkaç stratejileri kilit doğruluğundan emin olmak ana bilgisayar için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="05f34-130">Several strategies are available for the host to ensure the validity of the lock:</span></span>  
  
-   <span data-ttu-id="05f34-131">Ana yayın çağrıları Okuyucu-Yazıcı kilit engelleyebilirsiniz (örneğin, [Ihostsemaphore::releasesemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)) sağlarken bu bloğu kilitlenmeye neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="05f34-131">The host can block release calls on the reader-writer lock (for example, [IHostSemaphore::ReleaseSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)) while ensuring that this block does not cause deadlock.</span></span>  
  
-   <span data-ttu-id="05f34-132">Ana bilgisayar yeniden bu bloğu kilitlenmeye neden olmadığından emin olduktan Okuyucu-Yazıcı kilidi ile ilişkili olay nesnesinde beklemesini çıkış engelleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05f34-132">The host can block the exit from waiting on the event object associated with the reader-writer lock, again ensuring that this block does not cause deadlock.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05f34-133">`CreateRWLockOwnerIterator` yönetilmeyen kod şu anda yürütülen parçacıklarında çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="05f34-133">`CreateRWLockOwnerIterator` must be called only on threads that are currently executing unmanaged code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05f34-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="05f34-134">Requirements</span></span>  
 <span data-ttu-id="05f34-135">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05f34-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05f34-136">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="05f34-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="05f34-137">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="05f34-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="05f34-138">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05f34-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05f34-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="05f34-139">See Also</span></span>  
 [<span data-ttu-id="05f34-140">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="05f34-140">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="05f34-141">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="05f34-141">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
