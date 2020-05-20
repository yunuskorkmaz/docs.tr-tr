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
ms.openlocfilehash: fb2ecc80f272a3fc9b63b20c5956e7a28f117784
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703468"
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a><span data-ttu-id="80079-102">ICLRPolicyManager::SetActionOnFailure Yöntemi</span><span class="sxs-lookup"><span data-stu-id="80079-102">ICLRPolicyManager::SetActionOnFailure Method</span></span>
<span data-ttu-id="80079-103">Belirtilen hata oluştuğunda ortak dil çalışma zamanının (CLR) yapması gereken ilke eylemini belirtir.</span><span class="sxs-lookup"><span data-stu-id="80079-103">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80079-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="80079-104">Syntax</span></span>  
  
```cpp  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80079-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="80079-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="80079-106">'ndaki İşlem gerçekleştirilecek hata türünü belirten [EClrFailure](eclrfailure-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="80079-106">[in] One of the [EClrFailure](eclrfailure-enumeration.md) values, indicating the type of failure for which to take action.</span></span>  
  
 `action`  
 <span data-ttu-id="80079-107">'ndaki Bir hata oluştuğunda gerçekleştirilecek eylemi belirten [EPolicyAction](epolicyaction-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="80079-107">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action to be taken when a failure occurs.</span></span> <span data-ttu-id="80079-108">Desteklenen değerlerin bir listesi için, açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="80079-108">For a list of supported values, see the Remarks section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="80079-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="80079-109">Return Value</span></span>  
  
|<span data-ttu-id="80079-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="80079-110">HRESULT</span></span>|<span data-ttu-id="80079-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="80079-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="80079-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="80079-112">S_OK</span></span>|<span data-ttu-id="80079-113">`SetActionOnFailure`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="80079-113">`SetActionOnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="80079-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="80079-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="80079-115">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="80079-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="80079-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="80079-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="80079-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="80079-117">The call timed out.</span></span>|  
|<span data-ttu-id="80079-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="80079-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="80079-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="80079-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="80079-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="80079-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="80079-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="80079-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="80079-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="80079-122">E_FAIL</span></span>|<span data-ttu-id="80079-123">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="80079-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="80079-124">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="80079-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="80079-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="80079-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="80079-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="80079-126">E_INVALIDARG</span></span>|<span data-ttu-id="80079-127">Belirtilen işlem için bir ilke eylemi ayarlanamaz veya işlem için geçersiz bir ilke eylemi belirtildi.</span><span class="sxs-lookup"><span data-stu-id="80079-127">A policy action cannot be set for the specified operation, or an invalid policy action was specified for the operation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80079-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="80079-128">Remarks</span></span>  
 <span data-ttu-id="80079-129">Varsayılan olarak, CLR bellek gibi bir kaynağı ayıramadığında bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="80079-129">By default, the CLR throws an exception when it fails to allocate a resource such as memory.</span></span> <span data-ttu-id="80079-130">`SetActionOnFailure`konağın hata sonrasında gerçekleştirilecek ilke eylemini belirterek bu davranışı geçersiz kılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="80079-130">`SetActionOnFailure` allows the host to override this behavior by specifying the policy action to take upon failure.</span></span> <span data-ttu-id="80079-131">Aşağıdaki tabloda, desteklenen [EClrFailure](eclrfailure-enumeration.md) ve [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) değerlerinin birleşimleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="80079-131">The following table shows the combinations of [EClrFailure](eclrfailure-enumeration.md) and [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values that are supported.</span></span> <span data-ttu-id="80079-132">(FAIL_ ön eki [EClrFailure](eclrfailure-enumeration.md) değerlerinden çıkarılır.)</span><span class="sxs-lookup"><span data-stu-id="80079-132">(The FAIL_ prefix is omitted from [EClrFailure](eclrfailure-enumeration.md) values.)</span></span>  
  
||<span data-ttu-id="80079-133">CriticalHandle dışı kaynak</span><span class="sxs-lookup"><span data-stu-id="80079-133">NonCriticalResource</span></span>|<span data-ttu-id="80079-134">Kritikkaynak</span><span class="sxs-lookup"><span data-stu-id="80079-134">CriticalResource</span></span>|<span data-ttu-id="80079-135">FatalRuntime</span><span class="sxs-lookup"><span data-stu-id="80079-135">FatalRuntime</span></span>|<span data-ttu-id="80079-136">OrphanedLock</span><span class="sxs-lookup"><span data-stu-id="80079-136">OrphanedLock</span></span>|<span data-ttu-id="80079-137">StackOverflow</span><span class="sxs-lookup"><span data-stu-id="80079-137">StackOverflow</span></span>|<span data-ttu-id="80079-138">Accessihlaihlaline</span><span class="sxs-lookup"><span data-stu-id="80079-138">AccessViolation</span></span>|<span data-ttu-id="80079-139">CodeContract</span><span class="sxs-lookup"><span data-stu-id="80079-139">CodeContract</span></span>|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|<span data-ttu-id="80079-140">X</span><span class="sxs-lookup"><span data-stu-id="80079-140">X</span></span>|<span data-ttu-id="80079-141">X</span><span class="sxs-lookup"><span data-stu-id="80079-141">X</span></span>||||<span data-ttu-id="80079-142">Yok</span><span class="sxs-lookup"><span data-stu-id="80079-142">N/A</span></span>||  
|<span data-ttu-id="80079-143">eThrowException</span><span class="sxs-lookup"><span data-stu-id="80079-143">eThrowException</span></span>|<span data-ttu-id="80079-144">X</span><span class="sxs-lookup"><span data-stu-id="80079-144">X</span></span>|<span data-ttu-id="80079-145">X</span><span class="sxs-lookup"><span data-stu-id="80079-145">X</span></span>||||<span data-ttu-id="80079-146">Yok</span><span class="sxs-lookup"><span data-stu-id="80079-146">N/A</span></span>||  
|`eAbortThread`|<span data-ttu-id="80079-147">X</span><span class="sxs-lookup"><span data-stu-id="80079-147">X</span></span>|<span data-ttu-id="80079-148">X</span><span class="sxs-lookup"><span data-stu-id="80079-148">X</span></span>||||<span data-ttu-id="80079-149">Yok</span><span class="sxs-lookup"><span data-stu-id="80079-149">N/A</span></span>|<span data-ttu-id="80079-150">X</span><span class="sxs-lookup"><span data-stu-id="80079-150">X</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="80079-151">X</span><span class="sxs-lookup"><span data-stu-id="80079-151">X</span></span>|<span data-ttu-id="80079-152">X</span><span class="sxs-lookup"><span data-stu-id="80079-152">X</span></span>||||<span data-ttu-id="80079-153">Yok</span><span class="sxs-lookup"><span data-stu-id="80079-153">N/A</span></span>|<span data-ttu-id="80079-154">X</span><span class="sxs-lookup"><span data-stu-id="80079-154">X</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="80079-155">X</span><span class="sxs-lookup"><span data-stu-id="80079-155">X</span></span>|<span data-ttu-id="80079-156">X</span><span class="sxs-lookup"><span data-stu-id="80079-156">X</span></span>||<span data-ttu-id="80079-157">X</span><span class="sxs-lookup"><span data-stu-id="80079-157">X</span></span>||<span data-ttu-id="80079-158">Yok</span><span class="sxs-lookup"><span data-stu-id="80079-158">N/A</span></span>|<span data-ttu-id="80079-159">X</span><span class="sxs-lookup"><span data-stu-id="80079-159">X</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="80079-160">X</span><span class="sxs-lookup"><span data-stu-id="80079-160">X</span></span>|<span data-ttu-id="80079-161">X</span><span class="sxs-lookup"><span data-stu-id="80079-161">X</span></span>||<span data-ttu-id="80079-162">X</span><span class="sxs-lookup"><span data-stu-id="80079-162">X</span></span>|<span data-ttu-id="80079-163">X</span><span class="sxs-lookup"><span data-stu-id="80079-163">X</span></span>|<span data-ttu-id="80079-164">Yok</span><span class="sxs-lookup"><span data-stu-id="80079-164">N/A</span></span>|<span data-ttu-id="80079-165">X</span><span class="sxs-lookup"><span data-stu-id="80079-165">X</span></span>|  
|`eExitProcess`|<span data-ttu-id="80079-166">X</span><span class="sxs-lookup"><span data-stu-id="80079-166">X</span></span>|<span data-ttu-id="80079-167">X</span><span class="sxs-lookup"><span data-stu-id="80079-167">X</span></span>||<span data-ttu-id="80079-168">X</span><span class="sxs-lookup"><span data-stu-id="80079-168">X</span></span>|<span data-ttu-id="80079-169">X</span><span class="sxs-lookup"><span data-stu-id="80079-169">X</span></span>|<span data-ttu-id="80079-170">Yok</span><span class="sxs-lookup"><span data-stu-id="80079-170">N/A</span></span>|<span data-ttu-id="80079-171">X</span><span class="sxs-lookup"><span data-stu-id="80079-171">X</span></span>|  
|<span data-ttu-id="80079-172">eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="80079-172">eFastExitProcess</span></span>|<span data-ttu-id="80079-173">X</span><span class="sxs-lookup"><span data-stu-id="80079-173">X</span></span>|<span data-ttu-id="80079-174">X</span><span class="sxs-lookup"><span data-stu-id="80079-174">X</span></span>||<span data-ttu-id="80079-175">X</span><span class="sxs-lookup"><span data-stu-id="80079-175">X</span></span>|<span data-ttu-id="80079-176">X</span><span class="sxs-lookup"><span data-stu-id="80079-176">X</span></span>|<span data-ttu-id="80079-177">Yok</span><span class="sxs-lookup"><span data-stu-id="80079-177">N/A</span></span>||  
|`eRudeExitProcess`|<span data-ttu-id="80079-178">X</span><span class="sxs-lookup"><span data-stu-id="80079-178">X</span></span>|<span data-ttu-id="80079-179">X</span><span class="sxs-lookup"><span data-stu-id="80079-179">X</span></span>|<span data-ttu-id="80079-180">X</span><span class="sxs-lookup"><span data-stu-id="80079-180">X</span></span>|<span data-ttu-id="80079-181">X</span><span class="sxs-lookup"><span data-stu-id="80079-181">X</span></span>|<span data-ttu-id="80079-182">X</span><span class="sxs-lookup"><span data-stu-id="80079-182">X</span></span>|<span data-ttu-id="80079-183">Yok</span><span class="sxs-lookup"><span data-stu-id="80079-183">N/A</span></span>||  
|`eDisableRuntime`|<span data-ttu-id="80079-184">X</span><span class="sxs-lookup"><span data-stu-id="80079-184">X</span></span>|<span data-ttu-id="80079-185">X</span><span class="sxs-lookup"><span data-stu-id="80079-185">X</span></span>|<span data-ttu-id="80079-186">X</span><span class="sxs-lookup"><span data-stu-id="80079-186">X</span></span>|<span data-ttu-id="80079-187">X</span><span class="sxs-lookup"><span data-stu-id="80079-187">X</span></span>|<span data-ttu-id="80079-188">X</span><span class="sxs-lookup"><span data-stu-id="80079-188">X</span></span>|<span data-ttu-id="80079-189">Yok</span><span class="sxs-lookup"><span data-stu-id="80079-189">N/A</span></span>||  
  
## <a name="requirements"></a><span data-ttu-id="80079-190">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="80079-190">Requirements</span></span>  
 <span data-ttu-id="80079-191">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80079-191">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80079-192">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="80079-192">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="80079-193">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="80079-193">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="80079-194">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80079-194">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80079-195">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80079-195">See also</span></span>

- [<span data-ttu-id="80079-196">EClrFailure Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="80079-196">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="80079-197">EPolicyAction Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="80079-197">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="80079-198">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="80079-198">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="80079-199">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="80079-199">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
