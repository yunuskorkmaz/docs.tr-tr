---
description: ': Ihostsemafor:: Releasesemafor yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 368dc5ebe3017e03c0d6e8c57d0f122bc48d439f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707457"
---
# <a name="ihostsemaphorereleasesemaphore-method"></a><span data-ttu-id="04ef4-103">IHostSemaphore::ReleaseSemaphore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="04ef4-103">IHostSemaphore::ReleaseSemaphore Method</span></span>

<span data-ttu-id="04ef4-104">Geçerli [ıhostsemafor](ihostsemaphore-interface.md) örneğinin sayısını belirtilen miktarda arttırır.</span><span class="sxs-lookup"><span data-stu-id="04ef4-104">Increases the count of the current [IHostSemaphore](ihostsemaphore-interface.md) instance by the specified amount.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04ef4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="04ef4-105">Syntax</span></span>  
  
```cpp  
HRESULT ReleaseSemaphore (  
    [in]  LONG  lReleaseCount,  
    [out] LONG  *lpPreviousCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04ef4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="04ef4-106">Parameters</span></span>  

 `lReleaseCount`  
 <span data-ttu-id="04ef4-107">'ndaki Geçerli örnek sayısının artıralınacağı miktar `IHostSemaphore` .</span><span class="sxs-lookup"><span data-stu-id="04ef4-107">[in] The amount by which to increase the count of the current `IHostSemaphore` instance.</span></span> <span data-ttu-id="04ef4-108">Bu miktar sıfırdan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="04ef4-108">This amount must be greater than zero.</span></span>  
  
 `lpPreviousCount`  
 <span data-ttu-id="04ef4-109">dışı Önceki sayıma yönelik bir işaretçi veya arayan önceki sayıyı gerektirmiyorsa null.</span><span class="sxs-lookup"><span data-stu-id="04ef4-109">[out] A pointer to the previous count, or null if the caller does not require the previous count.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="04ef4-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="04ef4-110">Return Value</span></span>  
  
|<span data-ttu-id="04ef4-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="04ef4-111">HRESULT</span></span>|<span data-ttu-id="04ef4-112">Description</span><span class="sxs-lookup"><span data-stu-id="04ef4-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="04ef4-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="04ef4-113">S_OK</span></span>|<span data-ttu-id="04ef4-114">`ReleaseSemaphore` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="04ef4-114">`ReleaseSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="04ef4-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="04ef4-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="04ef4-116">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="04ef4-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="04ef4-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="04ef4-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="04ef4-118">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="04ef4-118">The call timed out.</span></span>|  
|<span data-ttu-id="04ef4-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="04ef4-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="04ef4-120">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="04ef4-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="04ef4-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="04ef4-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="04ef4-122">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="04ef4-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="04ef4-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="04ef4-123">E_FAIL</span></span>|<span data-ttu-id="04ef4-124">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="04ef4-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="04ef4-125">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="04ef4-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="04ef4-126">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="04ef4-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04ef4-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="04ef4-127">Remarks</span></span>  

 <span data-ttu-id="04ef4-128">CLR tipik olarak, `ReleaseSemaphore` bir kaynağı kullanmayı tamamladığından, parametresi için 1 değerini geçirerek konağa bildirimde bulunur `lReleaseCount` .</span><span class="sxs-lookup"><span data-stu-id="04ef4-128">The CLR typically calls `ReleaseSemaphore` to notify the host that it has finished using a resource, passing a value of 1 for the `lReleaseCount` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04ef4-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="04ef4-129">Requirements</span></span>  

 <span data-ttu-id="04ef4-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04ef4-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04ef4-131">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="04ef4-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="04ef4-132">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="04ef4-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="04ef4-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04ef4-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04ef4-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04ef4-134">See also</span></span>

- [<span data-ttu-id="04ef4-135">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="04ef4-135">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="04ef4-136">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="04ef4-136">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="04ef4-137">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="04ef4-137">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="04ef4-138">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="04ef4-138">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="04ef4-139">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="04ef4-139">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
