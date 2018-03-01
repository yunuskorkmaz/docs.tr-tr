---
title: "ICLRPolicyManager::SetTimeoutAndAction Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRPolicyManager.SetTimeoutAndAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetTimeoutAndAction
helpviewer_keywords:
- ICLRPolicyManager::SetTimeoutAndAction method [.NET Framework hosting]
- SetTimeoutAndAction method [.NET Framework hosting]
ms.assetid: 60454f91-d855-4ddf-bb6d-60a02f5eabab
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b67150b7544f1d8d25532c564800404b634cae99
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrpolicymanagersettimeoutandaction-method"></a><span data-ttu-id="e874f-102">ICLRPolicyManager::SetTimeoutAndAction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e874f-102">ICLRPolicyManager::SetTimeoutAndAction Method</span></span>
<span data-ttu-id="e874f-103">Belirtilen işlem için bir zaman aşımı değeri ayarlar ve ortak dil çalışma zamanı (CLR) işlemi oluştuğunda gerçekleştirmesi gereken ilke eylemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="e874f-103">Sets a timeout value for the specified operation, and specifies the policy action the common language runtime (CLR) should take when the operation occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e874f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e874f-104">Syntax</span></span>  
  
```  
HRESULT SetTimeoutAndAction (  
    [in] EClrOperation operation,  
    [in] DWORD dwMilliseconds,  
    [in] EPolicyAction action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e874f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e874f-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="e874f-106">[in] Aşağıdakilerden birini [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) değerleri, işlem için zaman aşımı ve ilke ayarlanacağı gösteren `action`.</span><span class="sxs-lookup"><span data-stu-id="e874f-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the operation for which to set the timeout and policy `action`.</span></span> <span data-ttu-id="e874f-107">Aşağıdaki değerleri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="e874f-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="e874f-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="e874f-108">OPR_AppDomainUnload</span></span>  
  
-   <span data-ttu-id="e874f-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="e874f-109">OPR_ProcessExit</span></span>  
  
-   <span data-ttu-id="e874f-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="e874f-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
-   <span data-ttu-id="e874f-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="e874f-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="e874f-112">[in] Yeni zaman aşımı değeri, milisaniye cinsinden.</span><span class="sxs-lookup"><span data-stu-id="e874f-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="e874f-113">SONSUZ nedenler değerini `operation` zaman aşımı için hiçbir zaman.</span><span class="sxs-lookup"><span data-stu-id="e874f-113">A value of INFINITE causes `operation` never to time out.</span></span>  
  
 `action`  
 <span data-ttu-id="e874f-114">[in] Aşağıdakilerden birini [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) değerleri, CLR ne zaman gerçekleştirmesi gereken ilke eylemini belirten `operation` oluşur.</span><span class="sxs-lookup"><span data-stu-id="e874f-114">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action that the CLR should take when `operation` occurs.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e874f-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e874f-115">Return Value</span></span>  
  
|<span data-ttu-id="e874f-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e874f-116">HRESULT</span></span>|<span data-ttu-id="e874f-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e874f-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e874f-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="e874f-118">S_OK</span></span>|<span data-ttu-id="e874f-119">`SetTimeoutAndAction`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e874f-119">`SetTimeoutAndAction` returned successfully.</span></span>|  
|<span data-ttu-id="e874f-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e874f-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e874f-121">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="e874f-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e874f-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e874f-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e874f-123">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="e874f-123">The call timed out.</span></span>|  
|<span data-ttu-id="e874f-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e874f-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e874f-125">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="e874f-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e874f-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e874f-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e874f-127">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="e874f-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e874f-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e874f-128">E_FAIL</span></span>|<span data-ttu-id="e874f-129">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e874f-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e874f-130">CLR, artık bir yöntem E_FAIL döndükten sonra işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e874f-130">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e874f-131">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="e874f-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e874f-132">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="e874f-132">E_INVALIDARG</span></span>|<span data-ttu-id="e874f-133">Zaman aşımı ayarlanamaz için belirtilen `operation`, ya da geçersiz bir değer için sağlanan `action`.</span><span class="sxs-lookup"><span data-stu-id="e874f-133">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `action`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e874f-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e874f-134">Remarks</span></span>  
 <span data-ttu-id="e874f-135">`SetTimeoutAndAction`yeteneklerini yalıtır [Iclrpolicymanager::setTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) ve [Iclrpolicymanager::setactionontimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) yöntemleri ve bu iki yöntem sıralı çağrıları yerine çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="e874f-135">`SetTimeoutAndAction` encapsulates the capabilities of the [ICLRPolicyManager::SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) and [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) methods, and can be called in place of sequential calls to these two methods.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e874f-136">Tüm ilke eylem değerlerini CLR işlemleri için zaman aşımı davranış olarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="e874f-136">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="e874f-137">Bu iki yöntem için geçerli değerler için konuları açıklamalar bölümlerine bakın.</span><span class="sxs-lookup"><span data-stu-id="e874f-137">See the Remarks sections of the topics for these two methods for valid values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e874f-138">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e874f-138">Requirements</span></span>  
 <span data-ttu-id="e874f-139">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e874f-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e874f-140">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e874f-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e874f-141">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e874f-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e874f-142">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e874f-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e874f-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e874f-143">See Also</span></span>  
 [<span data-ttu-id="e874f-144">EClrOperation Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="e874f-144">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="e874f-145">EPolicyAction Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="e874f-145">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="e874f-146">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e874f-146">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="e874f-147">SetActionOnTimeout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e874f-147">SetActionOnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)  
 [<span data-ttu-id="e874f-148">Iclrpolicymanager::settimeoutandaction</span><span class="sxs-lookup"><span data-stu-id="e874f-148">ICLRPolicyManager::SetTimeoutAndAction</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeoutandaction-method.md)
