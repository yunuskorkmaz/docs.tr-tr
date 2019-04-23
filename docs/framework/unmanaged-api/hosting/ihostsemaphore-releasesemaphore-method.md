---
title: IHostSemaphore::ReleaseSemaphore Yöntemi
ms.date: 03/30/2017
api_name:
- IHostSemaphore.ReleaseSemaphore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSemaphore::ReleaseSemaphore
helpviewer_keywords:
- ReleaseSemaphore method [.NET Framework hosting]
- IHostSemaphore::ReleaseSemaphore method [.NET Framework hosting]
ms.assetid: a343d197-979a-4ac6-ab8c-cb8a05f3120e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 24ec56345a5b48540d2451769f739a236a85e47b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59100619"
---
# <a name="ihostsemaphorereleasesemaphore-method"></a><span data-ttu-id="f825a-102">IHostSemaphore::ReleaseSemaphore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f825a-102">IHostSemaphore::ReleaseSemaphore Method</span></span>
<span data-ttu-id="f825a-103">Geçerli sayısını artırır [Ihostsemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) örneği tarafından belirtilen süre.</span><span class="sxs-lookup"><span data-stu-id="f825a-103">Increases the count of the current [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) instance by the specified amount.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f825a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f825a-104">Syntax</span></span>  
  
```  
HRESULT ReleaseSemaphore (  
    [in]  LONG  lReleaseCount,  
    [out] LONG  *lpPreviousCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f825a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f825a-105">Parameters</span></span>  
 `lReleaseCount`  
 <span data-ttu-id="f825a-106">[in] Geçerli sayısını artırmak tutarı `IHostSemaphore` örneği.</span><span class="sxs-lookup"><span data-stu-id="f825a-106">[in] The amount by which to increase the count of the current `IHostSemaphore` instance.</span></span> <span data-ttu-id="f825a-107">Bu miktar sıfırdan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f825a-107">This amount must be greater than zero.</span></span>  
  
 `lpPreviousCount`  
 <span data-ttu-id="f825a-108">[out] Önceki sayısı veya çağıranın önceki sayısı gerektirmiyorsa null bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f825a-108">[out] A pointer to the previous count, or null if the caller does not require the previous count.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f825a-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f825a-109">Return Value</span></span>  
  
|<span data-ttu-id="f825a-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f825a-110">HRESULT</span></span>|<span data-ttu-id="f825a-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f825a-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f825a-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="f825a-112">S_OK</span></span>|<span data-ttu-id="f825a-113">`ReleaseSemaphore` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="f825a-113">`ReleaseSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="f825a-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f825a-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f825a-115">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="f825a-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f825a-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f825a-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f825a-117">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="f825a-117">The call timed out.</span></span>|  
|<span data-ttu-id="f825a-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f825a-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f825a-119">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="f825a-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f825a-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f825a-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f825a-121">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="f825a-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f825a-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f825a-122">E_FAIL</span></span>|<span data-ttu-id="f825a-123">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="f825a-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f825a-124">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f825a-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f825a-125">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="f825a-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f825a-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f825a-126">Remarks</span></span>  
 <span data-ttu-id="f825a-127">CLR genellikle çağrıları `ReleaseSemaphore` için 1 değerini geçirme, bir kaynağı kullanarak tamamlanmış ana bilgisayara bildirmek için `lReleaseCount` parametresi.</span><span class="sxs-lookup"><span data-stu-id="f825a-127">The CLR typically calls `ReleaseSemaphore` to notify the host that it has finished using a resource, passing a value of 1 for the `lReleaseCount` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f825a-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f825a-128">Requirements</span></span>  
 <span data-ttu-id="f825a-129">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f825a-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f825a-130">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f825a-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f825a-131">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="f825a-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f825a-132">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f825a-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f825a-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f825a-133">See also</span></span>

- [<span data-ttu-id="f825a-134">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f825a-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="f825a-135">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f825a-135">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="f825a-136">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f825a-136">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="f825a-137">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f825a-137">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="f825a-138">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f825a-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
