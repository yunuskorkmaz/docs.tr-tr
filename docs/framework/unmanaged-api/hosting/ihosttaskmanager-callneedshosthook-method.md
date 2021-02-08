---
description: 'Şu konuda daha fazla bilgi edinin: IHostTaskManager:: Callgereksiz Showsthook yöntemi'
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
ms.openlocfilehash: 777e1e6c4ac094a7af077c481415167f57eed14d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784593"
---
# <a name="ihosttaskmanagercallneedshosthook-method"></a><span data-ttu-id="075c7-103">IHostTaskManager::CallNeedsHostHook Yöntemi</span><span class="sxs-lookup"><span data-stu-id="075c7-103">IHostTaskManager::CallNeedsHostHook Method</span></span>

<span data-ttu-id="075c7-104">Ana bilgisayarın, ortak dil çalışma zamanının (CLR) yönetilmeyen bir işleve belirtilen çağrıyı satır içinde yapıp gerçekleştiremeyeceğini belirtmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="075c7-104">Enables the host to specify whether the common language runtime (CLR) can inline the specified call to an unmanaged function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="075c7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="075c7-105">Syntax</span></span>  
  
```cpp  
HRESULT CallNeedsHostHook (  
    [in]  SIZE_T target,
    [out] BOOL   *pbCallNeedsHostHook  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="075c7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="075c7-106">Parameters</span></span>  

 `target`  
 <span data-ttu-id="075c7-107">'ndaki Çağrılan yönetilmeyen işlevin eşlenmiş Taşınabilir çalıştırılabilir (PE) dosyası içindeki adres.</span><span class="sxs-lookup"><span data-stu-id="075c7-107">[in] The address within the mapped portable executable (PE) file of the unmanaged function that is to be called.</span></span>  
  
 `pbCallNeedsHostHook`  
 <span data-ttu-id="075c7-108">dışı Konağın, çağrının takılıp gerektirmeyeceğini belirten bir Boole değeri işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="075c7-108">[out] A pointer to a Boolean value that indicates whether the host requires the call to be hooked.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="075c7-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="075c7-109">Return Value</span></span>  
  
|<span data-ttu-id="075c7-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="075c7-110">HRESULT</span></span>|<span data-ttu-id="075c7-111">Description</span><span class="sxs-lookup"><span data-stu-id="075c7-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="075c7-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="075c7-112">S_OK</span></span>|<span data-ttu-id="075c7-113">`CallNeedsHostHook` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="075c7-113">`CallNeedsHostHook` returned successfully.</span></span>|  
|<span data-ttu-id="075c7-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="075c7-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="075c7-115">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="075c7-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="075c7-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="075c7-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="075c7-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="075c7-117">The call timed out.</span></span>|  
|<span data-ttu-id="075c7-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="075c7-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="075c7-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="075c7-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="075c7-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="075c7-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="075c7-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="075c7-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="075c7-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="075c7-122">E_FAIL</span></span>|<span data-ttu-id="075c7-123">Bilinmeyen bir yıkıcı hatası oluştu.</span><span class="sxs-lookup"><span data-stu-id="075c7-123">An unknown catastrophic failure has occurred.</span></span> <span data-ttu-id="075c7-124">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="075c7-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="075c7-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="075c7-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="075c7-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="075c7-126">Remarks</span></span>  

 <span data-ttu-id="075c7-127">Kod yürütmeyi iyileştirmenize yardımcı olmak için CLR derleme sırasında her platform çağırma çağrısının analizini gerçekleştirerek çağrının satır içine eklenip eklenmeyeceğini tespit eder.</span><span class="sxs-lookup"><span data-stu-id="075c7-127">To help optimize code execution, the CLR performs an analysis of each platform invoke call during compilation to determine whether the call can be inlined.</span></span> <span data-ttu-id="075c7-128">`CallNeedsHostHook` yönetilmeyen bir işleve yapılan çağrının takılmasına gerek kalmadan konağın bu kararı geçersiz kılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="075c7-128">`CallNeedsHostHook` enables the host to override that decision by requiring that a call to an unmanaged function be hooked.</span></span> <span data-ttu-id="075c7-129">Ana bilgisayar bir kanca gerektiriyorsa, çalışma zamanı çağrıyı satır içine almaz.</span><span class="sxs-lookup"><span data-stu-id="075c7-129">If the host requires a hook, the runtime does not inline the call.</span></span>  
  
 <span data-ttu-id="075c7-130">Ana bilgisayar genellikle kayan nokta durumunu ayarlaması gereken bir kanca gerektirir veya bir çağrının, ana bilgisayarın bellek için çalışma zamanının veya yapılan kilitlerin isteklerini izleyememesi durumunda bir durum girdiğini belirten bildirim alma.</span><span class="sxs-lookup"><span data-stu-id="075c7-130">The host typically would require a hook where it must adjust a floating-point state, or upon receiving notification that a call is entering a state where the host cannot track the runtime's requests for memory or any locks taken.</span></span> <span data-ttu-id="075c7-131">Ana bilgisayar çağrının takılmayı gerektirdiğinde, çalışma zamanı, [Kurumsal çalışma zamanı](ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](ihosttaskmanager-leaveruntime-method.md), [smarenterruntime](ihosttaskmanager-reverseenterruntime-method.md)ve [ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md)çağrılarını kullanarak yönetilen koddan ve bu kod üzerinden geçiş konağını bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="075c7-131">When the host requires that the call be hooked, the runtime notifies the host of transitions to and from managed code by using calls to [EnterRuntime](ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](ihosttaskmanager-leaveruntime-method.md), [ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md), and [ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="075c7-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="075c7-132">Requirements</span></span>  

 <span data-ttu-id="075c7-133">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="075c7-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="075c7-134">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="075c7-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="075c7-135">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="075c7-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="075c7-136">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="075c7-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="075c7-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="075c7-137">See also</span></span>

- [<span data-ttu-id="075c7-138">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="075c7-138">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="075c7-139">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="075c7-139">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="075c7-140">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="075c7-140">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="075c7-141">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="075c7-141">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
