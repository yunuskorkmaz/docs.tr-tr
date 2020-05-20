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
ms.openlocfilehash: 0b8e7dfbe377e60b548003af10fb11392b514030
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703459"
---
# <a name="iclrpolicymanagersetactionontimeout-method"></a><span data-ttu-id="c05bb-102">ICLRPolicyManager::SetActionOnTimeout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c05bb-102">ICLRPolicyManager::SetActionOnTimeout Method</span></span>
<span data-ttu-id="c05bb-103">Belirtilen işlem zaman aşımına uğrarsa ortak dil çalışma zamanının (CLR) yapması gereken ilke eylemini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c05bb-103">Specifies the policy action the common language runtime (CLR) should take when the specified operation times out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c05bb-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c05bb-104">Syntax</span></span>  
  
```cpp  
HRESULT SetActionOnTimeout (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c05bb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c05bb-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="c05bb-106">'ndaki Zaman aşımı eyleminin belirtme işlemini belirten [EClrOperation](eclroperation-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="c05bb-106">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the operation for which to specify the timeout action.</span></span> <span data-ttu-id="c05bb-107">Aşağıdaki değerler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="c05bb-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="c05bb-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="c05bb-108">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="c05bb-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="c05bb-109">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="c05bb-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="c05bb-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="c05bb-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="c05bb-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `action`  
 <span data-ttu-id="c05bb-112">'ndaki İşlem zaman aşımına uğrarsa gerçekleştirilecek ilke eylemini gösteren [EPolicyAction](epolicyaction-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="c05bb-112">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the policy action to be taken when the operation times out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c05bb-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c05bb-113">Return Value</span></span>  
  
|<span data-ttu-id="c05bb-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c05bb-114">HRESULT</span></span>|<span data-ttu-id="c05bb-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c05bb-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c05bb-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="c05bb-116">S_OK</span></span>|<span data-ttu-id="c05bb-117">`SetActionOnTimeout`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="c05bb-117">`SetActionOnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="c05bb-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c05bb-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c05bb-119">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="c05bb-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c05bb-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c05bb-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c05bb-121">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="c05bb-121">The call timed out.</span></span>|  
|<span data-ttu-id="c05bb-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c05bb-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c05bb-123">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="c05bb-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c05bb-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c05bb-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c05bb-125">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="c05bb-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c05bb-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c05bb-126">E_FAIL</span></span>|<span data-ttu-id="c05bb-127">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="c05bb-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c05bb-128">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c05bb-128">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c05bb-129">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="c05bb-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c05bb-130">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c05bb-130">E_INVALIDARG</span></span>|<span data-ttu-id="c05bb-131">Belirtilen için bir zaman aşımı ayarlanamaz `operation` veya geçersiz bir değer sağlandı `operation` .</span><span class="sxs-lookup"><span data-stu-id="c05bb-131">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c05bb-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c05bb-132">Remarks</span></span>  
 <span data-ttu-id="c05bb-133">Zaman aşımı değeri, CLR tarafından ayarlanan varsayılan zaman aşımı ya da [ICLRPolicyManager:: setTimeout](iclrpolicymanager-settimeout-method.md) metoduna yapılan çağrıda ana bilgisayar tarafından belirtilen bir değer olabilir.</span><span class="sxs-lookup"><span data-stu-id="c05bb-133">The timeout value can be either the default timeout set by the CLR, or a value specified by the host in a call to the [ICLRPolicyManager::SetTimeout](iclrpolicymanager-settimeout-method.md) method.</span></span>  
  
 <span data-ttu-id="c05bb-134">Tüm ilke eylemi değerleri CLR işlemleri için zaman aşımı davranışı olarak belirtilemez.</span><span class="sxs-lookup"><span data-stu-id="c05bb-134">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="c05bb-135">`SetActionOnTimeout`genellikle davranışı yükseltmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c05bb-135">`SetActionOnTimeout` is typically used only to escalate behavior.</span></span> <span data-ttu-id="c05bb-136">Örneğin, bir ana bilgisayar, iş parçacığı iptal işlemini işlenmemiş iş parçacığı iptal edilecek olarak belirtebilir, ancak tersini belirtemez.</span><span class="sxs-lookup"><span data-stu-id="c05bb-136">For example, a host can specify that thread aborts be turned into rude thread aborts, but cannot specify the opposite.</span></span> <span data-ttu-id="c05bb-137">Aşağıdaki tabloda `action` geçerli değerler için geçerli değerler açıklanmaktadır `operation` .</span><span class="sxs-lookup"><span data-stu-id="c05bb-137">The table below describes the valid `action` values for valid `operation` values.</span></span>  
  
|<span data-ttu-id="c05bb-138">Değer`operation`</span><span class="sxs-lookup"><span data-stu-id="c05bb-138">Value for `operation`</span></span>|<span data-ttu-id="c05bb-139">İçin geçerli değerler`action`</span><span class="sxs-lookup"><span data-stu-id="c05bb-139">Valid values for `action`</span></span>|  
|---------------------------|-------------------------------|  
|<span data-ttu-id="c05bb-140">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="c05bb-140">OPR_ThreadRudeAbortInNonCriticalRegion</span></span><br /><br /> <span data-ttu-id="c05bb-141">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="c05bb-141">OPR_ThreadRudeAbortInCriticalRegion</span></span>|<span data-ttu-id="c05bb-142">-eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="c05bb-142">-   eRudeAbortThread</span></span><br /><span data-ttu-id="c05bb-143">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="c05bb-143">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="c05bb-144">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="c05bb-144">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="c05bb-145">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="c05bb-145">-   eExitProcess</span></span><br /><span data-ttu-id="c05bb-146">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="c05bb-146">-   eFastExitProcess</span></span><br /><span data-ttu-id="c05bb-147">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="c05bb-147">-   eRudeExitProcess</span></span><br /><span data-ttu-id="c05bb-148">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="c05bb-148">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="c05bb-149">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="c05bb-149">OPR_AppDomainUnload</span></span>|<span data-ttu-id="c05bb-150">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="c05bb-150">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="c05bb-151">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="c05bb-151">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="c05bb-152">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="c05bb-152">-   eExitProcess</span></span><br /><span data-ttu-id="c05bb-153">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="c05bb-153">-   eFastExitProcess</span></span><br /><span data-ttu-id="c05bb-154">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="c05bb-154">-   eRudeExitProcess</span></span><br /><span data-ttu-id="c05bb-155">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="c05bb-155">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="c05bb-156">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="c05bb-156">OPR_ProcessExit</span></span>|<span data-ttu-id="c05bb-157">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="c05bb-157">-   eExitProcess</span></span><br /><span data-ttu-id="c05bb-158">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="c05bb-158">-   eFastExitProcess</span></span><br /><span data-ttu-id="c05bb-159">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="c05bb-159">-   eRudeExitProcess</span></span><br /><span data-ttu-id="c05bb-160">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="c05bb-160">-   eDisableRuntime</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c05bb-161">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c05bb-161">Requirements</span></span>  
 <span data-ttu-id="c05bb-162">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c05bb-162">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c05bb-163">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c05bb-163">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c05bb-164">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="c05bb-164">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c05bb-165">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c05bb-165">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c05bb-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c05bb-166">See also</span></span>

- [<span data-ttu-id="c05bb-167">EClrOperation Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="c05bb-167">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="c05bb-168">EPolicyAction Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="c05bb-168">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="c05bb-169">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c05bb-169">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="c05bb-170">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c05bb-170">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
