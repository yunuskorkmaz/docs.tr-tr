---
description: ': ICLRPolicyManager:: SetActionOnTimeout yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: d682acd49bdc4fa0f8c58a1300e2215816fe2718
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689033"
---
# <a name="iclrpolicymanagersetactionontimeout-method"></a><span data-ttu-id="4d2ac-103">ICLRPolicyManager::SetActionOnTimeout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4d2ac-103">ICLRPolicyManager::SetActionOnTimeout Method</span></span>

<span data-ttu-id="4d2ac-104">Belirtilen işlem zaman aşımına uğrarsa ortak dil çalışma zamanının (CLR) yapması gereken ilke eylemini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4d2ac-104">Specifies the policy action the common language runtime (CLR) should take when the specified operation times out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d2ac-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4d2ac-105">Syntax</span></span>  
  
```cpp  
HRESULT SetActionOnTimeout (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d2ac-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4d2ac-106">Parameters</span></span>  

 `operation`  
 <span data-ttu-id="4d2ac-107">'ndaki Zaman aşımı eyleminin belirtme işlemini belirten [EClrOperation](eclroperation-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="4d2ac-107">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the operation for which to specify the timeout action.</span></span> <span data-ttu-id="4d2ac-108">Aşağıdaki değerler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="4d2ac-108">The following values are supported:</span></span>  
  
- <span data-ttu-id="4d2ac-109">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="4d2ac-109">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="4d2ac-110">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="4d2ac-110">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="4d2ac-111">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="4d2ac-111">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="4d2ac-112">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="4d2ac-112">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `action`  
 <span data-ttu-id="4d2ac-113">'ndaki İşlem zaman aşımına uğrarsa gerçekleştirilecek ilke eylemini gösteren [EPolicyAction](epolicyaction-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="4d2ac-113">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the policy action to be taken when the operation times out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4d2ac-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4d2ac-114">Return Value</span></span>  
  
|<span data-ttu-id="4d2ac-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4d2ac-115">HRESULT</span></span>|<span data-ttu-id="4d2ac-116">Description</span><span class="sxs-lookup"><span data-stu-id="4d2ac-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4d2ac-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="4d2ac-117">S_OK</span></span>|<span data-ttu-id="4d2ac-118">`SetActionOnTimeout` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="4d2ac-118">`SetActionOnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="4d2ac-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4d2ac-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4d2ac-120">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="4d2ac-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4d2ac-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4d2ac-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4d2ac-122">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="4d2ac-122">The call timed out.</span></span>|  
|<span data-ttu-id="4d2ac-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4d2ac-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4d2ac-124">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="4d2ac-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4d2ac-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4d2ac-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4d2ac-126">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="4d2ac-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4d2ac-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4d2ac-127">E_FAIL</span></span>|<span data-ttu-id="4d2ac-128">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="4d2ac-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4d2ac-129">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4d2ac-129">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4d2ac-130">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="4d2ac-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4d2ac-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="4d2ac-131">E_INVALIDARG</span></span>|<span data-ttu-id="4d2ac-132">Belirtilen için bir zaman aşımı ayarlanamaz `operation` veya geçersiz bir değer sağlandı `operation` .</span><span class="sxs-lookup"><span data-stu-id="4d2ac-132">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d2ac-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4d2ac-133">Remarks</span></span>  

 <span data-ttu-id="4d2ac-134">Zaman aşımı değeri, CLR tarafından ayarlanan varsayılan zaman aşımı ya da [ICLRPolicyManager:: setTimeout](iclrpolicymanager-settimeout-method.md) metoduna yapılan çağrıda ana bilgisayar tarafından belirtilen bir değer olabilir.</span><span class="sxs-lookup"><span data-stu-id="4d2ac-134">The timeout value can be either the default timeout set by the CLR, or a value specified by the host in a call to the [ICLRPolicyManager::SetTimeout](iclrpolicymanager-settimeout-method.md) method.</span></span>  
  
 <span data-ttu-id="4d2ac-135">Tüm ilke eylemi değerleri CLR işlemleri için zaman aşımı davranışı olarak belirtilemez.</span><span class="sxs-lookup"><span data-stu-id="4d2ac-135">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="4d2ac-136">`SetActionOnTimeout` genellikle davranışı yükseltmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4d2ac-136">`SetActionOnTimeout` is typically used only to escalate behavior.</span></span> <span data-ttu-id="4d2ac-137">Örneğin, bir ana bilgisayar, iş parçacığı iptal işlemini işlenmemiş iş parçacığı iptal edilecek olarak belirtebilir, ancak tersini belirtemez.</span><span class="sxs-lookup"><span data-stu-id="4d2ac-137">For example, a host can specify that thread aborts be turned into rude thread aborts, but cannot specify the opposite.</span></span> <span data-ttu-id="4d2ac-138">Aşağıdaki tabloda `action` geçerli değerler için geçerli değerler açıklanmaktadır `operation` .</span><span class="sxs-lookup"><span data-stu-id="4d2ac-138">The table below describes the valid `action` values for valid `operation` values.</span></span>  
  
|<span data-ttu-id="4d2ac-139">Değer `operation`</span><span class="sxs-lookup"><span data-stu-id="4d2ac-139">Value for `operation`</span></span>|<span data-ttu-id="4d2ac-140">İçin geçerli değerler `action`</span><span class="sxs-lookup"><span data-stu-id="4d2ac-140">Valid values for `action`</span></span>|  
|---------------------------|-------------------------------|  
|<span data-ttu-id="4d2ac-141">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="4d2ac-141">OPR_ThreadRudeAbortInNonCriticalRegion</span></span><br /><br /> <span data-ttu-id="4d2ac-142">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="4d2ac-142">OPR_ThreadRudeAbortInCriticalRegion</span></span>|<span data-ttu-id="4d2ac-143">-eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="4d2ac-143">-   eRudeAbortThread</span></span><br /><span data-ttu-id="4d2ac-144">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="4d2ac-144">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="4d2ac-145">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="4d2ac-145">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="4d2ac-146">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="4d2ac-146">-   eExitProcess</span></span><br /><span data-ttu-id="4d2ac-147">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="4d2ac-147">-   eFastExitProcess</span></span><br /><span data-ttu-id="4d2ac-148">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="4d2ac-148">-   eRudeExitProcess</span></span><br /><span data-ttu-id="4d2ac-149">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="4d2ac-149">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="4d2ac-150">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="4d2ac-150">OPR_AppDomainUnload</span></span>|<span data-ttu-id="4d2ac-151">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="4d2ac-151">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="4d2ac-152">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="4d2ac-152">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="4d2ac-153">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="4d2ac-153">-   eExitProcess</span></span><br /><span data-ttu-id="4d2ac-154">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="4d2ac-154">-   eFastExitProcess</span></span><br /><span data-ttu-id="4d2ac-155">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="4d2ac-155">-   eRudeExitProcess</span></span><br /><span data-ttu-id="4d2ac-156">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="4d2ac-156">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="4d2ac-157">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="4d2ac-157">OPR_ProcessExit</span></span>|<span data-ttu-id="4d2ac-158">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="4d2ac-158">-   eExitProcess</span></span><br /><span data-ttu-id="4d2ac-159">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="4d2ac-159">-   eFastExitProcess</span></span><br /><span data-ttu-id="4d2ac-160">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="4d2ac-160">-   eRudeExitProcess</span></span><br /><span data-ttu-id="4d2ac-161">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="4d2ac-161">-   eDisableRuntime</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4d2ac-162">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4d2ac-162">Requirements</span></span>  

 <span data-ttu-id="4d2ac-163">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d2ac-163">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d2ac-164">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4d2ac-164">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4d2ac-165">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="4d2ac-165">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4d2ac-166">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d2ac-166">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d2ac-167">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4d2ac-167">See also</span></span>

- [<span data-ttu-id="4d2ac-168">EClrOperation Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="4d2ac-168">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="4d2ac-169">EPolicyAction Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="4d2ac-169">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="4d2ac-170">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4d2ac-170">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="4d2ac-171">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4d2ac-171">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
