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
ms.openlocfilehash: cc1d16a2d57fea27c1c26fc55fbbfa9b74c25495
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435844"
---
# <a name="iclrpolicymanagersetactionontimeout-method"></a><span data-ttu-id="4a674-102">ICLRPolicyManager::SetActionOnTimeout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4a674-102">ICLRPolicyManager::SetActionOnTimeout Method</span></span>
<span data-ttu-id="4a674-103">Ortak dil çalışma zamanı (CLR) belirtilen işlem zaman aşımına uğradığında gerçekleştirmesi gereken ilke eylemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a674-103">Specifies the policy action the common language runtime (CLR) should take when the specified operation times out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a674-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4a674-104">Syntax</span></span>  
  
```  
HRESULT SetActionOnTimeout (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4a674-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4a674-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="4a674-106">[in] Aşağıdakilerden birini [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) işlemi zaman aşımı eylemi belirtmek üzere belirten değerleri.</span><span class="sxs-lookup"><span data-stu-id="4a674-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the operation for which to specify the timeout action.</span></span> <span data-ttu-id="4a674-107">Aşağıdaki değerleri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="4a674-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="4a674-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="4a674-108">OPR_AppDomainUnload</span></span>  
  
-   <span data-ttu-id="4a674-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="4a674-109">OPR_ProcessExit</span></span>  
  
-   <span data-ttu-id="4a674-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="4a674-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
-   <span data-ttu-id="4a674-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="4a674-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `action`  
 <span data-ttu-id="4a674-112">[in] Aşağıdakilerden birini [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) işlemi zaman aşımına uğradığında gerçekleştirilecek İlkesi eylemini belirten değer.</span><span class="sxs-lookup"><span data-stu-id="4a674-112">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action to be taken when the operation times out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4a674-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4a674-113">Return Value</span></span>  
  
|<span data-ttu-id="4a674-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4a674-114">HRESULT</span></span>|<span data-ttu-id="4a674-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4a674-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4a674-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="4a674-116">S_OK</span></span>|<span data-ttu-id="4a674-117">`SetActionOnTimeout` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="4a674-117">`SetActionOnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="4a674-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4a674-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4a674-119">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="4a674-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4a674-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4a674-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4a674-121">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="4a674-121">The call timed out.</span></span>|  
|<span data-ttu-id="4a674-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4a674-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4a674-123">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="4a674-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4a674-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4a674-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4a674-125">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="4a674-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4a674-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4a674-126">E_FAIL</span></span>|<span data-ttu-id="4a674-127">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="4a674-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4a674-128">CLR, artık bir yöntem E_FAIL döndükten sonra işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4a674-128">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4a674-129">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="4a674-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4a674-130">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="4a674-130">E_INVALIDARG</span></span>|<span data-ttu-id="4a674-131">Zaman aşımı ayarlanamaz için belirtilen `operation`, ya da geçersiz bir değer için sağlanan `operation`.</span><span class="sxs-lookup"><span data-stu-id="4a674-131">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a674-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4a674-132">Remarks</span></span>  
 <span data-ttu-id="4a674-133">Zaman aşımı değeri CLR tarafından ayarlanmış varsayılan zaman aşımı veya çağrıda konak tarafından belirtilen bir değer olabilir [Iclrpolicymanager::setTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4a674-133">The timeout value can be either the default timeout set by the CLR, or a value specified by the host in a call to the [ICLRPolicyManager::SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) method.</span></span>  
  
 <span data-ttu-id="4a674-134">Tüm ilke eylem değerlerini CLR işlemleri için zaman aşımı davranış olarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="4a674-134">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="4a674-135">`SetActionOnTimeout` genellikle yalnızca davranışı ilerletmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4a674-135">`SetActionOnTimeout` is typically used only to escalate behavior.</span></span> <span data-ttu-id="4a674-136">Örneğin, bir ana iş parçacığı iptalleri içine utangaç açılması belirtebilirsiniz iş parçacığı iptalleri ancak karşıtı belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="4a674-136">For example, a host can specify that thread aborts be turned into rude thread aborts, but cannot specify the opposite.</span></span> <span data-ttu-id="4a674-137">Aşağıdaki tabloda geçerli açıklanmaktadır `action` değerleri geçerli `operation` değerleri.</span><span class="sxs-lookup"><span data-stu-id="4a674-137">The table below describes the valid `action` values for valid `operation` values.</span></span>  
  
|<span data-ttu-id="4a674-138">Değeri `operation`</span><span class="sxs-lookup"><span data-stu-id="4a674-138">Value for `operation`</span></span>|<span data-ttu-id="4a674-139">İçin geçerli değerler `action`</span><span class="sxs-lookup"><span data-stu-id="4a674-139">Valid values for `action`</span></span>|  
|---------------------------|-------------------------------|  
|<span data-ttu-id="4a674-140">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="4a674-140">OPR_ThreadRudeAbortInNonCriticalRegion</span></span><br /><br /> <span data-ttu-id="4a674-141">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="4a674-141">OPR_ThreadRudeAbortInCriticalRegion</span></span>|<span data-ttu-id="4a674-142">-eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="4a674-142">-   eRudeAbortThread</span></span><br /><span data-ttu-id="4a674-143">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="4a674-143">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="4a674-144">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="4a674-144">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="4a674-145">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="4a674-145">-   eExitProcess</span></span><br /><span data-ttu-id="4a674-146">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="4a674-146">-   eFastExitProcess</span></span><br /><span data-ttu-id="4a674-147">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="4a674-147">-   eRudeExitProcess</span></span><br /><span data-ttu-id="4a674-148">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="4a674-148">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="4a674-149">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="4a674-149">OPR_AppDomainUnload</span></span>|<span data-ttu-id="4a674-150">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="4a674-150">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="4a674-151">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="4a674-151">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="4a674-152">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="4a674-152">-   eExitProcess</span></span><br /><span data-ttu-id="4a674-153">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="4a674-153">-   eFastExitProcess</span></span><br /><span data-ttu-id="4a674-154">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="4a674-154">-   eRudeExitProcess</span></span><br /><span data-ttu-id="4a674-155">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="4a674-155">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="4a674-156">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="4a674-156">OPR_ProcessExit</span></span>|<span data-ttu-id="4a674-157">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="4a674-157">-   eExitProcess</span></span><br /><span data-ttu-id="4a674-158">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="4a674-158">-   eFastExitProcess</span></span><br /><span data-ttu-id="4a674-159">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="4a674-159">-   eRudeExitProcess</span></span><br /><span data-ttu-id="4a674-160">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="4a674-160">-   eDisableRuntime</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4a674-161">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4a674-161">Requirements</span></span>  
 <span data-ttu-id="4a674-162">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a674-162">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a674-163">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4a674-163">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4a674-164">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="4a674-164">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4a674-165">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a674-165">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a674-166">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4a674-166">See Also</span></span>  
 [<span data-ttu-id="4a674-167">EClrOperation Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="4a674-167">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="4a674-168">EPolicyAction Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="4a674-168">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="4a674-169">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4a674-169">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="4a674-170">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4a674-170">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
