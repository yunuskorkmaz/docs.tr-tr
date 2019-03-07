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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 46462362e959b6af9d9b0d311f813e183dfb04df
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474481"
---
# <a name="iclrpolicymanagersetactionontimeout-method"></a><span data-ttu-id="e4f23-102">ICLRPolicyManager::SetActionOnTimeout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e4f23-102">ICLRPolicyManager::SetActionOnTimeout Method</span></span>
<span data-ttu-id="e4f23-103">Ortak dil çalışma zamanı (CLR) belirtilen işlem zaman aşımına uğradığında gerçekleştirmesi gereken ilke eylemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="e4f23-103">Specifies the policy action the common language runtime (CLR) should take when the specified operation times out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4f23-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e4f23-104">Syntax</span></span>  
  
```  
HRESULT SetActionOnTimeout (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4f23-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e4f23-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="e4f23-106">[in] Aşağıdakilerden birini [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) zaman aşımı eylemi belirtmek istediğiniz işlemi belirten değer.</span><span class="sxs-lookup"><span data-stu-id="e4f23-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the operation for which to specify the timeout action.</span></span> <span data-ttu-id="e4f23-107">Aşağıdaki değerleri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="e4f23-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="e4f23-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="e4f23-108">OPR_AppDomainUnload</span></span>  
  
-   <span data-ttu-id="e4f23-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="e4f23-109">OPR_ProcessExit</span></span>  
  
-   <span data-ttu-id="e4f23-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="e4f23-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
-   <span data-ttu-id="e4f23-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="e4f23-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `action`  
 <span data-ttu-id="e4f23-112">[in] Aşağıdakilerden birini [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) işlemi zaman aşımına olduğunda gerçekleştirilecek ilke eylemini belirten değer.</span><span class="sxs-lookup"><span data-stu-id="e4f23-112">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action to be taken when the operation times out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e4f23-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e4f23-113">Return Value</span></span>  
  
|<span data-ttu-id="e4f23-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e4f23-114">HRESULT</span></span>|<span data-ttu-id="e4f23-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e4f23-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e4f23-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="e4f23-116">S_OK</span></span>|<span data-ttu-id="e4f23-117">`SetActionOnTimeout` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e4f23-117">`SetActionOnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="e4f23-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e4f23-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e4f23-119">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="e4f23-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e4f23-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e4f23-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e4f23-121">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="e4f23-121">The call timed out.</span></span>|  
|<span data-ttu-id="e4f23-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e4f23-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e4f23-123">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="e4f23-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e4f23-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e4f23-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e4f23-125">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="e4f23-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e4f23-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e4f23-126">E_FAIL</span></span>|<span data-ttu-id="e4f23-127">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e4f23-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e4f23-128">CLR, artık E_FAIL bir yöntemin dönüşünün ardından, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e4f23-128">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e4f23-129">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="e4f23-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e4f23-130">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="e4f23-130">E_INVALIDARG</span></span>|<span data-ttu-id="e4f23-131">Bir zaman aşımı ayarlamak için belirtilen `operation`, ya da geçersiz bir değer için sağlanan `operation`.</span><span class="sxs-lookup"><span data-stu-id="e4f23-131">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4f23-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e4f23-132">Remarks</span></span>  
 <span data-ttu-id="e4f23-133">Zaman aşımı değeri CLR tarafından ayarlanan varsayılan zaman aşımı veya bir çağrı konak tarafından belirtilen bir değer olabilir [Iclrpolicymanager::setTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e4f23-133">The timeout value can be either the default timeout set by the CLR, or a value specified by the host in a call to the [ICLRPolicyManager::SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) method.</span></span>  
  
 <span data-ttu-id="e4f23-134">Tüm ilke eylem değerleri, CLR işlemleri için zaman aşımı davranışı olarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="e4f23-134">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="e4f23-135">`SetActionOnTimeout` genellikle yalnızca davranışı ilerletmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e4f23-135">`SetActionOnTimeout` is typically used only to escalate behavior.</span></span> <span data-ttu-id="e4f23-136">Örneğin, bir ana iş parçacığı iptalleri rude oturum açılması belirtebilirsiniz iş parçacığı iptalleri, ancak bunun tersi belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4f23-136">For example, a host can specify that thread aborts be turned into rude thread aborts, but cannot specify the opposite.</span></span> <span data-ttu-id="e4f23-137">Aşağıdaki tablo geçerli açıklar `action` değerleri geçerli `operation` değerleri.</span><span class="sxs-lookup"><span data-stu-id="e4f23-137">The table below describes the valid `action` values for valid `operation` values.</span></span>  
  
|<span data-ttu-id="e4f23-138">Değeri `operation`</span><span class="sxs-lookup"><span data-stu-id="e4f23-138">Value for `operation`</span></span>|<span data-ttu-id="e4f23-139">İçin geçerli değerler `action`</span><span class="sxs-lookup"><span data-stu-id="e4f23-139">Valid values for `action`</span></span>|  
|---------------------------|-------------------------------|  
|<span data-ttu-id="e4f23-140">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="e4f23-140">OPR_ThreadRudeAbortInNonCriticalRegion</span></span><br /><br /> <span data-ttu-id="e4f23-141">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="e4f23-141">OPR_ThreadRudeAbortInCriticalRegion</span></span>|<span data-ttu-id="e4f23-142">-   eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="e4f23-142">-   eRudeAbortThread</span></span><br /><span data-ttu-id="e4f23-143">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="e4f23-143">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="e4f23-144">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="e4f23-144">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="e4f23-145">-   eExitProcess</span><span class="sxs-lookup"><span data-stu-id="e4f23-145">-   eExitProcess</span></span><br /><span data-ttu-id="e4f23-146">-   eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="e4f23-146">-   eFastExitProcess</span></span><br /><span data-ttu-id="e4f23-147">-   eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="e4f23-147">-   eRudeExitProcess</span></span><br /><span data-ttu-id="e4f23-148">-   eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="e4f23-148">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="e4f23-149">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="e4f23-149">OPR_AppDomainUnload</span></span>|<span data-ttu-id="e4f23-150">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="e4f23-150">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="e4f23-151">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="e4f23-151">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="e4f23-152">-   eExitProcess</span><span class="sxs-lookup"><span data-stu-id="e4f23-152">-   eExitProcess</span></span><br /><span data-ttu-id="e4f23-153">-   eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="e4f23-153">-   eFastExitProcess</span></span><br /><span data-ttu-id="e4f23-154">-   eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="e4f23-154">-   eRudeExitProcess</span></span><br /><span data-ttu-id="e4f23-155">-   eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="e4f23-155">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="e4f23-156">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="e4f23-156">OPR_ProcessExit</span></span>|<span data-ttu-id="e4f23-157">-   eExitProcess</span><span class="sxs-lookup"><span data-stu-id="e4f23-157">-   eExitProcess</span></span><br /><span data-ttu-id="e4f23-158">-   eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="e4f23-158">-   eFastExitProcess</span></span><br /><span data-ttu-id="e4f23-159">-   eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="e4f23-159">-   eRudeExitProcess</span></span><br /><span data-ttu-id="e4f23-160">-   eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="e4f23-160">-   eDisableRuntime</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e4f23-161">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e4f23-161">Requirements</span></span>  
 <span data-ttu-id="e4f23-162">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4f23-162">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4f23-163">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e4f23-163">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e4f23-164">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e4f23-164">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e4f23-165">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4f23-165">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4f23-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4f23-166">See also</span></span>
- [<span data-ttu-id="e4f23-167">EClrOperation Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="e4f23-167">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="e4f23-168">EPolicyAction Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="e4f23-168">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="e4f23-169">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e4f23-169">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="e4f23-170">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e4f23-170">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
