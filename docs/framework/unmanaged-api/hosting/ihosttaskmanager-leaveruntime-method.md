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
ms.openlocfilehash: deaebbce3b9b8a26bf9668b826a6818dba94dcc3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501388"
---
# <a name="ihosttaskmanagerleaveruntime-method"></a><span data-ttu-id="ac4a3-102">IHostTaskManager::LeaveRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ac4a3-102">IHostTaskManager::LeaveRuntime Method</span></span>
<span data-ttu-id="ac4a3-103">Ana bilgisayara şu anda yürütülmekte olan görevin ortak dil çalışma zamanını (CLR) bırakmak üzere olduğunu bildirir ve yönetilmeyen kod girin.</span><span class="sxs-lookup"><span data-stu-id="ac4a3-103">Notifies the host that the currently executing task is about to leave the common language runtime (CLR) and enter unmanaged code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ac4a3-104">[IHostTaskManager:: EnterRuntime](ihosttaskmanager-enterruntime-method.md) öğesine karşılık gelen bir çağrı, ana bilgisayara şu anda yürütülmekte olan görevin yönetilen kodu yeniden girdiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="ac4a3-104">A corresponding call to [IHostTaskManager::EnterRuntime](ihosttaskmanager-enterruntime-method.md) notifies the host that the currently executing task is reentering managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac4a3-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ac4a3-105">Syntax</span></span>  
  
```cpp  
HRESULT LeaveRuntime (  
    [in] SIZE_T target  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac4a3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ac4a3-106">Parameters</span></span>  
 `target`  
 <span data-ttu-id="ac4a3-107">'ndaki Çağrılan yönetilmeyen işlevin eşlenmiş taşınabilir yürütülebilir dosyasındaki adres.</span><span class="sxs-lookup"><span data-stu-id="ac4a3-107">[in] The address within the mapped portable executable file of the unmanaged function to be called.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ac4a3-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ac4a3-108">Return Value</span></span>  
  
|<span data-ttu-id="ac4a3-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ac4a3-109">HRESULT</span></span>|<span data-ttu-id="ac4a3-110">Description</span><span class="sxs-lookup"><span data-stu-id="ac4a3-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ac4a3-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ac4a3-111">S_OK</span></span>|<span data-ttu-id="ac4a3-112">`LeaveRuntime`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="ac4a3-112">`LeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="ac4a3-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ac4a3-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ac4a3-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="ac4a3-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ac4a3-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ac4a3-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ac4a3-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="ac4a3-116">The call timed out.</span></span>|  
|<span data-ttu-id="ac4a3-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ac4a3-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ac4a3-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="ac4a3-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ac4a3-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ac4a3-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ac4a3-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="ac4a3-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ac4a3-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ac4a3-121">E_FAIL</span></span>|<span data-ttu-id="ac4a3-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="ac4a3-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ac4a3-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ac4a3-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ac4a3-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="ac4a3-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ac4a3-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="ac4a3-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="ac4a3-126">İstenen ayırmayı tamamlamaya yetecek miktarda bellek yok.</span><span class="sxs-lookup"><span data-stu-id="ac4a3-126">Not enough memory is available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac4a3-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ac4a3-127">Remarks</span></span>  
 <span data-ttu-id="ac4a3-128">Yönetilmeyen koddan ve öğesinden gelen çağrı dizileri iç içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="ac4a3-128">Call sequences to and from unmanaged code can be nested.</span></span> <span data-ttu-id="ac4a3-129">Örneğin, aşağıdaki liste `LeaveRuntime` ,, [IHostTaskManager:: Smarenterruntime](ihosttaskmanager-reverseenterruntime-method.md), [IHostTaskManager:: ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md)öğesine çağrı dizisinin, `IHostTaskManager::EnterRuntime` iç içe geçmiş katmanları belirlemesine izin veren bir kuramsal durum tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ac4a3-129">For example, the list below describes a hypothetical situation in which the sequence of calls to `LeaveRuntime`, [IHostTaskManager::ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md), [IHostTaskManager::ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md), and `IHostTaskManager::EnterRuntime` allows the host to identify the nested layers.</span></span>  
  
|<span data-ttu-id="ac4a3-130">Eylem</span><span class="sxs-lookup"><span data-stu-id="ac4a3-130">Action</span></span>|<span data-ttu-id="ac4a3-131">Karşılık gelen yöntem çağrısı</span><span class="sxs-lookup"><span data-stu-id="ac4a3-131">Corresponding Method Call</span></span>|  
|------------|-------------------------------|  
|<span data-ttu-id="ac4a3-132">Yönetilen bir Visual Basic çalıştırılabilir, platform Invoke kullanılarak C dilinde yazılmış yönetilmeyen bir işlevi çağırır.</span><span class="sxs-lookup"><span data-stu-id="ac4a3-132">A managed Visual Basic executable calls an unmanaged function written in C by using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="ac4a3-133">Yönetilmeyen C işlevi, C# dilinde yazılmış yönetilen DLL içindeki bir yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="ac4a3-133">The unmanaged C function calls a method in a managed DLL written in C#.</span></span>|`IHostTaskManager::ReverseEnterRuntime`|  
|<span data-ttu-id="ac4a3-134">Yönetilen C# işlevi, platform Invoke kullanılarak C dilinde yazılmış başka bir yönetilmeyen işlevi çağırır.</span><span class="sxs-lookup"><span data-stu-id="ac4a3-134">The managed C# function calls another unmanaged function written in C, also using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="ac4a3-135">İkinci yönetilmeyen işlev, C# işlevine yürütme döndürür.</span><span class="sxs-lookup"><span data-stu-id="ac4a3-135">The second unmanaged function returns execution to the C# function.</span></span>|`IHostTaskManager::EnterRuntime`|  
|<span data-ttu-id="ac4a3-136">C# işlevi, yürütmeyi ilk yönetilmeyen işleve döndürür.</span><span class="sxs-lookup"><span data-stu-id="ac4a3-136">The C# function returns execution to the first unmanaged function.</span></span>|`IHostTaskManager::ReverseLeaveRuntime`|  
|<span data-ttu-id="ac4a3-137">İlk yönetilmeyen işlev Visual Basic programına yürütme döndürür.</span><span class="sxs-lookup"><span data-stu-id="ac4a3-137">The first unmanaged function returns execution to the Visual Basic program.</span></span>|`IHostTaskManager::EnterRuntime`|  
  
## <a name="requirements"></a><span data-ttu-id="ac4a3-138">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ac4a3-138">Requirements</span></span>  
 <span data-ttu-id="ac4a3-139">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac4a3-139">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac4a3-140">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ac4a3-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ac4a3-141">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="ac4a3-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ac4a3-142">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac4a3-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac4a3-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac4a3-143">See also</span></span>

- [<span data-ttu-id="ac4a3-144">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ac4a3-144">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="ac4a3-145">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ac4a3-145">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="ac4a3-146">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ac4a3-146">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="ac4a3-147">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ac4a3-147">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
