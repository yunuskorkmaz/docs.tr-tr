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
ms.openlocfilehash: c64cee9ec9b62d87e0c4ae1aafaff59bb985ec95
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121349"
---
# <a name="ihosttasksetpriority-method"></a><span data-ttu-id="c7aa0-102">IHostTask::SetPriority Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c7aa0-102">IHostTask::SetPriority Method</span></span>
<span data-ttu-id="c7aa0-103">Konağın geçerli [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) örneği tarafından temsil edilen görev için iş parçacığı öncelik düzeyini ayarlamasını ister.</span><span class="sxs-lookup"><span data-stu-id="c7aa0-103">Requests that the host adjust the thread priority level for the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7aa0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c7aa0-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPriority (  
    [in] int newPriority  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7aa0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c7aa0-105">Parameters</span></span>  
 `newPriority`  
 <span data-ttu-id="c7aa0-106">'ndaki Geçerli `IHostTask` örneği tarafından temsil edilen görevin istenen iş parçacığı önceliği değerini temsil eden bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="c7aa0-106">[in] An integer that represents the requested thread priority value for the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c7aa0-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c7aa0-107">Return Value</span></span>  
  
|<span data-ttu-id="c7aa0-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c7aa0-108">HRESULT</span></span>|<span data-ttu-id="c7aa0-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c7aa0-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c7aa0-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c7aa0-110">S_OK</span></span>|<span data-ttu-id="c7aa0-111">`SetPriority` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="c7aa0-111">`SetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="c7aa0-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c7aa0-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c7aa0-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="c7aa0-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c7aa0-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c7aa0-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c7aa0-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="c7aa0-115">The call timed out.</span></span>|  
|<span data-ttu-id="c7aa0-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c7aa0-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c7aa0-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="c7aa0-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c7aa0-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c7aa0-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c7aa0-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="c7aa0-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c7aa0-120">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="c7aa0-120">E_FAIL</span></span>|<span data-ttu-id="c7aa0-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="c7aa0-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c7aa0-122">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c7aa0-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c7aa0-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="c7aa0-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7aa0-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c7aa0-124">Remarks</span></span>  
 <span data-ttu-id="c7aa0-125">İş parçacıkları, kısmen bir iş parçacığının öncelik düzeyini temel alan hepsini bir kez deneme sistemi kullanılarak işleme zamanına sahip olur.</span><span class="sxs-lookup"><span data-stu-id="c7aa0-125">Threads are granted processing time using a round-robin system that is partly based on a thread's priority level.</span></span> <span data-ttu-id="c7aa0-126">`SetPriority`, CLR 'nin geçerli görevin iş parçacığı öncelik düzeyini ayarlamasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="c7aa0-126">`SetPriority` allows the CLR to set that thread priority level for the current task.</span></span> <span data-ttu-id="c7aa0-127">Aşağıdaki `newPriority` değerleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="c7aa0-127">The following `newPriority` values are supported.</span></span>  
  
- <span data-ttu-id="c7aa0-128">THREAD_PRIORITY_ABOVE_NORMAL</span><span class="sxs-lookup"><span data-stu-id="c7aa0-128">THREAD_PRIORITY_ABOVE_NORMAL</span></span>  
  
- <span data-ttu-id="c7aa0-129">THREAD_PRIORITY_BELOW_NORMAL</span><span class="sxs-lookup"><span data-stu-id="c7aa0-129">THREAD_PRIORITY_BELOW_NORMAL</span></span>  
  
- <span data-ttu-id="c7aa0-130">THREAD_PRIORITY_HIGHEST</span><span class="sxs-lookup"><span data-stu-id="c7aa0-130">THREAD_PRIORITY_HIGHEST</span></span>  
  
- <span data-ttu-id="c7aa0-131">THREAD_PRIORITY_IDLE</span><span class="sxs-lookup"><span data-stu-id="c7aa0-131">THREAD_PRIORITY_IDLE</span></span>  
  
- <span data-ttu-id="c7aa0-132">THREAD_PRIORITY_LOWEST</span><span class="sxs-lookup"><span data-stu-id="c7aa0-132">THREAD_PRIORITY_LOWEST</span></span>  
  
- <span data-ttu-id="c7aa0-133">THREAD_PRIORITY_NORMAL</span><span class="sxs-lookup"><span data-stu-id="c7aa0-133">THREAD_PRIORITY_NORMAL</span></span>  
  
- <span data-ttu-id="c7aa0-134">THREAD_PRIORITY_TIME_CRITICAL</span><span class="sxs-lookup"><span data-stu-id="c7aa0-134">THREAD_PRIORITY_TIME_CRITICAL</span></span>  
  
 <span data-ttu-id="c7aa0-135">CLR, <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> değeri Kullanıcı kodu tarafından değiştirildiğinde `SetPriority` çağırır.</span><span class="sxs-lookup"><span data-stu-id="c7aa0-135">The CLR calls `SetPriority` when the value of the <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> is modified by user code.</span></span> <span data-ttu-id="c7aa0-136">Bir konak, iş parçacığı öncelik ataması için kendi algoritmalarını tanımlayabilir ve bu isteği yok saymaya ücretsizdir.</span><span class="sxs-lookup"><span data-stu-id="c7aa0-136">A host can define its own algorithms for thread priority assignment, and is free to ignore this request.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c7aa0-137">`SetPriority` iş parçacığı öncelik düzeyinin değiştirilip değiştirilmediğini raporlamaz.</span><span class="sxs-lookup"><span data-stu-id="c7aa0-137">`SetPriority` does not report whether the thread priority level was changed.</span></span> <span data-ttu-id="c7aa0-138">Görevin iş parçacığı öncelik düzeyinin değerini öğrenmek için [IHostTask:: GetPriority](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md) öğesini çağırın.</span><span class="sxs-lookup"><span data-stu-id="c7aa0-138">Call [IHostTask::GetPriority](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md) to determine the value of the task's thread priority level.</span></span>  
  
 <span data-ttu-id="c7aa0-139">İş parçacığı öncelik düzeyi değerleri Win32 `SetThreadPriority` işlevi tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="c7aa0-139">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span> <span data-ttu-id="c7aa0-140">İş parçacığı önceliği hakkında daha fazla bilgi için bkz. Windows platformu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="c7aa0-140">For more information about thread priority, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7aa0-141">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c7aa0-141">Requirements</span></span>  
 <span data-ttu-id="c7aa0-142">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7aa0-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7aa0-143">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c7aa0-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c7aa0-144">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="c7aa0-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c7aa0-145">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7aa0-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7aa0-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7aa0-146">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="c7aa0-147">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c7aa0-147">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="c7aa0-148">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c7aa0-148">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="c7aa0-149">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c7aa0-149">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="c7aa0-150">GetPriority Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c7aa0-150">GetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)
- [<span data-ttu-id="c7aa0-151">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c7aa0-151">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
