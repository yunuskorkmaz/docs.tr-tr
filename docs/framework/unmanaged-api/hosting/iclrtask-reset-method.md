---
title: ICLRTask::Reset Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRTask.Reset
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::Reset
helpviewer_keywords:
- ICLRTask::Reset method [.NET Framework hosting]
- Reset method, ICLRTask interface [.NET Framework hosting]
ms.assetid: 1bfb5d3a-0ffd-4bb4-9bf6-aec00cb675b7
topic_type:
- apiref
ms.openlocfilehash: b87bc026a2cac2d0b913128c43142d56aee03025
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725202"
---
# <a name="iclrtaskreset-method"></a><span data-ttu-id="05128-102">ICLRTask::Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="05128-102">ICLRTask::Reset Method</span></span>

<span data-ttu-id="05128-103">Ana bilgisayarın bir görevi tamamladığı ortak dil çalışma zamanına (CLR) bildirir ve CLR 'nin diğer bir görevi temsil etmesi için geçerli [ICLRTask](iclrtask-interface.md) örneğini yeniden kullanmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="05128-103">Informs the common language runtime (CLR) that the host has completed a task, and enables the CLR to reuse the current [ICLRTask](iclrtask-interface.md) instance to represent another task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05128-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="05128-104">Syntax</span></span>  
  
```cpp  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05128-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="05128-105">Parameters</span></span>  

 `fFull`  
 <span data-ttu-id="05128-106">[in] `true` , çalışma zamanı, geçerli örnekle ilgili güvenlik ve yerel ayar bilgilerine ek olarak iş parçacığı ile ilgili tüm statik değerleri sıfırlamalıdır `ICLRTask` ; Aksi durumda, `false` .</span><span class="sxs-lookup"><span data-stu-id="05128-106">[in] `true`, if the runtime should reset all thread-related static values in addition to the security and locale information related to the current `ICLRTask` instance; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="05128-107">Değer ise `true` , çalışma zamanı veya kullanılarak depolanan verileri sıfırlar <xref:System.Threading.Thread.AllocateDataSlot%2A> <xref:System.Threading.Thread.AllocateNamedDataSlot%2A> .</span><span class="sxs-lookup"><span data-stu-id="05128-107">If the value is `true`, the runtime resets data that was stored using <xref:System.Threading.Thread.AllocateDataSlot%2A> or <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="05128-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="05128-108">Return Value</span></span>  
  
|<span data-ttu-id="05128-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="05128-109">HRESULT</span></span>|<span data-ttu-id="05128-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="05128-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="05128-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="05128-111">S_OK</span></span>|<span data-ttu-id="05128-112">`Reset` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="05128-112">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="05128-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="05128-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="05128-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="05128-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="05128-115">yararlanan</span><span class="sxs-lookup"><span data-stu-id="05128-115">successfully</span></span>|  
|<span data-ttu-id="05128-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="05128-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="05128-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="05128-117">The call timed out.</span></span>|  
|<span data-ttu-id="05128-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="05128-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="05128-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="05128-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="05128-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="05128-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="05128-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="05128-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="05128-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="05128-122">E_FAIL</span></span>|<span data-ttu-id="05128-123">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="05128-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="05128-124">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="05128-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="05128-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="05128-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05128-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="05128-126">Remarks</span></span>  

 <span data-ttu-id="05128-127">CLR, `ICLRTask` her yeni örnek oluşturmak için her seferinde yeni örnekler oluşturma ek yükünü ortadan kaldırmak üzere önceden oluşturulmuş örnekleri geri dönüştürebilir.</span><span class="sxs-lookup"><span data-stu-id="05128-127">The CLR can recycle previously created `ICLRTask` instances to avoid the overhead of repeatedly creating new instances every time it needs a fresh task.</span></span> <span data-ttu-id="05128-128">Ana bilgisayar `ICLRTask::Reset` bir görevi tamamladığında [ICLRTask:: ExitTask](iclrtask-exittask-method.md) yerine çağırarak bu özelliği sunar.</span><span class="sxs-lookup"><span data-stu-id="05128-128">The host enables this feature by calling `ICLRTask::Reset` instead of [ICLRTask::ExitTask](iclrtask-exittask-method.md) when it has completed a task.</span></span> <span data-ttu-id="05128-129">Aşağıdaki liste, bir örneğin normal yaşam döngüsünü özetler `ICLRTask` :</span><span class="sxs-lookup"><span data-stu-id="05128-129">The following list summarizes the normal life cycle of an `ICLRTask` instance:</span></span>  
  
1. <span data-ttu-id="05128-130">Çalışma zamanı yeni bir `ICLRTask` örnek oluşturur.</span><span class="sxs-lookup"><span data-stu-id="05128-130">The runtime creates a new `ICLRTask` instance.</span></span>  
  
2. <span data-ttu-id="05128-131">Çalışma zamanı, geçerli ana bilgisayar görevine bir başvuru almak için [IHostTaskManager:: GetCurrentTask](ihosttaskmanager-getcurrenttask-method.md) öğesini çağırır.</span><span class="sxs-lookup"><span data-stu-id="05128-131">The runtime calls [IHostTaskManager::GetCurrentTask](ihosttaskmanager-getcurrenttask-method.md) to get a reference to the current host task.</span></span>  
  
3. <span data-ttu-id="05128-132">Çalışma zamanı, yeni örneği konak göreviyle ilişkilendirmek için [IHostTask:: SetCLRTask](ihosttask-setclrtask-method.md) öğesini çağırır.</span><span class="sxs-lookup"><span data-stu-id="05128-132">The runtime calls [IHostTask::SetCLRTask](ihosttask-setclrtask-method.md) to associate the new instance with the host task.</span></span>  
  
4. <span data-ttu-id="05128-133">Görev yürütülür ve tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="05128-133">The task executes and completes.</span></span>  
  
5. <span data-ttu-id="05128-134">Konak, çağırarak görevi yok eder `ICLRTask::ExitTask` .</span><span class="sxs-lookup"><span data-stu-id="05128-134">The host destroys the task by calling `ICLRTask::ExitTask`.</span></span>  
  
 <span data-ttu-id="05128-135">`Reset` Bu senaryoyu iki şekilde değiştirir.</span><span class="sxs-lookup"><span data-stu-id="05128-135">`Reset` alters this scenario in two ways.</span></span> <span data-ttu-id="05128-136">Yukarıdaki 5. adımda ana bilgisayar, `Reset` görevi temiz bir duruma sıfırlama yöntemini çağırır ve sonra `ICLRTask` örneği Ilişkili [IHostTask](ihosttask-interface.md) örneğinden ayırır.</span><span class="sxs-lookup"><span data-stu-id="05128-136">In step 5 above, the host calls `Reset` to reset the task to a clean state, and then decouples the `ICLRTask` instance from its associated [IHostTask](ihosttask-interface.md) instance.</span></span> <span data-ttu-id="05128-137">İsterseniz, ana bilgisayar `IHostTask` örneği yeniden kullanım için de önbelleğe alabilir.</span><span class="sxs-lookup"><span data-stu-id="05128-137">If desired, the host can also cache the `IHostTask` instance for reuse.</span></span> <span data-ttu-id="05128-138">Yukarıdaki 1. adımda, çalışma zamanı `ICLRTask` Yeni bir örnek oluşturmak yerine önbellekten geri dönüştürüldü.</span><span class="sxs-lookup"><span data-stu-id="05128-138">In step 1 above, the runtime pulls a recycled `ICLRTask` from the cache instead of creating a new instance.</span></span>  
  
 <span data-ttu-id="05128-139">Bu yaklaşım, konakta bir yeniden kullanılabilir çalışan görevleri havuzu da olduğunda iyi sonuç verir.</span><span class="sxs-lookup"><span data-stu-id="05128-139">This approach works well when the host also has a pool of reusable worker tasks.</span></span> <span data-ttu-id="05128-140">Ana bilgisayar örneklerinden birini yok eder `IHostTask` , çağırarak karşılık gelen öğesini yok eder `ICLRTask` `ExitTask` .</span><span class="sxs-lookup"><span data-stu-id="05128-140">When the host destroys one of its `IHostTask` instances, it destroys the corresponding `ICLRTask` by calling `ExitTask`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05128-141">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="05128-141">Requirements</span></span>  

 <span data-ttu-id="05128-142">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05128-142">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05128-143">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="05128-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="05128-144">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="05128-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="05128-145">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05128-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05128-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05128-146">See also</span></span>

- [<span data-ttu-id="05128-147">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="05128-147">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="05128-148">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="05128-148">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="05128-149">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="05128-149">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="05128-150">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="05128-150">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
