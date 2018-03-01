---
title: "ICLRPolicyManager::SetDefaultAction Yöntemi"
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
- ICLRPolicyManager.SetDefaultAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetDefaultAction
helpviewer_keywords:
- SetDefaultAction method [.NET Framework hosting]
- ICLRPolicyManager::SetDefaultAction method [.NET Framework hosting]
ms.assetid: f9411e7a-27df-451f-9f6c-d643d6a7a7ce
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 751853aaf4322c15b44bb9b912d293a081c24ba8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrpolicymanagersetdefaultaction-method"></a><span data-ttu-id="d5af4-102">ICLRPolicyManager::SetDefaultAction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d5af4-102">ICLRPolicyManager::SetDefaultAction Method</span></span>
<span data-ttu-id="d5af4-103">Ortak dil çalışma zamanı (CLR) belirtilen işlem oluştuğunda gerçekleştirmesi gereken ilke eylemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="d5af4-103">Specifies the policy action the common language runtime (CLR) should take when the specified operation occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5af4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d5af4-104">Syntax</span></span>  
  
```  
HRESULT SetDefaultAction (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d5af4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d5af4-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="d5af4-106">[in] Aşağıdakilerden birini [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) için hangi CLR davranışı özelleştirilmek eylemini belirten değer.</span><span class="sxs-lookup"><span data-stu-id="d5af4-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the action for which CLR behavior should be customized.</span></span>  
  
 `action`  
 <span data-ttu-id="d5af4-107">[in] Aşağıdakilerden birini [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) değerleri, CLR İlkesi eylem ne zaman almalıdır belirten `operation` oluşur.</span><span class="sxs-lookup"><span data-stu-id="d5af4-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action the CLR should take when `operation` occurs.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d5af4-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d5af4-108">Return Value</span></span>  
  
|<span data-ttu-id="d5af4-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d5af4-109">HRESULT</span></span>|<span data-ttu-id="d5af4-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d5af4-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d5af4-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d5af4-111">S_OK</span></span>|<span data-ttu-id="d5af4-112">`SetDefaultAction`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="d5af4-112">`SetDefaultAction` returned successfully.</span></span>|  
|<span data-ttu-id="d5af4-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d5af4-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d5af4-114">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="d5af4-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d5af4-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d5af4-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d5af4-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="d5af4-116">The call timed out.</span></span>|  
|<span data-ttu-id="d5af4-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d5af4-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d5af4-118">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="d5af4-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d5af4-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d5af4-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d5af4-120">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="d5af4-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d5af4-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d5af4-121">E_FAIL</span></span>|<span data-ttu-id="d5af4-122">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="d5af4-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d5af4-123">CLR, artık bir yöntem E_FAIL döndükten sonra işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d5af4-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d5af4-124">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="d5af4-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d5af4-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="d5af4-125">E_INVALIDARG</span></span>|<span data-ttu-id="d5af4-126">Geçersiz bir `action` için belirtilen `operation`, ya da geçersiz bir değer için sağlanan `operation`.</span><span class="sxs-lookup"><span data-stu-id="d5af4-126">An invalid `action` was specified for the `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5af4-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d5af4-127">Remarks</span></span>  
 <span data-ttu-id="d5af4-128">Tüm ilke eylem değerlerini CLR işlemleri için varsayılan davranış olarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="d5af4-128">Not all policy action values can be specified as the default behavior for CLR operations.</span></span> <span data-ttu-id="d5af4-129">`SetDefaultAction`genellikle yalnızca davranışı ilerletmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d5af4-129">`SetDefaultAction` can typically be used only to escalate behavior.</span></span> <span data-ttu-id="d5af4-130">Örneğin, bir ana iş parçacığı iptalleri içine utangaç açılması belirtebilirsiniz iş parçacığı iptalleri ancak karşıtı belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5af4-130">For example, a host can specify that thread aborts be turned into rude thread aborts, but cannot specify the opposite.</span></span> <span data-ttu-id="d5af4-131">Aşağıdaki tabloda geçerli açıklanmaktadır `action` her olası değerlerini `operation` değeri.</span><span class="sxs-lookup"><span data-stu-id="d5af4-131">The table below describes the valid `action` values for each possible `operation` value.</span></span>  
  
|<span data-ttu-id="d5af4-132">Değeri`operation`</span><span class="sxs-lookup"><span data-stu-id="d5af4-132">Value for `operation`</span></span>|<span data-ttu-id="d5af4-133">İçin geçerli değerler`action`</span><span class="sxs-lookup"><span data-stu-id="d5af4-133">Valid values for `action`</span></span>|  
|---------------------------|-------------------------------|  
|<span data-ttu-id="d5af4-134">OPR_ThreadAbort</span><span class="sxs-lookup"><span data-stu-id="d5af4-134">OPR_ThreadAbort</span></span>|<span data-ttu-id="d5af4-135">-eAbortThread</span><span class="sxs-lookup"><span data-stu-id="d5af4-135">-   eAbortThread</span></span><br /><span data-ttu-id="d5af4-136">-eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="d5af4-136">-   eRudeAbortThread</span></span><br /><span data-ttu-id="d5af4-137">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="d5af4-137">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="d5af4-138">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="d5af4-138">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="d5af4-139">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="d5af4-139">-   eExitProcess</span></span><br /><span data-ttu-id="d5af4-140">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="d5af4-140">-   eFastExitProcess</span></span><br /><span data-ttu-id="d5af4-141">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="d5af4-141">-   eRudeExitProcess</span></span><br /><span data-ttu-id="d5af4-142">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="d5af4-142">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="d5af4-143">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="d5af4-143">OPR_ThreadRudeAbortInNonCriticalRegion</span></span><br /><br /> <span data-ttu-id="d5af4-144">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="d5af4-144">OPR_ThreadRudeAbortInCriticalRegion</span></span>|<span data-ttu-id="d5af4-145">-eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="d5af4-145">-   eRudeAbortThread</span></span><br /><span data-ttu-id="d5af4-146">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="d5af4-146">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="d5af4-147">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="d5af4-147">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="d5af4-148">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="d5af4-148">-   eExitProcess</span></span><br /><span data-ttu-id="d5af4-149">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="d5af4-149">-   eFastExitProcess</span></span><br /><span data-ttu-id="d5af4-150">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="d5af4-150">-   eRudeExitProcess</span></span><br /><span data-ttu-id="d5af4-151">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="d5af4-151">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="d5af4-152">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="d5af4-152">OPR_AppDomainUnload</span></span>|<span data-ttu-id="d5af4-153">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="d5af4-153">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="d5af4-154">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="d5af4-154">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="d5af4-155">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="d5af4-155">-   eExitProcess</span></span><br /><span data-ttu-id="d5af4-156">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="d5af4-156">-   eFastExitProcess</span></span><br /><span data-ttu-id="d5af4-157">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="d5af4-157">-   eRudeExitProcess</span></span><br /><span data-ttu-id="d5af4-158">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="d5af4-158">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="d5af4-159">OPR_AppDomainRudeUnload</span><span class="sxs-lookup"><span data-stu-id="d5af4-159">OPR_AppDomainRudeUnload</span></span>|<span data-ttu-id="d5af4-160">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="d5af4-160">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="d5af4-161">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="d5af4-161">-   eExitProcess</span></span><br /><span data-ttu-id="d5af4-162">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="d5af4-162">-   eFastExitProcess</span></span><br /><span data-ttu-id="d5af4-163">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="d5af4-163">-   eRudeExitProcess</span></span><br /><span data-ttu-id="d5af4-164">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="d5af4-164">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="d5af4-165">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="d5af4-165">OPR_ProcessExit</span></span>|<span data-ttu-id="d5af4-166">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="d5af4-166">-   eExitProcess</span></span><br /><span data-ttu-id="d5af4-167">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="d5af4-167">-   eFastExitProcess</span></span><br /><span data-ttu-id="d5af4-168">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="d5af4-168">-   eRudeExitProcess</span></span><br /><span data-ttu-id="d5af4-169">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="d5af4-169">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="d5af4-170">OPR_FinalizerRun</span><span class="sxs-lookup"><span data-stu-id="d5af4-170">OPR_FinalizerRun</span></span>|<span data-ttu-id="d5af4-171">-eNoAction</span><span class="sxs-lookup"><span data-stu-id="d5af4-171">-   eNoAction</span></span><br /><span data-ttu-id="d5af4-172">-eAbortThread</span><span class="sxs-lookup"><span data-stu-id="d5af4-172">-   eAbortThread</span></span><br /><span data-ttu-id="d5af4-173">-eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="d5af4-173">-   eRudeAbortThread</span></span><br /><span data-ttu-id="d5af4-174">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="d5af4-174">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="d5af4-175">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="d5af4-175">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="d5af4-176">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="d5af4-176">-   eExitProcess</span></span><br /><span data-ttu-id="d5af4-177">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="d5af4-177">-   eFastExitProcess</span></span><br /><span data-ttu-id="d5af4-178">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="d5af4-178">-   eRudeExitProcess</span></span><br /><span data-ttu-id="d5af4-179">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="d5af4-179">-   eDisableRuntime</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d5af4-180">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d5af4-180">Requirements</span></span>  
 <span data-ttu-id="d5af4-181">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5af4-181">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5af4-182">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d5af4-182">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d5af4-183">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d5af4-183">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d5af4-184">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5af4-184">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5af4-185">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d5af4-185">See Also</span></span>  
 [<span data-ttu-id="d5af4-186">EClrOperation Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="d5af4-186">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="d5af4-187">EPolicyAction Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="d5af4-187">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="d5af4-188">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d5af4-188">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
