---
description: 'Daha fazla bilgi edinin: IHostTaskManager arabirimi'
title: IHostTaskManager Arabirimi
ms.date: 03/30/2017
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
ms.openlocfilehash: 67574550ba26970189ea53b8e6bdb867fea8549b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707493"
---
# <a name="ihosttaskmanager-interface"></a><span data-ttu-id="b1e7f-103">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b1e7f-103">IHostTaskManager Interface</span></span>

<span data-ttu-id="b1e7f-104">Ortak dil çalışma zamanının (CLR) standart işletim sistemi iş parçacığı veya fiber işlevlerini kullanmak yerine ana bilgisayar aracılığıyla görevlerle çalışmasına izin veren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b1e7f-104">Provides methods that allow the common language runtime (CLR) to work with tasks through the host instead of using the standard operating system threading or fiber functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b1e7f-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b1e7f-105">Methods</span></span>  
  
|<span data-ttu-id="b1e7f-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b1e7f-106">Method</span></span>|<span data-ttu-id="b1e7f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b1e7f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b1e7f-108">BeginDelayAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1e7f-108">BeginDelayAbort Method</span></span>](ihosttaskmanager-begindelayabort-method.md)|<span data-ttu-id="b1e7f-109">Ana bilgisayara, yönetilen kodun geçerli görevin durdurulmayan bir dönem girdiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="b1e7f-109">Notifies the host that managed code is entering a period in which the current task must not be aborted.</span></span>|  
|[<span data-ttu-id="b1e7f-110">BeginThreadAffinity Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1e7f-110">BeginThreadAffinity Method</span></span>](ihosttaskmanager-beginthreadaffinity-method.md)|<span data-ttu-id="b1e7f-111">Yönetilen koda, geçerli görevin başka bir işletim sistemi iş parçacığına taşınmaması gereken bir dönem girmediğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="b1e7f-111">Notifies the host that managed code is entering a period in which the current task must not be moved to another operating system thread.</span></span>|  
|[<span data-ttu-id="b1e7f-112">CallNeedsHostHook Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1e7f-112">CallNeedsHostHook Method</span></span>](ihosttaskmanager-callneedshosthook-method.md)|<span data-ttu-id="b1e7f-113">Ana bilgisayarın, ortak dil çalışma zamanının yönetilmeyen bir işleve belirtilen çağrıyı satır içinde yapıp gerçekleştiremeyeceğini belirtmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="b1e7f-113">Enables the host to specify whether the common language runtime can inline the specified call to an unmanaged function.</span></span>|  
|[<span data-ttu-id="b1e7f-114">CreateTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1e7f-114">CreateTask Method</span></span>](ihosttaskmanager-createtask-method.md)|<span data-ttu-id="b1e7f-115">Konağın yeni bir görev oluşturmasını ister.</span><span class="sxs-lookup"><span data-stu-id="b1e7f-115">Requests that the host create a new task.</span></span>|  
|[<span data-ttu-id="b1e7f-116">EndDelayAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1e7f-116">EndDelayAbort Method</span></span>](ihosttaskmanager-enddelayabort-method.md)|<span data-ttu-id="b1e7f-117">Daha önceki bir çağrısından sonra, yönetilen kodun geçerli görevin durdurulmadıkları dönemden çıkış yaptığını ana bilgisayara bildirir `BeginDelayAbort` .</span><span class="sxs-lookup"><span data-stu-id="b1e7f-117">Notifies the host that managed code is exiting the period in which the current task must not be aborted, following an earlier call to `BeginDelayAbort`.</span></span>|  
|[<span data-ttu-id="b1e7f-118">EndThreadAffinity Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1e7f-118">EndThreadAffinity Method</span></span>](ihosttaskmanager-endthreadaffinity-method.md)|<span data-ttu-id="b1e7f-119">Yönetilen kodun, önceki bir çağrısından sonra geçerli görevin başka bir işletim sistemi iş parçacığına taşınmaması gereken dönemden çıkış olduğunu bildirir `BeginThreadAffinity` .</span><span class="sxs-lookup"><span data-stu-id="b1e7f-119">Notifies the host that managed code is exiting the period in which the current task must not be moved to another operating system thread, following an earlier call to `BeginThreadAffinity`.</span></span>|  
|[<span data-ttu-id="b1e7f-120">EnterRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1e7f-120">EnterRuntime Method</span></span>](ihosttaskmanager-enterruntime-method.md)|<span data-ttu-id="b1e7f-121">Ana bilgisayara platform çağırma yöntemi gibi yönetilmeyen bir yönteme yapılan çağrının, CLR 'ye yürütme denetimi döndürdüğünü bildirir.</span><span class="sxs-lookup"><span data-stu-id="b1e7f-121">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the CLR.</span></span>|  
|[<span data-ttu-id="b1e7f-122">GetCurrentTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1e7f-122">GetCurrentTask Method</span></span>](ihosttaskmanager-getcurrenttask-method.md)|<span data-ttu-id="b1e7f-123">Bu çağrının yapıldığı işletim sistemi iş parçacığında yürütülmekte olan göreve yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="b1e7f-123">Gets an interface pointer to the task that is currently executing on the operating system thread from which this call is made.</span></span>|  
|[<span data-ttu-id="b1e7f-124">GetStackGuarantee Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1e7f-124">GetStackGuarantee Method</span></span>](ihosttaskmanager-getstackguarantee-method.md)|<span data-ttu-id="b1e7f-125">Bir yığın işlemi tamamlandıktan sonra, ancak bir işlemin kapatılmadan önce kullanılabilir olması garanti edilen yığın alanı miktarını alır.</span><span class="sxs-lookup"><span data-stu-id="b1e7f-125">Gets the amount of stack space that is guaranteed to be available after a stack operation completes, but before the closing of a process.</span></span>|  
|[<span data-ttu-id="b1e7f-126">LeaveRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1e7f-126">LeaveRuntime Method</span></span>](ihosttaskmanager-leaveruntime-method.md)|<span data-ttu-id="b1e7f-127">Yönetilmeyen bir işleve çağrı yapmak için yönetilen kodun ilgili olduğu konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="b1e7f-127">Notifies the host that managed code is about to make a call to an unmanaged function.</span></span>|  
|[<span data-ttu-id="b1e7f-128">ReverseEnterRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1e7f-128">ReverseEnterRuntime Method</span></span>](ihosttaskmanager-reverseenterruntime-method.md)|<span data-ttu-id="b1e7f-129">Ana bilgisayara, yönetilmeyen koddan ortak dil çalışma zamanı (CLR) için bir çağrının yapıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="b1e7f-129">Notifies the host that a call is being made into the common language runtime (CLR) from unmanaged code.</span></span>|  
|[<span data-ttu-id="b1e7f-130">ReverseLeaveRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1e7f-130">ReverseLeaveRuntime Method</span></span>](ihosttaskmanager-reverseleaveruntime-method.md)|<span data-ttu-id="b1e7f-131">Denetimin CLR 'den ayrıldığını ve yönetilen koddan çağrılan yönetilmeyen bir işlevi girdiğini ana bilgisayara bildirir.</span><span class="sxs-lookup"><span data-stu-id="b1e7f-131">Notifies the host that control is leaving the CLR and entering an unmanaged function that was, in turn, called from managed code.</span></span>|  
|[<span data-ttu-id="b1e7f-132">SetCLRTaskManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1e7f-132">SetCLRTaskManager Method</span></span>](ihosttaskmanager-setclrtaskmanager-method.md)|<span data-ttu-id="b1e7f-133">Bir konağa, CLR tarafından uygulanan bir [ICLRTaskManager](iclrtaskmanager-interface.md) örneğine yönelik arabirim işaretçisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b1e7f-133">Provides the host with an interface pointer to an [ICLRTaskManager](iclrtaskmanager-interface.md) instance implemented by the CLR.</span></span>|  
|[<span data-ttu-id="b1e7f-134">SetLocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1e7f-134">SetLocale Method</span></span>](ihosttaskmanager-setlocale-method.md)|<span data-ttu-id="b1e7f-135">Konağa CLR 'nin geçerli görevdeki yerel ayarı değiştirdiğinizi bildirir.</span><span class="sxs-lookup"><span data-stu-id="b1e7f-135">Notifies the host that the CLR has changed the locale on the current task.</span></span>|  
|[<span data-ttu-id="b1e7f-136">SetStackGuarantee Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1e7f-136">SetStackGuarantee Method</span></span>](ihosttaskmanager-setstackguarantee-method.md)|<span data-ttu-id="b1e7f-137">Yalnızca iç kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="b1e7f-137">Reserved for internal use only.</span></span>|  
|[<span data-ttu-id="b1e7f-138">SetUILocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1e7f-138">SetUILocale Method</span></span>](ihosttaskmanager-setuilocale-method.md)|<span data-ttu-id="b1e7f-139">Ana bilgisayara, geçerli görevde Kullanıcı arabirimi yerel ayarının değiştirildiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="b1e7f-139">Notifies the host that the user interface locale has been changed on the current task.</span></span>|  
|[<span data-ttu-id="b1e7f-140">Sleep Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1e7f-140">Sleep Method</span></span>](ihosttaskmanager-sleep-method.md)|<span data-ttu-id="b1e7f-141">Ana bilgisayara geçerli görevin uykuya geçmesini bildirir.</span><span class="sxs-lookup"><span data-stu-id="b1e7f-141">Notifies the host that the current task is going to sleep.</span></span>|  
|[<span data-ttu-id="b1e7f-142">SwitchToTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1e7f-142">SwitchToTask Method</span></span>](ihosttaskmanager-switchtotask-method.md)|<span data-ttu-id="b1e7f-143">Ana bilgisayara geçerli görevi geçiş yapmak zorunda olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="b1e7f-143">Notifies the host that it should switch out the current task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1e7f-144">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b1e7f-144">Remarks</span></span>  

 <span data-ttu-id="b1e7f-145">`IHostTaskManager` , yönetilen sunucudan yönetilmeyen koddan ve tam tersi yönde aktarım yapıldığında ve ana bilgisayarın kod yürütmesi sırasında gerçekleştirebileceği belirli eylemleri belirtmek için, CLR 'nin görev oluşturmasına ve yönetmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="b1e7f-145">`IHostTaskManager` allows the CLR to create and manage tasks, to provide hooks for the host to take action when control transfers from managed to unmanaged code and vice versa, and to specify certain actions the host can and cannot take during code execution.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1e7f-146">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b1e7f-146">Requirements</span></span>  

 <span data-ttu-id="b1e7f-147">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1e7f-147">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1e7f-148">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b1e7f-148">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b1e7f-149">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="b1e7f-149">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b1e7f-150">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1e7f-150">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1e7f-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1e7f-151">See also</span></span>

- [<span data-ttu-id="b1e7f-152">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b1e7f-152">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="b1e7f-153">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b1e7f-153">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="b1e7f-154">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b1e7f-154">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="b1e7f-155">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b1e7f-155">Hosting Interfaces</span></span>](hosting-interfaces.md)
