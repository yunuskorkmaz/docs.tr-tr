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
ms.openlocfilehash: 6b2f57c7147cc8ff2abff848bd1e4661c2f5e728
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95682893"
---
# <a name="ihostsyncmanagercreatecrstwithspincount-method"></a><span data-ttu-id="15bd1-102">IHostSyncManager::CreateCrstWithSpinCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="15bd1-102">IHostSyncManager::CreateCrstWithSpinCount Method</span></span>

<span data-ttu-id="15bd1-103">Eşitleme için döngü sayısı olan bir kritik bölüm nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="15bd1-103">Creates a critical section object with spin count for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15bd1-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="15bd1-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCrstWithSpinCount (  
    [in]  DWORD dwSpinCount,  
    [out] IHostCrst** ppCrst  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15bd1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="15bd1-105">Parameters</span></span>  

 `dwSpinCount`  
 <span data-ttu-id="15bd1-106">'ndaki Kritik bölüm nesnesinin döndürme sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="15bd1-106">[in] Specifies the spin count for the critical section object.</span></span>  
  
 `ppCrst`  
 <span data-ttu-id="15bd1-107">dışı [IHostCrst](ihostcrst-interface.md) örneğinin adresine yönelik bir işaretçi veya kritik bölüm oluşturulanmadıysa null.</span><span class="sxs-lookup"><span data-stu-id="15bd1-107">[out] A pointer to the address of an [IHostCrst](ihostcrst-interface.md) instance, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="15bd1-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="15bd1-108">Return Value</span></span>  
  
|<span data-ttu-id="15bd1-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="15bd1-109">HRESULT</span></span>|<span data-ttu-id="15bd1-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15bd1-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="15bd1-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="15bd1-111">S_OK</span></span>|<span data-ttu-id="15bd1-112">`CreateCrstWithSpinCount` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="15bd1-112">`CreateCrstWithSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="15bd1-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="15bd1-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="15bd1-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="15bd1-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="15bd1-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="15bd1-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="15bd1-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="15bd1-116">The call timed out.</span></span>|  
|<span data-ttu-id="15bd1-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="15bd1-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="15bd1-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="15bd1-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="15bd1-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="15bd1-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="15bd1-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="15bd1-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="15bd1-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="15bd1-121">E_FAIL</span></span>|<span data-ttu-id="15bd1-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="15bd1-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="15bd1-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="15bd1-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="15bd1-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="15bd1-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="15bd1-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="15bd1-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="15bd1-126">İstenen kritik bölümü oluşturmak için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="15bd1-126">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15bd1-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="15bd1-127">Remarks</span></span>  

 <span data-ttu-id="15bd1-128">Bir döndürme sayısı yalnızca çok işlemcili bir sistemde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="15bd1-128">A spin count is used only on a multi-processor system.</span></span> <span data-ttu-id="15bd1-129">Dönüş sayısı, bir çağıran iş parçacığının, kullanılamayan bir kritik bölümle ilişkili bir semafor üzerinde bekleme işlemi gerçekleştirmeden önce kaç kez dönmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="15bd1-129">The spin count specifies the number of times a calling thread must spin before it performs a wait operation on a semaphore that is associated with an unavailable critical section.</span></span> <span data-ttu-id="15bd1-130">Kritik bölüm, döndürme işlemi sırasında ücretsiz hale gelirse, çağıran iş parçacığı bekleme işlemini önler.</span><span class="sxs-lookup"><span data-stu-id="15bd1-130">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span> <span data-ttu-id="15bd1-131">`CreateCrstWithSpinCount` Win32 işlevini yansıtır `InitializeCriticalSectionAndSpinCount` .</span><span class="sxs-lookup"><span data-stu-id="15bd1-131">`CreateCrstWithSpinCount` mirrors the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15bd1-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="15bd1-132">Requirements</span></span>  

 <span data-ttu-id="15bd1-133">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15bd1-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15bd1-134">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="15bd1-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="15bd1-135">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="15bd1-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="15bd1-136">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15bd1-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15bd1-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15bd1-137">See also</span></span>

- [<span data-ttu-id="15bd1-138">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="15bd1-138">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="15bd1-139">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="15bd1-139">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="15bd1-140">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="15bd1-140">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
