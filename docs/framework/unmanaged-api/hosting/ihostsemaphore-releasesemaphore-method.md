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
ms.openlocfilehash: 660062fb69bb8fe0a06bbca9046d65175fb72f9a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683036"
---
# <a name="ihostsemaphorereleasesemaphore-method"></a><span data-ttu-id="cf83a-102">IHostSemaphore::ReleaseSemaphore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cf83a-102">IHostSemaphore::ReleaseSemaphore Method</span></span>

<span data-ttu-id="cf83a-103">Geçerli [ıhostsemafor](ihostsemaphore-interface.md) örneğinin sayısını belirtilen miktarda arttırır.</span><span class="sxs-lookup"><span data-stu-id="cf83a-103">Increases the count of the current [IHostSemaphore](ihostsemaphore-interface.md) instance by the specified amount.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf83a-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="cf83a-104">Syntax</span></span>  
  
```cpp  
HRESULT ReleaseSemaphore (  
    [in]  LONG  lReleaseCount,  
    [out] LONG  *lpPreviousCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf83a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cf83a-105">Parameters</span></span>  

 `lReleaseCount`  
 <span data-ttu-id="cf83a-106">'ndaki Geçerli örnek sayısının artıralınacağı miktar `IHostSemaphore` .</span><span class="sxs-lookup"><span data-stu-id="cf83a-106">[in] The amount by which to increase the count of the current `IHostSemaphore` instance.</span></span> <span data-ttu-id="cf83a-107">Bu miktar sıfırdan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cf83a-107">This amount must be greater than zero.</span></span>  
  
 `lpPreviousCount`  
 <span data-ttu-id="cf83a-108">dışı Önceki sayıma yönelik bir işaretçi veya arayan önceki sayıyı gerektirmiyorsa null.</span><span class="sxs-lookup"><span data-stu-id="cf83a-108">[out] A pointer to the previous count, or null if the caller does not require the previous count.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cf83a-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cf83a-109">Return Value</span></span>  
  
|<span data-ttu-id="cf83a-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cf83a-110">HRESULT</span></span>|<span data-ttu-id="cf83a-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cf83a-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cf83a-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="cf83a-112">S_OK</span></span>|<span data-ttu-id="cf83a-113">`ReleaseSemaphore` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="cf83a-113">`ReleaseSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="cf83a-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cf83a-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cf83a-115">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="cf83a-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cf83a-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cf83a-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cf83a-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="cf83a-117">The call timed out.</span></span>|  
|<span data-ttu-id="cf83a-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cf83a-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cf83a-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="cf83a-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cf83a-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cf83a-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cf83a-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="cf83a-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cf83a-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cf83a-122">E_FAIL</span></span>|<span data-ttu-id="cf83a-123">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="cf83a-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cf83a-124">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="cf83a-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cf83a-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="cf83a-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf83a-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cf83a-126">Remarks</span></span>  

 <span data-ttu-id="cf83a-127">CLR tipik olarak, `ReleaseSemaphore` bir kaynağı kullanmayı tamamladığından, parametresi için 1 değerini geçirerek konağa bildirimde bulunur `lReleaseCount` .</span><span class="sxs-lookup"><span data-stu-id="cf83a-127">The CLR typically calls `ReleaseSemaphore` to notify the host that it has finished using a resource, passing a value of 1 for the `lReleaseCount` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf83a-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cf83a-128">Requirements</span></span>  

 <span data-ttu-id="cf83a-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf83a-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf83a-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cf83a-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cf83a-131">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="cf83a-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cf83a-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf83a-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf83a-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf83a-133">See also</span></span>

- [<span data-ttu-id="cf83a-134">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cf83a-134">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="cf83a-135">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cf83a-135">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="cf83a-136">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cf83a-136">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="cf83a-137">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cf83a-137">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="cf83a-138">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cf83a-138">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
