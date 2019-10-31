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
ms.openlocfilehash: 8ac1c18d094deca50d461ef9ff0933a4f87176e0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132987"
---
# <a name="ihosttaskmanagerleaveruntime-method"></a><span data-ttu-id="ec683-102">IHostTaskManager::LeaveRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ec683-102">IHostTaskManager::LeaveRuntime Method</span></span>
<span data-ttu-id="ec683-103">Ana bilgisayara şu anda yürütülmekte olan görevin ortak dil çalışma zamanını (CLR) bırakmak üzere olduğunu bildirir ve yönetilmeyen kod girin.</span><span class="sxs-lookup"><span data-stu-id="ec683-103">Notifies the host that the currently executing task is about to leave the common language runtime (CLR) and enter unmanaged code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ec683-104">[IHostTaskManager:: EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md) öğesine karşılık gelen bir çağrı, ana bilgisayara şu anda yürütülmekte olan görevin yönetilen kodu yeniden girdiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="ec683-104">A corresponding call to [IHostTaskManager::EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md) notifies the host that the currently executing task is reentering managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec683-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ec683-105">Syntax</span></span>  
  
```cpp  
HRESULT LeaveRuntime (  
    [in] SIZE_T target  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec683-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ec683-106">Parameters</span></span>  
 `target`  
 <span data-ttu-id="ec683-107">'ndaki Çağrılan yönetilmeyen işlevin eşlenmiş taşınabilir yürütülebilir dosyasındaki adres.</span><span class="sxs-lookup"><span data-stu-id="ec683-107">[in] The address within the mapped portable executable file of the unmanaged function to be called.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ec683-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ec683-108">Return Value</span></span>  
  
|<span data-ttu-id="ec683-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ec683-109">HRESULT</span></span>|<span data-ttu-id="ec683-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ec683-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ec683-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ec683-111">S_OK</span></span>|<span data-ttu-id="ec683-112">`LeaveRuntime` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="ec683-112">`LeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="ec683-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ec683-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ec683-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="ec683-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ec683-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ec683-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ec683-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="ec683-116">The call timed out.</span></span>|  
|<span data-ttu-id="ec683-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ec683-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ec683-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="ec683-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ec683-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ec683-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ec683-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="ec683-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ec683-121">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="ec683-121">E_FAIL</span></span>|<span data-ttu-id="ec683-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="ec683-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ec683-123">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ec683-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ec683-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="ec683-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ec683-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="ec683-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="ec683-126">İstenen ayırmayı tamamlamaya yetecek miktarda bellek yok.</span><span class="sxs-lookup"><span data-stu-id="ec683-126">Not enough memory is available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec683-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ec683-127">Remarks</span></span>  
 <span data-ttu-id="ec683-128">Yönetilmeyen koddan ve öğesinden gelen çağrı dizileri iç içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="ec683-128">Call sequences to and from unmanaged code can be nested.</span></span> <span data-ttu-id="ec683-129">Örneğin, aşağıdaki liste `LeaveRuntime`, [IHostTaskManager:: Smarenterruntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), [IHostTaskManager:: ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)ve `IHostTaskManager::EnterRuntime` için çağrı dizisinin iç içe katmanlar.</span><span class="sxs-lookup"><span data-stu-id="ec683-129">For example, the list below describes a hypothetical situation in which the sequence of calls to `LeaveRuntime`, [IHostTaskManager::ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), [IHostTaskManager::ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md), and `IHostTaskManager::EnterRuntime` allows the host to identify the nested layers.</span></span>  
  
|<span data-ttu-id="ec683-130">Eylem</span><span class="sxs-lookup"><span data-stu-id="ec683-130">Action</span></span>|<span data-ttu-id="ec683-131">Karşılık gelen yöntem çağrısı</span><span class="sxs-lookup"><span data-stu-id="ec683-131">Corresponding Method Call</span></span>|  
|------------|-------------------------------|  
|<span data-ttu-id="ec683-132">Yönetilen bir Visual Basic çalıştırılabilir, platform Invoke kullanılarak C dilinde yazılmış yönetilmeyen bir işlevi çağırır.</span><span class="sxs-lookup"><span data-stu-id="ec683-132">A managed Visual Basic executable calls an unmanaged function written in C by using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="ec683-133">Yönetilmeyen C işlevi, içinde C#YAZıLMıŞ yönetilen DLL içindeki bir yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="ec683-133">The unmanaged C function calls a method in a managed DLL written in C#.</span></span>|`IHostTaskManager::ReverseEnterRuntime`|  
|<span data-ttu-id="ec683-134">Yönetilen C# işlev, platform Invoke kullanılarak C dilinde yazılmış başka bir yönetilmeyen işlevi çağırır.</span><span class="sxs-lookup"><span data-stu-id="ec683-134">The managed C# function calls another unmanaged function written in C, also using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="ec683-135">İkinci yönetilmeyen işlev, C# işlevine yürütme döndürür.</span><span class="sxs-lookup"><span data-stu-id="ec683-135">The second unmanaged function returns execution to the C# function.</span></span>|`IHostTaskManager::EnterRuntime`|  
|<span data-ttu-id="ec683-136">İşlev C# , yürütmeyi ilk yönetilmeyen işleve döndürür.</span><span class="sxs-lookup"><span data-stu-id="ec683-136">The C# function returns execution to the first unmanaged function.</span></span>|`IHostTaskManager::ReverseLeaveRuntime`|  
|<span data-ttu-id="ec683-137">İlk yönetilmeyen işlev Visual Basic programına yürütme döndürür.</span><span class="sxs-lookup"><span data-stu-id="ec683-137">The first unmanaged function returns execution to the Visual Basic program.</span></span>|`IHostTaskManager::EnterRuntime`|  
  
## <a name="requirements"></a><span data-ttu-id="ec683-138">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ec683-138">Requirements</span></span>  
 <span data-ttu-id="ec683-139">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec683-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec683-140">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ec683-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ec683-141">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="ec683-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ec683-142">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec683-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec683-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec683-143">See also</span></span>

- [<span data-ttu-id="ec683-144">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ec683-144">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="ec683-145">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ec683-145">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="ec683-146">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ec683-146">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="ec683-147">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ec683-147">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
