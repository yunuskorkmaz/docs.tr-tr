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
ms.openlocfilehash: 8f44247ca7904a40f5ebc092d95c2e08b6048438
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725579"
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a><span data-ttu-id="f5769-102">ICLRPolicyManager::SetActionOnFailure Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f5769-102">ICLRPolicyManager::SetActionOnFailure Method</span></span>

<span data-ttu-id="f5769-103">Belirtilen hata oluştuğunda ortak dil çalışma zamanının (CLR) yapması gereken ilke eylemini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f5769-103">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5769-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="f5769-104">Syntax</span></span>  
  
```cpp  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5769-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f5769-105">Parameters</span></span>  

 `failure`  
 <span data-ttu-id="f5769-106">'ndaki İşlem gerçekleştirilecek hata türünü belirten [EClrFailure](eclrfailure-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="f5769-106">[in] One of the [EClrFailure](eclrfailure-enumeration.md) values, indicating the type of failure for which to take action.</span></span>  
  
 `action`  
 <span data-ttu-id="f5769-107">'ndaki Bir hata oluştuğunda gerçekleştirilecek eylemi belirten [EPolicyAction](epolicyaction-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="f5769-107">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action to be taken when a failure occurs.</span></span> <span data-ttu-id="f5769-108">Desteklenen değerlerin bir listesi için, açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="f5769-108">For a list of supported values, see the Remarks section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f5769-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f5769-109">Return Value</span></span>  
  
|<span data-ttu-id="f5769-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f5769-110">HRESULT</span></span>|<span data-ttu-id="f5769-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f5769-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f5769-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="f5769-112">S_OK</span></span>|<span data-ttu-id="f5769-113">`SetActionOnFailure` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="f5769-113">`SetActionOnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="f5769-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f5769-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f5769-115">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="f5769-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f5769-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f5769-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f5769-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="f5769-117">The call timed out.</span></span>|  
|<span data-ttu-id="f5769-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f5769-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f5769-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="f5769-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f5769-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f5769-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f5769-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="f5769-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f5769-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f5769-122">E_FAIL</span></span>|<span data-ttu-id="f5769-123">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="f5769-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f5769-124">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f5769-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f5769-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="f5769-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f5769-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f5769-126">E_INVALIDARG</span></span>|<span data-ttu-id="f5769-127">Belirtilen işlem için bir ilke eylemi ayarlanamaz veya işlem için geçersiz bir ilke eylemi belirtildi.</span><span class="sxs-lookup"><span data-stu-id="f5769-127">A policy action cannot be set for the specified operation, or an invalid policy action was specified for the operation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5769-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f5769-128">Remarks</span></span>  

 <span data-ttu-id="f5769-129">Varsayılan olarak, CLR bellek gibi bir kaynağı ayıramadığında bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f5769-129">By default, the CLR throws an exception when it fails to allocate a resource such as memory.</span></span> <span data-ttu-id="f5769-130">`SetActionOnFailure` konağın hata sonrasında gerçekleştirilecek ilke eylemini belirterek bu davranışı geçersiz kılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="f5769-130">`SetActionOnFailure` allows the host to override this behavior by specifying the policy action to take upon failure.</span></span> <span data-ttu-id="f5769-131">Aşağıdaki tabloda, desteklenen [EClrFailure](eclrfailure-enumeration.md) ve [EPolicyAction](epolicyaction-enumeration.md) değerlerinin birleşimleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f5769-131">The following table shows the combinations of [EClrFailure](eclrfailure-enumeration.md) and [EPolicyAction](epolicyaction-enumeration.md) values that are supported.</span></span> <span data-ttu-id="f5769-132">(FAIL_ ön eki [EClrFailure](eclrfailure-enumeration.md) değerlerinden çıkarılır.)</span><span class="sxs-lookup"><span data-stu-id="f5769-132">(The FAIL_ prefix is omitted from [EClrFailure](eclrfailure-enumeration.md) values.)</span></span>  
  
||<span data-ttu-id="f5769-133">CriticalHandle dışı kaynak</span><span class="sxs-lookup"><span data-stu-id="f5769-133">NonCriticalResource</span></span>|<span data-ttu-id="f5769-134">Kritikkaynak</span><span class="sxs-lookup"><span data-stu-id="f5769-134">CriticalResource</span></span>|<span data-ttu-id="f5769-135">FatalRuntime</span><span class="sxs-lookup"><span data-stu-id="f5769-135">FatalRuntime</span></span>|<span data-ttu-id="f5769-136">OrphanedLock</span><span class="sxs-lookup"><span data-stu-id="f5769-136">OrphanedLock</span></span>|<span data-ttu-id="f5769-137">StackOverflow</span><span class="sxs-lookup"><span data-stu-id="f5769-137">StackOverflow</span></span>|<span data-ttu-id="f5769-138">Accessihlaihlaline</span><span class="sxs-lookup"><span data-stu-id="f5769-138">AccessViolation</span></span>|<span data-ttu-id="f5769-139">CodeContract</span><span class="sxs-lookup"><span data-stu-id="f5769-139">CodeContract</span></span>|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|<span data-ttu-id="f5769-140">X</span><span class="sxs-lookup"><span data-stu-id="f5769-140">X</span></span>|<span data-ttu-id="f5769-141">X</span><span class="sxs-lookup"><span data-stu-id="f5769-141">X</span></span>||||<span data-ttu-id="f5769-142">YOK</span><span class="sxs-lookup"><span data-stu-id="f5769-142">N/A</span></span>||  
|<span data-ttu-id="f5769-143">eThrowException</span><span class="sxs-lookup"><span data-stu-id="f5769-143">eThrowException</span></span>|<span data-ttu-id="f5769-144">X</span><span class="sxs-lookup"><span data-stu-id="f5769-144">X</span></span>|<span data-ttu-id="f5769-145">X</span><span class="sxs-lookup"><span data-stu-id="f5769-145">X</span></span>||||<span data-ttu-id="f5769-146">YOK</span><span class="sxs-lookup"><span data-stu-id="f5769-146">N/A</span></span>||  
|`eAbortThread`|<span data-ttu-id="f5769-147">X</span><span class="sxs-lookup"><span data-stu-id="f5769-147">X</span></span>|<span data-ttu-id="f5769-148">X</span><span class="sxs-lookup"><span data-stu-id="f5769-148">X</span></span>||||<span data-ttu-id="f5769-149">YOK</span><span class="sxs-lookup"><span data-stu-id="f5769-149">N/A</span></span>|<span data-ttu-id="f5769-150">X</span><span class="sxs-lookup"><span data-stu-id="f5769-150">X</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="f5769-151">X</span><span class="sxs-lookup"><span data-stu-id="f5769-151">X</span></span>|<span data-ttu-id="f5769-152">X</span><span class="sxs-lookup"><span data-stu-id="f5769-152">X</span></span>||||<span data-ttu-id="f5769-153">YOK</span><span class="sxs-lookup"><span data-stu-id="f5769-153">N/A</span></span>|<span data-ttu-id="f5769-154">X</span><span class="sxs-lookup"><span data-stu-id="f5769-154">X</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="f5769-155">X</span><span class="sxs-lookup"><span data-stu-id="f5769-155">X</span></span>|<span data-ttu-id="f5769-156">X</span><span class="sxs-lookup"><span data-stu-id="f5769-156">X</span></span>||<span data-ttu-id="f5769-157">X</span><span class="sxs-lookup"><span data-stu-id="f5769-157">X</span></span>||<span data-ttu-id="f5769-158">YOK</span><span class="sxs-lookup"><span data-stu-id="f5769-158">N/A</span></span>|<span data-ttu-id="f5769-159">X</span><span class="sxs-lookup"><span data-stu-id="f5769-159">X</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="f5769-160">X</span><span class="sxs-lookup"><span data-stu-id="f5769-160">X</span></span>|<span data-ttu-id="f5769-161">X</span><span class="sxs-lookup"><span data-stu-id="f5769-161">X</span></span>||<span data-ttu-id="f5769-162">X</span><span class="sxs-lookup"><span data-stu-id="f5769-162">X</span></span>|<span data-ttu-id="f5769-163">X</span><span class="sxs-lookup"><span data-stu-id="f5769-163">X</span></span>|<span data-ttu-id="f5769-164">YOK</span><span class="sxs-lookup"><span data-stu-id="f5769-164">N/A</span></span>|<span data-ttu-id="f5769-165">X</span><span class="sxs-lookup"><span data-stu-id="f5769-165">X</span></span>|  
|`eExitProcess`|<span data-ttu-id="f5769-166">X</span><span class="sxs-lookup"><span data-stu-id="f5769-166">X</span></span>|<span data-ttu-id="f5769-167">X</span><span class="sxs-lookup"><span data-stu-id="f5769-167">X</span></span>||<span data-ttu-id="f5769-168">X</span><span class="sxs-lookup"><span data-stu-id="f5769-168">X</span></span>|<span data-ttu-id="f5769-169">X</span><span class="sxs-lookup"><span data-stu-id="f5769-169">X</span></span>|<span data-ttu-id="f5769-170">YOK</span><span class="sxs-lookup"><span data-stu-id="f5769-170">N/A</span></span>|<span data-ttu-id="f5769-171">X</span><span class="sxs-lookup"><span data-stu-id="f5769-171">X</span></span>|  
|<span data-ttu-id="f5769-172">eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="f5769-172">eFastExitProcess</span></span>|<span data-ttu-id="f5769-173">X</span><span class="sxs-lookup"><span data-stu-id="f5769-173">X</span></span>|<span data-ttu-id="f5769-174">X</span><span class="sxs-lookup"><span data-stu-id="f5769-174">X</span></span>||<span data-ttu-id="f5769-175">X</span><span class="sxs-lookup"><span data-stu-id="f5769-175">X</span></span>|<span data-ttu-id="f5769-176">X</span><span class="sxs-lookup"><span data-stu-id="f5769-176">X</span></span>|<span data-ttu-id="f5769-177">YOK</span><span class="sxs-lookup"><span data-stu-id="f5769-177">N/A</span></span>||  
|`eRudeExitProcess`|<span data-ttu-id="f5769-178">X</span><span class="sxs-lookup"><span data-stu-id="f5769-178">X</span></span>|<span data-ttu-id="f5769-179">X</span><span class="sxs-lookup"><span data-stu-id="f5769-179">X</span></span>|<span data-ttu-id="f5769-180">X</span><span class="sxs-lookup"><span data-stu-id="f5769-180">X</span></span>|<span data-ttu-id="f5769-181">X</span><span class="sxs-lookup"><span data-stu-id="f5769-181">X</span></span>|<span data-ttu-id="f5769-182">X</span><span class="sxs-lookup"><span data-stu-id="f5769-182">X</span></span>|<span data-ttu-id="f5769-183">YOK</span><span class="sxs-lookup"><span data-stu-id="f5769-183">N/A</span></span>||  
|`eDisableRuntime`|<span data-ttu-id="f5769-184">X</span><span class="sxs-lookup"><span data-stu-id="f5769-184">X</span></span>|<span data-ttu-id="f5769-185">X</span><span class="sxs-lookup"><span data-stu-id="f5769-185">X</span></span>|<span data-ttu-id="f5769-186">X</span><span class="sxs-lookup"><span data-stu-id="f5769-186">X</span></span>|<span data-ttu-id="f5769-187">X</span><span class="sxs-lookup"><span data-stu-id="f5769-187">X</span></span>|<span data-ttu-id="f5769-188">X</span><span class="sxs-lookup"><span data-stu-id="f5769-188">X</span></span>|<span data-ttu-id="f5769-189">YOK</span><span class="sxs-lookup"><span data-stu-id="f5769-189">N/A</span></span>||  
  
## <a name="requirements"></a><span data-ttu-id="f5769-190">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f5769-190">Requirements</span></span>  

 <span data-ttu-id="f5769-191">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5769-191">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5769-192">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f5769-192">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f5769-193">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="f5769-193">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f5769-194">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5769-194">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5769-195">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5769-195">See also</span></span>

- [<span data-ttu-id="f5769-196">EClrFailure Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="f5769-196">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="f5769-197">EPolicyAction Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="f5769-197">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="f5769-198">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f5769-198">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="f5769-199">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f5769-199">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
