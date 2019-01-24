---
title: IHostTaskManager::LeaveRuntime Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTaskManager.LeaveRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::LeaveRuntime
helpviewer_keywords:
- IHostTaskManager::LeaveRuntime method [.NET Framework hosting]
- LeaveRuntime method [.NET Framework hosting]
ms.assetid: 43689cc4-e48e-46e5-a22d-bafd768b8759
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e22ed258390f7adc9bbf8cd425afe208b2f9b12c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607049"
---
# <a name="ihosttaskmanagerleaveruntime-method"></a><span data-ttu-id="e9cd0-102">IHostTaskManager::LeaveRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e9cd0-102">IHostTaskManager::LeaveRuntime Method</span></span>
<span data-ttu-id="e9cd0-103">Konak şu anda yürütülen görev hakkında ortak dil çalışma zamanı (CLR) bırakın ve yönetilmeyen kodu girmeniz olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="e9cd0-103">Notifies the host that the currently executing task is about to leave the common language runtime (CLR) and enter unmanaged code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e9cd0-104">Karşılık gelen bir çağrı [Ihosttaskmanager::enterruntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md) konak şu anda yürütülmekte olan görevi yönetilen kod yeniden girildi bildirir.</span><span class="sxs-lookup"><span data-stu-id="e9cd0-104">A corresponding call to [IHostTaskManager::EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md) notifies the host that the currently executing task is reentering managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9cd0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e9cd0-105">Syntax</span></span>  
  
```  
HRESULT LeaveRuntime (  
    [in] SIZE_T target  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e9cd0-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e9cd0-106">Parameters</span></span>  
 `target`  
 <span data-ttu-id="e9cd0-107">[in] Çağrılacak yönetilmeyen işlev eşlenen taşınabilir çalıştırılabilir dosyasının içinde adresi.</span><span class="sxs-lookup"><span data-stu-id="e9cd0-107">[in] The address within the mapped portable executable file of the unmanaged function to be called.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e9cd0-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e9cd0-108">Return Value</span></span>  
  
|<span data-ttu-id="e9cd0-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e9cd0-109">HRESULT</span></span>|<span data-ttu-id="e9cd0-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e9cd0-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e9cd0-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e9cd0-111">S_OK</span></span>|<span data-ttu-id="e9cd0-112">`LeaveRuntime` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e9cd0-112">`LeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="e9cd0-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e9cd0-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e9cd0-114">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="e9cd0-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e9cd0-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e9cd0-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e9cd0-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="e9cd0-116">The call timed out.</span></span>|  
|<span data-ttu-id="e9cd0-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e9cd0-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e9cd0-118">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="e9cd0-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e9cd0-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e9cd0-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e9cd0-120">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="e9cd0-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e9cd0-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e9cd0-121">E_FAIL</span></span>|<span data-ttu-id="e9cd0-122">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e9cd0-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e9cd0-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e9cd0-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e9cd0-124">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="e9cd0-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e9cd0-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="e9cd0-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="e9cd0-126">İstenen ayırma tamamlamak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="e9cd0-126">Not enough memory is available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9cd0-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e9cd0-127">Remarks</span></span>  
 <span data-ttu-id="e9cd0-128">Arama dizileri için ve yönetilmeyen koddan yuvalanabilir.</span><span class="sxs-lookup"><span data-stu-id="e9cd0-128">Call sequences to and from unmanaged code can be nested.</span></span> <span data-ttu-id="e9cd0-129">Örneğin, aşağıdaki listede, kuramsal bir durumda açıklar için çağrı `LeaveRuntime`, [Ihosttaskmanager::reverseenterruntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), [Ihosttaskmanager::reverseleaveruntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md), ve `IHostTaskManager::EnterRuntime` ana bilgisayarın iç içe katmanlar belirlemenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="e9cd0-129">For example, the list below describes a hypothetical situation in which the sequence of calls to `LeaveRuntime`, [IHostTaskManager::ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), [IHostTaskManager::ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md), and `IHostTaskManager::EnterRuntime` allows the host to identify the nested layers.</span></span>  
  
|<span data-ttu-id="e9cd0-130">Eylem</span><span class="sxs-lookup"><span data-stu-id="e9cd0-130">Action</span></span>|<span data-ttu-id="e9cd0-131">İlgili yöntem çağrısı</span><span class="sxs-lookup"><span data-stu-id="e9cd0-131">Corresponding Method Call</span></span>|  
|------------|-------------------------------|  
|<span data-ttu-id="e9cd0-132">Yönetilen bir Visual Basic yürütülebilir çağrıları platformu kullanarak C için yazılmış yönetilmeyen bir işlev çağırır.</span><span class="sxs-lookup"><span data-stu-id="e9cd0-132">A managed Visual Basic executable calls an unmanaged function written in C by using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="e9cd0-133">Yönetilmeyen C işlevi yazılan yönetilen bir DLL içindeki bir yöntemi çağıran C#.</span><span class="sxs-lookup"><span data-stu-id="e9cd0-133">The unmanaged C function calls a method in a managed DLL written in C#.</span></span>|`IHostTaskManager::ReverseEnterRuntime`|  
|<span data-ttu-id="e9cd0-134">Yönetilen C# işlevi C için yazılmış olan ve başka bir yönetilmeyen işlev çağrıları, ayrıca platformunu kullanarak çağırın.</span><span class="sxs-lookup"><span data-stu-id="e9cd0-134">The managed C# function calls another unmanaged function written in C, also using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="e9cd0-135">İkinci yönetilmeyen işlev yürütmesi döndürür C# işlevi.</span><span class="sxs-lookup"><span data-stu-id="e9cd0-135">The second unmanaged function returns execution to the C# function.</span></span>|`IHostTaskManager::EnterRuntime`|  
|<span data-ttu-id="e9cd0-136">C# İşlevi yürütme için ilk yönetilmeyen işlev döndürür.</span><span class="sxs-lookup"><span data-stu-id="e9cd0-136">The C# function returns execution to the first unmanaged function.</span></span>|`IHostTaskManager::ReverseLeaveRuntime`|  
|<span data-ttu-id="e9cd0-137">İlk yönetilmeyen işlev yürütme için Visual Basic programını döndürür.</span><span class="sxs-lookup"><span data-stu-id="e9cd0-137">The first unmanaged function returns execution to the Visual Basic program.</span></span>|`IHostTaskManager::EnterRuntime`|  
  
## <a name="requirements"></a><span data-ttu-id="e9cd0-138">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e9cd0-138">Requirements</span></span>  
 <span data-ttu-id="e9cd0-139">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9cd0-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9cd0-140">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e9cd0-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e9cd0-141">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e9cd0-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e9cd0-142">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9cd0-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9cd0-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9cd0-143">See also</span></span>
- [<span data-ttu-id="e9cd0-144">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9cd0-144">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="e9cd0-145">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9cd0-145">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="e9cd0-146">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9cd0-146">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="e9cd0-147">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9cd0-147">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
