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
ms.openlocfilehash: 17fca3e5a2d763277d3a5f9f72e2d35be6fc350c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124637"
---
# <a name="iclrtaskreset-method"></a><span data-ttu-id="a7e1e-102">ICLRTask::Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a7e1e-102">ICLRTask::Reset Method</span></span>
<span data-ttu-id="a7e1e-103">Ana bilgisayarın bir görevi tamamladığı ortak dil çalışma zamanına (CLR) bildirir ve CLR 'nin diğer bir görevi temsil etmesi için geçerli [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) örneğini yeniden kullanmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a7e1e-103">Informs the common language runtime (CLR) that the host has completed a task, and enables the CLR to reuse the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance to represent another task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7e1e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a7e1e-104">Syntax</span></span>  
  
```cpp  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7e1e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a7e1e-105">Parameters</span></span>  
 `fFull`  
 <span data-ttu-id="a7e1e-106">[in] `true`, çalışma zamanı, geçerli `ICLRTask` örneğiyle ilgili güvenlik ve yerel ayar bilgilerine ek olarak iş parçacığında ilgili tüm statik değerleri sıfırlamamalıdır; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="a7e1e-106">[in] `true`, if the runtime should reset all thread-related static values in addition to the security and locale information related to the current `ICLRTask` instance; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="a7e1e-107">Değer `true`ise, çalışma zamanı <xref:System.Threading.Thread.AllocateDataSlot%2A> veya <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>kullanılarak depolanan verileri sıfırlar.</span><span class="sxs-lookup"><span data-stu-id="a7e1e-107">If the value is `true`, the runtime resets data that was stored using <xref:System.Threading.Thread.AllocateDataSlot%2A> or <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a7e1e-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a7e1e-108">Return Value</span></span>  
  
|<span data-ttu-id="a7e1e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a7e1e-109">HRESULT</span></span>|<span data-ttu-id="a7e1e-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7e1e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a7e1e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a7e1e-111">S_OK</span></span>|<span data-ttu-id="a7e1e-112">`Reset` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="a7e1e-112">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="a7e1e-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a7e1e-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a7e1e-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="a7e1e-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="a7e1e-115">yararlanan</span><span class="sxs-lookup"><span data-stu-id="a7e1e-115">successfully</span></span>|  
|<span data-ttu-id="a7e1e-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a7e1e-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a7e1e-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="a7e1e-117">The call timed out.</span></span>|  
|<span data-ttu-id="a7e1e-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a7e1e-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a7e1e-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a7e1e-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a7e1e-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a7e1e-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a7e1e-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="a7e1e-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a7e1e-122">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="a7e1e-122">E_FAIL</span></span>|<span data-ttu-id="a7e1e-123">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a7e1e-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a7e1e-124">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a7e1e-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a7e1e-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="a7e1e-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7e1e-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a7e1e-126">Remarks</span></span>  
 <span data-ttu-id="a7e1e-127">CLR, her yeni örnek oluşturmak için her seferinde yeni örnekler oluşturma ek yükünü ortadan kaldırmak üzere önceden oluşturulmuş `ICLRTask` örneklerini geri dönüştürebilir.</span><span class="sxs-lookup"><span data-stu-id="a7e1e-127">The CLR can recycle previously created `ICLRTask` instances to avoid the overhead of repeatedly creating new instances every time it needs a fresh task.</span></span> <span data-ttu-id="a7e1e-128">Konak bir görevi tamamladığında [ICLRTask:: ExitTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md) yerine `ICLRTask::Reset` çağırarak bu özelliği sunar.</span><span class="sxs-lookup"><span data-stu-id="a7e1e-128">The host enables this feature by calling `ICLRTask::Reset` instead of [ICLRTask::ExitTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md) when it has completed a task.</span></span> <span data-ttu-id="a7e1e-129">Aşağıdaki liste bir `ICLRTask` örneğinin normal yaşam döngüsünü özetler:</span><span class="sxs-lookup"><span data-stu-id="a7e1e-129">The following list summarizes the normal life cycle of an `ICLRTask` instance:</span></span>  
  
1. <span data-ttu-id="a7e1e-130">Çalışma zamanı yeni bir `ICLRTask` örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a7e1e-130">The runtime creates a new `ICLRTask` instance.</span></span>  
  
2. <span data-ttu-id="a7e1e-131">Çalışma zamanı, geçerli ana bilgisayar görevine bir başvuru almak için [IHostTaskManager:: GetCurrentTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md) öğesini çağırır.</span><span class="sxs-lookup"><span data-stu-id="a7e1e-131">The runtime calls [IHostTaskManager::GetCurrentTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md) to get a reference to the current host task.</span></span>  
  
3. <span data-ttu-id="a7e1e-132">Çalışma zamanı, yeni örneği konak göreviyle ilişkilendirmek için [IHostTask:: SetCLRTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md) öğesini çağırır.</span><span class="sxs-lookup"><span data-stu-id="a7e1e-132">The runtime calls [IHostTask::SetCLRTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md) to associate the new instance with the host task.</span></span>  
  
4. <span data-ttu-id="a7e1e-133">Görev yürütülür ve tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="a7e1e-133">The task executes and completes.</span></span>  
  
5. <span data-ttu-id="a7e1e-134">Ana bilgisayar `ICLRTask::ExitTask`çağırarak görevi yok eder.</span><span class="sxs-lookup"><span data-stu-id="a7e1e-134">The host destroys the task by calling `ICLRTask::ExitTask`.</span></span>  
  
 <span data-ttu-id="a7e1e-135">`Reset` bu senaryoyu iki şekilde değiştirir.</span><span class="sxs-lookup"><span data-stu-id="a7e1e-135">`Reset` alters this scenario in two ways.</span></span> <span data-ttu-id="a7e1e-136">Yukarıdaki 5. adımda ana bilgisayar, görevi temiz bir duruma sıfırlamak için `Reset` çağırır ve sonra `ICLRTask` örneğini ilişkili [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) örneğinden ayırır.</span><span class="sxs-lookup"><span data-stu-id="a7e1e-136">In step 5 above, the host calls `Reset` to reset the task to a clean state, and then decouples the `ICLRTask` instance from its associated [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span> <span data-ttu-id="a7e1e-137">İsterseniz, konak `IHostTask` örneği yeniden kullanım için de önbelleğe alabilir.</span><span class="sxs-lookup"><span data-stu-id="a7e1e-137">If desired, the host can also cache the `IHostTask` instance for reuse.</span></span> <span data-ttu-id="a7e1e-138">Yukarıdaki 1. adımda, çalışma zamanı yeni bir örnek oluşturmak yerine önbellekten geri dönüşümlü bir `ICLRTask` çeker.</span><span class="sxs-lookup"><span data-stu-id="a7e1e-138">In step 1 above, the runtime pulls a recycled `ICLRTask` from the cache instead of creating a new instance.</span></span>  
  
 <span data-ttu-id="a7e1e-139">Bu yaklaşım, konakta bir yeniden kullanılabilir çalışan görevleri havuzu da olduğunda iyi sonuç verir.</span><span class="sxs-lookup"><span data-stu-id="a7e1e-139">This approach works well when the host also has a pool of reusable worker tasks.</span></span> <span data-ttu-id="a7e1e-140">Ana bilgisayar `IHostTask` örneklerinden birini yok eder, `ExitTask`çağırarak karşılık gelen `ICLRTask` yok eder.</span><span class="sxs-lookup"><span data-stu-id="a7e1e-140">When the host destroys one of its `IHostTask` instances, it destroys the corresponding `ICLRTask` by calling `ExitTask`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7e1e-141">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a7e1e-141">Requirements</span></span>  
 <span data-ttu-id="a7e1e-142">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7e1e-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7e1e-143">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a7e1e-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a7e1e-144">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="a7e1e-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a7e1e-145">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7e1e-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7e1e-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7e1e-146">See also</span></span>

- [<span data-ttu-id="a7e1e-147">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a7e1e-147">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="a7e1e-148">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a7e1e-148">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="a7e1e-149">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a7e1e-149">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="a7e1e-150">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a7e1e-150">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
