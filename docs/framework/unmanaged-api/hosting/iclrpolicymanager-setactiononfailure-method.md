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
ms.openlocfilehash: 5dc8e27ed1a5701886c3583a7515e4212f490208
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a><span data-ttu-id="8f470-102">ICLRPolicyManager::SetActionOnFailure Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8f470-102">ICLRPolicyManager::SetActionOnFailure Method</span></span>
<span data-ttu-id="8f470-103">Belirtilen bir hata oluşursa, ortak dil çalışma zamanı (CLR) gerçekleştirmesi gereken ilke eylemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="8f470-103">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f470-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8f470-104">Syntax</span></span>  
  
```  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8f470-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8f470-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="8f470-106">[in] Aşağıdakilerden birini [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) nedenine ilişkin hata türü belirten değerleri.</span><span class="sxs-lookup"><span data-stu-id="8f470-106">[in] One of the [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values, indicating the type of failure for which to take action.</span></span>  
  
 `action`  
 <span data-ttu-id="8f470-107">[in] Aşağıdakilerden birini [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) belirten bir hata oluşursa, eylemin gerçekleştirilmesine değerleri.</span><span class="sxs-lookup"><span data-stu-id="8f470-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action to be taken when a failure occurs.</span></span> <span data-ttu-id="8f470-108">Desteklenen değerler listesi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="8f470-108">For a list of supported values, see the Remarks section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8f470-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8f470-109">Return Value</span></span>  
  
|<span data-ttu-id="8f470-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8f470-110">HRESULT</span></span>|<span data-ttu-id="8f470-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8f470-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8f470-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="8f470-112">S_OK</span></span>|<span data-ttu-id="8f470-113">`SetActionOnFailure`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="8f470-113">`SetActionOnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="8f470-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8f470-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8f470-115">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="8f470-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8f470-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8f470-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8f470-117">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="8f470-117">The call timed out.</span></span>|  
|<span data-ttu-id="8f470-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8f470-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8f470-119">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="8f470-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8f470-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8f470-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8f470-121">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="8f470-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8f470-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8f470-122">E_FAIL</span></span>|<span data-ttu-id="8f470-123">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="8f470-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8f470-124">CLR, artık bir yöntem E_FAIL döndükten sonra işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="8f470-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8f470-125">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="8f470-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8f470-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8f470-126">E_INVALIDARG</span></span>|<span data-ttu-id="8f470-127">Belirtilen işlem için bir ilke eylemi ayarlanamaz veya işlem için geçersiz ilke eylem belirtildi.</span><span class="sxs-lookup"><span data-stu-id="8f470-127">A policy action cannot be set for the specified operation, or an invalid policy action was specified for the operation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f470-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8f470-128">Remarks</span></span>  
 <span data-ttu-id="8f470-129">Bellek gibi bir kaynak ayırma başarısız olduğunda varsayılan olarak, CLR özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8f470-129">By default, the CLR throws an exception when it fails to allocate a resource such as memory.</span></span> <span data-ttu-id="8f470-130">`SetActionOnFailure`hata yapması üzerine yapılacak İlkesi eylem belirterek bu davranışı geçersiz kılmak için ana sağlar.</span><span class="sxs-lookup"><span data-stu-id="8f470-130">`SetActionOnFailure` allows the host to override this behavior by specifying the policy action to take upon failure.</span></span> <span data-ttu-id="8f470-131">Aşağıdaki tablo bileşimlerine gösterir [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) ve [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) desteklenen değerler.</span><span class="sxs-lookup"><span data-stu-id="8f470-131">The following table shows the combinations of [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) and [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values that are supported.</span></span> <span data-ttu-id="8f470-132">(FAIL_ öneki gelen atlanmış [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) değerleri.)</span><span class="sxs-lookup"><span data-stu-id="8f470-132">(The FAIL_ prefix is omitted from [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values.)</span></span>  
  
||<span data-ttu-id="8f470-133">NonCriticalResource</span><span class="sxs-lookup"><span data-stu-id="8f470-133">NonCriticalResource</span></span>|<span data-ttu-id="8f470-134">CriticalResource</span><span class="sxs-lookup"><span data-stu-id="8f470-134">CriticalResource</span></span>|<span data-ttu-id="8f470-135">FatalRuntime</span><span class="sxs-lookup"><span data-stu-id="8f470-135">FatalRuntime</span></span>|<span data-ttu-id="8f470-136">OrphanedLock</span><span class="sxs-lookup"><span data-stu-id="8f470-136">OrphanedLock</span></span>|<span data-ttu-id="8f470-137">StackOverflow</span><span class="sxs-lookup"><span data-stu-id="8f470-137">StackOverflow</span></span>|<span data-ttu-id="8f470-138">AccessViolation</span><span class="sxs-lookup"><span data-stu-id="8f470-138">AccessViolation</span></span>|<span data-ttu-id="8f470-139">CodeContract</span><span class="sxs-lookup"><span data-stu-id="8f470-139">CodeContract</span></span>|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|<span data-ttu-id="8f470-140">X</span><span class="sxs-lookup"><span data-stu-id="8f470-140">X</span></span>|<span data-ttu-id="8f470-141">X</span><span class="sxs-lookup"><span data-stu-id="8f470-141">X</span></span>||||<span data-ttu-id="8f470-142">Yok</span><span class="sxs-lookup"><span data-stu-id="8f470-142">N/A</span></span>||  
|<span data-ttu-id="8f470-143">eThrowException</span><span class="sxs-lookup"><span data-stu-id="8f470-143">eThrowException</span></span>|<span data-ttu-id="8f470-144">X</span><span class="sxs-lookup"><span data-stu-id="8f470-144">X</span></span>|<span data-ttu-id="8f470-145">X</span><span class="sxs-lookup"><span data-stu-id="8f470-145">X</span></span>||||<span data-ttu-id="8f470-146">Yok</span><span class="sxs-lookup"><span data-stu-id="8f470-146">N/A</span></span>||  
|`eAbortThread`|<span data-ttu-id="8f470-147">X</span><span class="sxs-lookup"><span data-stu-id="8f470-147">X</span></span>|<span data-ttu-id="8f470-148">X</span><span class="sxs-lookup"><span data-stu-id="8f470-148">X</span></span>||||<span data-ttu-id="8f470-149">Yok</span><span class="sxs-lookup"><span data-stu-id="8f470-149">N/A</span></span>|<span data-ttu-id="8f470-150">X</span><span class="sxs-lookup"><span data-stu-id="8f470-150">X</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="8f470-151">X</span><span class="sxs-lookup"><span data-stu-id="8f470-151">X</span></span>|<span data-ttu-id="8f470-152">X</span><span class="sxs-lookup"><span data-stu-id="8f470-152">X</span></span>||||<span data-ttu-id="8f470-153">Yok</span><span class="sxs-lookup"><span data-stu-id="8f470-153">N/A</span></span>|<span data-ttu-id="8f470-154">X</span><span class="sxs-lookup"><span data-stu-id="8f470-154">X</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="8f470-155">X</span><span class="sxs-lookup"><span data-stu-id="8f470-155">X</span></span>|<span data-ttu-id="8f470-156">X</span><span class="sxs-lookup"><span data-stu-id="8f470-156">X</span></span>||<span data-ttu-id="8f470-157">X</span><span class="sxs-lookup"><span data-stu-id="8f470-157">X</span></span>||<span data-ttu-id="8f470-158">Yok</span><span class="sxs-lookup"><span data-stu-id="8f470-158">N/A</span></span>|<span data-ttu-id="8f470-159">X</span><span class="sxs-lookup"><span data-stu-id="8f470-159">X</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="8f470-160">X</span><span class="sxs-lookup"><span data-stu-id="8f470-160">X</span></span>|<span data-ttu-id="8f470-161">X</span><span class="sxs-lookup"><span data-stu-id="8f470-161">X</span></span>||<span data-ttu-id="8f470-162">X</span><span class="sxs-lookup"><span data-stu-id="8f470-162">X</span></span>|<span data-ttu-id="8f470-163">X</span><span class="sxs-lookup"><span data-stu-id="8f470-163">X</span></span>|<span data-ttu-id="8f470-164">Yok</span><span class="sxs-lookup"><span data-stu-id="8f470-164">N/A</span></span>|<span data-ttu-id="8f470-165">X</span><span class="sxs-lookup"><span data-stu-id="8f470-165">X</span></span>|  
|`eExitProcess`|<span data-ttu-id="8f470-166">X</span><span class="sxs-lookup"><span data-stu-id="8f470-166">X</span></span>|<span data-ttu-id="8f470-167">X</span><span class="sxs-lookup"><span data-stu-id="8f470-167">X</span></span>||<span data-ttu-id="8f470-168">X</span><span class="sxs-lookup"><span data-stu-id="8f470-168">X</span></span>|<span data-ttu-id="8f470-169">X</span><span class="sxs-lookup"><span data-stu-id="8f470-169">X</span></span>|<span data-ttu-id="8f470-170">Yok</span><span class="sxs-lookup"><span data-stu-id="8f470-170">N/A</span></span>|<span data-ttu-id="8f470-171">X</span><span class="sxs-lookup"><span data-stu-id="8f470-171">X</span></span>|  
|<span data-ttu-id="8f470-172">eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="8f470-172">eFastExitProcess</span></span>|<span data-ttu-id="8f470-173">X</span><span class="sxs-lookup"><span data-stu-id="8f470-173">X</span></span>|<span data-ttu-id="8f470-174">X</span><span class="sxs-lookup"><span data-stu-id="8f470-174">X</span></span>||<span data-ttu-id="8f470-175">X</span><span class="sxs-lookup"><span data-stu-id="8f470-175">X</span></span>|<span data-ttu-id="8f470-176">X</span><span class="sxs-lookup"><span data-stu-id="8f470-176">X</span></span>|<span data-ttu-id="8f470-177">Yok</span><span class="sxs-lookup"><span data-stu-id="8f470-177">N/A</span></span>||  
|`eRudeExitProcess`|<span data-ttu-id="8f470-178">X</span><span class="sxs-lookup"><span data-stu-id="8f470-178">X</span></span>|<span data-ttu-id="8f470-179">X</span><span class="sxs-lookup"><span data-stu-id="8f470-179">X</span></span>|<span data-ttu-id="8f470-180">X</span><span class="sxs-lookup"><span data-stu-id="8f470-180">X</span></span>|<span data-ttu-id="8f470-181">X</span><span class="sxs-lookup"><span data-stu-id="8f470-181">X</span></span>|<span data-ttu-id="8f470-182">X</span><span class="sxs-lookup"><span data-stu-id="8f470-182">X</span></span>|<span data-ttu-id="8f470-183">Yok</span><span class="sxs-lookup"><span data-stu-id="8f470-183">N/A</span></span>||  
|`eDisableRuntime`|<span data-ttu-id="8f470-184">X</span><span class="sxs-lookup"><span data-stu-id="8f470-184">X</span></span>|<span data-ttu-id="8f470-185">X</span><span class="sxs-lookup"><span data-stu-id="8f470-185">X</span></span>|<span data-ttu-id="8f470-186">X</span><span class="sxs-lookup"><span data-stu-id="8f470-186">X</span></span>|<span data-ttu-id="8f470-187">X</span><span class="sxs-lookup"><span data-stu-id="8f470-187">X</span></span>|<span data-ttu-id="8f470-188">X</span><span class="sxs-lookup"><span data-stu-id="8f470-188">X</span></span>|<span data-ttu-id="8f470-189">Yok</span><span class="sxs-lookup"><span data-stu-id="8f470-189">N/A</span></span>||  
  
## <a name="requirements"></a><span data-ttu-id="8f470-190">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8f470-190">Requirements</span></span>  
 <span data-ttu-id="8f470-191">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f470-191">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f470-192">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8f470-192">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8f470-193">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="8f470-193">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8f470-194">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f470-194">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f470-195">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8f470-195">See Also</span></span>  
 [<span data-ttu-id="8f470-196">EClrFailure numaralandırması</span><span class="sxs-lookup"><span data-stu-id="8f470-196">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="8f470-197">EPolicyAction numaralandırması</span><span class="sxs-lookup"><span data-stu-id="8f470-197">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="8f470-198">Iclrcontrol arabirimi</span><span class="sxs-lookup"><span data-stu-id="8f470-198">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="8f470-199">Iclrpolicymanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="8f470-199">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
