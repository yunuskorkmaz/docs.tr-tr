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
ms.openlocfilehash: 80b4bb2f6a547250acbc16a89e7396c60cc50d87
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720457"
---
# <a name="ihosttasksetpriority-method"></a><span data-ttu-id="fa054-102">IHostTask::SetPriority Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fa054-102">IHostTask::SetPriority Method</span></span>

<span data-ttu-id="fa054-103">Konağın geçerli [IHostTask](ihosttask-interface.md) örneği tarafından temsil edilen görev için iş parçacığı öncelik düzeyini ayarlamasını ister.</span><span class="sxs-lookup"><span data-stu-id="fa054-103">Requests that the host adjust the thread priority level for the task represented by the current [IHostTask](ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa054-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="fa054-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPriority (  
    [in] int newPriority  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa054-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fa054-105">Parameters</span></span>  

 `newPriority`  
 <span data-ttu-id="fa054-106">'ndaki Geçerli örnek tarafından temsil edilen görevin istenen iş parçacığı önceliği değerini temsil eden bir tamsayı `IHostTask` .</span><span class="sxs-lookup"><span data-stu-id="fa054-106">[in] An integer that represents the requested thread priority value for the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fa054-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fa054-107">Return Value</span></span>  
  
|<span data-ttu-id="fa054-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fa054-108">HRESULT</span></span>|<span data-ttu-id="fa054-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa054-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fa054-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="fa054-110">S_OK</span></span>|<span data-ttu-id="fa054-111">`SetPriority` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="fa054-111">`SetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="fa054-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fa054-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fa054-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="fa054-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fa054-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fa054-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fa054-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="fa054-115">The call timed out.</span></span>|  
|<span data-ttu-id="fa054-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fa054-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fa054-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="fa054-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fa054-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fa054-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fa054-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="fa054-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fa054-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fa054-120">E_FAIL</span></span>|<span data-ttu-id="fa054-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="fa054-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fa054-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="fa054-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fa054-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="fa054-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa054-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fa054-124">Remarks</span></span>  

 <span data-ttu-id="fa054-125">İş parçacıkları, kısmen bir iş parçacığının öncelik düzeyini temel alan hepsini bir kez deneme sistemi kullanılarak işleme zamanına sahip olur.</span><span class="sxs-lookup"><span data-stu-id="fa054-125">Threads are granted processing time using a round-robin system that is partly based on a thread's priority level.</span></span> <span data-ttu-id="fa054-126">`SetPriority` CLR 'nin geçerli görev için iş parçacığı öncelik düzeyini ayarlamasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="fa054-126">`SetPriority` allows the CLR to set that thread priority level for the current task.</span></span> <span data-ttu-id="fa054-127">Aşağıdaki `newPriority` değerler desteklenir.</span><span class="sxs-lookup"><span data-stu-id="fa054-127">The following `newPriority` values are supported.</span></span>  
  
- <span data-ttu-id="fa054-128">THREAD_PRIORITY_ABOVE_NORMAL</span><span class="sxs-lookup"><span data-stu-id="fa054-128">THREAD_PRIORITY_ABOVE_NORMAL</span></span>  
  
- <span data-ttu-id="fa054-129">THREAD_PRIORITY_BELOW_NORMAL</span><span class="sxs-lookup"><span data-stu-id="fa054-129">THREAD_PRIORITY_BELOW_NORMAL</span></span>  
  
- <span data-ttu-id="fa054-130">THREAD_PRIORITY_HIGHEST</span><span class="sxs-lookup"><span data-stu-id="fa054-130">THREAD_PRIORITY_HIGHEST</span></span>  
  
- <span data-ttu-id="fa054-131">THREAD_PRIORITY_IDLE</span><span class="sxs-lookup"><span data-stu-id="fa054-131">THREAD_PRIORITY_IDLE</span></span>  
  
- <span data-ttu-id="fa054-132">THREAD_PRIORITY_LOWEST</span><span class="sxs-lookup"><span data-stu-id="fa054-132">THREAD_PRIORITY_LOWEST</span></span>  
  
- <span data-ttu-id="fa054-133">THREAD_PRIORITY_NORMAL</span><span class="sxs-lookup"><span data-stu-id="fa054-133">THREAD_PRIORITY_NORMAL</span></span>  
  
- <span data-ttu-id="fa054-134">THREAD_PRIORITY_TIME_CRITICAL</span><span class="sxs-lookup"><span data-stu-id="fa054-134">THREAD_PRIORITY_TIME_CRITICAL</span></span>  
  
 <span data-ttu-id="fa054-135">`SetPriority`Değeri <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> Kullanıcı kodu tarafından değiştirildiğinde clr çağırır.</span><span class="sxs-lookup"><span data-stu-id="fa054-135">The CLR calls `SetPriority` when the value of the <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> is modified by user code.</span></span> <span data-ttu-id="fa054-136">Bir konak, iş parçacığı öncelik ataması için kendi algoritmalarını tanımlayabilir ve bu isteği yok saymaya ücretsizdir.</span><span class="sxs-lookup"><span data-stu-id="fa054-136">A host can define its own algorithms for thread priority assignment, and is free to ignore this request.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fa054-137">`SetPriority` iş parçacığı öncelik düzeyinin değiştirilip değiştirilmediğini raporlamaz.</span><span class="sxs-lookup"><span data-stu-id="fa054-137">`SetPriority` does not report whether the thread priority level was changed.</span></span> <span data-ttu-id="fa054-138">Görevin iş parçacığı öncelik düzeyinin değerini öğrenmek için [IHostTask:: GetPriority](ihosttask-getpriority-method.md) öğesini çağırın.</span><span class="sxs-lookup"><span data-stu-id="fa054-138">Call [IHostTask::GetPriority](ihosttask-getpriority-method.md) to determine the value of the task's thread priority level.</span></span>  
  
 <span data-ttu-id="fa054-139">İş parçacığı öncelik düzeyi değerleri Win32 işlevi tarafından tanımlanır `SetThreadPriority` .</span><span class="sxs-lookup"><span data-stu-id="fa054-139">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span> <span data-ttu-id="fa054-140">İş parçacığı önceliği hakkında daha fazla bilgi için bkz. Windows platformu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="fa054-140">For more information about thread priority, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa054-141">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fa054-141">Requirements</span></span>  

 <span data-ttu-id="fa054-142">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa054-142">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa054-143">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fa054-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fa054-144">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="fa054-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fa054-145">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa054-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa054-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa054-146">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="fa054-147">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fa054-147">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="fa054-148">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fa054-148">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="fa054-149">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fa054-149">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="fa054-150">GetPriority Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fa054-150">GetPriority Method</span></span>](ihosttask-getpriority-method.md)
- [<span data-ttu-id="fa054-151">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fa054-151">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
