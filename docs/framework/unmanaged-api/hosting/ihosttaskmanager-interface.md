---
title: IHostTaskManager Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager
helpviewer_keywords:
- IHostTaskManager interface [.NET Framework hosting]
ms.assetid: 4a0b05b9-3ef1-4607-b7c8-bd4dd43647a0
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9573891a2c27a2a92eccd0522f84175effa8037a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskmanager-interface"></a><span data-ttu-id="3e868-102">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3e868-102">IHostTaskManager Interface</span></span>
<span data-ttu-id="3e868-103">Ortak dil çalışma zamanı (CLR) standart işletim sistemi iş parçacığı oluşturma veya fiber işlevlerini kullanmak yerine ana bilgisayar üzerinden görevlerle çalışmaya izin yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e868-103">Provides methods that allow the common language runtime (CLR) to work with tasks through the host instead of using the standard operating system threading or fiber functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3e868-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="3e868-104">Methods</span></span>  
  
|<span data-ttu-id="3e868-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="3e868-105">Method</span></span>|<span data-ttu-id="3e868-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3e868-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3e868-107">BeginDelayAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3e868-107">BeginDelayAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md)|<span data-ttu-id="3e868-108">Yönetilen kod konak bir süre içinde geçerli görev iptal gerekir girme bildirir.</span><span class="sxs-lookup"><span data-stu-id="3e868-108">Notifies the host that managed code is entering a period in which the current task must not be aborted.</span></span>|  
|[<span data-ttu-id="3e868-109">BeginThreadAffinity Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3e868-109">BeginThreadAffinity Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md)|<span data-ttu-id="3e868-110">Yönetilen kod konak bir süre içinde geçerli görev başka bir işletim sistemi iş parçacığına taşınmalıdır değil girme bildirir.</span><span class="sxs-lookup"><span data-stu-id="3e868-110">Notifies the host that managed code is entering a period in which the current task must not be moved to another operating system thread.</span></span>|  
|[<span data-ttu-id="3e868-111">CallNeedsHostHook Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3e868-111">CallNeedsHostHook Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-callneedshosthook-method.md)|<span data-ttu-id="3e868-112">Ortak dil çalışma zamanı satır içi belirtilen yönetilmeyen işlev çağrısı için olup olmadığını belirlemek ana bilgisayarı sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e868-112">Enables the host to specify whether the common language runtime can inline the specified call to an unmanaged function.</span></span>|  
|[<span data-ttu-id="3e868-113">CreateTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3e868-113">CreateTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md)|<span data-ttu-id="3e868-114">İstekleri ana bilgisayar yeni bir görev oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3e868-114">Requests that the host create a new task.</span></span>|  
|[<span data-ttu-id="3e868-115">EndDelayAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3e868-115">EndDelayAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md)|<span data-ttu-id="3e868-116">Yönetilen kod ana bilgisayar, bir önceki çağrısından, geçerli görev gerekir iptal, dönem çıkıyor bildirir `BeginDelayAbort`.</span><span class="sxs-lookup"><span data-stu-id="3e868-116">Notifies the host that managed code is exiting the period in which the current task must not be aborted, following an earlier call to `BeginDelayAbort`.</span></span>|  
|[<span data-ttu-id="3e868-117">EndThreadAffinity Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3e868-117">EndThreadAffinity Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md)|<span data-ttu-id="3e868-118">Yönetilen kod ana bilgisayar, bir önceki çağrısından, geçerli görev değil taşınması gerekir başka bir işletim sistemi iş parçacığına dönemi çıkıyor bildirir `BeginThreadAffinity`.</span><span class="sxs-lookup"><span data-stu-id="3e868-118">Notifies the host that managed code is exiting the period in which the current task must not be moved to another operating system thread, following an earlier call to `BeginThreadAffinity`.</span></span>|  
|[<span data-ttu-id="3e868-119">EnterRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3e868-119">EnterRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)|<span data-ttu-id="3e868-120">Konak, yönetilmeyen bir yöntem çağrısı bir platform çağırma yöntemi olarak CLR yürütme denetimi döndürmektir bildirir.</span><span class="sxs-lookup"><span data-stu-id="3e868-120">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the CLR.</span></span>|  
|[<span data-ttu-id="3e868-121">GetCurrentTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3e868-121">GetCurrentTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md)|<span data-ttu-id="3e868-122">Bu çağrı yapılır işletim sistemi iş parçacığı üzerinde şu anda yürütülmekte görev için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="3e868-122">Gets an interface pointer to the task that is currently executing on the operating system thread from which this call is made.</span></span>|  
|[<span data-ttu-id="3e868-123">GetStackGuarantee Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3e868-123">GetStackGuarantee Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getstackguarantee-method.md)|<span data-ttu-id="3e868-124">Yığın işlemi tamamlandıktan sonra kullanılabilir olması garanti yığın alanı, ancak bir işlemin kapanmadan önce miktarını alır.</span><span class="sxs-lookup"><span data-stu-id="3e868-124">Gets the amount of stack space that is guaranteed to be available after a stack operation completes, but before the closing of a process.</span></span>|  
|[<span data-ttu-id="3e868-125">LeaveRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3e868-125">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)|<span data-ttu-id="3e868-126">Yönetilmeyen işlev çağrısı yapmak üzere, yönetilen kod ana bilgisayarın olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="3e868-126">Notifies the host that managed code is about to make a call to an unmanaged function.</span></span>|  
|[<span data-ttu-id="3e868-127">ReverseEnterRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3e868-127">ReverseEnterRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)|<span data-ttu-id="3e868-128">Konak bir çağrı yönetilmeyen koddan ortak dil çalışma zamanı (CLR) içine yapılıyor bildirir.</span><span class="sxs-lookup"><span data-stu-id="3e868-128">Notifies the host that a call is being made into the common language runtime (CLR) from unmanaged code.</span></span>|  
|[<span data-ttu-id="3e868-129">ReverseLeaveRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3e868-129">ReverseLeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)|<span data-ttu-id="3e868-130">Ana bilgisayar denetimi CLR bırakarak ve buna karşılık, yönetilen koddan çağrıldı bir yönetilmeyen işlevi giriliyor bildirir.</span><span class="sxs-lookup"><span data-stu-id="3e868-130">Notifies the host that control is leaving the CLR and entering an unmanaged function that was, in turn, called from managed code.</span></span>|  
|[<span data-ttu-id="3e868-131">SetCLRTaskManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3e868-131">SetCLRTaskManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setclrtaskmanager-method.md)|<span data-ttu-id="3e868-132">Ana bilgisayar için bir arabirim işaretçisi sağlayan bir [Iclrtaskmanager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) CLR tarafından uygulanan örneği.</span><span class="sxs-lookup"><span data-stu-id="3e868-132">Provides the host with an interface pointer to an [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) instance implemented by the CLR.</span></span>|  
|[<span data-ttu-id="3e868-133">SetLocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3e868-133">SetLocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setlocale-method.md)|<span data-ttu-id="3e868-134">Ana bilgisayar CLR geçerli görevde yerel değiştiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="3e868-134">Notifies the host that the CLR has changed the locale on the current task.</span></span>|  
|[<span data-ttu-id="3e868-135">SetStackGuarantee Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3e868-135">SetStackGuarantee Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setstackguarantee-method.md)|<span data-ttu-id="3e868-136">Yalnızca iç kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="3e868-136">Reserved for internal use only.</span></span>|  
|[<span data-ttu-id="3e868-137">SetUILocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3e868-137">SetUILocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setuilocale-method.md)|<span data-ttu-id="3e868-138">Konak üzerinde geçerli görev kullanıcı arabirimi yerel ayarı değiştirildi bildirir.</span><span class="sxs-lookup"><span data-stu-id="3e868-138">Notifies the host that the user interface locale has been changed on the current task.</span></span>|  
|[<span data-ttu-id="3e868-139">Sleep Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3e868-139">Sleep Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md)|<span data-ttu-id="3e868-140">Geçerli görev uyku gittiği konak bildirir.</span><span class="sxs-lookup"><span data-stu-id="3e868-140">Notifies the host that the current task is going to sleep.</span></span>|  
|[<span data-ttu-id="3e868-141">SwitchToTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3e868-141">SwitchToTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md)|<span data-ttu-id="3e868-142">Geçerli görev moduna geçirmelisiniz konak bildirir.</span><span class="sxs-lookup"><span data-stu-id="3e868-142">Notifies the host that it should switch out the current task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e868-143">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3e868-143">Remarks</span></span>  
 <span data-ttu-id="3e868-144">`IHostTaskManager`oluşturmak ve görevleri yönetmek CLR sağlar denetim yönetilmeyen kod ve tersi yönde yönetilen aktarır durumlarda eyleme ve belirli eylemleri belirtmek için ana bilgisayar için kancaları sağlamak için konak olabilir ve kod yürütme sırasında alamıyor.</span><span class="sxs-lookup"><span data-stu-id="3e868-144">`IHostTaskManager` allows the CLR to create and manage tasks, to provide hooks for the host to take action when control transfers from managed to unmanaged code and vice versa, and to specify certain actions the host can and cannot take during code execution.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e868-145">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3e868-145">Requirements</span></span>  
 <span data-ttu-id="3e868-146">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e868-146">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e868-147">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3e868-147">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3e868-148">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="3e868-148">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3e868-149">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e868-149">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e868-150">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3e868-150">See Also</span></span>  
 [<span data-ttu-id="3e868-151">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3e868-151">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="3e868-152">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3e868-152">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="3e868-153">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3e868-153">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="3e868-154">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3e868-154">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
