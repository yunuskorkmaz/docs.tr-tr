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
ms.openlocfilehash: 3039855a58e6db6a403ab33c226b4b8b390668f7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758597"
---
# <a name="iclrtaskreset-method"></a><span data-ttu-id="00213-102">ICLRTask::Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="00213-102">ICLRTask::Reset Method</span></span>
<span data-ttu-id="00213-103">Ortak dil çalışma zamanı (CLR), konak bir görev tamamlandıktan ve geçerli yeniden kullanmak CLR sağlar bildirir [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) temsil eden başka bir görev örneği.</span><span class="sxs-lookup"><span data-stu-id="00213-103">Informs the common language runtime (CLR) that the host has completed a task, and enables the CLR to reuse the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance to represent another task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00213-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="00213-104">Syntax</span></span>  
  
```cpp  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00213-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="00213-105">Parameters</span></span>  
 `fFull`  
 <span data-ttu-id="00213-106">[in] `true`, çalışma zamanı iş parçacığı ile ilgili tüm statik değerleri geçerli ilgili güvenlik ve yerel bilgilerine ek olarak sıfırlamalısınız `ICLRTask` örneği; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="00213-106">[in] `true`, if the runtime should reset all thread-related static values in addition to the security and locale information related to the current `ICLRTask` instance; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="00213-107">Değer ise `true`, çalışma zamanı kullanarak depolanan verileri sıfırlar <xref:System.Threading.Thread.AllocateDataSlot%2A> veya <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.</span><span class="sxs-lookup"><span data-stu-id="00213-107">If the value is `true`, the runtime resets data that was stored using <xref:System.Threading.Thread.AllocateDataSlot%2A> or <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="00213-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="00213-108">Return Value</span></span>  
  
|<span data-ttu-id="00213-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="00213-109">HRESULT</span></span>|<span data-ttu-id="00213-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="00213-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="00213-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="00213-111">S_OK</span></span>|<span data-ttu-id="00213-112">`Reset` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="00213-112">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="00213-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="00213-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="00213-114">CLR'yi bir işleme yüklü değil veya CLR içinde bunu yapamazsınız yönetilen kodu çalıştırmak veya çağrısı işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="00213-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="00213-115">başarıyla</span><span class="sxs-lookup"><span data-stu-id="00213-115">successfully</span></span>|  
|<span data-ttu-id="00213-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="00213-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="00213-117">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="00213-117">The call timed out.</span></span>|  
|<span data-ttu-id="00213-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="00213-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="00213-119">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="00213-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="00213-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="00213-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="00213-121">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="00213-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="00213-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="00213-122">E_FAIL</span></span>|<span data-ttu-id="00213-123">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="00213-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="00213-124">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="00213-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="00213-125">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="00213-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00213-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="00213-126">Remarks</span></span>  
 <span data-ttu-id="00213-127">CLR daha önce oluşturduğunuz dönüşüm `ICLRTask` yeni bir görev ihtiyaç duyduğu her zaman sürekli olarak yeni örnekleri oluşturma ek yükü önlemek için örnekleri.</span><span class="sxs-lookup"><span data-stu-id="00213-127">The CLR can recycle previously created `ICLRTask` instances to avoid the overhead of repeatedly creating new instances every time it needs a fresh task.</span></span> <span data-ttu-id="00213-128">Konağı çağırarak bu özelliği etkinleştirir `ICLRTask::Reset` yerine [Iclrtask::exittask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md) ne zaman tamamlandığının bir görev.</span><span class="sxs-lookup"><span data-stu-id="00213-128">The host enables this feature by calling `ICLRTask::Reset` instead of [ICLRTask::ExitTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md) when it has completed a task.</span></span> <span data-ttu-id="00213-129">Aşağıdaki listede normal yaşam döngüsü özetlenmektedir bir `ICLRTask` örneği:</span><span class="sxs-lookup"><span data-stu-id="00213-129">The following list summarizes the normal life cycle of an `ICLRTask` instance:</span></span>  
  
1. <span data-ttu-id="00213-130">Yeni bir çalışma zamanı oluşturur `ICLRTask` örneği.</span><span class="sxs-lookup"><span data-stu-id="00213-130">The runtime creates a new `ICLRTask` instance.</span></span>  
  
2. <span data-ttu-id="00213-131">Çalışma zamanı çağrıları [Ihosttaskmanager::getcurrenttask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md) geçerli konak göreve bir başvuru almak için.</span><span class="sxs-lookup"><span data-stu-id="00213-131">The runtime calls [IHostTaskManager::GetCurrentTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md) to get a reference to the current host task.</span></span>  
  
3. <span data-ttu-id="00213-132">Çalışma zamanı çağrıları [Ihosttask::setclrtask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md) yeni örnek konak göreviyle ilişkilendirilecek.</span><span class="sxs-lookup"><span data-stu-id="00213-132">The runtime calls [IHostTask::SetCLRTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md) to associate the new instance with the host task.</span></span>  
  
4. <span data-ttu-id="00213-133">Görev yürütür ve tamamlar.</span><span class="sxs-lookup"><span data-stu-id="00213-133">The task executes and completes.</span></span>  
  
5. <span data-ttu-id="00213-134">Çağırarak görev ana bilgisayarı yok eder `ICLRTask::ExitTask`.</span><span class="sxs-lookup"><span data-stu-id="00213-134">The host destroys the task by calling `ICLRTask::ExitTask`.</span></span>  
  
 <span data-ttu-id="00213-135">`Reset` Bu senaryo iki yolla değiştirir.</span><span class="sxs-lookup"><span data-stu-id="00213-135">`Reset` alters this scenario in two ways.</span></span> <span data-ttu-id="00213-136">Konak çağrıları yukarıdaki 5. adımda `Reset` görev temiz bir duruma sıfırlanır ve sonra ayırır `ICLRTask` ilişkili örneğinden [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="00213-136">In step 5 above, the host calls `Reset` to reset the task to a clean state, and then decouples the `ICLRTask` instance from its associated [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span> <span data-ttu-id="00213-137">İsterseniz, konak de önbelleğe alabilir `IHostTask` yeniden kullanım için örneği.</span><span class="sxs-lookup"><span data-stu-id="00213-137">If desired, the host can also cache the `IHostTask` instance for reuse.</span></span> <span data-ttu-id="00213-138">Yukarıdaki 1. adımda, çalışma zamanı bir geri çeker `ICLRTask` yeni bir örneğini oluşturmak yerine önbellekteki.</span><span class="sxs-lookup"><span data-stu-id="00213-138">In step 1 above, the runtime pulls a recycled `ICLRTask` from the cache instead of creating a new instance.</span></span>  
  
 <span data-ttu-id="00213-139">Bu yaklaşım da ana bilgisayar görevleri yeniden kullanılabilir çalışan havuzu da sahip olduğunda çalışır.</span><span class="sxs-lookup"><span data-stu-id="00213-139">This approach works well when the host also has a pool of reusable worker tasks.</span></span> <span data-ttu-id="00213-140">Ne zaman konak yok eder birini kendi `IHostTask` örnekleri, karşılık gelen yok eder `ICLRTask` çağırarak `ExitTask`.</span><span class="sxs-lookup"><span data-stu-id="00213-140">When the host destroys one of its `IHostTask` instances, it destroys the corresponding `ICLRTask` by calling `ExitTask`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00213-141">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="00213-141">Requirements</span></span>  
 <span data-ttu-id="00213-142">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00213-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00213-143">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="00213-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="00213-144">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="00213-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="00213-145">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00213-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00213-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00213-146">See also</span></span>

- [<span data-ttu-id="00213-147">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00213-147">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="00213-148">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00213-148">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="00213-149">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00213-149">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="00213-150">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00213-150">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
