---
title: IHostTask::SetPriority Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTask.SetPriority
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::SetPriority
helpviewer_keywords:
- IHostTask::SetPriority method [.NET Framework hosting]
- SetPriority method [.NET Framework hosting]
ms.assetid: cd8c379b-c7a0-434f-8e23-899bd26be75d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5382341a8c0c6455438af9e8c476348ab2467a6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789512"
---
# <a name="ihosttasksetpriority-method"></a><span data-ttu-id="a70a6-102">IHostTask::SetPriority Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a70a6-102">IHostTask::SetPriority Method</span></span>
<span data-ttu-id="a70a6-103">Düzey istekler ana iş parçacığı önceliği ayarlamak için geçerli tarafından temsil edilen bir görev [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="a70a6-103">Requests that the host adjust the thread priority level for the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a70a6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a70a6-104">Syntax</span></span>  
  
```  
HRESULT SetPriority (  
    [in] int newPriority  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a70a6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a70a6-105">Parameters</span></span>  
 `newPriority`  
 <span data-ttu-id="a70a6-106">[in] Geçerli tarafından temsil edilen bir görev için istenen iş parçacığı öncelik değeri temsil eden bir tamsayı `IHostTask` örneği.</span><span class="sxs-lookup"><span data-stu-id="a70a6-106">[in] An integer that represents the requested thread priority value for the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a70a6-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a70a6-107">Return Value</span></span>  
  
|<span data-ttu-id="a70a6-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a70a6-108">HRESULT</span></span>|<span data-ttu-id="a70a6-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a70a6-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a70a6-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a70a6-110">S_OK</span></span>|<span data-ttu-id="a70a6-111">`SetPriority` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="a70a6-111">`SetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="a70a6-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a70a6-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a70a6-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="a70a6-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a70a6-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a70a6-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a70a6-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="a70a6-115">The call timed out.</span></span>|  
|<span data-ttu-id="a70a6-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a70a6-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a70a6-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="a70a6-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a70a6-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a70a6-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a70a6-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="a70a6-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a70a6-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a70a6-120">E_FAIL</span></span>|<span data-ttu-id="a70a6-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a70a6-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a70a6-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a70a6-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a70a6-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="a70a6-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a70a6-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a70a6-124">Remarks</span></span>  
 <span data-ttu-id="a70a6-125">İş parçacıkları kısmen bir iş parçacığının öncelik düzeyini temel alan bir hepsini bir kez deneme sistemi kullanarak verilen işlem.</span><span class="sxs-lookup"><span data-stu-id="a70a6-125">Threads are granted processing time using a round-robin system that is partly based on a thread's priority level.</span></span> <span data-ttu-id="a70a6-126">`SetPriority` Geçerli görev için bu iş parçacığı öncelik düzeyi ayarlamak CLR sağlar.</span><span class="sxs-lookup"><span data-stu-id="a70a6-126">`SetPriority` allows the CLR to set that thread priority level for the current task.</span></span> <span data-ttu-id="a70a6-127">Aşağıdaki `newPriority` değerler desteklenir.</span><span class="sxs-lookup"><span data-stu-id="a70a6-127">The following `newPriority` values are supported.</span></span>  
  
- <span data-ttu-id="a70a6-128">THREAD_PRIORITY_ABOVE_NORMAL</span><span class="sxs-lookup"><span data-stu-id="a70a6-128">THREAD_PRIORITY_ABOVE_NORMAL</span></span>  
  
- <span data-ttu-id="a70a6-129">THREAD_PRIORITY_BELOW_NORMAL</span><span class="sxs-lookup"><span data-stu-id="a70a6-129">THREAD_PRIORITY_BELOW_NORMAL</span></span>  
  
- <span data-ttu-id="a70a6-130">THREAD_PRIORITY_HIGHEST</span><span class="sxs-lookup"><span data-stu-id="a70a6-130">THREAD_PRIORITY_HIGHEST</span></span>  
  
- <span data-ttu-id="a70a6-131">THREAD_PRIORITY_IDLE</span><span class="sxs-lookup"><span data-stu-id="a70a6-131">THREAD_PRIORITY_IDLE</span></span>  
  
- <span data-ttu-id="a70a6-132">THREAD_PRIORITY_LOWEST</span><span class="sxs-lookup"><span data-stu-id="a70a6-132">THREAD_PRIORITY_LOWEST</span></span>  
  
- <span data-ttu-id="a70a6-133">THREAD_PRIORITY_NORMAL</span><span class="sxs-lookup"><span data-stu-id="a70a6-133">THREAD_PRIORITY_NORMAL</span></span>  
  
- <span data-ttu-id="a70a6-134">THREAD_PRIORITY_TIME_CRITICAL</span><span class="sxs-lookup"><span data-stu-id="a70a6-134">THREAD_PRIORITY_TIME_CRITICAL</span></span>  
  
 <span data-ttu-id="a70a6-135">CLR çağrıları `SetPriority` zaman değerini <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> kullanıcı kodu tarafından değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="a70a6-135">The CLR calls `SetPriority` when the value of the <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> is modified by user code.</span></span> <span data-ttu-id="a70a6-136">Bir ana iş parçacığı önceliği ataması için kendi algoritmaları tanımlayabilir ve bu isteği yok saymak ücretsizdir.</span><span class="sxs-lookup"><span data-stu-id="a70a6-136">A host can define its own algorithms for thread priority assignment, and is free to ignore this request.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a70a6-137">`SetPriority` iş parçacığı öncelik düzeyi değiştirilip değiştirilmediğini raporlamaz.</span><span class="sxs-lookup"><span data-stu-id="a70a6-137">`SetPriority` does not report whether the thread priority level was changed.</span></span> <span data-ttu-id="a70a6-138">Çağrı [Ihosttask::getpriority](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md) görevin iş parçacığı öncelik düzeyi değerini belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="a70a6-138">Call [IHostTask::GetPriority](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md) to determine the value of the task's thread priority level.</span></span>  
  
 <span data-ttu-id="a70a6-139">Win32 iş parçacığı öncelik düzeyi değerleri tanımlanmış `SetThreadPriority` işlevi.</span><span class="sxs-lookup"><span data-stu-id="a70a6-139">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span> <span data-ttu-id="a70a6-140">İş parçacığı önceliği hakkında daha fazla bilgi için Windows Platform belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="a70a6-140">For more information about thread priority, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a70a6-141">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a70a6-141">Requirements</span></span>  
 <span data-ttu-id="a70a6-142">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a70a6-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a70a6-143">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a70a6-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a70a6-144">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="a70a6-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a70a6-145">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a70a6-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a70a6-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a70a6-146">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="a70a6-147">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a70a6-147">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="a70a6-148">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a70a6-148">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="a70a6-149">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a70a6-149">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="a70a6-150">GetPriority Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a70a6-150">GetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)
- [<span data-ttu-id="a70a6-151">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a70a6-151">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
