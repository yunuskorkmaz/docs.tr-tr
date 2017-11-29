---
title: "IHostTask::SetPriority Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTask.SetPriority
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTask::SetPriority
helpviewer_keywords:
- IHostTask::SetPriority method [.NET Framework hosting]
- SetPriority method [.NET Framework hosting]
ms.assetid: cd8c379b-c7a0-434f-8e23-899bd26be75d
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 34dabcb35f46d4a2b0536e00fa1fd69637b14cb2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttasksetpriority-method"></a><span data-ttu-id="c5a8d-102">IHostTask::SetPriority Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c5a8d-102">IHostTask::SetPriority Method</span></span>
<span data-ttu-id="c5a8d-103">Düzey istekler ana iş parçacığı önceliği ayarlamak için geçerli tarafından temsil edilen görev [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="c5a8d-103">Requests that the host adjust the thread priority level for the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5a8d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c5a8d-104">Syntax</span></span>  
  
```  
HRESULT SetPriority (  
    [in] int newPriority  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c5a8d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c5a8d-105">Parameters</span></span>  
 `newPriority`  
 <span data-ttu-id="c5a8d-106">[in] Geçerli tarafından temsil edilen görev için istenen iş parçacığı öncelik değeri temsil eden bir tamsayı `IHostTask` örneği.</span><span class="sxs-lookup"><span data-stu-id="c5a8d-106">[in] An integer that represents the requested thread priority value for the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c5a8d-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c5a8d-107">Return Value</span></span>  
  
|<span data-ttu-id="c5a8d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c5a8d-108">HRESULT</span></span>|<span data-ttu-id="c5a8d-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c5a8d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c5a8d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c5a8d-110">S_OK</span></span>|<span data-ttu-id="c5a8d-111">`SetPriority`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="c5a8d-111">`SetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="c5a8d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c5a8d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c5a8d-113">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="c5a8d-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c5a8d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c5a8d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c5a8d-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="c5a8d-115">The call timed out.</span></span>|  
|<span data-ttu-id="c5a8d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c5a8d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c5a8d-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="c5a8d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c5a8d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c5a8d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c5a8d-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="c5a8d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c5a8d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c5a8d-120">E_FAIL</span></span>|<span data-ttu-id="c5a8d-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="c5a8d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c5a8d-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c5a8d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c5a8d-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="c5a8d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5a8d-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c5a8d-124">Remarks</span></span>  
 <span data-ttu-id="c5a8d-125">İş parçacığı verilen bir iş parçacığının öncelik düzeyine kısmen dayalı bir hepsini sistemiyle zaman işliyor.</span><span class="sxs-lookup"><span data-stu-id="c5a8d-125">Threads are granted processing time using a round-robin system that is partly based on a thread's priority level.</span></span> <span data-ttu-id="c5a8d-126">`SetPriority`Geçerli görev o iş parçacığı öncelik düzeyini ayarlamak CLR sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5a8d-126">`SetPriority` allows the CLR to set that thread priority level for the current task.</span></span> <span data-ttu-id="c5a8d-127">Aşağıdaki `newPriority` değerler desteklenir.</span><span class="sxs-lookup"><span data-stu-id="c5a8d-127">The following `newPriority` values are supported.</span></span>  
  
-   <span data-ttu-id="c5a8d-128">THREAD_PRIORITY_ABOVE_NORMAL</span><span class="sxs-lookup"><span data-stu-id="c5a8d-128">THREAD_PRIORITY_ABOVE_NORMAL</span></span>  
  
-   <span data-ttu-id="c5a8d-129">THREAD_PRIORITY_BELOW_NORMAL</span><span class="sxs-lookup"><span data-stu-id="c5a8d-129">THREAD_PRIORITY_BELOW_NORMAL</span></span>  
  
-   <span data-ttu-id="c5a8d-130">THREAD_PRIORITY_HIGHEST</span><span class="sxs-lookup"><span data-stu-id="c5a8d-130">THREAD_PRIORITY_HIGHEST</span></span>  
  
-   <span data-ttu-id="c5a8d-131">THREAD_PRIORITY_IDLE</span><span class="sxs-lookup"><span data-stu-id="c5a8d-131">THREAD_PRIORITY_IDLE</span></span>  
  
-   <span data-ttu-id="c5a8d-132">THREAD_PRIORITY_LOWEST</span><span class="sxs-lookup"><span data-stu-id="c5a8d-132">THREAD_PRIORITY_LOWEST</span></span>  
  
-   <span data-ttu-id="c5a8d-133">THREAD_PRIORITY_NORMAL</span><span class="sxs-lookup"><span data-stu-id="c5a8d-133">THREAD_PRIORITY_NORMAL</span></span>  
  
-   <span data-ttu-id="c5a8d-134">THREAD_PRIORITY_TIME_CRITICAL</span><span class="sxs-lookup"><span data-stu-id="c5a8d-134">THREAD_PRIORITY_TIME_CRITICAL</span></span>  
  
 <span data-ttu-id="c5a8d-135">CLR çağrıları `SetPriority` zaman değerini <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> kullanıcı kodu tarafından değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="c5a8d-135">The CLR calls `SetPriority` when the value of the <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> is modified by user code.</span></span> <span data-ttu-id="c5a8d-136">Bir ana iş parçacığı önceliği atama için kendi algoritmaları tanımlayabilir ve bu isteği yok saymak ücretsizdir.</span><span class="sxs-lookup"><span data-stu-id="c5a8d-136">A host can define its own algorithms for thread priority assignment, and is free to ignore this request.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c5a8d-137">`SetPriority`iş parçacığı öncelik düzeyi değiştirilip değiştirilmediğini bildirmiyor.</span><span class="sxs-lookup"><span data-stu-id="c5a8d-137">`SetPriority` does not report whether the thread priority level was changed.</span></span> <span data-ttu-id="c5a8d-138">Çağrı [Ihosttask::getpriority](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md) görev iş parçacığı öncelik düzeyi değeri belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="c5a8d-138">Call [IHostTask::GetPriority](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md) to determine the value of the task's thread priority level.</span></span>  
  
 <span data-ttu-id="c5a8d-139">İş parçacığı öncelik düzeyi değerleri Win32 tarafından tanımlanan `SetThreadPriority` işlevi.</span><span class="sxs-lookup"><span data-stu-id="c5a8d-139">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span> <span data-ttu-id="c5a8d-140">İş parçacığı önceliği hakkında daha fazla bilgi için Windows platformu belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="c5a8d-140">For more information about thread priority, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5a8d-141">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c5a8d-141">Requirements</span></span>  
 <span data-ttu-id="c5a8d-142">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5a8d-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5a8d-143">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c5a8d-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c5a8d-144">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="c5a8d-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c5a8d-145">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5a8d-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5a8d-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c5a8d-146">See Also</span></span>  
 <xref:System.Threading.Thread>  
 [<span data-ttu-id="c5a8d-147">Iclrtask arabirimi</span><span class="sxs-lookup"><span data-stu-id="c5a8d-147">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="c5a8d-148">Iclrtaskmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="c5a8d-148">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="c5a8d-149">Ihosttask arabirimi</span><span class="sxs-lookup"><span data-stu-id="c5a8d-149">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="c5a8d-150">GetPriority yöntemi</span><span class="sxs-lookup"><span data-stu-id="c5a8d-150">GetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)  
 [<span data-ttu-id="c5a8d-151">Ihosttaskmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="c5a8d-151">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
