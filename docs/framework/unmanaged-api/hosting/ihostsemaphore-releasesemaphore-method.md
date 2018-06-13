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
ms.openlocfilehash: bb5d3f28d083574985e28e2c043743989c8b4680
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440408"
---
# <a name="ihostsemaphorereleasesemaphore-method"></a><span data-ttu-id="dcbfa-102">IHostSemaphore::ReleaseSemaphore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dcbfa-102">IHostSemaphore::ReleaseSemaphore Method</span></span>
<span data-ttu-id="dcbfa-103">Geçerli sayısını azaltır [Ihostsemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) örneği tarafından belirtilen tutar.</span><span class="sxs-lookup"><span data-stu-id="dcbfa-103">Increases the count of the current [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) instance by the specified amount.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcbfa-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dcbfa-104">Syntax</span></span>  
  
```  
HRESULT ReleaseSemaphore (  
    [in]  LONG  lReleaseCount,  
    [out] LONG  *lpPreviousCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dcbfa-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dcbfa-105">Parameters</span></span>  
 `lReleaseCount`  
 <span data-ttu-id="dcbfa-106">[in] Geçerli sayısını artırmak için bir miktarda `IHostSemaphore` örneği.</span><span class="sxs-lookup"><span data-stu-id="dcbfa-106">[in] The amount by which to increase the count of the current `IHostSemaphore` instance.</span></span> <span data-ttu-id="dcbfa-107">Bu miktar sıfırdan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dcbfa-107">This amount must be greater than zero.</span></span>  
  
 `lpPreviousCount`  
 <span data-ttu-id="dcbfa-108">[out] Önceki sayısı veya çağıranın önceki sayısı gerektirmiyorsa null işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dcbfa-108">[out] A pointer to the previous count, or null if the caller does not require the previous count.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dcbfa-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="dcbfa-109">Return Value</span></span>  
  
|<span data-ttu-id="dcbfa-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dcbfa-110">HRESULT</span></span>|<span data-ttu-id="dcbfa-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dcbfa-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dcbfa-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="dcbfa-112">S_OK</span></span>|<span data-ttu-id="dcbfa-113">`ReleaseSemaphore` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="dcbfa-113">`ReleaseSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="dcbfa-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dcbfa-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dcbfa-115">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="dcbfa-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dcbfa-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dcbfa-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dcbfa-117">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="dcbfa-117">The call timed out.</span></span>|  
|<span data-ttu-id="dcbfa-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dcbfa-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dcbfa-119">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="dcbfa-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dcbfa-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dcbfa-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dcbfa-121">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="dcbfa-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dcbfa-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dcbfa-122">E_FAIL</span></span>|<span data-ttu-id="dcbfa-123">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="dcbfa-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dcbfa-124">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="dcbfa-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dcbfa-125">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="dcbfa-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dcbfa-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dcbfa-126">Remarks</span></span>  
 <span data-ttu-id="dcbfa-127">CLR genellikle çağırır `ReleaseSemaphore` ana bilgisayar, değerini 1 olarak geçirme bir kaynağı kullanarak tamamlandığını bildirmek için `lReleaseCount` parametresi.</span><span class="sxs-lookup"><span data-stu-id="dcbfa-127">The CLR typically calls `ReleaseSemaphore` to notify the host that it has finished using a resource, passing a value of 1 for the `lReleaseCount` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcbfa-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dcbfa-128">Requirements</span></span>  
 <span data-ttu-id="dcbfa-129">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcbfa-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcbfa-130">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dcbfa-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dcbfa-131">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="dcbfa-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dcbfa-132">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcbfa-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcbfa-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dcbfa-133">See Also</span></span>  
 [<span data-ttu-id="dcbfa-134">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dcbfa-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="dcbfa-135">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dcbfa-135">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="dcbfa-136">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dcbfa-136">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="dcbfa-137">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dcbfa-137">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="dcbfa-138">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dcbfa-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
