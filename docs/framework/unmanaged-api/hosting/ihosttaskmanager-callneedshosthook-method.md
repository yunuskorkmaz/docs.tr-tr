---
title: "IHostTaskManager::CallNeedsHostHook Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.CallNeedsHostHook
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::CallNeedsHostHook
helpviewer_keywords:
- CallNeedsHostHook method [.NET Framework hosting]
- IHostTaskManager::CallNeedsHostHook method [.NET Framework hosting]
ms.assetid: b60f1f59-9825-4b57-961f-d2979518e6a7
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0daa122b3576c1a6e6e192a4992549e704721bb4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskmanagercallneedshosthook-method"></a><span data-ttu-id="526b5-102">IHostTaskManager::CallNeedsHostHook Yöntemi</span><span class="sxs-lookup"><span data-stu-id="526b5-102">IHostTaskManager::CallNeedsHostHook Method</span></span>
<span data-ttu-id="526b5-103">Ortak dil çalışma zamanı (CLR) olup olmadığını satır içi belirtilen yönetilmeyen işlev çağrısı belirtebileceğiniz konağı etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="526b5-103">Enables the host to specify whether the common language runtime (CLR) can inline the specified call to an unmanaged function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="526b5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="526b5-104">Syntax</span></span>  
  
```  
HRESULT CallNeedsHostHook (  
    [in]  SIZE_T target,   
    [out] BOOL   *pbCallNeedsHostHook  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="526b5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="526b5-105">Parameters</span></span>  
 `target`  
 <span data-ttu-id="526b5-106">[in] Çağrılacak olan yönetilmeyen işlevinin eşlenen taşınabilir yürütülebilir (PE) dosyasındaki adresi.</span><span class="sxs-lookup"><span data-stu-id="526b5-106">[in] The address within the mapped portable executable (PE) file of the unmanaged function that is to be called.</span></span>  
  
 `pbCallNeedsHostHook`  
 <span data-ttu-id="526b5-107">[out] Ana sayfaya için çağrı gerekli olup olmadığını gösteren bir Boole değeri için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="526b5-107">[out] A pointer to a Boolean value that indicates whether the host requires the call to be hooked.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="526b5-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="526b5-108">Return Value</span></span>  
  
|<span data-ttu-id="526b5-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="526b5-109">HRESULT</span></span>|<span data-ttu-id="526b5-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="526b5-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="526b5-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="526b5-111">S_OK</span></span>|<span data-ttu-id="526b5-112">`CallNeedsHostHook`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="526b5-112">`CallNeedsHostHook` returned successfully.</span></span>|  
|<span data-ttu-id="526b5-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="526b5-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="526b5-114">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="526b5-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="526b5-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="526b5-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="526b5-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="526b5-116">The call timed out.</span></span>|  
|<span data-ttu-id="526b5-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="526b5-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="526b5-118">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="526b5-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="526b5-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="526b5-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="526b5-120">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="526b5-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="526b5-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="526b5-121">E_FAIL</span></span>|<span data-ttu-id="526b5-122">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="526b5-122">An unknown catastrophic failure has occurred.</span></span> <span data-ttu-id="526b5-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="526b5-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="526b5-124">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="526b5-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="526b5-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="526b5-125">Remarks</span></span>  
 <span data-ttu-id="526b5-126">Kod yürütmeyi en iyi duruma getirmek için her platform için bir çözümleme CLR yapar çağrı içermesinden izin verilip verilmeyeceğini belirlemek için derleme sırasında çağrısı başlatılacak.</span><span class="sxs-lookup"><span data-stu-id="526b5-126">To help optimize code execution, the CLR performs an analysis of each platform invoke call during compilation to determine whether the call can be inlined.</span></span> <span data-ttu-id="526b5-127">`CallNeedsHostHook`yönetilmeyen işlev çağrısı sayfaya gerektirerek kararı geçersiz kılmak ana bilgisayarı sağlar.</span><span class="sxs-lookup"><span data-stu-id="526b5-127">`CallNeedsHostHook` enables the host to override that decision by requiring that a call to an unmanaged function be hooked.</span></span> <span data-ttu-id="526b5-128">Konak bir kanca gerektiriyorsa, çalışma zamanı hizalı değil çağrı yapar.</span><span class="sxs-lookup"><span data-stu-id="526b5-128">If the host requires a hook, the runtime does not inline the call.</span></span>  
  
 <span data-ttu-id="526b5-129">Konak, genellikle bir kayan nokta durumu ayarlamanız gerekir veya bir çağrı ana bellek veya gerçekleştirilecek kilitleri için zamanının istekleri burada izleyemez durumu giriyor bildirim alma sırasında bir kanca gerekir.</span><span class="sxs-lookup"><span data-stu-id="526b5-129">The host typically would require a hook where it must adjust a floating-point state, or upon receiving notification that a call is entering a state where the host cannot track the runtime's requests for memory or any locks taken.</span></span> <span data-ttu-id="526b5-130">Konak çağrı sayfaya gerektirdiğinde, çalışma zamanı ve yönetilen kod gelen geçişleri ana çağrıları kullanarak bildirir [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), ve [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="526b5-130">When the host requires that the call be hooked, the runtime notifies the host of transitions to and from managed code by using calls to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), and [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="526b5-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="526b5-131">Requirements</span></span>  
 <span data-ttu-id="526b5-132">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="526b5-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="526b5-133">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="526b5-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="526b5-134">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="526b5-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="526b5-135">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="526b5-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="526b5-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="526b5-136">See Also</span></span>  
 [<span data-ttu-id="526b5-137">Iclrtask arabirimi</span><span class="sxs-lookup"><span data-stu-id="526b5-137">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="526b5-138">Iclrtaskmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="526b5-138">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="526b5-139">Ihosttask arabirimi</span><span class="sxs-lookup"><span data-stu-id="526b5-139">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="526b5-140">Ihosttaskmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="526b5-140">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
