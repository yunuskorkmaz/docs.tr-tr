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
ms.openlocfilehash: 34d9e1a3747ecf3dffc925d7883599b773dd51f1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638976"
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a><span data-ttu-id="3825f-102">ICLRPolicyManager::SetActionOnFailure Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3825f-102">ICLRPolicyManager::SetActionOnFailure Method</span></span>
<span data-ttu-id="3825f-103">Belirtilen bir hata oluşursa, ortak dil çalışma zamanı (CLR) gerçekleştirmesi gereken ilke eylemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="3825f-103">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3825f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3825f-104">Syntax</span></span>  
  
```  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3825f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3825f-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="3825f-106">[in] Aşağıdakilerden birini [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) nedenine ilişkin hata türü belirten değerleri.</span><span class="sxs-lookup"><span data-stu-id="3825f-106">[in] One of the [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values, indicating the type of failure for which to take action.</span></span>  
  
 `action`  
 <span data-ttu-id="3825f-107">[in] Aşağıdakilerden birini [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) bir hata oluştuğunda yapılacak eylem belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="3825f-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action to be taken when a failure occurs.</span></span> <span data-ttu-id="3825f-108">Desteklenen değerler listesi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="3825f-108">For a list of supported values, see the Remarks section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3825f-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3825f-109">Return Value</span></span>  
  
|<span data-ttu-id="3825f-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3825f-110">HRESULT</span></span>|<span data-ttu-id="3825f-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3825f-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3825f-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="3825f-112">S_OK</span></span>|<span data-ttu-id="3825f-113">`SetActionOnFailure` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="3825f-113">`SetActionOnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="3825f-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3825f-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3825f-115">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="3825f-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3825f-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3825f-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3825f-117">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="3825f-117">The call timed out.</span></span>|  
|<span data-ttu-id="3825f-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3825f-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3825f-119">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="3825f-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3825f-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3825f-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3825f-121">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="3825f-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3825f-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3825f-122">E_FAIL</span></span>|<span data-ttu-id="3825f-123">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="3825f-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3825f-124">CLR, artık E_FAIL bir yöntemin dönüşünün ardından, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="3825f-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3825f-125">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="3825f-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3825f-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="3825f-126">E_INVALIDARG</span></span>|<span data-ttu-id="3825f-127">İlkesi eylemi belirtilen işlem için ayarlanamaz veya işlem için geçersiz ilke eylem belirtildi.</span><span class="sxs-lookup"><span data-stu-id="3825f-127">A policy action cannot be set for the specified operation, or an invalid policy action was specified for the operation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3825f-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3825f-128">Remarks</span></span>  
 <span data-ttu-id="3825f-129">Bellek gibi bir kaynağı ayırmak başarısız olduğunda varsayılan olarak, CLR özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3825f-129">By default, the CLR throws an exception when it fails to allocate a resource such as memory.</span></span> <span data-ttu-id="3825f-130">`SetActionOnFailure` Başarısızlık durumunda ilke eylemin belirterek bu davranışı geçersiz kılmak için ana sağlar.</span><span class="sxs-lookup"><span data-stu-id="3825f-130">`SetActionOnFailure` allows the host to override this behavior by specifying the policy action to take upon failure.</span></span> <span data-ttu-id="3825f-131">Aşağıdaki tabloda bileşimleri gösterir [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) ve [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) desteklenen değerleri.</span><span class="sxs-lookup"><span data-stu-id="3825f-131">The following table shows the combinations of [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) and [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values that are supported.</span></span> <span data-ttu-id="3825f-132">(FAIL_ önek gelen atlanırsa [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) değerleri.)</span><span class="sxs-lookup"><span data-stu-id="3825f-132">(The FAIL_ prefix is omitted from [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values.)</span></span>  
  
||<span data-ttu-id="3825f-133">NonCriticalResource</span><span class="sxs-lookup"><span data-stu-id="3825f-133">NonCriticalResource</span></span>|<span data-ttu-id="3825f-134">CriticalResource</span><span class="sxs-lookup"><span data-stu-id="3825f-134">CriticalResource</span></span>|<span data-ttu-id="3825f-135">FatalRuntime</span><span class="sxs-lookup"><span data-stu-id="3825f-135">FatalRuntime</span></span>|<span data-ttu-id="3825f-136">OrphanedLock</span><span class="sxs-lookup"><span data-stu-id="3825f-136">OrphanedLock</span></span>|<span data-ttu-id="3825f-137">StackOverflow</span><span class="sxs-lookup"><span data-stu-id="3825f-137">StackOverflow</span></span>|<span data-ttu-id="3825f-138">AccessViolation</span><span class="sxs-lookup"><span data-stu-id="3825f-138">AccessViolation</span></span>|<span data-ttu-id="3825f-139">CodeContract</span><span class="sxs-lookup"><span data-stu-id="3825f-139">CodeContract</span></span>|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|<span data-ttu-id="3825f-140">X</span><span class="sxs-lookup"><span data-stu-id="3825f-140">X</span></span>|<span data-ttu-id="3825f-141">X</span><span class="sxs-lookup"><span data-stu-id="3825f-141">X</span></span>||||<span data-ttu-id="3825f-142">Yok</span><span class="sxs-lookup"><span data-stu-id="3825f-142">N/A</span></span>||  
|<span data-ttu-id="3825f-143">eThrowException</span><span class="sxs-lookup"><span data-stu-id="3825f-143">eThrowException</span></span>|<span data-ttu-id="3825f-144">X</span><span class="sxs-lookup"><span data-stu-id="3825f-144">X</span></span>|<span data-ttu-id="3825f-145">X</span><span class="sxs-lookup"><span data-stu-id="3825f-145">X</span></span>||||<span data-ttu-id="3825f-146">Yok</span><span class="sxs-lookup"><span data-stu-id="3825f-146">N/A</span></span>||  
|`eAbortThread`|<span data-ttu-id="3825f-147">X</span><span class="sxs-lookup"><span data-stu-id="3825f-147">X</span></span>|<span data-ttu-id="3825f-148">X</span><span class="sxs-lookup"><span data-stu-id="3825f-148">X</span></span>||||<span data-ttu-id="3825f-149">Yok</span><span class="sxs-lookup"><span data-stu-id="3825f-149">N/A</span></span>|<span data-ttu-id="3825f-150">X</span><span class="sxs-lookup"><span data-stu-id="3825f-150">X</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="3825f-151">X</span><span class="sxs-lookup"><span data-stu-id="3825f-151">X</span></span>|<span data-ttu-id="3825f-152">X</span><span class="sxs-lookup"><span data-stu-id="3825f-152">X</span></span>||||<span data-ttu-id="3825f-153">Yok</span><span class="sxs-lookup"><span data-stu-id="3825f-153">N/A</span></span>|<span data-ttu-id="3825f-154">X</span><span class="sxs-lookup"><span data-stu-id="3825f-154">X</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="3825f-155">X</span><span class="sxs-lookup"><span data-stu-id="3825f-155">X</span></span>|<span data-ttu-id="3825f-156">X</span><span class="sxs-lookup"><span data-stu-id="3825f-156">X</span></span>||<span data-ttu-id="3825f-157">X</span><span class="sxs-lookup"><span data-stu-id="3825f-157">X</span></span>||<span data-ttu-id="3825f-158">Yok</span><span class="sxs-lookup"><span data-stu-id="3825f-158">N/A</span></span>|<span data-ttu-id="3825f-159">X</span><span class="sxs-lookup"><span data-stu-id="3825f-159">X</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="3825f-160">X</span><span class="sxs-lookup"><span data-stu-id="3825f-160">X</span></span>|<span data-ttu-id="3825f-161">X</span><span class="sxs-lookup"><span data-stu-id="3825f-161">X</span></span>||<span data-ttu-id="3825f-162">X</span><span class="sxs-lookup"><span data-stu-id="3825f-162">X</span></span>|<span data-ttu-id="3825f-163">X</span><span class="sxs-lookup"><span data-stu-id="3825f-163">X</span></span>|<span data-ttu-id="3825f-164">Yok</span><span class="sxs-lookup"><span data-stu-id="3825f-164">N/A</span></span>|<span data-ttu-id="3825f-165">X</span><span class="sxs-lookup"><span data-stu-id="3825f-165">X</span></span>|  
|`eExitProcess`|<span data-ttu-id="3825f-166">X</span><span class="sxs-lookup"><span data-stu-id="3825f-166">X</span></span>|<span data-ttu-id="3825f-167">X</span><span class="sxs-lookup"><span data-stu-id="3825f-167">X</span></span>||<span data-ttu-id="3825f-168">X</span><span class="sxs-lookup"><span data-stu-id="3825f-168">X</span></span>|<span data-ttu-id="3825f-169">X</span><span class="sxs-lookup"><span data-stu-id="3825f-169">X</span></span>|<span data-ttu-id="3825f-170">Yok</span><span class="sxs-lookup"><span data-stu-id="3825f-170">N/A</span></span>|<span data-ttu-id="3825f-171">X</span><span class="sxs-lookup"><span data-stu-id="3825f-171">X</span></span>|  
|<span data-ttu-id="3825f-172">eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="3825f-172">eFastExitProcess</span></span>|<span data-ttu-id="3825f-173">X</span><span class="sxs-lookup"><span data-stu-id="3825f-173">X</span></span>|<span data-ttu-id="3825f-174">X</span><span class="sxs-lookup"><span data-stu-id="3825f-174">X</span></span>||<span data-ttu-id="3825f-175">X</span><span class="sxs-lookup"><span data-stu-id="3825f-175">X</span></span>|<span data-ttu-id="3825f-176">X</span><span class="sxs-lookup"><span data-stu-id="3825f-176">X</span></span>|<span data-ttu-id="3825f-177">Yok</span><span class="sxs-lookup"><span data-stu-id="3825f-177">N/A</span></span>||  
|`eRudeExitProcess`|<span data-ttu-id="3825f-178">X</span><span class="sxs-lookup"><span data-stu-id="3825f-178">X</span></span>|<span data-ttu-id="3825f-179">X</span><span class="sxs-lookup"><span data-stu-id="3825f-179">X</span></span>|<span data-ttu-id="3825f-180">X</span><span class="sxs-lookup"><span data-stu-id="3825f-180">X</span></span>|<span data-ttu-id="3825f-181">X</span><span class="sxs-lookup"><span data-stu-id="3825f-181">X</span></span>|<span data-ttu-id="3825f-182">X</span><span class="sxs-lookup"><span data-stu-id="3825f-182">X</span></span>|<span data-ttu-id="3825f-183">Yok</span><span class="sxs-lookup"><span data-stu-id="3825f-183">N/A</span></span>||  
|`eDisableRuntime`|<span data-ttu-id="3825f-184">X</span><span class="sxs-lookup"><span data-stu-id="3825f-184">X</span></span>|<span data-ttu-id="3825f-185">X</span><span class="sxs-lookup"><span data-stu-id="3825f-185">X</span></span>|<span data-ttu-id="3825f-186">X</span><span class="sxs-lookup"><span data-stu-id="3825f-186">X</span></span>|<span data-ttu-id="3825f-187">X</span><span class="sxs-lookup"><span data-stu-id="3825f-187">X</span></span>|<span data-ttu-id="3825f-188">X</span><span class="sxs-lookup"><span data-stu-id="3825f-188">X</span></span>|<span data-ttu-id="3825f-189">Yok</span><span class="sxs-lookup"><span data-stu-id="3825f-189">N/A</span></span>||  
  
## <a name="requirements"></a><span data-ttu-id="3825f-190">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3825f-190">Requirements</span></span>  
 <span data-ttu-id="3825f-191">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3825f-191">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3825f-192">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3825f-192">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3825f-193">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="3825f-193">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3825f-194">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3825f-194">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3825f-195">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3825f-195">See also</span></span>

- [<span data-ttu-id="3825f-196">EClrFailure Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="3825f-196">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="3825f-197">EPolicyAction Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="3825f-197">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="3825f-198">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3825f-198">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="3825f-199">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3825f-199">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
