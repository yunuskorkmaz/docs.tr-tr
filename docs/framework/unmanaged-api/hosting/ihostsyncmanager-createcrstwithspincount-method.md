---
title: IHostSyncManager::CreateCrstWithSpinCount Yöntemi
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateCrstWithSpinCount
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateCrstWithSpinCount
helpviewer_keywords:
- CreateCrstWithSpinCount method [.NET Framework hosting]
- IHostSyncManager::CreateCrstWithSpinCount method [.NET Framework hosting]
ms.assetid: 7280fa8c-3639-4abf-91cb-bc343da742d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c4dd73efbad5ffac47c8585facd1717d77147fa
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501597"
---
# <a name="ihostsyncmanagercreatecrstwithspincount-method"></a><span data-ttu-id="a83d7-102">IHostSyncManager::CreateCrstWithSpinCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a83d7-102">IHostSyncManager::CreateCrstWithSpinCount Method</span></span>
<span data-ttu-id="a83d7-103">Eşitleme döndürme sayısına sahip bir kritik bölüm nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a83d7-103">Creates a critical section object with spin count for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a83d7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a83d7-104">Syntax</span></span>  
  
```  
HRESULT CreateCrstWithSpinCount (  
    [in]  DWORD dwSpinCount,  
    [out] IHostCrst** ppCrst  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a83d7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a83d7-105">Parameters</span></span>  
 `dwSpinCount`  
 <span data-ttu-id="a83d7-106">[in] Kritik bölüm nesne döndürme sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a83d7-106">[in] Specifies the spin count for the critical section object.</span></span>  
  
 `ppCrst`  
 <span data-ttu-id="a83d7-107">[out] Adresine bir işaretçi bir [Ihostcrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) örneği veya kritik bölüm oluşturulamadı yoksa null.</span><span class="sxs-lookup"><span data-stu-id="a83d7-107">[out] A pointer to the address of an [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a83d7-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a83d7-108">Return Value</span></span>  
  
|<span data-ttu-id="a83d7-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a83d7-109">HRESULT</span></span>|<span data-ttu-id="a83d7-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a83d7-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a83d7-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a83d7-111">S_OK</span></span>|<span data-ttu-id="a83d7-112">`CreateCrstWithSpinCount` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="a83d7-112">`CreateCrstWithSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="a83d7-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a83d7-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a83d7-114">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="a83d7-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a83d7-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a83d7-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a83d7-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="a83d7-116">The call timed out.</span></span>|  
|<span data-ttu-id="a83d7-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a83d7-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a83d7-118">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="a83d7-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a83d7-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a83d7-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a83d7-120">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="a83d7-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a83d7-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a83d7-121">E_FAIL</span></span>|<span data-ttu-id="a83d7-122">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a83d7-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a83d7-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a83d7-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a83d7-124">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="a83d7-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a83d7-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="a83d7-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="a83d7-126">İstenen kritik bölüm oluşturmak kullanılabilecek yeterli bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="a83d7-126">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a83d7-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a83d7-127">Remarks</span></span>  
 <span data-ttu-id="a83d7-128">Döngü sayısı yalnızca birden çok işlemcili bir sistemi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a83d7-128">A spin count is used only on a multi-processor system.</span></span> <span data-ttu-id="a83d7-129">Döngü sayısı kullanılamayan bir kritik bölümü ile ilişkili olan bir semaforu üzerinde bir bekleme işlemini gerçekleştirmeden önce bir çağıran iş parçacığını dönmesi gerekir sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a83d7-129">The spin count specifies the number of times a calling thread must spin before it performs a wait operation on a semaphore that is associated with an unavailable critical section.</span></span> <span data-ttu-id="a83d7-130">Kritik bölüm döndürme işlemi sırasında boş hale gelirse, çağıran iş parçacığını bekleme işlemi önler.</span><span class="sxs-lookup"><span data-stu-id="a83d7-130">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span> <span data-ttu-id="a83d7-131">`CreateCrstWithSpinCount` Win32 yansıtır `InitializeCriticalSectionAndSpinCount` işlevi.</span><span class="sxs-lookup"><span data-stu-id="a83d7-131">`CreateCrstWithSpinCount` mirrors the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a83d7-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a83d7-132">Requirements</span></span>  
 <span data-ttu-id="a83d7-133">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a83d7-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a83d7-134">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a83d7-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a83d7-135">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="a83d7-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a83d7-136">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a83d7-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a83d7-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a83d7-137">See also</span></span>
- [<span data-ttu-id="a83d7-138">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a83d7-138">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="a83d7-139">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a83d7-139">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="a83d7-140">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a83d7-140">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
