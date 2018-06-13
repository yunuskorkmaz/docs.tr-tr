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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 29267d032f5e38e352592edc50dbded68aaa9f61
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435948"
---
# <a name="iclrtaskreset-method"></a><span data-ttu-id="781d6-102">ICLRTask::Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="781d6-102">ICLRTask::Reset Method</span></span>
<span data-ttu-id="781d6-103">Konak bir görev tamamlandıktan ve CLR geçerli yeniden kullanmanıza olanak sağlayan ortak dil çalışma zamanı (CLR) bildiren [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) örneği başka bir görev temsil eder.</span><span class="sxs-lookup"><span data-stu-id="781d6-103">Informs the common language runtime (CLR) that the host has completed a task, and enables the CLR to reuse the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance to represent another task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="781d6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="781d6-104">Syntax</span></span>  
  
```  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="781d6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="781d6-105">Parameters</span></span>  
 `fFull`  
 <span data-ttu-id="781d6-106">[in] `true`, çalışma zamanı iş parçacığı ile ilgili tüm statik değerler geçerli ilgili güvenlik ve yerel bilgilerine ek olarak sıfırlamalıdır `ICLRTask` örnek; Aksi halde, `false`.</span><span class="sxs-lookup"><span data-stu-id="781d6-106">[in] `true`, if the runtime should reset all thread-related static values in addition to the security and locale information related to the current `ICLRTask` instance; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="781d6-107">Değer ise `true`, çalışma zamanı kullanılarak depolanmış olan verilerin sıfırlar <xref:System.Threading.Thread.AllocateDataSlot%2A> veya <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.</span><span class="sxs-lookup"><span data-stu-id="781d6-107">If the value is `true`, the runtime resets data that was stored using <xref:System.Threading.Thread.AllocateDataSlot%2A> or <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="781d6-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="781d6-108">Return Value</span></span>  
  
|<span data-ttu-id="781d6-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="781d6-109">HRESULT</span></span>|<span data-ttu-id="781d6-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="781d6-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="781d6-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="781d6-111">S_OK</span></span>|<span data-ttu-id="781d6-112">`Reset` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="781d6-112">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="781d6-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="781d6-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="781d6-114">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrısı bir durumda.</span><span class="sxs-lookup"><span data-stu-id="781d6-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="781d6-115">başarıyla</span><span class="sxs-lookup"><span data-stu-id="781d6-115">successfully</span></span>|  
|<span data-ttu-id="781d6-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="781d6-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="781d6-117">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="781d6-117">The call timed out.</span></span>|  
|<span data-ttu-id="781d6-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="781d6-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="781d6-119">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="781d6-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="781d6-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="781d6-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="781d6-121">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="781d6-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="781d6-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="781d6-122">E_FAIL</span></span>|<span data-ttu-id="781d6-123">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="781d6-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="781d6-124">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="781d6-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="781d6-125">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="781d6-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="781d6-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="781d6-126">Remarks</span></span>  
 <span data-ttu-id="781d6-127">CLR daha önce oluşturduğunuz dönüşüm `ICLRTask` , yeni bir görev gerektiği her zaman sürekli yeni örnekleri oluşturma yükünü önlemek için örnekleri.</span><span class="sxs-lookup"><span data-stu-id="781d6-127">The CLR can recycle previously created `ICLRTask` instances to avoid the overhead of repeatedly creating new instances every time it needs a fresh task.</span></span> <span data-ttu-id="781d6-128">Ana bilgisayar çağırarak bu özellik sağlar `ICLRTask::Reset` yerine [Iclrtask::exittask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md) zaman tamamlanmış bir görevi.</span><span class="sxs-lookup"><span data-stu-id="781d6-128">The host enables this feature by calling `ICLRTask::Reset` instead of [ICLRTask::ExitTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md) when it has completed a task.</span></span> <span data-ttu-id="781d6-129">Aşağıdaki listede normal yaşam döngüsünü özetlenmektedir bir `ICLRTask` örneği:</span><span class="sxs-lookup"><span data-stu-id="781d6-129">The following list summarizes the normal life cycle of an `ICLRTask` instance:</span></span>  
  
1.  <span data-ttu-id="781d6-130">Yeni bir çalışma zamanı oluşturur `ICLRTask` örneği.</span><span class="sxs-lookup"><span data-stu-id="781d6-130">The runtime creates a new `ICLRTask` instance.</span></span>  
  
2.  <span data-ttu-id="781d6-131">Çalışma zamanı çağrıları [Ihosttaskmanager::getcurrenttask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md) geçerli ana bilgisayar görev başvuru alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="781d6-131">The runtime calls [IHostTaskManager::GetCurrentTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md) to get a reference to the current host task.</span></span>  
  
3.  <span data-ttu-id="781d6-132">Çalışma zamanı çağrıları [Ihosttask::setclrtask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md) yeni örnek konak görev ile ilişkilendirilecek.</span><span class="sxs-lookup"><span data-stu-id="781d6-132">The runtime calls [IHostTask::SetCLRTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md) to associate the new instance with the host task.</span></span>  
  
4.  <span data-ttu-id="781d6-133">Görevi yürütür ve tamamlar.</span><span class="sxs-lookup"><span data-stu-id="781d6-133">The task executes and completes.</span></span>  
  
5.  <span data-ttu-id="781d6-134">Konak çağırarak görev bozar `ICLRTask::ExitTask`.</span><span class="sxs-lookup"><span data-stu-id="781d6-134">The host destroys the task by calling `ICLRTask::ExitTask`.</span></span>  
  
 <span data-ttu-id="781d6-135">`Reset` Bu senaryo iki yolla değiştirir.</span><span class="sxs-lookup"><span data-stu-id="781d6-135">`Reset` alters this scenario in two ways.</span></span> <span data-ttu-id="781d6-136">Konak çağrıları yukarıdaki 5. adımda `Reset` görev temiz bir duruma sıfırlanır ve sonra ayrıştırır `ICLRTask` , ilişkili örneğinden [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="781d6-136">In step 5 above, the host calls `Reset` to reset the task to a clean state, and then decouples the `ICLRTask` instance from its associated [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span> <span data-ttu-id="781d6-137">İsterseniz, konak de önbelleğe alabilir `IHostTask` örneği yeniden kullanım için.</span><span class="sxs-lookup"><span data-stu-id="781d6-137">If desired, the host can also cache the `IHostTask` instance for reuse.</span></span> <span data-ttu-id="781d6-138">Yukarıdaki 1. adımda, çalışma zamanı bir geri çeker `ICLRTask` yeni bir örneğini oluşturmak yerine önbelleğinden.</span><span class="sxs-lookup"><span data-stu-id="781d6-138">In step 1 above, the runtime pulls a recycled `ICLRTask` from the cache instead of creating a new instance.</span></span>  
  
 <span data-ttu-id="781d6-139">Bu yaklaşım, iyi konak yeniden kullanılabilir çalışan görevleri havuzu de sahip olduğunda çalışır.</span><span class="sxs-lookup"><span data-stu-id="781d6-139">This approach works well when the host also has a pool of reusable worker tasks.</span></span> <span data-ttu-id="781d6-140">Ne zaman konak bozar birini kendi `IHostTask` örnekleri, karşılık gelen bozar `ICLRTask` çağırarak `ExitTask`.</span><span class="sxs-lookup"><span data-stu-id="781d6-140">When the host destroys one of its `IHostTask` instances, it destroys the corresponding `ICLRTask` by calling `ExitTask`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="781d6-141">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="781d6-141">Requirements</span></span>  
 <span data-ttu-id="781d6-142">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="781d6-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="781d6-143">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="781d6-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="781d6-144">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="781d6-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="781d6-145">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="781d6-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="781d6-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="781d6-146">See Also</span></span>  
 [<span data-ttu-id="781d6-147">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="781d6-147">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="781d6-148">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="781d6-148">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="781d6-149">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="781d6-149">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="781d6-150">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="781d6-150">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
