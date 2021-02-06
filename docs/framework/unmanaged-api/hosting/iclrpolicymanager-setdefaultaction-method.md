---
description: ': ICLRPolicyManager:: SetDefaultAction Yöntemi hakkında daha fazla bilgi edinin'
title: ICLRPolicyManager::SetDefaultAction Yöntemi
ms.date: 03/30/2017
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
ms.openlocfilehash: cedf29f6217660493b151e06220158e931385d79
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637371"
---
# <a name="iclrpolicymanagersetdefaultaction-method"></a><span data-ttu-id="5cf6a-103">ICLRPolicyManager::SetDefaultAction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5cf6a-103">ICLRPolicyManager::SetDefaultAction Method</span></span>

<span data-ttu-id="5cf6a-104">Belirtilen işlem gerçekleştiğinde ortak dil çalışma zamanının (CLR) yapması gereken ilke eylemini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5cf6a-104">Specifies the policy action the common language runtime (CLR) should take when the specified operation occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cf6a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5cf6a-105">Syntax</span></span>  
  
```cpp  
HRESULT SetDefaultAction (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5cf6a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5cf6a-106">Parameters</span></span>  

 `operation`  
 <span data-ttu-id="5cf6a-107">'ndaki CLR davranışının özelleştirilmesi gereken eylemi belirten [EClrOperation](eclroperation-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="5cf6a-107">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the action for which CLR behavior should be customized.</span></span>  
  
 `action`  
 <span data-ttu-id="5cf6a-108">'ndaki Her gerçekleştiğinde CLR 'nin yapması gereken ilke eylemini gösteren [EPolicyAction](epolicyaction-enumeration.md) değerlerinden biri `operation` .</span><span class="sxs-lookup"><span data-stu-id="5cf6a-108">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the policy action the CLR should take when `operation` occurs.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5cf6a-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5cf6a-109">Return Value</span></span>  
  
|<span data-ttu-id="5cf6a-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5cf6a-110">HRESULT</span></span>|<span data-ttu-id="5cf6a-111">Description</span><span class="sxs-lookup"><span data-stu-id="5cf6a-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5cf6a-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="5cf6a-112">S_OK</span></span>|<span data-ttu-id="5cf6a-113">`SetDefaultAction` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="5cf6a-113">`SetDefaultAction` returned successfully.</span></span>|  
|<span data-ttu-id="5cf6a-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5cf6a-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5cf6a-115">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="5cf6a-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5cf6a-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5cf6a-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5cf6a-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="5cf6a-117">The call timed out.</span></span>|  
|<span data-ttu-id="5cf6a-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5cf6a-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5cf6a-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="5cf6a-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5cf6a-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5cf6a-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5cf6a-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="5cf6a-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5cf6a-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5cf6a-122">E_FAIL</span></span>|<span data-ttu-id="5cf6a-123">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="5cf6a-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5cf6a-124">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="5cf6a-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5cf6a-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="5cf6a-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5cf6a-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="5cf6a-126">E_INVALIDARG</span></span>|<span data-ttu-id="5cf6a-127">İçin geçersiz bir `action` `operation` değer belirtildi veya geçersiz bir değer sağlandı `operation` .</span><span class="sxs-lookup"><span data-stu-id="5cf6a-127">An invalid `action` was specified for the `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5cf6a-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5cf6a-128">Remarks</span></span>  

 <span data-ttu-id="5cf6a-129">Tüm ilke eylemi değerleri CLR işlemleri için varsayılan davranış olarak belirtilemez.</span><span class="sxs-lookup"><span data-stu-id="5cf6a-129">Not all policy action values can be specified as the default behavior for CLR operations.</span></span> <span data-ttu-id="5cf6a-130">`SetDefaultAction` Genellikle, davranışı yükseltmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5cf6a-130">`SetDefaultAction` can typically be used only to escalate behavior.</span></span> <span data-ttu-id="5cf6a-131">Örneğin, bir ana bilgisayar, iş parçacığı iptal işlemini işlenmemiş iş parçacığı iptal edilecek olarak belirtebilir, ancak tersini belirtemez.</span><span class="sxs-lookup"><span data-stu-id="5cf6a-131">For example, a host can specify that thread aborts be turned into rude thread aborts, but cannot specify the opposite.</span></span> <span data-ttu-id="5cf6a-132">Aşağıdaki tabloda `action` olası her bir değer için geçerli değerler açıklanmaktadır `operation` .</span><span class="sxs-lookup"><span data-stu-id="5cf6a-132">The table below describes the valid `action` values for each possible `operation` value.</span></span>  
  
|<span data-ttu-id="5cf6a-133">Değer `operation`</span><span class="sxs-lookup"><span data-stu-id="5cf6a-133">Value for `operation`</span></span>|<span data-ttu-id="5cf6a-134">İçin geçerli değerler `action`</span><span class="sxs-lookup"><span data-stu-id="5cf6a-134">Valid values for `action`</span></span>|  
|---------------------------|-------------------------------|  
|<span data-ttu-id="5cf6a-135">OPR_ThreadAbort</span><span class="sxs-lookup"><span data-stu-id="5cf6a-135">OPR_ThreadAbort</span></span>|<span data-ttu-id="5cf6a-136">-eAbortThread</span><span class="sxs-lookup"><span data-stu-id="5cf6a-136">-   eAbortThread</span></span><br /><span data-ttu-id="5cf6a-137">-eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="5cf6a-137">-   eRudeAbortThread</span></span><br /><span data-ttu-id="5cf6a-138">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="5cf6a-138">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="5cf6a-139">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="5cf6a-139">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="5cf6a-140">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="5cf6a-140">-   eExitProcess</span></span><br /><span data-ttu-id="5cf6a-141">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="5cf6a-141">-   eFastExitProcess</span></span><br /><span data-ttu-id="5cf6a-142">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="5cf6a-142">-   eRudeExitProcess</span></span><br /><span data-ttu-id="5cf6a-143">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="5cf6a-143">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="5cf6a-144">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="5cf6a-144">OPR_ThreadRudeAbortInNonCriticalRegion</span></span><br /><br /> <span data-ttu-id="5cf6a-145">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="5cf6a-145">OPR_ThreadRudeAbortInCriticalRegion</span></span>|<span data-ttu-id="5cf6a-146">-eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="5cf6a-146">-   eRudeAbortThread</span></span><br /><span data-ttu-id="5cf6a-147">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="5cf6a-147">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="5cf6a-148">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="5cf6a-148">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="5cf6a-149">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="5cf6a-149">-   eExitProcess</span></span><br /><span data-ttu-id="5cf6a-150">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="5cf6a-150">-   eFastExitProcess</span></span><br /><span data-ttu-id="5cf6a-151">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="5cf6a-151">-   eRudeExitProcess</span></span><br /><span data-ttu-id="5cf6a-152">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="5cf6a-152">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="5cf6a-153">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="5cf6a-153">OPR_AppDomainUnload</span></span>|<span data-ttu-id="5cf6a-154">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="5cf6a-154">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="5cf6a-155">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="5cf6a-155">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="5cf6a-156">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="5cf6a-156">-   eExitProcess</span></span><br /><span data-ttu-id="5cf6a-157">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="5cf6a-157">-   eFastExitProcess</span></span><br /><span data-ttu-id="5cf6a-158">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="5cf6a-158">-   eRudeExitProcess</span></span><br /><span data-ttu-id="5cf6a-159">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="5cf6a-159">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="5cf6a-160">OPR_AppDomainRudeUnload</span><span class="sxs-lookup"><span data-stu-id="5cf6a-160">OPR_AppDomainRudeUnload</span></span>|<span data-ttu-id="5cf6a-161">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="5cf6a-161">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="5cf6a-162">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="5cf6a-162">-   eExitProcess</span></span><br /><span data-ttu-id="5cf6a-163">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="5cf6a-163">-   eFastExitProcess</span></span><br /><span data-ttu-id="5cf6a-164">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="5cf6a-164">-   eRudeExitProcess</span></span><br /><span data-ttu-id="5cf6a-165">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="5cf6a-165">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="5cf6a-166">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="5cf6a-166">OPR_ProcessExit</span></span>|<span data-ttu-id="5cf6a-167">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="5cf6a-167">-   eExitProcess</span></span><br /><span data-ttu-id="5cf6a-168">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="5cf6a-168">-   eFastExitProcess</span></span><br /><span data-ttu-id="5cf6a-169">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="5cf6a-169">-   eRudeExitProcess</span></span><br /><span data-ttu-id="5cf6a-170">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="5cf6a-170">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="5cf6a-171">OPR_FinalizerRun</span><span class="sxs-lookup"><span data-stu-id="5cf6a-171">OPR_FinalizerRun</span></span>|<span data-ttu-id="5cf6a-172">-eNoAction</span><span class="sxs-lookup"><span data-stu-id="5cf6a-172">-   eNoAction</span></span><br /><span data-ttu-id="5cf6a-173">-eAbortThread</span><span class="sxs-lookup"><span data-stu-id="5cf6a-173">-   eAbortThread</span></span><br /><span data-ttu-id="5cf6a-174">-eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="5cf6a-174">-   eRudeAbortThread</span></span><br /><span data-ttu-id="5cf6a-175">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="5cf6a-175">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="5cf6a-176">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="5cf6a-176">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="5cf6a-177">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="5cf6a-177">-   eExitProcess</span></span><br /><span data-ttu-id="5cf6a-178">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="5cf6a-178">-   eFastExitProcess</span></span><br /><span data-ttu-id="5cf6a-179">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="5cf6a-179">-   eRudeExitProcess</span></span><br /><span data-ttu-id="5cf6a-180">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="5cf6a-180">-   eDisableRuntime</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5cf6a-181">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5cf6a-181">Requirements</span></span>  

 <span data-ttu-id="5cf6a-182">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5cf6a-182">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cf6a-183">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5cf6a-183">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5cf6a-184">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="5cf6a-184">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5cf6a-185">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cf6a-185">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cf6a-186">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5cf6a-186">See also</span></span>

- [<span data-ttu-id="5cf6a-187">EClrOperation Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="5cf6a-187">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="5cf6a-188">EPolicyAction Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="5cf6a-188">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="5cf6a-189">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5cf6a-189">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
