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
ms.openlocfilehash: f5a595651baa48553997c2cba138f4f61bd530f0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133098"
---
# <a name="ihosttaskmanagercallneedshosthook-method"></a><span data-ttu-id="cbbe3-102">IHostTaskManager::CallNeedsHostHook Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cbbe3-102">IHostTaskManager::CallNeedsHostHook Method</span></span>
<span data-ttu-id="cbbe3-103">Ana bilgisayarın, ortak dil çalışma zamanının (CLR) yönetilmeyen bir işleve belirtilen çağrıyı satır içinde yapıp gerçekleştiremeyeceğini belirtmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="cbbe3-103">Enables the host to specify whether the common language runtime (CLR) can inline the specified call to an unmanaged function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbbe3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cbbe3-104">Syntax</span></span>  
  
```cpp  
HRESULT CallNeedsHostHook (  
    [in]  SIZE_T target,   
    [out] BOOL   *pbCallNeedsHostHook  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cbbe3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cbbe3-105">Parameters</span></span>  
 `target`  
 <span data-ttu-id="cbbe3-106">'ndaki Çağrılan yönetilmeyen işlevin eşlenmiş Taşınabilir çalıştırılabilir (PE) dosyası içindeki adres.</span><span class="sxs-lookup"><span data-stu-id="cbbe3-106">[in] The address within the mapped portable executable (PE) file of the unmanaged function that is to be called.</span></span>  
  
 `pbCallNeedsHostHook`  
 <span data-ttu-id="cbbe3-107">dışı Konağın, çağrının takılıp gerektirmeyeceğini belirten bir Boole değeri işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="cbbe3-107">[out] A pointer to a Boolean value that indicates whether the host requires the call to be hooked.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cbbe3-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cbbe3-108">Return Value</span></span>  
  
|<span data-ttu-id="cbbe3-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cbbe3-109">HRESULT</span></span>|<span data-ttu-id="cbbe3-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cbbe3-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cbbe3-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="cbbe3-111">S_OK</span></span>|<span data-ttu-id="cbbe3-112">`CallNeedsHostHook` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="cbbe3-112">`CallNeedsHostHook` returned successfully.</span></span>|  
|<span data-ttu-id="cbbe3-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cbbe3-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cbbe3-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="cbbe3-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cbbe3-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cbbe3-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cbbe3-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="cbbe3-116">The call timed out.</span></span>|  
|<span data-ttu-id="cbbe3-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cbbe3-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cbbe3-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="cbbe3-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cbbe3-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cbbe3-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cbbe3-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="cbbe3-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cbbe3-121">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="cbbe3-121">E_FAIL</span></span>|<span data-ttu-id="cbbe3-122">Bilinmeyen bir yıkıcı hatası oluştu.</span><span class="sxs-lookup"><span data-stu-id="cbbe3-122">An unknown catastrophic failure has occurred.</span></span> <span data-ttu-id="cbbe3-123">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="cbbe3-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cbbe3-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="cbbe3-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cbbe3-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cbbe3-125">Remarks</span></span>  
 <span data-ttu-id="cbbe3-126">Kod yürütmeyi iyileştirmenize yardımcı olmak için CLR derleme sırasında her platform çağırma çağrısının analizini gerçekleştirerek çağrının satır içine eklenip eklenmeyeceğini tespit eder.</span><span class="sxs-lookup"><span data-stu-id="cbbe3-126">To help optimize code execution, the CLR performs an analysis of each platform invoke call during compilation to determine whether the call can be inlined.</span></span> <span data-ttu-id="cbbe3-127">`CallNeedsHostHook`, konağın yönetilmeyen bir işleve yönelik çağrının takılmasına gerek kalmadan bu kararı geçersiz kılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="cbbe3-127">`CallNeedsHostHook` enables the host to override that decision by requiring that a call to an unmanaged function be hooked.</span></span> <span data-ttu-id="cbbe3-128">Ana bilgisayar bir kanca gerektiriyorsa, çalışma zamanı çağrıyı satır içine almaz.</span><span class="sxs-lookup"><span data-stu-id="cbbe3-128">If the host requires a hook, the runtime does not inline the call.</span></span>  
  
 <span data-ttu-id="cbbe3-129">Ana bilgisayar genellikle kayan nokta durumunu ayarlaması gereken bir kanca gerektirir veya bir çağrının, ana bilgisayarın bellek için çalışma zamanının veya yapılan kilitlerin isteklerini izleyememesi durumunda bir durum girdiğini belirten bildirim alma.</span><span class="sxs-lookup"><span data-stu-id="cbbe3-129">The host typically would require a hook where it must adjust a floating-point state, or upon receiving notification that a call is entering a state where the host cannot track the runtime's requests for memory or any locks taken.</span></span> <span data-ttu-id="cbbe3-130">Ana bilgisayar çağrının takılmayı gerektirdiğinde, çalışma zamanı, [Kurumsal çalışma zamanı](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [smarenterruntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)ve [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)çağrılarını kullanarak yönetilen koddan ve bu kod üzerinden geçiş konağını bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="cbbe3-130">When the host requires that the call be hooked, the runtime notifies the host of transitions to and from managed code by using calls to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), and [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbbe3-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cbbe3-131">Requirements</span></span>  
 <span data-ttu-id="cbbe3-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbbe3-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbbe3-133">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cbbe3-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cbbe3-134">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="cbbe3-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cbbe3-135">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbbe3-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbbe3-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cbbe3-136">See also</span></span>

- [<span data-ttu-id="cbbe3-137">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cbbe3-137">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="cbbe3-138">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cbbe3-138">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="cbbe3-139">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cbbe3-139">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="cbbe3-140">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cbbe3-140">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
