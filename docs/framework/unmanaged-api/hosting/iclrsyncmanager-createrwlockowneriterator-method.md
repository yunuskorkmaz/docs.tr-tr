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
ms.openlocfilehash: 450530baed850a66327c4b1326c399529b3de67d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64630577"
---
# <a name="iclrsyncmanagercreaterwlockowneriterator-method"></a><span data-ttu-id="a9875-102">ICLRSyncManager::CreateRWLockOwnerIterator Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a9875-102">ICLRSyncManager::CreateRWLockOwnerIterator Method</span></span>
<span data-ttu-id="a9875-103">Ortak dil çalışma zamanı (CLR) Okuyucu-Yazıcı kilit Bekleyen görevler kümesini belirlemek için kullanılacak ana bilgisayar için bir yineleyici oluşturma isteği.</span><span class="sxs-lookup"><span data-stu-id="a9875-103">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9875-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a9875-104">Syntax</span></span>  
  
```  
HRESULT CreateRWLockOwnerIterator (  
    [in]  SIZE_T    cookie,  
    [out] SIZE_T   *pIterator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9875-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a9875-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="a9875-106">[in] İstenen Okuyucu-Yazıcı kilidi ile ilişkili tanımlama.</span><span class="sxs-lookup"><span data-stu-id="a9875-106">[in] The cookie associated with the desired reader-writer lock.</span></span>  
  
 `pIterator`  
 <span data-ttu-id="a9875-107">[out] Geçirilebilir bir yineleyici için bir işaretçi [GetRWLockOwnerNext](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) ve [Deleterwlockownerıterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="a9875-107">[out] A pointer to an iterator that can be passed to the [GetRWLockOwnerNext](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) and [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) methods.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a9875-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a9875-108">Return Value</span></span>  
  
|<span data-ttu-id="a9875-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a9875-109">HRESULT</span></span>|<span data-ttu-id="a9875-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a9875-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a9875-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a9875-111">S_OK</span></span>|<span data-ttu-id="a9875-112">`CreateRWLockOwnerIterator` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="a9875-112">`CreateRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="a9875-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a9875-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a9875-114">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="a9875-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a9875-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a9875-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a9875-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="a9875-116">The call timed out.</span></span>|  
|<span data-ttu-id="a9875-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a9875-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a9875-118">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="a9875-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a9875-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a9875-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a9875-120">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="a9875-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a9875-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a9875-121">E_FAIL</span></span>|<span data-ttu-id="a9875-122">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a9875-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a9875-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a9875-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a9875-124">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="a9875-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a9875-125">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="a9875-125">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="a9875-126">`CreateRWLockOwnerIterator` yönetilen kod çalışmakta olan bir iş parçacığında çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="a9875-126">`CreateRWLockOwnerIterator` was called on a thread that is currently running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9875-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a9875-127">Remarks</span></span>  
 <span data-ttu-id="a9875-128">Ana bilgisayar genellikle arama `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`, ve `GetRWLockOwnerNext` kilitlenme algılaması sırasında yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a9875-128">Hosts typically call the `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`, and `GetRWLockOwnerNext` methods during deadlock detection.</span></span> <span data-ttu-id="a9875-129">Konak, CLR Okuyucu-Yazıcı kilidi Canlı girişimi yaptığından Okuyucu-Yazıcı kilidi hala geçerli olduğunu sağlamaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="a9875-129">The host is responsible for ensuring that the reader-writer lock is still valid, because the CLR makes no attempt to keep the reader-writer lock alive.</span></span> <span data-ttu-id="a9875-130">Çeşitli stratejileri kilit doğruluğundan emin olmak konak için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="a9875-130">Several strategies are available for the host to ensure the validity of the lock:</span></span>  
  
- <span data-ttu-id="a9875-131">Ana sürüm Okuyucu-Yazıcı kilidi çağrılarda engelleyebilirsiniz (örneğin, [Ihostsemaphore::releasesemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)) sağlarken bu blok kilitlenmeye neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="a9875-131">The host can block release calls on the reader-writer lock (for example, [IHostSemaphore::ReleaseSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)) while ensuring that this block does not cause deadlock.</span></span>  
  
- <span data-ttu-id="a9875-132">Konak, bu blok kilitlenmeye neden olmadığından yeniden sağlama Okuyucu-Yazıcı kilidi ile ilişkili olay nesnesindeki beklemesini çıkış engelleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a9875-132">The host can block the exit from waiting on the event object associated with the reader-writer lock, again ensuring that this block does not cause deadlock.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a9875-133">`CreateRWLockOwnerIterator` şu anda yürütülen yönetilmeyen kod parçacıklarında çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a9875-133">`CreateRWLockOwnerIterator` must be called only on threads that are currently executing unmanaged code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9875-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a9875-134">Requirements</span></span>  
 <span data-ttu-id="a9875-135">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9875-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9875-136">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a9875-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a9875-137">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="a9875-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a9875-138">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9875-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9875-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9875-139">See also</span></span>

- [<span data-ttu-id="a9875-140">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a9875-140">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="a9875-141">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a9875-141">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
