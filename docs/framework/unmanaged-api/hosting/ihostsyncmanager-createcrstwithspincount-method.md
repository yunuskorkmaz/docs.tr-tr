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
ms.openlocfilehash: 632b8d43ed459d489825dc796d39864e2ed15ec3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139418"
---
# <a name="ihostsyncmanagercreatecrstwithspincount-method"></a><span data-ttu-id="d8bad-102">IHostSyncManager::CreateCrstWithSpinCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d8bad-102">IHostSyncManager::CreateCrstWithSpinCount Method</span></span>
<span data-ttu-id="d8bad-103">Eşitleme için döngü sayısı olan bir kritik bölüm nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d8bad-103">Creates a critical section object with spin count for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8bad-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8bad-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCrstWithSpinCount (  
    [in]  DWORD dwSpinCount,  
    [out] IHostCrst** ppCrst  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8bad-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d8bad-105">Parameters</span></span>  
 `dwSpinCount`  
 <span data-ttu-id="d8bad-106">'ndaki Kritik bölüm nesnesinin döndürme sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d8bad-106">[in] Specifies the spin count for the critical section object.</span></span>  
  
 `ppCrst`  
 <span data-ttu-id="d8bad-107">dışı [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) örneğinin adresine yönelik bir işaretçi veya kritik bölüm oluşturulanmadıysa null.</span><span class="sxs-lookup"><span data-stu-id="d8bad-107">[out] A pointer to the address of an [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d8bad-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d8bad-108">Return Value</span></span>  
  
|<span data-ttu-id="d8bad-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d8bad-109">HRESULT</span></span>|<span data-ttu-id="d8bad-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d8bad-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d8bad-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d8bad-111">S_OK</span></span>|<span data-ttu-id="d8bad-112">`CreateCrstWithSpinCount` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="d8bad-112">`CreateCrstWithSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="d8bad-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d8bad-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d8bad-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="d8bad-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d8bad-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d8bad-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d8bad-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="d8bad-116">The call timed out.</span></span>|  
|<span data-ttu-id="d8bad-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d8bad-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d8bad-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="d8bad-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d8bad-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d8bad-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d8bad-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="d8bad-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d8bad-121">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="d8bad-121">E_FAIL</span></span>|<span data-ttu-id="d8bad-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="d8bad-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d8bad-123">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d8bad-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d8bad-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="d8bad-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d8bad-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="d8bad-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="d8bad-126">İstenen kritik bölümü oluşturmak için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="d8bad-126">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8bad-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8bad-127">Remarks</span></span>  
 <span data-ttu-id="d8bad-128">Bir döndürme sayısı yalnızca çok işlemcili bir sistemde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d8bad-128">A spin count is used only on a multi-processor system.</span></span> <span data-ttu-id="d8bad-129">Dönüş sayısı, bir çağıran iş parçacığının, kullanılamayan bir kritik bölümle ilişkili bir semafor üzerinde bekleme işlemi gerçekleştirmeden önce kaç kez dönmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d8bad-129">The spin count specifies the number of times a calling thread must spin before it performs a wait operation on a semaphore that is associated with an unavailable critical section.</span></span> <span data-ttu-id="d8bad-130">Kritik bölüm, döndürme işlemi sırasında ücretsiz hale gelirse, çağıran iş parçacığı bekleme işlemini önler.</span><span class="sxs-lookup"><span data-stu-id="d8bad-130">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span> <span data-ttu-id="d8bad-131">`CreateCrstWithSpinCount` Win32 `InitializeCriticalSectionAndSpinCount` işlevini yansıtır.</span><span class="sxs-lookup"><span data-stu-id="d8bad-131">`CreateCrstWithSpinCount` mirrors the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8bad-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d8bad-132">Requirements</span></span>  
 <span data-ttu-id="d8bad-133">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8bad-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8bad-134">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d8bad-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d8bad-135">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="d8bad-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d8bad-136">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8bad-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8bad-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8bad-137">See also</span></span>

- [<span data-ttu-id="d8bad-138">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8bad-138">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="d8bad-139">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8bad-139">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="d8bad-140">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8bad-140">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
