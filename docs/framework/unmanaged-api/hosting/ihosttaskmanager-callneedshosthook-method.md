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
ms.workload: dotnet
ms.openlocfilehash: 4774c9f37f73692bf8d9455c51e76aa4c590f925
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskmanagercallneedshosthook-method"></a><span data-ttu-id="4bdaa-102">IHostTaskManager::CallNeedsHostHook Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4bdaa-102">IHostTaskManager::CallNeedsHostHook Method</span></span>
<span data-ttu-id="4bdaa-103">Ortak dil çalışma zamanı (CLR) olup olmadığını satır içi belirtilen yönetilmeyen işlev çağrısı belirtebileceğiniz konağı etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="4bdaa-103">Enables the host to specify whether the common language runtime (CLR) can inline the specified call to an unmanaged function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bdaa-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4bdaa-104">Syntax</span></span>  
  
```  
HRESULT CallNeedsHostHook (  
    [in]  SIZE_T target,   
    [out] BOOL   *pbCallNeedsHostHook  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4bdaa-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4bdaa-105">Parameters</span></span>  
 `target`  
 <span data-ttu-id="4bdaa-106">[in] Çağrılacak olan yönetilmeyen işlevinin eşlenen taşınabilir yürütülebilir (PE) dosyasındaki adresi.</span><span class="sxs-lookup"><span data-stu-id="4bdaa-106">[in] The address within the mapped portable executable (PE) file of the unmanaged function that is to be called.</span></span>  
  
 `pbCallNeedsHostHook`  
 <span data-ttu-id="4bdaa-107">[out] Ana sayfaya için çağrı gerekli olup olmadığını gösteren bir Boole değeri için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4bdaa-107">[out] A pointer to a Boolean value that indicates whether the host requires the call to be hooked.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4bdaa-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4bdaa-108">Return Value</span></span>  
  
|<span data-ttu-id="4bdaa-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4bdaa-109">HRESULT</span></span>|<span data-ttu-id="4bdaa-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4bdaa-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4bdaa-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="4bdaa-111">S_OK</span></span>|<span data-ttu-id="4bdaa-112">`CallNeedsHostHook`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="4bdaa-112">`CallNeedsHostHook` returned successfully.</span></span>|  
|<span data-ttu-id="4bdaa-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4bdaa-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4bdaa-114">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="4bdaa-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4bdaa-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4bdaa-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4bdaa-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="4bdaa-116">The call timed out.</span></span>|  
|<span data-ttu-id="4bdaa-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4bdaa-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4bdaa-118">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="4bdaa-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4bdaa-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4bdaa-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4bdaa-120">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="4bdaa-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4bdaa-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4bdaa-121">E_FAIL</span></span>|<span data-ttu-id="4bdaa-122">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="4bdaa-122">An unknown catastrophic failure has occurred.</span></span> <span data-ttu-id="4bdaa-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4bdaa-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4bdaa-124">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="4bdaa-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4bdaa-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4bdaa-125">Remarks</span></span>  
 <span data-ttu-id="4bdaa-126">Kod yürütmeyi en iyi duruma getirmek için her platform için bir çözümleme CLR yapar çağrı içermesinden izin verilip verilmeyeceğini belirlemek için derleme sırasında çağrısı başlatılacak.</span><span class="sxs-lookup"><span data-stu-id="4bdaa-126">To help optimize code execution, the CLR performs an analysis of each platform invoke call during compilation to determine whether the call can be inlined.</span></span> <span data-ttu-id="4bdaa-127">`CallNeedsHostHook`yönetilmeyen işlev çağrısı sayfaya gerektirerek kararı geçersiz kılmak ana bilgisayarı sağlar.</span><span class="sxs-lookup"><span data-stu-id="4bdaa-127">`CallNeedsHostHook` enables the host to override that decision by requiring that a call to an unmanaged function be hooked.</span></span> <span data-ttu-id="4bdaa-128">Konak bir kanca gerektiriyorsa, çalışma zamanı hizalı değil çağrı yapar.</span><span class="sxs-lookup"><span data-stu-id="4bdaa-128">If the host requires a hook, the runtime does not inline the call.</span></span>  
  
 <span data-ttu-id="4bdaa-129">Konak, genellikle bir kayan nokta durumu ayarlamanız gerekir veya bir çağrı ana bellek veya gerçekleştirilecek kilitleri için zamanının istekleri burada izleyemez durumu giriyor bildirim alma sırasında bir kanca gerekir.</span><span class="sxs-lookup"><span data-stu-id="4bdaa-129">The host typically would require a hook where it must adjust a floating-point state, or upon receiving notification that a call is entering a state where the host cannot track the runtime's requests for memory or any locks taken.</span></span> <span data-ttu-id="4bdaa-130">Konak çağrı sayfaya gerektirdiğinde, çalışma zamanı ve yönetilen kod gelen geçişleri ana çağrıları kullanarak bildirir [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), ve [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="4bdaa-130">When the host requires that the call be hooked, the runtime notifies the host of transitions to and from managed code by using calls to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), and [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bdaa-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4bdaa-131">Requirements</span></span>  
 <span data-ttu-id="4bdaa-132">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4bdaa-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bdaa-133">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4bdaa-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4bdaa-134">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="4bdaa-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4bdaa-135">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bdaa-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bdaa-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4bdaa-136">See Also</span></span>  
 [<span data-ttu-id="4bdaa-137">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4bdaa-137">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="4bdaa-138">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4bdaa-138">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="4bdaa-139">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4bdaa-139">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="4bdaa-140">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4bdaa-140">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
