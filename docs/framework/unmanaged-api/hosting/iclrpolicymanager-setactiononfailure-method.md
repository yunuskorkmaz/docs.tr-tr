---
title: ICLRPolicyManager::SetActionOnFailure Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetActionOnFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetActionOnFailure
helpviewer_keywords:
- SetActionOnFailure method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnFailure method [.NET Framework hosting]
ms.assetid: 4664033f-db97-4388-b988-2ec470796e58
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 76f064d1683615ef8f665cf1facaa31d61b294a5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759602"
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a><span data-ttu-id="3a1da-102">ICLRPolicyManager::SetActionOnFailure Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3a1da-102">ICLRPolicyManager::SetActionOnFailure Method</span></span>
<span data-ttu-id="3a1da-103">Belirtilen bir hata oluşursa, ortak dil çalışma zamanı (CLR) gerçekleştirmesi gereken ilke eylemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="3a1da-103">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a1da-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3a1da-104">Syntax</span></span>  
  
```cpp  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a1da-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3a1da-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="3a1da-106">[in] Aşağıdakilerden birini [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) nedenine ilişkin hata türü belirten değerleri.</span><span class="sxs-lookup"><span data-stu-id="3a1da-106">[in] One of the [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values, indicating the type of failure for which to take action.</span></span>  
  
 `action`  
 <span data-ttu-id="3a1da-107">[in] Aşağıdakilerden birini [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) bir hata oluştuğunda yapılacak eylem belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="3a1da-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action to be taken when a failure occurs.</span></span> <span data-ttu-id="3a1da-108">Desteklenen değerler listesi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="3a1da-108">For a list of supported values, see the Remarks section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3a1da-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3a1da-109">Return Value</span></span>  
  
|<span data-ttu-id="3a1da-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3a1da-110">HRESULT</span></span>|<span data-ttu-id="3a1da-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3a1da-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3a1da-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="3a1da-112">S_OK</span></span>|<span data-ttu-id="3a1da-113">`SetActionOnFailure` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="3a1da-113">`SetActionOnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="3a1da-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3a1da-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3a1da-115">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="3a1da-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3a1da-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3a1da-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3a1da-117">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="3a1da-117">The call timed out.</span></span>|  
|<span data-ttu-id="3a1da-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3a1da-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3a1da-119">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="3a1da-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3a1da-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3a1da-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3a1da-121">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="3a1da-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3a1da-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3a1da-122">E_FAIL</span></span>|<span data-ttu-id="3a1da-123">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="3a1da-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3a1da-124">CLR, artık E_FAIL bir yöntemin dönüşünün ardından, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="3a1da-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3a1da-125">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="3a1da-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3a1da-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="3a1da-126">E_INVALIDARG</span></span>|<span data-ttu-id="3a1da-127">İlkesi eylemi belirtilen işlem için ayarlanamaz veya işlem için geçersiz ilke eylem belirtildi.</span><span class="sxs-lookup"><span data-stu-id="3a1da-127">A policy action cannot be set for the specified operation, or an invalid policy action was specified for the operation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a1da-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3a1da-128">Remarks</span></span>  
 <span data-ttu-id="3a1da-129">Bellek gibi bir kaynağı ayırmak başarısız olduğunda varsayılan olarak, CLR özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3a1da-129">By default, the CLR throws an exception when it fails to allocate a resource such as memory.</span></span> <span data-ttu-id="3a1da-130">`SetActionOnFailure` Başarısızlık durumunda ilke eylemin belirterek bu davranışı geçersiz kılmak için ana sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a1da-130">`SetActionOnFailure` allows the host to override this behavior by specifying the policy action to take upon failure.</span></span> <span data-ttu-id="3a1da-131">Aşağıdaki tabloda bileşimleri gösterir [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) ve [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) desteklenen değerleri.</span><span class="sxs-lookup"><span data-stu-id="3a1da-131">The following table shows the combinations of [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) and [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values that are supported.</span></span> <span data-ttu-id="3a1da-132">(FAIL_ önek gelen atlanırsa [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) değerleri.)</span><span class="sxs-lookup"><span data-stu-id="3a1da-132">(The FAIL_ prefix is omitted from [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values.)</span></span>  
  
||<span data-ttu-id="3a1da-133">NonCriticalResource</span><span class="sxs-lookup"><span data-stu-id="3a1da-133">NonCriticalResource</span></span>|<span data-ttu-id="3a1da-134">CriticalResource</span><span class="sxs-lookup"><span data-stu-id="3a1da-134">CriticalResource</span></span>|<span data-ttu-id="3a1da-135">FatalRuntime</span><span class="sxs-lookup"><span data-stu-id="3a1da-135">FatalRuntime</span></span>|<span data-ttu-id="3a1da-136">OrphanedLock</span><span class="sxs-lookup"><span data-stu-id="3a1da-136">OrphanedLock</span></span>|<span data-ttu-id="3a1da-137">StackOverflow</span><span class="sxs-lookup"><span data-stu-id="3a1da-137">StackOverflow</span></span>|<span data-ttu-id="3a1da-138">AccessViolation</span><span class="sxs-lookup"><span data-stu-id="3a1da-138">AccessViolation</span></span>|<span data-ttu-id="3a1da-139">CodeContract</span><span class="sxs-lookup"><span data-stu-id="3a1da-139">CodeContract</span></span>|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|<span data-ttu-id="3a1da-140">X</span><span class="sxs-lookup"><span data-stu-id="3a1da-140">X</span></span>|<span data-ttu-id="3a1da-141">X</span><span class="sxs-lookup"><span data-stu-id="3a1da-141">X</span></span>||||<span data-ttu-id="3a1da-142">Yok</span><span class="sxs-lookup"><span data-stu-id="3a1da-142">N/A</span></span>||  
|<span data-ttu-id="3a1da-143">eThrowException</span><span class="sxs-lookup"><span data-stu-id="3a1da-143">eThrowException</span></span>|<span data-ttu-id="3a1da-144">X</span><span class="sxs-lookup"><span data-stu-id="3a1da-144">X</span></span>|<span data-ttu-id="3a1da-145">X</span><span class="sxs-lookup"><span data-stu-id="3a1da-145">X</span></span>||||<span data-ttu-id="3a1da-146">Yok</span><span class="sxs-lookup"><span data-stu-id="3a1da-146">N/A</span></span>||  
|`eAbortThread`|<span data-ttu-id="3a1da-147">X</span><span class="sxs-lookup"><span data-stu-id="3a1da-147">X</span></span>|<span data-ttu-id="3a1da-148">X</span><span class="sxs-lookup"><span data-stu-id="3a1da-148">X</span></span>||||<span data-ttu-id="3a1da-149">Yok</span><span class="sxs-lookup"><span data-stu-id="3a1da-149">N/A</span></span>|<span data-ttu-id="3a1da-150">X</span><span class="sxs-lookup"><span data-stu-id="3a1da-150">X</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="3a1da-151">X</span><span class="sxs-lookup"><span data-stu-id="3a1da-151">X</span></span>|<span data-ttu-id="3a1da-152">X</span><span class="sxs-lookup"><span data-stu-id="3a1da-152">X</span></span>||||<span data-ttu-id="3a1da-153">Yok</span><span class="sxs-lookup"><span data-stu-id="3a1da-153">N/A</span></span>|<span data-ttu-id="3a1da-154">X</span><span class="sxs-lookup"><span data-stu-id="3a1da-154">X</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="3a1da-155">X</span><span class="sxs-lookup"><span data-stu-id="3a1da-155">X</span></span>|<span data-ttu-id="3a1da-156">X</span><span class="sxs-lookup"><span data-stu-id="3a1da-156">X</span></span>||<span data-ttu-id="3a1da-157">X</span><span class="sxs-lookup"><span data-stu-id="3a1da-157">X</span></span>||<span data-ttu-id="3a1da-158">Yok</span><span class="sxs-lookup"><span data-stu-id="3a1da-158">N/A</span></span>|<span data-ttu-id="3a1da-159">X</span><span class="sxs-lookup"><span data-stu-id="3a1da-159">X</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="3a1da-160">X</span><span class="sxs-lookup"><span data-stu-id="3a1da-160">X</span></span>|<span data-ttu-id="3a1da-161">X</span><span class="sxs-lookup"><span data-stu-id="3a1da-161">X</span></span>||<span data-ttu-id="3a1da-162">X</span><span class="sxs-lookup"><span data-stu-id="3a1da-162">X</span></span>|<span data-ttu-id="3a1da-163">X</span><span class="sxs-lookup"><span data-stu-id="3a1da-163">X</span></span>|<span data-ttu-id="3a1da-164">Yok</span><span class="sxs-lookup"><span data-stu-id="3a1da-164">N/A</span></span>|<span data-ttu-id="3a1da-165">X</span><span class="sxs-lookup"><span data-stu-id="3a1da-165">X</span></span>|  
|`eExitProcess`|<span data-ttu-id="3a1da-166">X</span><span class="sxs-lookup"><span data-stu-id="3a1da-166">X</span></span>|<span data-ttu-id="3a1da-167">X</span><span class="sxs-lookup"><span data-stu-id="3a1da-167">X</span></span>||<span data-ttu-id="3a1da-168">X</span><span class="sxs-lookup"><span data-stu-id="3a1da-168">X</span></span>|<span data-ttu-id="3a1da-169">X</span><span class="sxs-lookup"><span data-stu-id="3a1da-169">X</span></span>|<span data-ttu-id="3a1da-170">Yok</span><span class="sxs-lookup"><span data-stu-id="3a1da-170">N/A</span></span>|<span data-ttu-id="3a1da-171">X</span><span class="sxs-lookup"><span data-stu-id="3a1da-171">X</span></span>|  
|<span data-ttu-id="3a1da-172">eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="3a1da-172">eFastExitProcess</span></span>|<span data-ttu-id="3a1da-173">X</span><span class="sxs-lookup"><span data-stu-id="3a1da-173">X</span></span>|<span data-ttu-id="3a1da-174">X</span><span class="sxs-lookup"><span data-stu-id="3a1da-174">X</span></span>||<span data-ttu-id="3a1da-175">X</span><span class="sxs-lookup"><span data-stu-id="3a1da-175">X</span></span>|<span data-ttu-id="3a1da-176">X</span><span class="sxs-lookup"><span data-stu-id="3a1da-176">X</span></span>|<span data-ttu-id="3a1da-177">Yok</span><span class="sxs-lookup"><span data-stu-id="3a1da-177">N/A</span></span>||  
|`eRudeExitProcess`|<span data-ttu-id="3a1da-178">X</span><span class="sxs-lookup"><span data-stu-id="3a1da-178">X</span></span>|<span data-ttu-id="3a1da-179">X</span><span class="sxs-lookup"><span data-stu-id="3a1da-179">X</span></span>|<span data-ttu-id="3a1da-180">X</span><span class="sxs-lookup"><span data-stu-id="3a1da-180">X</span></span>|<span data-ttu-id="3a1da-181">X</span><span class="sxs-lookup"><span data-stu-id="3a1da-181">X</span></span>|<span data-ttu-id="3a1da-182">X</span><span class="sxs-lookup"><span data-stu-id="3a1da-182">X</span></span>|<span data-ttu-id="3a1da-183">Yok</span><span class="sxs-lookup"><span data-stu-id="3a1da-183">N/A</span></span>||  
|`eDisableRuntime`|<span data-ttu-id="3a1da-184">X</span><span class="sxs-lookup"><span data-stu-id="3a1da-184">X</span></span>|<span data-ttu-id="3a1da-185">X</span><span class="sxs-lookup"><span data-stu-id="3a1da-185">X</span></span>|<span data-ttu-id="3a1da-186">X</span><span class="sxs-lookup"><span data-stu-id="3a1da-186">X</span></span>|<span data-ttu-id="3a1da-187">X</span><span class="sxs-lookup"><span data-stu-id="3a1da-187">X</span></span>|<span data-ttu-id="3a1da-188">X</span><span class="sxs-lookup"><span data-stu-id="3a1da-188">X</span></span>|<span data-ttu-id="3a1da-189">Yok</span><span class="sxs-lookup"><span data-stu-id="3a1da-189">N/A</span></span>||  
  
## <a name="requirements"></a><span data-ttu-id="3a1da-190">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3a1da-190">Requirements</span></span>  
 <span data-ttu-id="3a1da-191">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a1da-191">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a1da-192">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3a1da-192">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3a1da-193">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="3a1da-193">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3a1da-194">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a1da-194">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a1da-195">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3a1da-195">See also</span></span>

- [<span data-ttu-id="3a1da-196">EClrFailure Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="3a1da-196">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="3a1da-197">EPolicyAction Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="3a1da-197">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="3a1da-198">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3a1da-198">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="3a1da-199">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3a1da-199">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
