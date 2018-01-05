---
title: "ICLRPolicyManager::SetActionOnFailure Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRPolicyManager.SetActionOnFailure
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRPolicyManager::SetActionOnFailure
helpviewer_keywords:
- SetActionOnFailure method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnFailure method [.NET Framework hosting]
ms.assetid: 4664033f-db97-4388-b988-2ec470796e58
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4440b36485ed900b5e64adcead2525dbb7d5206e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a><span data-ttu-id="c93de-102">ICLRPolicyManager::SetActionOnFailure Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c93de-102">ICLRPolicyManager::SetActionOnFailure Method</span></span>
<span data-ttu-id="c93de-103">Belirtilen bir hata oluşursa, ortak dil çalışma zamanı (CLR) gerçekleştirmesi gereken ilke eylemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="c93de-103">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c93de-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c93de-104">Syntax</span></span>  
  
```  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c93de-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c93de-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="c93de-106">[in] Aşağıdakilerden birini [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) nedenine ilişkin hata türü belirten değerleri.</span><span class="sxs-lookup"><span data-stu-id="c93de-106">[in] One of the [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values, indicating the type of failure for which to take action.</span></span>  
  
 `action`  
 <span data-ttu-id="c93de-107">[in] Aşağıdakilerden birini [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) belirten bir hata oluşursa, eylemin gerçekleştirilmesine değerleri.</span><span class="sxs-lookup"><span data-stu-id="c93de-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action to be taken when a failure occurs.</span></span> <span data-ttu-id="c93de-108">Desteklenen değerler listesi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="c93de-108">For a list of supported values, see the Remarks section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c93de-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c93de-109">Return Value</span></span>  
  
|<span data-ttu-id="c93de-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c93de-110">HRESULT</span></span>|<span data-ttu-id="c93de-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c93de-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c93de-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="c93de-112">S_OK</span></span>|<span data-ttu-id="c93de-113">`SetActionOnFailure`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="c93de-113">`SetActionOnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="c93de-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c93de-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c93de-115">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="c93de-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c93de-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c93de-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c93de-117">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="c93de-117">The call timed out.</span></span>|  
|<span data-ttu-id="c93de-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c93de-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c93de-119">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="c93de-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c93de-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c93de-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c93de-121">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="c93de-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c93de-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c93de-122">E_FAIL</span></span>|<span data-ttu-id="c93de-123">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="c93de-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c93de-124">CLR, artık bir yöntem E_FAIL döndükten sonra işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c93de-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c93de-125">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="c93de-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c93de-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c93de-126">E_INVALIDARG</span></span>|<span data-ttu-id="c93de-127">Belirtilen işlem için bir ilke eylemi ayarlanamaz veya işlem için geçersiz ilke eylem belirtildi.</span><span class="sxs-lookup"><span data-stu-id="c93de-127">A policy action cannot be set for the specified operation, or an invalid policy action was specified for the operation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c93de-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c93de-128">Remarks</span></span>  
 <span data-ttu-id="c93de-129">Bellek gibi bir kaynak ayırma başarısız olduğunda varsayılan olarak, CLR özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c93de-129">By default, the CLR throws an exception when it fails to allocate a resource such as memory.</span></span> <span data-ttu-id="c93de-130">`SetActionOnFailure`hata yapması üzerine yapılacak İlkesi eylem belirterek bu davranışı geçersiz kılmak için ana sağlar.</span><span class="sxs-lookup"><span data-stu-id="c93de-130">`SetActionOnFailure` allows the host to override this behavior by specifying the policy action to take upon failure.</span></span> <span data-ttu-id="c93de-131">Aşağıdaki tablo bileşimlerine gösterir [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) ve [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) desteklenen değerler.</span><span class="sxs-lookup"><span data-stu-id="c93de-131">The following table shows the combinations of [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) and [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values that are supported.</span></span> <span data-ttu-id="c93de-132">(FAIL_ öneki gelen atlanmış [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) değerleri.)</span><span class="sxs-lookup"><span data-stu-id="c93de-132">(The FAIL_ prefix is omitted from [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values.)</span></span>  
  
||<span data-ttu-id="c93de-133">NonCriticalResource</span><span class="sxs-lookup"><span data-stu-id="c93de-133">NonCriticalResource</span></span>|<span data-ttu-id="c93de-134">CriticalResource</span><span class="sxs-lookup"><span data-stu-id="c93de-134">CriticalResource</span></span>|<span data-ttu-id="c93de-135">FatalRuntime</span><span class="sxs-lookup"><span data-stu-id="c93de-135">FatalRuntime</span></span>|<span data-ttu-id="c93de-136">OrphanedLock</span><span class="sxs-lookup"><span data-stu-id="c93de-136">OrphanedLock</span></span>|<span data-ttu-id="c93de-137">StackOverflow</span><span class="sxs-lookup"><span data-stu-id="c93de-137">StackOverflow</span></span>|<span data-ttu-id="c93de-138">AccessViolation</span><span class="sxs-lookup"><span data-stu-id="c93de-138">AccessViolation</span></span>|<span data-ttu-id="c93de-139">CodeContract</span><span class="sxs-lookup"><span data-stu-id="c93de-139">CodeContract</span></span>|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|<span data-ttu-id="c93de-140">X</span><span class="sxs-lookup"><span data-stu-id="c93de-140">X</span></span>|<span data-ttu-id="c93de-141">X</span><span class="sxs-lookup"><span data-stu-id="c93de-141">X</span></span>||||<span data-ttu-id="c93de-142">Yok</span><span class="sxs-lookup"><span data-stu-id="c93de-142">N/A</span></span>||  
|<span data-ttu-id="c93de-143">eThrowException</span><span class="sxs-lookup"><span data-stu-id="c93de-143">eThrowException</span></span>|<span data-ttu-id="c93de-144">X</span><span class="sxs-lookup"><span data-stu-id="c93de-144">X</span></span>|<span data-ttu-id="c93de-145">X</span><span class="sxs-lookup"><span data-stu-id="c93de-145">X</span></span>||||<span data-ttu-id="c93de-146">Yok</span><span class="sxs-lookup"><span data-stu-id="c93de-146">N/A</span></span>||  
|`eAbortThread`|<span data-ttu-id="c93de-147">X</span><span class="sxs-lookup"><span data-stu-id="c93de-147">X</span></span>|<span data-ttu-id="c93de-148">X</span><span class="sxs-lookup"><span data-stu-id="c93de-148">X</span></span>||||<span data-ttu-id="c93de-149">Yok</span><span class="sxs-lookup"><span data-stu-id="c93de-149">N/A</span></span>|<span data-ttu-id="c93de-150">X</span><span class="sxs-lookup"><span data-stu-id="c93de-150">X</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="c93de-151">X</span><span class="sxs-lookup"><span data-stu-id="c93de-151">X</span></span>|<span data-ttu-id="c93de-152">X</span><span class="sxs-lookup"><span data-stu-id="c93de-152">X</span></span>||||<span data-ttu-id="c93de-153">Yok</span><span class="sxs-lookup"><span data-stu-id="c93de-153">N/A</span></span>|<span data-ttu-id="c93de-154">X</span><span class="sxs-lookup"><span data-stu-id="c93de-154">X</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="c93de-155">X</span><span class="sxs-lookup"><span data-stu-id="c93de-155">X</span></span>|<span data-ttu-id="c93de-156">X</span><span class="sxs-lookup"><span data-stu-id="c93de-156">X</span></span>||<span data-ttu-id="c93de-157">X</span><span class="sxs-lookup"><span data-stu-id="c93de-157">X</span></span>||<span data-ttu-id="c93de-158">Yok</span><span class="sxs-lookup"><span data-stu-id="c93de-158">N/A</span></span>|<span data-ttu-id="c93de-159">X</span><span class="sxs-lookup"><span data-stu-id="c93de-159">X</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="c93de-160">X</span><span class="sxs-lookup"><span data-stu-id="c93de-160">X</span></span>|<span data-ttu-id="c93de-161">X</span><span class="sxs-lookup"><span data-stu-id="c93de-161">X</span></span>||<span data-ttu-id="c93de-162">X</span><span class="sxs-lookup"><span data-stu-id="c93de-162">X</span></span>|<span data-ttu-id="c93de-163">X</span><span class="sxs-lookup"><span data-stu-id="c93de-163">X</span></span>|<span data-ttu-id="c93de-164">Yok</span><span class="sxs-lookup"><span data-stu-id="c93de-164">N/A</span></span>|<span data-ttu-id="c93de-165">X</span><span class="sxs-lookup"><span data-stu-id="c93de-165">X</span></span>|  
|`eExitProcess`|<span data-ttu-id="c93de-166">X</span><span class="sxs-lookup"><span data-stu-id="c93de-166">X</span></span>|<span data-ttu-id="c93de-167">X</span><span class="sxs-lookup"><span data-stu-id="c93de-167">X</span></span>||<span data-ttu-id="c93de-168">X</span><span class="sxs-lookup"><span data-stu-id="c93de-168">X</span></span>|<span data-ttu-id="c93de-169">X</span><span class="sxs-lookup"><span data-stu-id="c93de-169">X</span></span>|<span data-ttu-id="c93de-170">Yok</span><span class="sxs-lookup"><span data-stu-id="c93de-170">N/A</span></span>|<span data-ttu-id="c93de-171">X</span><span class="sxs-lookup"><span data-stu-id="c93de-171">X</span></span>|  
|<span data-ttu-id="c93de-172">eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="c93de-172">eFastExitProcess</span></span>|<span data-ttu-id="c93de-173">X</span><span class="sxs-lookup"><span data-stu-id="c93de-173">X</span></span>|<span data-ttu-id="c93de-174">X</span><span class="sxs-lookup"><span data-stu-id="c93de-174">X</span></span>||<span data-ttu-id="c93de-175">X</span><span class="sxs-lookup"><span data-stu-id="c93de-175">X</span></span>|<span data-ttu-id="c93de-176">X</span><span class="sxs-lookup"><span data-stu-id="c93de-176">X</span></span>|<span data-ttu-id="c93de-177">Yok</span><span class="sxs-lookup"><span data-stu-id="c93de-177">N/A</span></span>||  
|`eRudeExitProcess`|<span data-ttu-id="c93de-178">X</span><span class="sxs-lookup"><span data-stu-id="c93de-178">X</span></span>|<span data-ttu-id="c93de-179">X</span><span class="sxs-lookup"><span data-stu-id="c93de-179">X</span></span>|<span data-ttu-id="c93de-180">X</span><span class="sxs-lookup"><span data-stu-id="c93de-180">X</span></span>|<span data-ttu-id="c93de-181">X</span><span class="sxs-lookup"><span data-stu-id="c93de-181">X</span></span>|<span data-ttu-id="c93de-182">X</span><span class="sxs-lookup"><span data-stu-id="c93de-182">X</span></span>|<span data-ttu-id="c93de-183">Yok</span><span class="sxs-lookup"><span data-stu-id="c93de-183">N/A</span></span>||  
|`eDisableRuntime`|<span data-ttu-id="c93de-184">X</span><span class="sxs-lookup"><span data-stu-id="c93de-184">X</span></span>|<span data-ttu-id="c93de-185">X</span><span class="sxs-lookup"><span data-stu-id="c93de-185">X</span></span>|<span data-ttu-id="c93de-186">X</span><span class="sxs-lookup"><span data-stu-id="c93de-186">X</span></span>|<span data-ttu-id="c93de-187">X</span><span class="sxs-lookup"><span data-stu-id="c93de-187">X</span></span>|<span data-ttu-id="c93de-188">X</span><span class="sxs-lookup"><span data-stu-id="c93de-188">X</span></span>|<span data-ttu-id="c93de-189">Yok</span><span class="sxs-lookup"><span data-stu-id="c93de-189">N/A</span></span>||  
  
## <a name="requirements"></a><span data-ttu-id="c93de-190">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c93de-190">Requirements</span></span>  
 <span data-ttu-id="c93de-191">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c93de-191">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c93de-192">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c93de-192">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c93de-193">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="c93de-193">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c93de-194">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c93de-194">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c93de-195">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c93de-195">See Also</span></span>  
 [<span data-ttu-id="c93de-196">EClrFailure Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="c93de-196">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="c93de-197">EPolicyAction Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="c93de-197">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="c93de-198">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c93de-198">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="c93de-199">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c93de-199">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
