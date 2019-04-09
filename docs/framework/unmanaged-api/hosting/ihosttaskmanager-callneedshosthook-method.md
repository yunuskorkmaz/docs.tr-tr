---
title: IHostTaskManager::CallNeedsHostHook Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTaskManager.CallNeedsHostHook
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::CallNeedsHostHook
helpviewer_keywords:
- CallNeedsHostHook method [.NET Framework hosting]
- IHostTaskManager::CallNeedsHostHook method [.NET Framework hosting]
ms.assetid: b60f1f59-9825-4b57-961f-d2979518e6a7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: adc270be51988cba78c6e522b16b480baef725c4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59139236"
---
# <a name="ihosttaskmanagercallneedshosthook-method"></a><span data-ttu-id="5a032-102">IHostTaskManager::CallNeedsHostHook Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5a032-102">IHostTaskManager::CallNeedsHostHook Method</span></span>
<span data-ttu-id="5a032-103">Ortak dil çalışma zamanı (CLR) satır içi belirtilen yönetilmeyen bir işlev çağrısı için olup olmadığını belirlemek konak sağlar.</span><span class="sxs-lookup"><span data-stu-id="5a032-103">Enables the host to specify whether the common language runtime (CLR) can inline the specified call to an unmanaged function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a032-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5a032-104">Syntax</span></span>  
  
```  
HRESULT CallNeedsHostHook (  
    [in]  SIZE_T target,   
    [out] BOOL   *pbCallNeedsHostHook  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a032-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5a032-105">Parameters</span></span>  
 `target`  
 <span data-ttu-id="5a032-106">[in] Çağrılacak olan yönetilmeyen işlev eşlenen taşınabilir yürütülebilir (PE) dosyanın dahilindeki adres.</span><span class="sxs-lookup"><span data-stu-id="5a032-106">[in] The address within the mapped portable executable (PE) file of the unmanaged function that is to be called.</span></span>  
  
 `pbCallNeedsHostHook`  
 <span data-ttu-id="5a032-107">[out] Konak çağrısı yayılmış gerekip gerekmediğini belirten bir Boole değeri için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5a032-107">[out] A pointer to a Boolean value that indicates whether the host requires the call to be hooked.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5a032-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5a032-108">Return Value</span></span>  
  
|<span data-ttu-id="5a032-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5a032-109">HRESULT</span></span>|<span data-ttu-id="5a032-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5a032-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5a032-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="5a032-111">S_OK</span></span>|`CallNeedsHostHook` <span data-ttu-id="5a032-112">başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="5a032-112">returned successfully.</span></span>|  
|<span data-ttu-id="5a032-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5a032-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5a032-114">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="5a032-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5a032-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5a032-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5a032-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="5a032-116">The call timed out.</span></span>|  
|<span data-ttu-id="5a032-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5a032-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5a032-118">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="5a032-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5a032-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5a032-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5a032-120">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="5a032-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5a032-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5a032-121">E_FAIL</span></span>|<span data-ttu-id="5a032-122">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="5a032-122">An unknown catastrophic failure has occurred.</span></span> <span data-ttu-id="5a032-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="5a032-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5a032-124">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="5a032-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a032-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5a032-125">Remarks</span></span>  
 <span data-ttu-id="5a032-126">CLR kod yürütme en iyi duruma getirmek için her platform için analiz gerçekleştirir çağrı satır içine alınmış olup olmadığını belirlemek için derleme sırasında çağrısı başlatılacak.</span><span class="sxs-lookup"><span data-stu-id="5a032-126">To help optimize code execution, the CLR performs an analysis of each platform invoke call during compilation to determine whether the call can be inlined.</span></span> `CallNeedsHostHook` <span data-ttu-id="5a032-127">yönetilmeyen bir işlev çağrısı kancalandı gerektirerek kararı geçersiz kılmak konak sağlar.</span><span class="sxs-lookup"><span data-stu-id="5a032-127">enables the host to override that decision by requiring that a call to an unmanaged function be hooked.</span></span> <span data-ttu-id="5a032-128">Konak bir kanca gerektiriyorsa, çalışma zamanı satır çağrı yapar.</span><span class="sxs-lookup"><span data-stu-id="5a032-128">If the host requires a hook, the runtime does not inline the call.</span></span>  
  
 <span data-ttu-id="5a032-129">Konak, genellikle bir kayan nokta durumu ayarlamanız gerekir veya çağrı ana bilgisayar bellek ya da kilitleri alınan çalışma zamanının istekleri nereye izleyemez bir duruma giriyor bildirim alma sırasında bir kanca gerekir.</span><span class="sxs-lookup"><span data-stu-id="5a032-129">The host typically would require a hook where it must adjust a floating-point state, or upon receiving notification that a call is entering a state where the host cannot track the runtime's requests for memory or any locks taken.</span></span> <span data-ttu-id="5a032-130">Konak çağrı yayılmış gerektirdiğinde, çalışma zamanı ana bilgisayarı geçişleri için ve yönetilen koddan çağrıları kullanarak bildirir [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), ve [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="5a032-130">When the host requires that the call be hooked, the runtime notifies the host of transitions to and from managed code by using calls to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), and [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a032-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5a032-131">Requirements</span></span>  
 <span data-ttu-id="5a032-132">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a032-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a032-133">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5a032-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5a032-134">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="5a032-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="5a032-135">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="5a032-135">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5a032-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a032-136">See also</span></span>

- [<span data-ttu-id="5a032-137">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5a032-137">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="5a032-138">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5a032-138">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="5a032-139">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5a032-139">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="5a032-140">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5a032-140">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
