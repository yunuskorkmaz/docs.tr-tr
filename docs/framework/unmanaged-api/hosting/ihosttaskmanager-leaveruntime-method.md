---
description: 'Şu konuda daha fazla bilgi edinin: IHostTaskManager:: LeaveRuntime yöntemi'
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
ms.openlocfilehash: 7b18bdc17b9cfd52b68309a07c6714fd1efa66cb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707453"
---
# <a name="ihosttaskmanagerleaveruntime-method"></a><span data-ttu-id="0f542-103">IHostTaskManager::LeaveRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f542-103">IHostTaskManager::LeaveRuntime Method</span></span>

<span data-ttu-id="0f542-104">Ana bilgisayara şu anda yürütülmekte olan görevin ortak dil çalışma zamanını (CLR) bırakmak üzere olduğunu bildirir ve yönetilmeyen kod girin.</span><span class="sxs-lookup"><span data-stu-id="0f542-104">Notifies the host that the currently executing task is about to leave the common language runtime (CLR) and enter unmanaged code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0f542-105">[IHostTaskManager:: EnterRuntime](ihosttaskmanager-enterruntime-method.md) öğesine karşılık gelen bir çağrı, ana bilgisayara şu anda yürütülmekte olan görevin yönetilen kodu yeniden girdiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="0f542-105">A corresponding call to [IHostTaskManager::EnterRuntime](ihosttaskmanager-enterruntime-method.md) notifies the host that the currently executing task is reentering managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f542-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0f542-106">Syntax</span></span>  
  
```cpp  
HRESULT LeaveRuntime (  
    [in] SIZE_T target  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f542-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0f542-107">Parameters</span></span>  

 `target`  
 <span data-ttu-id="0f542-108">'ndaki Çağrılan yönetilmeyen işlevin eşlenmiş taşınabilir yürütülebilir dosyasındaki adres.</span><span class="sxs-lookup"><span data-stu-id="0f542-108">[in] The address within the mapped portable executable file of the unmanaged function to be called.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f542-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0f542-109">Return Value</span></span>  
  
|<span data-ttu-id="0f542-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0f542-110">HRESULT</span></span>|<span data-ttu-id="0f542-111">Description</span><span class="sxs-lookup"><span data-stu-id="0f542-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0f542-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="0f542-112">S_OK</span></span>|<span data-ttu-id="0f542-113">`LeaveRuntime` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="0f542-113">`LeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="0f542-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0f542-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0f542-115">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="0f542-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0f542-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0f542-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0f542-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="0f542-117">The call timed out.</span></span>|  
|<span data-ttu-id="0f542-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0f542-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0f542-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="0f542-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0f542-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0f542-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0f542-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="0f542-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0f542-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0f542-122">E_FAIL</span></span>|<span data-ttu-id="0f542-123">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="0f542-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0f542-124">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0f542-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0f542-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="0f542-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0f542-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="0f542-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="0f542-127">İstenen ayırmayı tamamlamaya yetecek miktarda bellek yok.</span><span class="sxs-lookup"><span data-stu-id="0f542-127">Not enough memory is available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f542-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0f542-128">Remarks</span></span>  

 <span data-ttu-id="0f542-129">Yönetilmeyen koddan ve öğesinden gelen çağrı dizileri iç içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="0f542-129">Call sequences to and from unmanaged code can be nested.</span></span> <span data-ttu-id="0f542-130">Örneğin, aşağıdaki liste `LeaveRuntime` ,, [IHostTaskManager:: Smarenterruntime](ihosttaskmanager-reverseenterruntime-method.md), [IHostTaskManager:: ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md)öğesine çağrı dizisinin, `IHostTaskManager::EnterRuntime` iç içe geçmiş katmanları belirlemesine izin veren bir kuramsal durum tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0f542-130">For example, the list below describes a hypothetical situation in which the sequence of calls to `LeaveRuntime`, [IHostTaskManager::ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md), [IHostTaskManager::ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md), and `IHostTaskManager::EnterRuntime` allows the host to identify the nested layers.</span></span>  
  
|<span data-ttu-id="0f542-131">Eylem</span><span class="sxs-lookup"><span data-stu-id="0f542-131">Action</span></span>|<span data-ttu-id="0f542-132">Karşılık gelen yöntem çağrısı</span><span class="sxs-lookup"><span data-stu-id="0f542-132">Corresponding Method Call</span></span>|  
|------------|-------------------------------|  
|<span data-ttu-id="0f542-133">Yönetilen bir Visual Basic çalıştırılabilir, platform Invoke kullanılarak C dilinde yazılmış yönetilmeyen bir işlevi çağırır.</span><span class="sxs-lookup"><span data-stu-id="0f542-133">A managed Visual Basic executable calls an unmanaged function written in C by using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="0f542-134">Yönetilmeyen C işlevi, C# dilinde yazılmış yönetilen DLL içindeki bir yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="0f542-134">The unmanaged C function calls a method in a managed DLL written in C#.</span></span>|`IHostTaskManager::ReverseEnterRuntime`|  
|<span data-ttu-id="0f542-135">Yönetilen C# işlevi, platform Invoke kullanılarak C dilinde yazılmış başka bir yönetilmeyen işlevi çağırır.</span><span class="sxs-lookup"><span data-stu-id="0f542-135">The managed C# function calls another unmanaged function written in C, also using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="0f542-136">İkinci yönetilmeyen işlev, C# işlevine yürütme döndürür.</span><span class="sxs-lookup"><span data-stu-id="0f542-136">The second unmanaged function returns execution to the C# function.</span></span>|`IHostTaskManager::EnterRuntime`|  
|<span data-ttu-id="0f542-137">C# işlevi, yürütmeyi ilk yönetilmeyen işleve döndürür.</span><span class="sxs-lookup"><span data-stu-id="0f542-137">The C# function returns execution to the first unmanaged function.</span></span>|`IHostTaskManager::ReverseLeaveRuntime`|  
|<span data-ttu-id="0f542-138">İlk yönetilmeyen işlev Visual Basic programına yürütme döndürür.</span><span class="sxs-lookup"><span data-stu-id="0f542-138">The first unmanaged function returns execution to the Visual Basic program.</span></span>|`IHostTaskManager::EnterRuntime`|  
  
## <a name="requirements"></a><span data-ttu-id="0f542-139">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0f542-139">Requirements</span></span>  

 <span data-ttu-id="0f542-140">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f542-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f542-141">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0f542-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0f542-142">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="0f542-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0f542-143">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f542-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f542-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f542-144">See also</span></span>

- [<span data-ttu-id="0f542-145">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0f542-145">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="0f542-146">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0f542-146">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="0f542-147">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0f542-147">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="0f542-148">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0f542-148">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
