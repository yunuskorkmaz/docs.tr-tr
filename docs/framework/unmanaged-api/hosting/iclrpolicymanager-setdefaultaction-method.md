---
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
ms.openlocfilehash: 93070690ea6b30b22949953f1ed0b8c5b1e92764
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732490"
---
# <a name="iclrpolicymanagersetdefaultaction-method"></a><span data-ttu-id="7c2b4-102">ICLRPolicyManager::SetDefaultAction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7c2b4-102">ICLRPolicyManager::SetDefaultAction Method</span></span>

<span data-ttu-id="7c2b4-103">Belirtilen işlem gerçekleştiğinde ortak dil çalışma zamanının (CLR) yapması gereken ilke eylemini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7c2b4-103">Specifies the policy action the common language runtime (CLR) should take when the specified operation occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c2b4-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7c2b4-104">Syntax</span></span>  
  
```cpp  
HRESULT SetDefaultAction (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c2b4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7c2b4-105">Parameters</span></span>  

 `operation`  
 <span data-ttu-id="7c2b4-106">'ndaki CLR davranışının özelleştirilmesi gereken eylemi belirten [EClrOperation](eclroperation-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="7c2b4-106">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the action for which CLR behavior should be customized.</span></span>  
  
 `action`  
 <span data-ttu-id="7c2b4-107">'ndaki Her gerçekleştiğinde CLR 'nin yapması gereken ilke eylemini gösteren [EPolicyAction](epolicyaction-enumeration.md) değerlerinden biri `operation` .</span><span class="sxs-lookup"><span data-stu-id="7c2b4-107">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the policy action the CLR should take when `operation` occurs.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7c2b4-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7c2b4-108">Return Value</span></span>  
  
|<span data-ttu-id="7c2b4-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7c2b4-109">HRESULT</span></span>|<span data-ttu-id="7c2b4-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7c2b4-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7c2b4-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="7c2b4-111">S_OK</span></span>|<span data-ttu-id="7c2b4-112">`SetDefaultAction` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="7c2b4-112">`SetDefaultAction` returned successfully.</span></span>|  
|<span data-ttu-id="7c2b4-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7c2b4-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7c2b4-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="7c2b4-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7c2b4-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7c2b4-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7c2b4-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="7c2b4-116">The call timed out.</span></span>|  
|<span data-ttu-id="7c2b4-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7c2b4-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7c2b4-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="7c2b4-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7c2b4-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7c2b4-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7c2b4-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="7c2b4-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7c2b4-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7c2b4-121">E_FAIL</span></span>|<span data-ttu-id="7c2b4-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="7c2b4-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7c2b4-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="7c2b4-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7c2b4-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="7c2b4-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7c2b4-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="7c2b4-125">E_INVALIDARG</span></span>|<span data-ttu-id="7c2b4-126">İçin geçersiz bir `action` `operation` değer belirtildi veya geçersiz bir değer sağlandı `operation` .</span><span class="sxs-lookup"><span data-stu-id="7c2b4-126">An invalid `action` was specified for the `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c2b4-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7c2b4-127">Remarks</span></span>  

 <span data-ttu-id="7c2b4-128">Tüm ilke eylemi değerleri CLR işlemleri için varsayılan davranış olarak belirtilemez.</span><span class="sxs-lookup"><span data-stu-id="7c2b4-128">Not all policy action values can be specified as the default behavior for CLR operations.</span></span> <span data-ttu-id="7c2b4-129">`SetDefaultAction` Genellikle, davranışı yükseltmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7c2b4-129">`SetDefaultAction` can typically be used only to escalate behavior.</span></span> <span data-ttu-id="7c2b4-130">Örneğin, bir ana bilgisayar, iş parçacığı iptal işlemini işlenmemiş iş parçacığı iptal edilecek olarak belirtebilir, ancak tersini belirtemez.</span><span class="sxs-lookup"><span data-stu-id="7c2b4-130">For example, a host can specify that thread aborts be turned into rude thread aborts, but cannot specify the opposite.</span></span> <span data-ttu-id="7c2b4-131">Aşağıdaki tabloda `action` olası her bir değer için geçerli değerler açıklanmaktadır `operation` .</span><span class="sxs-lookup"><span data-stu-id="7c2b4-131">The table below describes the valid `action` values for each possible `operation` value.</span></span>  
  
|<span data-ttu-id="7c2b4-132">Değer `operation`</span><span class="sxs-lookup"><span data-stu-id="7c2b4-132">Value for `operation`</span></span>|<span data-ttu-id="7c2b4-133">İçin geçerli değerler `action`</span><span class="sxs-lookup"><span data-stu-id="7c2b4-133">Valid values for `action`</span></span>|  
|---------------------------|-------------------------------|  
|<span data-ttu-id="7c2b4-134">OPR_ThreadAbort</span><span class="sxs-lookup"><span data-stu-id="7c2b4-134">OPR_ThreadAbort</span></span>|<span data-ttu-id="7c2b4-135">-eAbortThread</span><span class="sxs-lookup"><span data-stu-id="7c2b4-135">-   eAbortThread</span></span><br /><span data-ttu-id="7c2b4-136">-eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="7c2b4-136">-   eRudeAbortThread</span></span><br /><span data-ttu-id="7c2b4-137">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="7c2b4-137">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="7c2b4-138">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="7c2b4-138">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="7c2b4-139">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="7c2b4-139">-   eExitProcess</span></span><br /><span data-ttu-id="7c2b4-140">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="7c2b4-140">-   eFastExitProcess</span></span><br /><span data-ttu-id="7c2b4-141">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="7c2b4-141">-   eRudeExitProcess</span></span><br /><span data-ttu-id="7c2b4-142">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="7c2b4-142">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="7c2b4-143">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="7c2b4-143">OPR_ThreadRudeAbortInNonCriticalRegion</span></span><br /><br /> <span data-ttu-id="7c2b4-144">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="7c2b4-144">OPR_ThreadRudeAbortInCriticalRegion</span></span>|<span data-ttu-id="7c2b4-145">-eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="7c2b4-145">-   eRudeAbortThread</span></span><br /><span data-ttu-id="7c2b4-146">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="7c2b4-146">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="7c2b4-147">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="7c2b4-147">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="7c2b4-148">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="7c2b4-148">-   eExitProcess</span></span><br /><span data-ttu-id="7c2b4-149">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="7c2b4-149">-   eFastExitProcess</span></span><br /><span data-ttu-id="7c2b4-150">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="7c2b4-150">-   eRudeExitProcess</span></span><br /><span data-ttu-id="7c2b4-151">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="7c2b4-151">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="7c2b4-152">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="7c2b4-152">OPR_AppDomainUnload</span></span>|<span data-ttu-id="7c2b4-153">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="7c2b4-153">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="7c2b4-154">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="7c2b4-154">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="7c2b4-155">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="7c2b4-155">-   eExitProcess</span></span><br /><span data-ttu-id="7c2b4-156">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="7c2b4-156">-   eFastExitProcess</span></span><br /><span data-ttu-id="7c2b4-157">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="7c2b4-157">-   eRudeExitProcess</span></span><br /><span data-ttu-id="7c2b4-158">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="7c2b4-158">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="7c2b4-159">OPR_AppDomainRudeUnload</span><span class="sxs-lookup"><span data-stu-id="7c2b4-159">OPR_AppDomainRudeUnload</span></span>|<span data-ttu-id="7c2b4-160">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="7c2b4-160">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="7c2b4-161">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="7c2b4-161">-   eExitProcess</span></span><br /><span data-ttu-id="7c2b4-162">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="7c2b4-162">-   eFastExitProcess</span></span><br /><span data-ttu-id="7c2b4-163">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="7c2b4-163">-   eRudeExitProcess</span></span><br /><span data-ttu-id="7c2b4-164">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="7c2b4-164">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="7c2b4-165">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="7c2b4-165">OPR_ProcessExit</span></span>|<span data-ttu-id="7c2b4-166">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="7c2b4-166">-   eExitProcess</span></span><br /><span data-ttu-id="7c2b4-167">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="7c2b4-167">-   eFastExitProcess</span></span><br /><span data-ttu-id="7c2b4-168">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="7c2b4-168">-   eRudeExitProcess</span></span><br /><span data-ttu-id="7c2b4-169">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="7c2b4-169">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="7c2b4-170">OPR_FinalizerRun</span><span class="sxs-lookup"><span data-stu-id="7c2b4-170">OPR_FinalizerRun</span></span>|<span data-ttu-id="7c2b4-171">-eNoAction</span><span class="sxs-lookup"><span data-stu-id="7c2b4-171">-   eNoAction</span></span><br /><span data-ttu-id="7c2b4-172">-eAbortThread</span><span class="sxs-lookup"><span data-stu-id="7c2b4-172">-   eAbortThread</span></span><br /><span data-ttu-id="7c2b4-173">-eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="7c2b4-173">-   eRudeAbortThread</span></span><br /><span data-ttu-id="7c2b4-174">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="7c2b4-174">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="7c2b4-175">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="7c2b4-175">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="7c2b4-176">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="7c2b4-176">-   eExitProcess</span></span><br /><span data-ttu-id="7c2b4-177">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="7c2b4-177">-   eFastExitProcess</span></span><br /><span data-ttu-id="7c2b4-178">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="7c2b4-178">-   eRudeExitProcess</span></span><br /><span data-ttu-id="7c2b4-179">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="7c2b4-179">-   eDisableRuntime</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7c2b4-180">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7c2b4-180">Requirements</span></span>  

 <span data-ttu-id="7c2b4-181">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c2b4-181">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c2b4-182">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7c2b4-182">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7c2b4-183">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="7c2b4-183">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7c2b4-184">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c2b4-184">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c2b4-185">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7c2b4-185">See also</span></span>

- [<span data-ttu-id="7c2b4-186">EClrOperation Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7c2b4-186">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="7c2b4-187">EPolicyAction Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7c2b4-187">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="7c2b4-188">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7c2b4-188">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
