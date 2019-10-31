---
title: ICLRPolicyManager::SetActionOnTimeout Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetActionOnTimeout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetActionOnTimeout
helpviewer_keywords:
- SetActionOnTimeout method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnTimeout method [.NET Framework hosting]
ms.assetid: 38439fa1-2b99-4fa8-a6ec-08afc0f83b9c
topic_type:
- apiref
ms.openlocfilehash: 9ef906ed5e8a6985c084741bf06b683da79c546e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140792"
---
# <a name="iclrpolicymanagersetactionontimeout-method"></a><span data-ttu-id="a9de2-102">ICLRPolicyManager::SetActionOnTimeout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a9de2-102">ICLRPolicyManager::SetActionOnTimeout Method</span></span>
<span data-ttu-id="a9de2-103">Belirtilen işlem zaman aşımına uğrarsa ortak dil çalışma zamanının (CLR) yapması gereken ilke eylemini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a9de2-103">Specifies the policy action the common language runtime (CLR) should take when the specified operation times out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9de2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a9de2-104">Syntax</span></span>  
  
```cpp  
HRESULT SetActionOnTimeout (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9de2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a9de2-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="a9de2-106">'ndaki Zaman aşımı eyleminin belirtme işlemini belirten [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="a9de2-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the operation for which to specify the timeout action.</span></span> <span data-ttu-id="a9de2-107">Aşağıdaki değerler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="a9de2-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="a9de2-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="a9de2-108">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="a9de2-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="a9de2-109">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="a9de2-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="a9de2-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="a9de2-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="a9de2-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `action`  
 <span data-ttu-id="a9de2-112">'ndaki İşlem zaman aşımına uğrarsa gerçekleştirilecek ilke eylemini gösteren [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="a9de2-112">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action to be taken when the operation times out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a9de2-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a9de2-113">Return Value</span></span>  
  
|<span data-ttu-id="a9de2-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a9de2-114">HRESULT</span></span>|<span data-ttu-id="a9de2-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a9de2-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a9de2-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="a9de2-116">S_OK</span></span>|<span data-ttu-id="a9de2-117">`SetActionOnTimeout` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="a9de2-117">`SetActionOnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="a9de2-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a9de2-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a9de2-119">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="a9de2-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a9de2-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a9de2-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a9de2-121">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="a9de2-121">The call timed out.</span></span>|  
|<span data-ttu-id="a9de2-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a9de2-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a9de2-123">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a9de2-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a9de2-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a9de2-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a9de2-125">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="a9de2-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a9de2-126">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="a9de2-126">E_FAIL</span></span>|<span data-ttu-id="a9de2-127">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a9de2-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a9de2-128">Bir yöntem E_FAıL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a9de2-128">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a9de2-129">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="a9de2-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a9de2-130">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a9de2-130">E_INVALIDARG</span></span>|<span data-ttu-id="a9de2-131">Belirtilen `operation`için zaman aşımı ayarlanamaz veya `operation`için geçersiz bir değer sağlandı.</span><span class="sxs-lookup"><span data-stu-id="a9de2-131">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9de2-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a9de2-132">Remarks</span></span>  
 <span data-ttu-id="a9de2-133">Zaman aşımı değeri, CLR tarafından ayarlanan varsayılan zaman aşımı ya da [ICLRPolicyManager:: setTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) metoduna yapılan çağrıda ana bilgisayar tarafından belirtilen bir değer olabilir.</span><span class="sxs-lookup"><span data-stu-id="a9de2-133">The timeout value can be either the default timeout set by the CLR, or a value specified by the host in a call to the [ICLRPolicyManager::SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) method.</span></span>  
  
 <span data-ttu-id="a9de2-134">Tüm ilke eylemi değerleri CLR işlemleri için zaman aşımı davranışı olarak belirtilemez.</span><span class="sxs-lookup"><span data-stu-id="a9de2-134">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="a9de2-135">`SetActionOnTimeout` genellikle yalnızca davranışı yükseltmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a9de2-135">`SetActionOnTimeout` is typically used only to escalate behavior.</span></span> <span data-ttu-id="a9de2-136">Örneğin, bir ana bilgisayar, iş parçacığı iptal işlemini işlenmemiş iş parçacığı iptal edilecek olarak belirtebilir, ancak tersini belirtemez.</span><span class="sxs-lookup"><span data-stu-id="a9de2-136">For example, a host can specify that thread aborts be turned into rude thread aborts, but cannot specify the opposite.</span></span> <span data-ttu-id="a9de2-137">Aşağıdaki tabloda geçerli `operation` değerlerinin geçerli `action` değerleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a9de2-137">The table below describes the valid `action` values for valid `operation` values.</span></span>  
  
|<span data-ttu-id="a9de2-138">`operation` için değer</span><span class="sxs-lookup"><span data-stu-id="a9de2-138">Value for `operation`</span></span>|<span data-ttu-id="a9de2-139">`action` için geçerli değerler</span><span class="sxs-lookup"><span data-stu-id="a9de2-139">Valid values for `action`</span></span>|  
|---------------------------|-------------------------------|  
|<span data-ttu-id="a9de2-140">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="a9de2-140">OPR_ThreadRudeAbortInNonCriticalRegion</span></span><br /><br /> <span data-ttu-id="a9de2-141">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="a9de2-141">OPR_ThreadRudeAbortInCriticalRegion</span></span>|<span data-ttu-id="a9de2-142">-eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="a9de2-142">-   eRudeAbortThread</span></span><br /><span data-ttu-id="a9de2-143">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="a9de2-143">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="a9de2-144">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="a9de2-144">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="a9de2-145">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="a9de2-145">-   eExitProcess</span></span><br /><span data-ttu-id="a9de2-146">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="a9de2-146">-   eFastExitProcess</span></span><br /><span data-ttu-id="a9de2-147">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="a9de2-147">-   eRudeExitProcess</span></span><br /><span data-ttu-id="a9de2-148">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="a9de2-148">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="a9de2-149">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="a9de2-149">OPR_AppDomainUnload</span></span>|<span data-ttu-id="a9de2-150">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="a9de2-150">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="a9de2-151">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="a9de2-151">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="a9de2-152">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="a9de2-152">-   eExitProcess</span></span><br /><span data-ttu-id="a9de2-153">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="a9de2-153">-   eFastExitProcess</span></span><br /><span data-ttu-id="a9de2-154">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="a9de2-154">-   eRudeExitProcess</span></span><br /><span data-ttu-id="a9de2-155">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="a9de2-155">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="a9de2-156">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="a9de2-156">OPR_ProcessExit</span></span>|<span data-ttu-id="a9de2-157">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="a9de2-157">-   eExitProcess</span></span><br /><span data-ttu-id="a9de2-158">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="a9de2-158">-   eFastExitProcess</span></span><br /><span data-ttu-id="a9de2-159">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="a9de2-159">-   eRudeExitProcess</span></span><br /><span data-ttu-id="a9de2-160">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="a9de2-160">-   eDisableRuntime</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a9de2-161">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a9de2-161">Requirements</span></span>  
 <span data-ttu-id="a9de2-162">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9de2-162">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9de2-163">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a9de2-163">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a9de2-164">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="a9de2-164">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a9de2-165">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9de2-165">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9de2-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9de2-166">See also</span></span>

- [<span data-ttu-id="a9de2-167">EClrOperation Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="a9de2-167">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="a9de2-168">EPolicyAction Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="a9de2-168">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="a9de2-169">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a9de2-169">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="a9de2-170">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a9de2-170">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
