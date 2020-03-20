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
ms.openlocfilehash: 8b8b8521a09fa54a105e8263a471ab0467fb6ccc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176298"
---
# <a name="ihosttaskmanagercallneedshosthook-method"></a><span data-ttu-id="afdce-102">IHostTaskManager::CallNeedsHostHook Yöntemi</span><span class="sxs-lookup"><span data-stu-id="afdce-102">IHostTaskManager::CallNeedsHostHook Method</span></span>
<span data-ttu-id="afdce-103">Ortak dil çalışma zamanının (CLR) yönetilen olmayan bir işleve belirtilen çağrıyı sıralayıp sıralayamayacağını belirtmek için ana bilgisayara olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="afdce-103">Enables the host to specify whether the common language runtime (CLR) can inline the specified call to an unmanaged function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afdce-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="afdce-104">Syntax</span></span>  
  
```cpp  
HRESULT CallNeedsHostHook (  
    [in]  SIZE_T target,
    [out] BOOL   *pbCallNeedsHostHook  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="afdce-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="afdce-105">Parameters</span></span>  
 `target`  
 <span data-ttu-id="afdce-106">[içinde] Çağrılacak olan yönetilmeyen işlevin eşlenen taşınabilir yürütülebilir (PE) dosyasındaki adres.</span><span class="sxs-lookup"><span data-stu-id="afdce-106">[in] The address within the mapped portable executable (PE) file of the unmanaged function that is to be called.</span></span>  
  
 `pbCallNeedsHostHook`  
 <span data-ttu-id="afdce-107">[çıkış] Ana bilgisayar çağrısının bağlanmayı gerektirip gerektirmediğini gösteren Boolean değerine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="afdce-107">[out] A pointer to a Boolean value that indicates whether the host requires the call to be hooked.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="afdce-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="afdce-108">Return Value</span></span>  
  
|<span data-ttu-id="afdce-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="afdce-109">HRESULT</span></span>|<span data-ttu-id="afdce-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="afdce-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="afdce-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="afdce-111">S_OK</span></span>|<span data-ttu-id="afdce-112">`CallNeedsHostHook`başarıyla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="afdce-112">`CallNeedsHostHook` returned successfully.</span></span>|  
|<span data-ttu-id="afdce-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="afdce-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="afdce-114">CLR bir işleme yüklenmedi veya CLR yönetilen kodu çalıştıramadığı veya aramayı başarıyla işleyemediği bir durumdadır.</span><span class="sxs-lookup"><span data-stu-id="afdce-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="afdce-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="afdce-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="afdce-116">Arama zaman doldu.</span><span class="sxs-lookup"><span data-stu-id="afdce-116">The call timed out.</span></span>|  
|<span data-ttu-id="afdce-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="afdce-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="afdce-118">Arayan kilidin sahibi değildir.</span><span class="sxs-lookup"><span data-stu-id="afdce-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="afdce-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="afdce-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="afdce-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="afdce-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="afdce-121">E_faıl</span><span class="sxs-lookup"><span data-stu-id="afdce-121">E_FAIL</span></span>|<span data-ttu-id="afdce-122">Bilinmeyen bir felaket hatası meydana geldi.</span><span class="sxs-lookup"><span data-stu-id="afdce-122">An unknown catastrophic failure has occurred.</span></span> <span data-ttu-id="afdce-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="afdce-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="afdce-124">Barındırma yöntemleri sonraki aramalar HOST_E_CLRNOTAVAILABLE döndürün.</span><span class="sxs-lookup"><span data-stu-id="afdce-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="afdce-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="afdce-125">Remarks</span></span>  
 <span data-ttu-id="afdce-126">Kod yürütmeyi optimize etmeye yardımcı olmak için CLR, çağrının eklenmiş olup olmadığını belirlemek için derleme sırasında her platformun çağrı çağrısının bir çözümlemesi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="afdce-126">To help optimize code execution, the CLR performs an analysis of each platform invoke call during compilation to determine whether the call can be inlined.</span></span> <span data-ttu-id="afdce-127">`CallNeedsHostHook`yönetilmeyen bir işleve çağrının bağlanmasını gerektirerek ana bilgisayar sahibinin bu kararı geçersiz kılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="afdce-127">`CallNeedsHostHook` enables the host to override that decision by requiring that a call to an unmanaged function be hooked.</span></span> <span data-ttu-id="afdce-128">Ana bilgisayar bir kanca gerektiriyorsa, çalışma süresi çağrıyı satır lı olarak göstermez.</span><span class="sxs-lookup"><span data-stu-id="afdce-128">If the host requires a hook, the runtime does not inline the call.</span></span>  
  
 <span data-ttu-id="afdce-129">Ana bilgisayar genellikle kayan nokta durumunu ayarlaması gereken bir kanca gerektirir veya bir çağrının çalışma zamanının bellek isteklerini veya alınan kilitleri izleyemediği bir duruma girdiğine dair bildirim alındıktan sonra.</span><span class="sxs-lookup"><span data-stu-id="afdce-129">The host typically would require a hook where it must adjust a floating-point state, or upon receiving notification that a call is entering a state where the host cannot track the runtime's requests for memory or any locks taken.</span></span> <span data-ttu-id="afdce-130">Ana bilgisayar aramanın bağlanmasını gerektirdiğinde, çalışma zamanı [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)ve [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)çağrılarını kullanarak yönetilen koda geçişlerin ana bilgisayarını not eder.</span><span class="sxs-lookup"><span data-stu-id="afdce-130">When the host requires that the call be hooked, the runtime notifies the host of transitions to and from managed code by using calls to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), and [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afdce-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="afdce-131">Requirements</span></span>  
 <span data-ttu-id="afdce-132">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="afdce-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afdce-133">**Üstbilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="afdce-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="afdce-134">**Kütüphane:** MSCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="afdce-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="afdce-135">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afdce-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afdce-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="afdce-136">See also</span></span>

- [<span data-ttu-id="afdce-137">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="afdce-137">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="afdce-138">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="afdce-138">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="afdce-139">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="afdce-139">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="afdce-140">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="afdce-140">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
