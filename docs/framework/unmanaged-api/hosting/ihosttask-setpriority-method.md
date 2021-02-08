---
description: 'Şu konuda daha fazla bilgi edinin: IHostTask:: SetPriority Yöntemi'
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
ms.openlocfilehash: c3e8fee954e5cbea2d084141a4b2d22d2fa5e95b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784645"
---
# <a name="ihosttasksetpriority-method"></a><span data-ttu-id="21e9b-103">IHostTask::SetPriority Yöntemi</span><span class="sxs-lookup"><span data-stu-id="21e9b-103">IHostTask::SetPriority Method</span></span>

<span data-ttu-id="21e9b-104">Konağın geçerli [IHostTask](ihosttask-interface.md) örneği tarafından temsil edilen görev için iş parçacığı öncelik düzeyini ayarlamasını ister.</span><span class="sxs-lookup"><span data-stu-id="21e9b-104">Requests that the host adjust the thread priority level for the task represented by the current [IHostTask](ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21e9b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21e9b-105">Syntax</span></span>  
  
```cpp  
HRESULT SetPriority (  
    [in] int newPriority  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21e9b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="21e9b-106">Parameters</span></span>  

 `newPriority`  
 <span data-ttu-id="21e9b-107">'ndaki Geçerli örnek tarafından temsil edilen görevin istenen iş parçacığı önceliği değerini temsil eden bir tamsayı `IHostTask` .</span><span class="sxs-lookup"><span data-stu-id="21e9b-107">[in] An integer that represents the requested thread priority value for the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="21e9b-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="21e9b-108">Return Value</span></span>  
  
|<span data-ttu-id="21e9b-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="21e9b-109">HRESULT</span></span>|<span data-ttu-id="21e9b-110">Description</span><span class="sxs-lookup"><span data-stu-id="21e9b-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="21e9b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="21e9b-111">S_OK</span></span>|<span data-ttu-id="21e9b-112">`SetPriority` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="21e9b-112">`SetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="21e9b-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="21e9b-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="21e9b-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="21e9b-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="21e9b-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="21e9b-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="21e9b-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="21e9b-116">The call timed out.</span></span>|  
|<span data-ttu-id="21e9b-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="21e9b-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="21e9b-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="21e9b-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="21e9b-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="21e9b-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="21e9b-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="21e9b-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="21e9b-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="21e9b-121">E_FAIL</span></span>|<span data-ttu-id="21e9b-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="21e9b-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="21e9b-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="21e9b-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="21e9b-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="21e9b-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21e9b-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21e9b-125">Remarks</span></span>  

 <span data-ttu-id="21e9b-126">İş parçacıkları, kısmen bir iş parçacığının öncelik düzeyini temel alan hepsini bir kez deneme sistemi kullanılarak işleme zamanına sahip olur.</span><span class="sxs-lookup"><span data-stu-id="21e9b-126">Threads are granted processing time using a round-robin system that is partly based on a thread's priority level.</span></span> <span data-ttu-id="21e9b-127">`SetPriority` CLR 'nin geçerli görev için iş parçacığı öncelik düzeyini ayarlamasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="21e9b-127">`SetPriority` allows the CLR to set that thread priority level for the current task.</span></span> <span data-ttu-id="21e9b-128">Aşağıdaki `newPriority` değerler desteklenir.</span><span class="sxs-lookup"><span data-stu-id="21e9b-128">The following `newPriority` values are supported.</span></span>  
  
- <span data-ttu-id="21e9b-129">THREAD_PRIORITY_ABOVE_NORMAL</span><span class="sxs-lookup"><span data-stu-id="21e9b-129">THREAD_PRIORITY_ABOVE_NORMAL</span></span>  
  
- <span data-ttu-id="21e9b-130">THREAD_PRIORITY_BELOW_NORMAL</span><span class="sxs-lookup"><span data-stu-id="21e9b-130">THREAD_PRIORITY_BELOW_NORMAL</span></span>  
  
- <span data-ttu-id="21e9b-131">THREAD_PRIORITY_HIGHEST</span><span class="sxs-lookup"><span data-stu-id="21e9b-131">THREAD_PRIORITY_HIGHEST</span></span>  
  
- <span data-ttu-id="21e9b-132">THREAD_PRIORITY_IDLE</span><span class="sxs-lookup"><span data-stu-id="21e9b-132">THREAD_PRIORITY_IDLE</span></span>  
  
- <span data-ttu-id="21e9b-133">THREAD_PRIORITY_LOWEST</span><span class="sxs-lookup"><span data-stu-id="21e9b-133">THREAD_PRIORITY_LOWEST</span></span>  
  
- <span data-ttu-id="21e9b-134">THREAD_PRIORITY_NORMAL</span><span class="sxs-lookup"><span data-stu-id="21e9b-134">THREAD_PRIORITY_NORMAL</span></span>  
  
- <span data-ttu-id="21e9b-135">THREAD_PRIORITY_TIME_CRITICAL</span><span class="sxs-lookup"><span data-stu-id="21e9b-135">THREAD_PRIORITY_TIME_CRITICAL</span></span>  
  
 <span data-ttu-id="21e9b-136">`SetPriority`Değeri <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> Kullanıcı kodu tarafından değiştirildiğinde clr çağırır.</span><span class="sxs-lookup"><span data-stu-id="21e9b-136">The CLR calls `SetPriority` when the value of the <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> is modified by user code.</span></span> <span data-ttu-id="21e9b-137">Bir konak, iş parçacığı öncelik ataması için kendi algoritmalarını tanımlayabilir ve bu isteği yok saymaya ücretsizdir.</span><span class="sxs-lookup"><span data-stu-id="21e9b-137">A host can define its own algorithms for thread priority assignment, and is free to ignore this request.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="21e9b-138">`SetPriority` iş parçacığı öncelik düzeyinin değiştirilip değiştirilmediğini raporlamaz.</span><span class="sxs-lookup"><span data-stu-id="21e9b-138">`SetPriority` does not report whether the thread priority level was changed.</span></span> <span data-ttu-id="21e9b-139">Görevin iş parçacığı öncelik düzeyinin değerini öğrenmek için [IHostTask:: GetPriority](ihosttask-getpriority-method.md) öğesini çağırın.</span><span class="sxs-lookup"><span data-stu-id="21e9b-139">Call [IHostTask::GetPriority](ihosttask-getpriority-method.md) to determine the value of the task's thread priority level.</span></span>  
  
 <span data-ttu-id="21e9b-140">İş parçacığı öncelik düzeyi değerleri Win32 işlevi tarafından tanımlanır `SetThreadPriority` .</span><span class="sxs-lookup"><span data-stu-id="21e9b-140">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span> <span data-ttu-id="21e9b-141">İş parçacığı önceliği hakkında daha fazla bilgi için bkz. Windows platformu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="21e9b-141">For more information about thread priority, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21e9b-142">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="21e9b-142">Requirements</span></span>  

 <span data-ttu-id="21e9b-143">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21e9b-143">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21e9b-144">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="21e9b-144">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="21e9b-145">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="21e9b-145">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="21e9b-146">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21e9b-146">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21e9b-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21e9b-147">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="21e9b-148">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="21e9b-148">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="21e9b-149">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="21e9b-149">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="21e9b-150">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="21e9b-150">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="21e9b-151">GetPriority Yöntemi</span><span class="sxs-lookup"><span data-stu-id="21e9b-151">GetPriority Method</span></span>](ihosttask-getpriority-method.md)
- [<span data-ttu-id="21e9b-152">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="21e9b-152">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
