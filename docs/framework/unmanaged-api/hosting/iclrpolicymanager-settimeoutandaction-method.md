---
title: ICLRPolicyManager::SetTimeoutAndAction Yöntemi
ms.date: 03/30/2017
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
ms.openlocfilehash: 3a58664a7dc81059214246b53cf967b50cd61063
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140745"
---
# <a name="iclrpolicymanagersettimeoutandaction-method"></a><span data-ttu-id="48156-102">ICLRPolicyManager::SetTimeoutAndAction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="48156-102">ICLRPolicyManager::SetTimeoutAndAction Method</span></span>
<span data-ttu-id="48156-103">Belirtilen işlem için bir zaman aşımı değeri ayarlar ve işlem gerçekleştiğinde ortak dil çalışma zamanının (CLR) yapması gereken ilke eylemini belirtir.</span><span class="sxs-lookup"><span data-stu-id="48156-103">Sets a timeout value for the specified operation, and specifies the policy action the common language runtime (CLR) should take when the operation occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48156-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="48156-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTimeoutAndAction (  
    [in] EClrOperation operation,  
    [in] DWORD dwMilliseconds,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="48156-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="48156-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="48156-106">'ndaki Zaman aşımı ve ilke `action`ayarlanacak işlemi belirten [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="48156-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the operation for which to set the timeout and policy `action`.</span></span> <span data-ttu-id="48156-107">Aşağıdaki değerler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="48156-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="48156-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="48156-108">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="48156-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="48156-109">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="48156-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="48156-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="48156-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="48156-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="48156-112">'ndaki Milisaniye cinsinden yeni zaman aşımı değeri.</span><span class="sxs-lookup"><span data-stu-id="48156-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="48156-113">Sonsuz değeri `operation` zaman aşımına uğramamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="48156-113">A value of INFINITE causes `operation` never to time out.</span></span>  
  
 `action`  
 <span data-ttu-id="48156-114">'ndaki `operation` gerçekleştiğinde CLR 'nin yapması gereken ilke eylemini gösteren [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="48156-114">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action that the CLR should take when `operation` occurs.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="48156-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="48156-115">Return Value</span></span>  
  
|<span data-ttu-id="48156-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="48156-116">HRESULT</span></span>|<span data-ttu-id="48156-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="48156-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="48156-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="48156-118">S_OK</span></span>|<span data-ttu-id="48156-119">`SetTimeoutAndAction` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="48156-119">`SetTimeoutAndAction` returned successfully.</span></span>|  
|<span data-ttu-id="48156-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="48156-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="48156-121">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="48156-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="48156-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="48156-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="48156-123">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="48156-123">The call timed out.</span></span>|  
|<span data-ttu-id="48156-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="48156-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="48156-125">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="48156-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="48156-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="48156-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="48156-127">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="48156-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="48156-128">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="48156-128">E_FAIL</span></span>|<span data-ttu-id="48156-129">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="48156-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="48156-130">Bir yöntem E_FAıL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="48156-130">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="48156-131">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="48156-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="48156-132">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="48156-132">E_INVALIDARG</span></span>|<span data-ttu-id="48156-133">Belirtilen `operation`için zaman aşımı ayarlanamaz veya `action`için geçersiz bir değer sağlandı.</span><span class="sxs-lookup"><span data-stu-id="48156-133">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `action`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48156-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="48156-134">Remarks</span></span>  
 <span data-ttu-id="48156-135">`SetTimeoutAndAction` [ICLRPolicyManager:: setTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) ve [ICLRPolicyManager:: SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) yöntemlerinin yeteneklerini kapsüller ve bu iki yönteme sıralı çağrılar yerine çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="48156-135">`SetTimeoutAndAction` encapsulates the capabilities of the [ICLRPolicyManager::SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) and [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) methods, and can be called in place of sequential calls to these two methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="48156-136">Tüm ilke eylemi değerleri CLR işlemleri için zaman aşımı davranışı olarak belirtilemez.</span><span class="sxs-lookup"><span data-stu-id="48156-136">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="48156-137">Geçerli değerler için bu iki yöntem için konuların açıklamalar bölümlerine bakın.</span><span class="sxs-lookup"><span data-stu-id="48156-137">See the Remarks sections of the topics for these two methods for valid values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48156-138">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="48156-138">Requirements</span></span>  
 <span data-ttu-id="48156-139">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48156-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48156-140">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="48156-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="48156-141">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="48156-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="48156-142">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48156-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48156-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48156-143">See also</span></span>

- [<span data-ttu-id="48156-144">EClrOperation Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="48156-144">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="48156-145">EPolicyAction Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="48156-145">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="48156-146">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="48156-146">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="48156-147">SetActionOnTimeout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="48156-147">SetActionOnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)
- [<span data-ttu-id="48156-148">ICLRPolicyManager:: Settimeoutandadction</span><span class="sxs-lookup"><span data-stu-id="48156-148">ICLRPolicyManager::SetTimeoutAndAction</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeoutandaction-method.md)
