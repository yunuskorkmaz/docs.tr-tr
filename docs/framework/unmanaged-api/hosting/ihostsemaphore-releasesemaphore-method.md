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
ms.openlocfilehash: 33a92365e7765befe669439eabefac607232ff15
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139468"
---
# <a name="ihostsemaphorereleasesemaphore-method"></a><span data-ttu-id="07e1b-102">IHostSemaphore::ReleaseSemaphore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="07e1b-102">IHostSemaphore::ReleaseSemaphore Method</span></span>
<span data-ttu-id="07e1b-103">Geçerli [ıhostsemafor](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) örneğinin sayısını belirtilen miktarda arttırır.</span><span class="sxs-lookup"><span data-stu-id="07e1b-103">Increases the count of the current [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) instance by the specified amount.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07e1b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="07e1b-104">Syntax</span></span>  
  
```cpp  
HRESULT ReleaseSemaphore (  
    [in]  LONG  lReleaseCount,  
    [out] LONG  *lpPreviousCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07e1b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="07e1b-105">Parameters</span></span>  
 `lReleaseCount`  
 <span data-ttu-id="07e1b-106">'ndaki Geçerli `IHostSemaphore` örneğinin sayısını artırmak için gereken miktar.</span><span class="sxs-lookup"><span data-stu-id="07e1b-106">[in] The amount by which to increase the count of the current `IHostSemaphore` instance.</span></span> <span data-ttu-id="07e1b-107">Bu miktar sıfırdan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="07e1b-107">This amount must be greater than zero.</span></span>  
  
 `lpPreviousCount`  
 <span data-ttu-id="07e1b-108">dışı Önceki sayıma yönelik bir işaretçi veya arayan önceki sayıyı gerektirmiyorsa null.</span><span class="sxs-lookup"><span data-stu-id="07e1b-108">[out] A pointer to the previous count, or null if the caller does not require the previous count.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="07e1b-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="07e1b-109">Return Value</span></span>  
  
|<span data-ttu-id="07e1b-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="07e1b-110">HRESULT</span></span>|<span data-ttu-id="07e1b-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07e1b-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="07e1b-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="07e1b-112">S_OK</span></span>|<span data-ttu-id="07e1b-113">`ReleaseSemaphore` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="07e1b-113">`ReleaseSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="07e1b-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="07e1b-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="07e1b-115">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="07e1b-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="07e1b-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="07e1b-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="07e1b-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="07e1b-117">The call timed out.</span></span>|  
|<span data-ttu-id="07e1b-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="07e1b-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="07e1b-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="07e1b-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="07e1b-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="07e1b-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="07e1b-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="07e1b-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="07e1b-122">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="07e1b-122">E_FAIL</span></span>|<span data-ttu-id="07e1b-123">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="07e1b-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="07e1b-124">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="07e1b-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="07e1b-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="07e1b-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="07e1b-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="07e1b-126">Remarks</span></span>  
 <span data-ttu-id="07e1b-127">CLR genellikle, ana bilgisayara bir kaynağı kullanarak tamamlandığını bildirmek için `ReleaseSemaphore` çağırır ve `lReleaseCount` parametresi için 1 değerini geçirmiştir.</span><span class="sxs-lookup"><span data-stu-id="07e1b-127">The CLR typically calls `ReleaseSemaphore` to notify the host that it has finished using a resource, passing a value of 1 for the `lReleaseCount` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07e1b-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="07e1b-128">Requirements</span></span>  
 <span data-ttu-id="07e1b-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07e1b-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07e1b-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="07e1b-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="07e1b-131">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="07e1b-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="07e1b-132">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07e1b-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07e1b-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07e1b-133">See also</span></span>

- [<span data-ttu-id="07e1b-134">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="07e1b-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="07e1b-135">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="07e1b-135">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="07e1b-136">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="07e1b-136">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="07e1b-137">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="07e1b-137">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="07e1b-138">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="07e1b-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
