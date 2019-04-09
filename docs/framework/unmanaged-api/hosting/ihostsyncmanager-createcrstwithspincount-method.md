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
ms.openlocfilehash: 1a288edc89029804de277484741c1895af7859b1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081534"
---
# <a name="ihostsyncmanagercreatecrstwithspincount-method"></a><span data-ttu-id="d37a3-102">IHostSyncManager::CreateCrstWithSpinCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d37a3-102">IHostSyncManager::CreateCrstWithSpinCount Method</span></span>
<span data-ttu-id="d37a3-103">Eşitleme döndürme sayısına sahip bir kritik bölüm nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d37a3-103">Creates a critical section object with spin count for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d37a3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d37a3-104">Syntax</span></span>  
  
```  
HRESULT CreateCrstWithSpinCount (  
    [in]  DWORD dwSpinCount,  
    [out] IHostCrst** ppCrst  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d37a3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d37a3-105">Parameters</span></span>  
 `dwSpinCount`  
 <span data-ttu-id="d37a3-106">[in] Kritik bölüm nesne döndürme sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d37a3-106">[in] Specifies the spin count for the critical section object.</span></span>  
  
 `ppCrst`  
 <span data-ttu-id="d37a3-107">[out] Adresine bir işaretçi bir [Ihostcrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) örneği veya kritik bölüm oluşturulamadı yoksa null.</span><span class="sxs-lookup"><span data-stu-id="d37a3-107">[out] A pointer to the address of an [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d37a3-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d37a3-108">Return Value</span></span>  
  
|<span data-ttu-id="d37a3-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d37a3-109">HRESULT</span></span>|<span data-ttu-id="d37a3-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d37a3-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d37a3-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d37a3-111">S_OK</span></span>|`CreateCrstWithSpinCount` <span data-ttu-id="d37a3-112">başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="d37a3-112">returned successfully.</span></span>|  
|<span data-ttu-id="d37a3-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d37a3-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d37a3-114">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="d37a3-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d37a3-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d37a3-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d37a3-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="d37a3-116">The call timed out.</span></span>|  
|<span data-ttu-id="d37a3-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d37a3-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d37a3-118">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="d37a3-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d37a3-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d37a3-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d37a3-120">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="d37a3-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d37a3-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d37a3-121">E_FAIL</span></span>|<span data-ttu-id="d37a3-122">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="d37a3-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d37a3-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d37a3-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d37a3-124">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="d37a3-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d37a3-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="d37a3-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="d37a3-126">İstenen kritik bölüm oluşturmak kullanılabilecek yeterli bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="d37a3-126">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d37a3-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d37a3-127">Remarks</span></span>  
 <span data-ttu-id="d37a3-128">Döngü sayısı yalnızca birden çok işlemcili bir sistemi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d37a3-128">A spin count is used only on a multi-processor system.</span></span> <span data-ttu-id="d37a3-129">Döngü sayısı kullanılamayan bir kritik bölümü ile ilişkili olan bir semaforu üzerinde bir bekleme işlemini gerçekleştirmeden önce bir çağıran iş parçacığını dönmesi gerekir sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d37a3-129">The spin count specifies the number of times a calling thread must spin before it performs a wait operation on a semaphore that is associated with an unavailable critical section.</span></span> <span data-ttu-id="d37a3-130">Kritik bölüm döndürme işlemi sırasında boş hale gelirse, çağıran iş parçacığını bekleme işlemi önler.</span><span class="sxs-lookup"><span data-stu-id="d37a3-130">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span> `CreateCrstWithSpinCount` <span data-ttu-id="d37a3-131">Win32 yansıtır `InitializeCriticalSectionAndSpinCount` işlevi.</span><span class="sxs-lookup"><span data-stu-id="d37a3-131">mirrors the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d37a3-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d37a3-132">Requirements</span></span>  
 <span data-ttu-id="d37a3-133">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d37a3-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d37a3-134">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d37a3-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d37a3-135">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d37a3-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="d37a3-136">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="d37a3-136">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d37a3-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d37a3-137">See also</span></span>

- [<span data-ttu-id="d37a3-138">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d37a3-138">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="d37a3-139">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d37a3-139">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="d37a3-140">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d37a3-140">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
