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
ms.openlocfilehash: 727cd82226b9a59c4879ffea5e87f93dd5fe38c9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504114"
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a><span data-ttu-id="ceedc-102">ICLRPolicyManager::SetActionOnFailure Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ceedc-102">ICLRPolicyManager::SetActionOnFailure Method</span></span>
<span data-ttu-id="ceedc-103">Belirtilen hata oluştuğunda ortak dil çalışma zamanının (CLR) yapması gereken ilke eylemini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ceedc-103">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ceedc-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ceedc-104">Syntax</span></span>  
  
```cpp  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ceedc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ceedc-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="ceedc-106">'ndaki İşlem gerçekleştirilecek hata türünü belirten [EClrFailure](eclrfailure-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="ceedc-106">[in] One of the [EClrFailure](eclrfailure-enumeration.md) values, indicating the type of failure for which to take action.</span></span>  
  
 `action`  
 <span data-ttu-id="ceedc-107">'ndaki Bir hata oluştuğunda gerçekleştirilecek eylemi belirten [EPolicyAction](epolicyaction-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="ceedc-107">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action to be taken when a failure occurs.</span></span> <span data-ttu-id="ceedc-108">Desteklenen değerlerin bir listesi için, açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="ceedc-108">For a list of supported values, see the Remarks section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ceedc-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ceedc-109">Return Value</span></span>  
  
|<span data-ttu-id="ceedc-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ceedc-110">HRESULT</span></span>|<span data-ttu-id="ceedc-111">Description</span><span class="sxs-lookup"><span data-stu-id="ceedc-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ceedc-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="ceedc-112">S_OK</span></span>|<span data-ttu-id="ceedc-113">`SetActionOnFailure`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="ceedc-113">`SetActionOnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="ceedc-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ceedc-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ceedc-115">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="ceedc-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ceedc-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ceedc-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ceedc-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="ceedc-117">The call timed out.</span></span>|  
|<span data-ttu-id="ceedc-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ceedc-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ceedc-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="ceedc-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ceedc-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ceedc-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ceedc-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="ceedc-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ceedc-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ceedc-122">E_FAIL</span></span>|<span data-ttu-id="ceedc-123">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="ceedc-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ceedc-124">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ceedc-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ceedc-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="ceedc-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ceedc-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="ceedc-126">E_INVALIDARG</span></span>|<span data-ttu-id="ceedc-127">Belirtilen işlem için bir ilke eylemi ayarlanamaz veya işlem için geçersiz bir ilke eylemi belirtildi.</span><span class="sxs-lookup"><span data-stu-id="ceedc-127">A policy action cannot be set for the specified operation, or an invalid policy action was specified for the operation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ceedc-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ceedc-128">Remarks</span></span>  
 <span data-ttu-id="ceedc-129">Varsayılan olarak, CLR bellek gibi bir kaynağı ayıramadığında bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ceedc-129">By default, the CLR throws an exception when it fails to allocate a resource such as memory.</span></span> <span data-ttu-id="ceedc-130">`SetActionOnFailure`konağın hata sonrasında gerçekleştirilecek ilke eylemini belirterek bu davranışı geçersiz kılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="ceedc-130">`SetActionOnFailure` allows the host to override this behavior by specifying the policy action to take upon failure.</span></span> <span data-ttu-id="ceedc-131">Aşağıdaki tabloda, desteklenen [EClrFailure](eclrfailure-enumeration.md) ve [EPolicyAction](epolicyaction-enumeration.md) değerlerinin birleşimleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ceedc-131">The following table shows the combinations of [EClrFailure](eclrfailure-enumeration.md) and [EPolicyAction](epolicyaction-enumeration.md) values that are supported.</span></span> <span data-ttu-id="ceedc-132">(FAIL_ ön eki [EClrFailure](eclrfailure-enumeration.md) değerlerinden çıkarılır.)</span><span class="sxs-lookup"><span data-stu-id="ceedc-132">(The FAIL_ prefix is omitted from [EClrFailure](eclrfailure-enumeration.md) values.)</span></span>  
  
||<span data-ttu-id="ceedc-133">CriticalHandle dışı kaynak</span><span class="sxs-lookup"><span data-stu-id="ceedc-133">NonCriticalResource</span></span>|<span data-ttu-id="ceedc-134">Kritikkaynak</span><span class="sxs-lookup"><span data-stu-id="ceedc-134">CriticalResource</span></span>|<span data-ttu-id="ceedc-135">FatalRuntime</span><span class="sxs-lookup"><span data-stu-id="ceedc-135">FatalRuntime</span></span>|<span data-ttu-id="ceedc-136">OrphanedLock</span><span class="sxs-lookup"><span data-stu-id="ceedc-136">OrphanedLock</span></span>|<span data-ttu-id="ceedc-137">StackOverflow</span><span class="sxs-lookup"><span data-stu-id="ceedc-137">StackOverflow</span></span>|<span data-ttu-id="ceedc-138">Accessihlaihlaline</span><span class="sxs-lookup"><span data-stu-id="ceedc-138">AccessViolation</span></span>|<span data-ttu-id="ceedc-139">CodeContract</span><span class="sxs-lookup"><span data-stu-id="ceedc-139">CodeContract</span></span>|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|<span data-ttu-id="ceedc-140">X</span><span class="sxs-lookup"><span data-stu-id="ceedc-140">X</span></span>|<span data-ttu-id="ceedc-141">X</span><span class="sxs-lookup"><span data-stu-id="ceedc-141">X</span></span>||||<span data-ttu-id="ceedc-142">Yok</span><span class="sxs-lookup"><span data-stu-id="ceedc-142">N/A</span></span>||  
|<span data-ttu-id="ceedc-143">eThrowException</span><span class="sxs-lookup"><span data-stu-id="ceedc-143">eThrowException</span></span>|<span data-ttu-id="ceedc-144">X</span><span class="sxs-lookup"><span data-stu-id="ceedc-144">X</span></span>|<span data-ttu-id="ceedc-145">X</span><span class="sxs-lookup"><span data-stu-id="ceedc-145">X</span></span>||||<span data-ttu-id="ceedc-146">Yok</span><span class="sxs-lookup"><span data-stu-id="ceedc-146">N/A</span></span>||  
|`eAbortThread`|<span data-ttu-id="ceedc-147">X</span><span class="sxs-lookup"><span data-stu-id="ceedc-147">X</span></span>|<span data-ttu-id="ceedc-148">X</span><span class="sxs-lookup"><span data-stu-id="ceedc-148">X</span></span>||||<span data-ttu-id="ceedc-149">Yok</span><span class="sxs-lookup"><span data-stu-id="ceedc-149">N/A</span></span>|<span data-ttu-id="ceedc-150">X</span><span class="sxs-lookup"><span data-stu-id="ceedc-150">X</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="ceedc-151">X</span><span class="sxs-lookup"><span data-stu-id="ceedc-151">X</span></span>|<span data-ttu-id="ceedc-152">X</span><span class="sxs-lookup"><span data-stu-id="ceedc-152">X</span></span>||||<span data-ttu-id="ceedc-153">Yok</span><span class="sxs-lookup"><span data-stu-id="ceedc-153">N/A</span></span>|<span data-ttu-id="ceedc-154">X</span><span class="sxs-lookup"><span data-stu-id="ceedc-154">X</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="ceedc-155">X</span><span class="sxs-lookup"><span data-stu-id="ceedc-155">X</span></span>|<span data-ttu-id="ceedc-156">X</span><span class="sxs-lookup"><span data-stu-id="ceedc-156">X</span></span>||<span data-ttu-id="ceedc-157">X</span><span class="sxs-lookup"><span data-stu-id="ceedc-157">X</span></span>||<span data-ttu-id="ceedc-158">Yok</span><span class="sxs-lookup"><span data-stu-id="ceedc-158">N/A</span></span>|<span data-ttu-id="ceedc-159">X</span><span class="sxs-lookup"><span data-stu-id="ceedc-159">X</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="ceedc-160">X</span><span class="sxs-lookup"><span data-stu-id="ceedc-160">X</span></span>|<span data-ttu-id="ceedc-161">X</span><span class="sxs-lookup"><span data-stu-id="ceedc-161">X</span></span>||<span data-ttu-id="ceedc-162">X</span><span class="sxs-lookup"><span data-stu-id="ceedc-162">X</span></span>|<span data-ttu-id="ceedc-163">X</span><span class="sxs-lookup"><span data-stu-id="ceedc-163">X</span></span>|<span data-ttu-id="ceedc-164">Yok</span><span class="sxs-lookup"><span data-stu-id="ceedc-164">N/A</span></span>|<span data-ttu-id="ceedc-165">X</span><span class="sxs-lookup"><span data-stu-id="ceedc-165">X</span></span>|  
|`eExitProcess`|<span data-ttu-id="ceedc-166">X</span><span class="sxs-lookup"><span data-stu-id="ceedc-166">X</span></span>|<span data-ttu-id="ceedc-167">X</span><span class="sxs-lookup"><span data-stu-id="ceedc-167">X</span></span>||<span data-ttu-id="ceedc-168">X</span><span class="sxs-lookup"><span data-stu-id="ceedc-168">X</span></span>|<span data-ttu-id="ceedc-169">X</span><span class="sxs-lookup"><span data-stu-id="ceedc-169">X</span></span>|<span data-ttu-id="ceedc-170">Yok</span><span class="sxs-lookup"><span data-stu-id="ceedc-170">N/A</span></span>|<span data-ttu-id="ceedc-171">X</span><span class="sxs-lookup"><span data-stu-id="ceedc-171">X</span></span>|  
|<span data-ttu-id="ceedc-172">eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="ceedc-172">eFastExitProcess</span></span>|<span data-ttu-id="ceedc-173">X</span><span class="sxs-lookup"><span data-stu-id="ceedc-173">X</span></span>|<span data-ttu-id="ceedc-174">X</span><span class="sxs-lookup"><span data-stu-id="ceedc-174">X</span></span>||<span data-ttu-id="ceedc-175">X</span><span class="sxs-lookup"><span data-stu-id="ceedc-175">X</span></span>|<span data-ttu-id="ceedc-176">X</span><span class="sxs-lookup"><span data-stu-id="ceedc-176">X</span></span>|<span data-ttu-id="ceedc-177">Yok</span><span class="sxs-lookup"><span data-stu-id="ceedc-177">N/A</span></span>||  
|`eRudeExitProcess`|<span data-ttu-id="ceedc-178">X</span><span class="sxs-lookup"><span data-stu-id="ceedc-178">X</span></span>|<span data-ttu-id="ceedc-179">X</span><span class="sxs-lookup"><span data-stu-id="ceedc-179">X</span></span>|<span data-ttu-id="ceedc-180">X</span><span class="sxs-lookup"><span data-stu-id="ceedc-180">X</span></span>|<span data-ttu-id="ceedc-181">X</span><span class="sxs-lookup"><span data-stu-id="ceedc-181">X</span></span>|<span data-ttu-id="ceedc-182">X</span><span class="sxs-lookup"><span data-stu-id="ceedc-182">X</span></span>|<span data-ttu-id="ceedc-183">Yok</span><span class="sxs-lookup"><span data-stu-id="ceedc-183">N/A</span></span>||  
|`eDisableRuntime`|<span data-ttu-id="ceedc-184">X</span><span class="sxs-lookup"><span data-stu-id="ceedc-184">X</span></span>|<span data-ttu-id="ceedc-185">X</span><span class="sxs-lookup"><span data-stu-id="ceedc-185">X</span></span>|<span data-ttu-id="ceedc-186">X</span><span class="sxs-lookup"><span data-stu-id="ceedc-186">X</span></span>|<span data-ttu-id="ceedc-187">X</span><span class="sxs-lookup"><span data-stu-id="ceedc-187">X</span></span>|<span data-ttu-id="ceedc-188">X</span><span class="sxs-lookup"><span data-stu-id="ceedc-188">X</span></span>|<span data-ttu-id="ceedc-189">Yok</span><span class="sxs-lookup"><span data-stu-id="ceedc-189">N/A</span></span>||  
  
## <a name="requirements"></a><span data-ttu-id="ceedc-190">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ceedc-190">Requirements</span></span>  
 <span data-ttu-id="ceedc-191">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ceedc-191">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ceedc-192">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ceedc-192">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ceedc-193">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="ceedc-193">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ceedc-194">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ceedc-194">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ceedc-195">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ceedc-195">See also</span></span>

- [<span data-ttu-id="ceedc-196">EClrFailure Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="ceedc-196">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="ceedc-197">EPolicyAction Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="ceedc-197">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="ceedc-198">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ceedc-198">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="ceedc-199">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ceedc-199">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
