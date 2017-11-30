---
title: "IHostTaskManager::LeaveRuntime Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.LeaveRuntime
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::LeaveRuntime
helpviewer_keywords:
- IHostTaskManager::LeaveRuntime method [.NET Framework hosting]
- LeaveRuntime method [.NET Framework hosting]
ms.assetid: 43689cc4-e48e-46e5-a22d-bafd768b8759
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 326fa3d495cafe187f06e1e6a804cbe90fb12efd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskmanagerleaveruntime-method"></a><span data-ttu-id="b999b-102">IHostTaskManager::LeaveRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b999b-102">IHostTaskManager::LeaveRuntime Method</span></span>
<span data-ttu-id="b999b-103">Konak şu anda yürütülen görev hakkında ortak dil çalışma zamanı (CLR) bırakın ve yönetilmeyen kodu girmeniz olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="b999b-103">Notifies the host that the currently executing task is about to leave the common language runtime (CLR) and enter unmanaged code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b999b-104">Karşılık gelen çağrıyı [Ihosttaskmanager::enterruntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md) ana bilgisayar şu anda yürütülen görev yönetilen kod yeniden girme bildirir.</span><span class="sxs-lookup"><span data-stu-id="b999b-104">A corresponding call to [IHostTaskManager::EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md) notifies the host that the currently executing task is reentering managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b999b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b999b-105">Syntax</span></span>  
  
```  
HRESULT LeaveRuntime (  
    [in] SIZE_T target  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b999b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b999b-106">Parameters</span></span>  
 `target`  
 <span data-ttu-id="b999b-107">[in] Yönetilmeyen işlevinin çağrılmasına eşlenen taşınabilir yürütülebilir dosyası içinde adresi.</span><span class="sxs-lookup"><span data-stu-id="b999b-107">[in] The address within the mapped portable executable file of the unmanaged function to be called.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b999b-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b999b-108">Return Value</span></span>  
  
|<span data-ttu-id="b999b-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b999b-109">HRESULT</span></span>|<span data-ttu-id="b999b-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b999b-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b999b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b999b-111">S_OK</span></span>|<span data-ttu-id="b999b-112">`LeaveRuntime`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="b999b-112">`LeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="b999b-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b999b-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b999b-114">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="b999b-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b999b-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b999b-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b999b-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="b999b-116">The call timed out.</span></span>|  
|<span data-ttu-id="b999b-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b999b-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b999b-118">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="b999b-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b999b-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b999b-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b999b-120">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="b999b-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b999b-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b999b-121">E_FAIL</span></span>|<span data-ttu-id="b999b-122">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="b999b-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b999b-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b999b-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b999b-124">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="b999b-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b999b-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="b999b-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="b999b-126">İstenen ayırma tamamlamak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="b999b-126">Not enough memory is available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b999b-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b999b-127">Remarks</span></span>  
 <span data-ttu-id="b999b-128">Çağrı sıraları için ve yönetilmeyen koddan iç içe.</span><span class="sxs-lookup"><span data-stu-id="b999b-128">Call sequences to and from unmanaged code can be nested.</span></span> <span data-ttu-id="b999b-129">Örneğin, aşağıdaki listede bir kuramsal durumda açıklar çağrıları dizisini `LeaveRuntime`, [Ihosttaskmanager::reverseenterruntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), [Ihosttaskmanager::reverseleaveruntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md), ve `IHostTaskManager::EnterRuntime` iç içe geçmiş katmanları tanımlamak için ana sağlar.</span><span class="sxs-lookup"><span data-stu-id="b999b-129">For example, the list below describes a hypothetical situation in which the sequence of calls to `LeaveRuntime`, [IHostTaskManager::ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), [IHostTaskManager::ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md), and `IHostTaskManager::EnterRuntime` allows the host to identify the nested layers.</span></span>  
  
|<span data-ttu-id="b999b-130">Eylem</span><span class="sxs-lookup"><span data-stu-id="b999b-130">Action</span></span>|<span data-ttu-id="b999b-131">İlgili yöntem çağrısı</span><span class="sxs-lookup"><span data-stu-id="b999b-131">Corresponding Method Call</span></span>|  
|------------|-------------------------------|  
|<span data-ttu-id="b999b-132">Yönetilen bir Visual Basic yürütülebilir çağrılar C'de platform kullanılarak yazılmış bir yönetilmeyen işlevi çağırır.</span><span class="sxs-lookup"><span data-stu-id="b999b-132">A managed Visual Basic executable calls an unmanaged function written in C by using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="b999b-133">Yönetilmeyen C işlev DLL'de C# dilinde yazılan yönetilen bir yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="b999b-133">The unmanaged C function calls a method in a managed DLL written in C#.</span></span>|`IHostTaskManager::ReverseEnterRuntime`|  
|<span data-ttu-id="b999b-134">Ayrıca platformu kullanılarak C'de yazılmış başka bir yönetilmeyen işlev çağırma yönetilen C# işlevi çağırır.</span><span class="sxs-lookup"><span data-stu-id="b999b-134">The managed C# function calls another unmanaged function written in C, also using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="b999b-135">İkinci yönetilmeyen işlevi yürütme için C# işlevi döndürür.</span><span class="sxs-lookup"><span data-stu-id="b999b-135">The second unmanaged function returns execution to the C# function.</span></span>|`IHostTaskManager::EnterRuntime`|  
|<span data-ttu-id="b999b-136">C# işlevi yürütme ilk yönetilmeyen işlevi döndürür.</span><span class="sxs-lookup"><span data-stu-id="b999b-136">The C# function returns execution to the first unmanaged function.</span></span>|`IHostTaskManager::ReverseLeaveRuntime`|  
|<span data-ttu-id="b999b-137">İlk yönetilmeyen işlevi Visual Basic programı yürütme döndürür.</span><span class="sxs-lookup"><span data-stu-id="b999b-137">The first unmanaged function returns execution to the Visual Basic program.</span></span>|`IHostTaskManager::EnterRuntime`|  
  
## <a name="requirements"></a><span data-ttu-id="b999b-138">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b999b-138">Requirements</span></span>  
 <span data-ttu-id="b999b-139">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b999b-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b999b-140">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b999b-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b999b-141">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="b999b-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b999b-142">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b999b-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b999b-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b999b-143">See Also</span></span>  
 [<span data-ttu-id="b999b-144">Iclrtask arabirimi</span><span class="sxs-lookup"><span data-stu-id="b999b-144">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="b999b-145">Iclrtaskmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="b999b-145">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="b999b-146">Ihosttask arabirimi</span><span class="sxs-lookup"><span data-stu-id="b999b-146">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="b999b-147">Ihosttaskmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="b999b-147">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
