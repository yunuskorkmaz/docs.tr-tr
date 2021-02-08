---
description: ': ICLRPolicyManager:: SetActionOnFailure yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 67d3ca5d7924caf0a768b4de53b4b24f1c72fa27
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789807"
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a><span data-ttu-id="44c16-103">ICLRPolicyManager::SetActionOnFailure Yöntemi</span><span class="sxs-lookup"><span data-stu-id="44c16-103">ICLRPolicyManager::SetActionOnFailure Method</span></span>

<span data-ttu-id="44c16-104">Belirtilen hata oluştuğunda ortak dil çalışma zamanının (CLR) yapması gereken ilke eylemini belirtir.</span><span class="sxs-lookup"><span data-stu-id="44c16-104">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44c16-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="44c16-105">Syntax</span></span>  
  
```cpp  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44c16-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="44c16-106">Parameters</span></span>  

 `failure`  
 <span data-ttu-id="44c16-107">'ndaki İşlem gerçekleştirilecek hata türünü belirten [EClrFailure](eclrfailure-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="44c16-107">[in] One of the [EClrFailure](eclrfailure-enumeration.md) values, indicating the type of failure for which to take action.</span></span>  
  
 `action`  
 <span data-ttu-id="44c16-108">'ndaki Bir hata oluştuğunda gerçekleştirilecek eylemi belirten [EPolicyAction](epolicyaction-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="44c16-108">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action to be taken when a failure occurs.</span></span> <span data-ttu-id="44c16-109">Desteklenen değerlerin bir listesi için, açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="44c16-109">For a list of supported values, see the Remarks section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="44c16-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="44c16-110">Return Value</span></span>  
  
|<span data-ttu-id="44c16-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="44c16-111">HRESULT</span></span>|<span data-ttu-id="44c16-112">Description</span><span class="sxs-lookup"><span data-stu-id="44c16-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="44c16-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="44c16-113">S_OK</span></span>|<span data-ttu-id="44c16-114">`SetActionOnFailure` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="44c16-114">`SetActionOnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="44c16-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="44c16-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="44c16-116">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="44c16-116">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="44c16-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="44c16-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="44c16-118">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="44c16-118">The call timed out.</span></span>|  
|<span data-ttu-id="44c16-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="44c16-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="44c16-120">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="44c16-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="44c16-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="44c16-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="44c16-122">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="44c16-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="44c16-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="44c16-123">E_FAIL</span></span>|<span data-ttu-id="44c16-124">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="44c16-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="44c16-125">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="44c16-125">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="44c16-126">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="44c16-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="44c16-127">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="44c16-127">E_INVALIDARG</span></span>|<span data-ttu-id="44c16-128">Belirtilen işlem için bir ilke eylemi ayarlanamaz veya işlem için geçersiz bir ilke eylemi belirtildi.</span><span class="sxs-lookup"><span data-stu-id="44c16-128">A policy action cannot be set for the specified operation, or an invalid policy action was specified for the operation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44c16-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="44c16-129">Remarks</span></span>  

 <span data-ttu-id="44c16-130">Varsayılan olarak, CLR bellek gibi bir kaynağı ayıramadığında bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="44c16-130">By default, the CLR throws an exception when it fails to allocate a resource such as memory.</span></span> <span data-ttu-id="44c16-131">`SetActionOnFailure` konağın hata sonrasında gerçekleştirilecek ilke eylemini belirterek bu davranışı geçersiz kılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="44c16-131">`SetActionOnFailure` allows the host to override this behavior by specifying the policy action to take upon failure.</span></span> <span data-ttu-id="44c16-132">Aşağıdaki tabloda, desteklenen [EClrFailure](eclrfailure-enumeration.md) ve [EPolicyAction](epolicyaction-enumeration.md) değerlerinin birleşimleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="44c16-132">The following table shows the combinations of [EClrFailure](eclrfailure-enumeration.md) and [EPolicyAction](epolicyaction-enumeration.md) values that are supported.</span></span> <span data-ttu-id="44c16-133">(FAIL_ ön eki [EClrFailure](eclrfailure-enumeration.md) değerlerinden çıkarılır.)</span><span class="sxs-lookup"><span data-stu-id="44c16-133">(The FAIL_ prefix is omitted from [EClrFailure](eclrfailure-enumeration.md) values.)</span></span>  
  
||<span data-ttu-id="44c16-134">CriticalHandle dışı kaynak</span><span class="sxs-lookup"><span data-stu-id="44c16-134">NonCriticalResource</span></span>|<span data-ttu-id="44c16-135">Kritikkaynak</span><span class="sxs-lookup"><span data-stu-id="44c16-135">CriticalResource</span></span>|<span data-ttu-id="44c16-136">FatalRuntime</span><span class="sxs-lookup"><span data-stu-id="44c16-136">FatalRuntime</span></span>|<span data-ttu-id="44c16-137">OrphanedLock</span><span class="sxs-lookup"><span data-stu-id="44c16-137">OrphanedLock</span></span>|<span data-ttu-id="44c16-138">StackOverflow</span><span class="sxs-lookup"><span data-stu-id="44c16-138">StackOverflow</span></span>|<span data-ttu-id="44c16-139">Accessihlaihlaline</span><span class="sxs-lookup"><span data-stu-id="44c16-139">AccessViolation</span></span>|<span data-ttu-id="44c16-140">CodeContract</span><span class="sxs-lookup"><span data-stu-id="44c16-140">CodeContract</span></span>|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|<span data-ttu-id="44c16-141">X</span><span class="sxs-lookup"><span data-stu-id="44c16-141">X</span></span>|<span data-ttu-id="44c16-142">X</span><span class="sxs-lookup"><span data-stu-id="44c16-142">X</span></span>||||<span data-ttu-id="44c16-143">Yok</span><span class="sxs-lookup"><span data-stu-id="44c16-143">N/A</span></span>||  
|<span data-ttu-id="44c16-144">eThrowException</span><span class="sxs-lookup"><span data-stu-id="44c16-144">eThrowException</span></span>|<span data-ttu-id="44c16-145">X</span><span class="sxs-lookup"><span data-stu-id="44c16-145">X</span></span>|<span data-ttu-id="44c16-146">X</span><span class="sxs-lookup"><span data-stu-id="44c16-146">X</span></span>||||<span data-ttu-id="44c16-147">Yok</span><span class="sxs-lookup"><span data-stu-id="44c16-147">N/A</span></span>||  
|`eAbortThread`|<span data-ttu-id="44c16-148">X</span><span class="sxs-lookup"><span data-stu-id="44c16-148">X</span></span>|<span data-ttu-id="44c16-149">X</span><span class="sxs-lookup"><span data-stu-id="44c16-149">X</span></span>||||<span data-ttu-id="44c16-150">Yok</span><span class="sxs-lookup"><span data-stu-id="44c16-150">N/A</span></span>|<span data-ttu-id="44c16-151">X</span><span class="sxs-lookup"><span data-stu-id="44c16-151">X</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="44c16-152">X</span><span class="sxs-lookup"><span data-stu-id="44c16-152">X</span></span>|<span data-ttu-id="44c16-153">X</span><span class="sxs-lookup"><span data-stu-id="44c16-153">X</span></span>||||<span data-ttu-id="44c16-154">Yok</span><span class="sxs-lookup"><span data-stu-id="44c16-154">N/A</span></span>|<span data-ttu-id="44c16-155">X</span><span class="sxs-lookup"><span data-stu-id="44c16-155">X</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="44c16-156">X</span><span class="sxs-lookup"><span data-stu-id="44c16-156">X</span></span>|<span data-ttu-id="44c16-157">X</span><span class="sxs-lookup"><span data-stu-id="44c16-157">X</span></span>||<span data-ttu-id="44c16-158">X</span><span class="sxs-lookup"><span data-stu-id="44c16-158">X</span></span>||<span data-ttu-id="44c16-159">Yok</span><span class="sxs-lookup"><span data-stu-id="44c16-159">N/A</span></span>|<span data-ttu-id="44c16-160">X</span><span class="sxs-lookup"><span data-stu-id="44c16-160">X</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="44c16-161">X</span><span class="sxs-lookup"><span data-stu-id="44c16-161">X</span></span>|<span data-ttu-id="44c16-162">X</span><span class="sxs-lookup"><span data-stu-id="44c16-162">X</span></span>||<span data-ttu-id="44c16-163">X</span><span class="sxs-lookup"><span data-stu-id="44c16-163">X</span></span>|<span data-ttu-id="44c16-164">X</span><span class="sxs-lookup"><span data-stu-id="44c16-164">X</span></span>|<span data-ttu-id="44c16-165">Yok</span><span class="sxs-lookup"><span data-stu-id="44c16-165">N/A</span></span>|<span data-ttu-id="44c16-166">X</span><span class="sxs-lookup"><span data-stu-id="44c16-166">X</span></span>|  
|`eExitProcess`|<span data-ttu-id="44c16-167">X</span><span class="sxs-lookup"><span data-stu-id="44c16-167">X</span></span>|<span data-ttu-id="44c16-168">X</span><span class="sxs-lookup"><span data-stu-id="44c16-168">X</span></span>||<span data-ttu-id="44c16-169">X</span><span class="sxs-lookup"><span data-stu-id="44c16-169">X</span></span>|<span data-ttu-id="44c16-170">X</span><span class="sxs-lookup"><span data-stu-id="44c16-170">X</span></span>|<span data-ttu-id="44c16-171">Yok</span><span class="sxs-lookup"><span data-stu-id="44c16-171">N/A</span></span>|<span data-ttu-id="44c16-172">X</span><span class="sxs-lookup"><span data-stu-id="44c16-172">X</span></span>|  
|<span data-ttu-id="44c16-173">eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="44c16-173">eFastExitProcess</span></span>|<span data-ttu-id="44c16-174">X</span><span class="sxs-lookup"><span data-stu-id="44c16-174">X</span></span>|<span data-ttu-id="44c16-175">X</span><span class="sxs-lookup"><span data-stu-id="44c16-175">X</span></span>||<span data-ttu-id="44c16-176">X</span><span class="sxs-lookup"><span data-stu-id="44c16-176">X</span></span>|<span data-ttu-id="44c16-177">X</span><span class="sxs-lookup"><span data-stu-id="44c16-177">X</span></span>|<span data-ttu-id="44c16-178">Yok</span><span class="sxs-lookup"><span data-stu-id="44c16-178">N/A</span></span>||  
|`eRudeExitProcess`|<span data-ttu-id="44c16-179">X</span><span class="sxs-lookup"><span data-stu-id="44c16-179">X</span></span>|<span data-ttu-id="44c16-180">X</span><span class="sxs-lookup"><span data-stu-id="44c16-180">X</span></span>|<span data-ttu-id="44c16-181">X</span><span class="sxs-lookup"><span data-stu-id="44c16-181">X</span></span>|<span data-ttu-id="44c16-182">X</span><span class="sxs-lookup"><span data-stu-id="44c16-182">X</span></span>|<span data-ttu-id="44c16-183">X</span><span class="sxs-lookup"><span data-stu-id="44c16-183">X</span></span>|<span data-ttu-id="44c16-184">Yok</span><span class="sxs-lookup"><span data-stu-id="44c16-184">N/A</span></span>||  
|`eDisableRuntime`|<span data-ttu-id="44c16-185">X</span><span class="sxs-lookup"><span data-stu-id="44c16-185">X</span></span>|<span data-ttu-id="44c16-186">X</span><span class="sxs-lookup"><span data-stu-id="44c16-186">X</span></span>|<span data-ttu-id="44c16-187">X</span><span class="sxs-lookup"><span data-stu-id="44c16-187">X</span></span>|<span data-ttu-id="44c16-188">X</span><span class="sxs-lookup"><span data-stu-id="44c16-188">X</span></span>|<span data-ttu-id="44c16-189">X</span><span class="sxs-lookup"><span data-stu-id="44c16-189">X</span></span>|<span data-ttu-id="44c16-190">Yok</span><span class="sxs-lookup"><span data-stu-id="44c16-190">N/A</span></span>||  
  
## <a name="requirements"></a><span data-ttu-id="44c16-191">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="44c16-191">Requirements</span></span>  

 <span data-ttu-id="44c16-192">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44c16-192">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44c16-193">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="44c16-193">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="44c16-194">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="44c16-194">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="44c16-195">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44c16-195">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44c16-196">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44c16-196">See also</span></span>

- [<span data-ttu-id="44c16-197">EClrFailure Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="44c16-197">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="44c16-198">EPolicyAction Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="44c16-198">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="44c16-199">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="44c16-199">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="44c16-200">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="44c16-200">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
