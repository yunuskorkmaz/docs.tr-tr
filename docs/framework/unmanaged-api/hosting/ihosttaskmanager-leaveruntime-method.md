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
ms.openlocfilehash: 855f8a5d3582bbad59301a344d8a51198c40a051
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673052"
---
# <a name="ihosttaskmanagerleaveruntime-method"></a><span data-ttu-id="b9c66-102">IHostTaskManager::LeaveRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b9c66-102">IHostTaskManager::LeaveRuntime Method</span></span>

<span data-ttu-id="b9c66-103">Ana bilgisayara şu anda yürütülmekte olan görevin ortak dil çalışma zamanını (CLR) bırakmak üzere olduğunu bildirir ve yönetilmeyen kod girin.</span><span class="sxs-lookup"><span data-stu-id="b9c66-103">Notifies the host that the currently executing task is about to leave the common language runtime (CLR) and enter unmanaged code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b9c66-104">[IHostTaskManager:: EnterRuntime](ihosttaskmanager-enterruntime-method.md) öğesine karşılık gelen bir çağrı, ana bilgisayara şu anda yürütülmekte olan görevin yönetilen kodu yeniden girdiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="b9c66-104">A corresponding call to [IHostTaskManager::EnterRuntime](ihosttaskmanager-enterruntime-method.md) notifies the host that the currently executing task is reentering managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9c66-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b9c66-105">Syntax</span></span>  
  
```cpp  
HRESULT LeaveRuntime (  
    [in] SIZE_T target  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9c66-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b9c66-106">Parameters</span></span>  

 `target`  
 <span data-ttu-id="b9c66-107">'ndaki Çağrılan yönetilmeyen işlevin eşlenmiş taşınabilir yürütülebilir dosyasındaki adres.</span><span class="sxs-lookup"><span data-stu-id="b9c66-107">[in] The address within the mapped portable executable file of the unmanaged function to be called.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b9c66-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b9c66-108">Return Value</span></span>  
  
|<span data-ttu-id="b9c66-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b9c66-109">HRESULT</span></span>|<span data-ttu-id="b9c66-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b9c66-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b9c66-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b9c66-111">S_OK</span></span>|<span data-ttu-id="b9c66-112">`LeaveRuntime` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="b9c66-112">`LeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="b9c66-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b9c66-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b9c66-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="b9c66-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b9c66-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b9c66-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b9c66-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="b9c66-116">The call timed out.</span></span>|  
|<span data-ttu-id="b9c66-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b9c66-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b9c66-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="b9c66-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b9c66-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b9c66-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b9c66-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="b9c66-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b9c66-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b9c66-121">E_FAIL</span></span>|<span data-ttu-id="b9c66-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="b9c66-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b9c66-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b9c66-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b9c66-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="b9c66-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b9c66-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="b9c66-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="b9c66-126">İstenen ayırmayı tamamlamaya yetecek miktarda bellek yok.</span><span class="sxs-lookup"><span data-stu-id="b9c66-126">Not enough memory is available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9c66-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b9c66-127">Remarks</span></span>  

 <span data-ttu-id="b9c66-128">Yönetilmeyen koddan ve öğesinden gelen çağrı dizileri iç içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="b9c66-128">Call sequences to and from unmanaged code can be nested.</span></span> <span data-ttu-id="b9c66-129">Örneğin, aşağıdaki liste `LeaveRuntime` ,, [IHostTaskManager:: Smarenterruntime](ihosttaskmanager-reverseenterruntime-method.md), [IHostTaskManager:: ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md)öğesine çağrı dizisinin, `IHostTaskManager::EnterRuntime` iç içe geçmiş katmanları belirlemesine izin veren bir kuramsal durum tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b9c66-129">For example, the list below describes a hypothetical situation in which the sequence of calls to `LeaveRuntime`, [IHostTaskManager::ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md), [IHostTaskManager::ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md), and `IHostTaskManager::EnterRuntime` allows the host to identify the nested layers.</span></span>  
  
|<span data-ttu-id="b9c66-130">Eylem</span><span class="sxs-lookup"><span data-stu-id="b9c66-130">Action</span></span>|<span data-ttu-id="b9c66-131">Karşılık gelen yöntem çağrısı</span><span class="sxs-lookup"><span data-stu-id="b9c66-131">Corresponding Method Call</span></span>|  
|------------|-------------------------------|  
|<span data-ttu-id="b9c66-132">Yönetilen bir Visual Basic çalıştırılabilir, platform Invoke kullanılarak C dilinde yazılmış yönetilmeyen bir işlevi çağırır.</span><span class="sxs-lookup"><span data-stu-id="b9c66-132">A managed Visual Basic executable calls an unmanaged function written in C by using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="b9c66-133">Yönetilmeyen C işlevi, C# dilinde yazılmış yönetilen DLL içindeki bir yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="b9c66-133">The unmanaged C function calls a method in a managed DLL written in C#.</span></span>|`IHostTaskManager::ReverseEnterRuntime`|  
|<span data-ttu-id="b9c66-134">Yönetilen C# işlevi, platform Invoke kullanılarak C dilinde yazılmış başka bir yönetilmeyen işlevi çağırır.</span><span class="sxs-lookup"><span data-stu-id="b9c66-134">The managed C# function calls another unmanaged function written in C, also using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="b9c66-135">İkinci yönetilmeyen işlev, C# işlevine yürütme döndürür.</span><span class="sxs-lookup"><span data-stu-id="b9c66-135">The second unmanaged function returns execution to the C# function.</span></span>|`IHostTaskManager::EnterRuntime`|  
|<span data-ttu-id="b9c66-136">C# işlevi, yürütmeyi ilk yönetilmeyen işleve döndürür.</span><span class="sxs-lookup"><span data-stu-id="b9c66-136">The C# function returns execution to the first unmanaged function.</span></span>|`IHostTaskManager::ReverseLeaveRuntime`|  
|<span data-ttu-id="b9c66-137">İlk yönetilmeyen işlev Visual Basic programına yürütme döndürür.</span><span class="sxs-lookup"><span data-stu-id="b9c66-137">The first unmanaged function returns execution to the Visual Basic program.</span></span>|`IHostTaskManager::EnterRuntime`|  
  
## <a name="requirements"></a><span data-ttu-id="b9c66-138">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b9c66-138">Requirements</span></span>  

 <span data-ttu-id="b9c66-139">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9c66-139">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9c66-140">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b9c66-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b9c66-141">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="b9c66-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b9c66-142">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9c66-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9c66-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b9c66-143">See also</span></span>

- [<span data-ttu-id="b9c66-144">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b9c66-144">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="b9c66-145">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b9c66-145">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="b9c66-146">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b9c66-146">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="b9c66-147">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b9c66-147">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
