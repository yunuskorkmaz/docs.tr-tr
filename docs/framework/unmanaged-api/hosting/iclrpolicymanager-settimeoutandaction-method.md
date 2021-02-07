---
description: ': ICLRPolicyManager:: Settimeoutandadction yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: c91d43cce381bef804b30e9e1dcb50574ddcd1b4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716581"
---
# <a name="iclrpolicymanagersettimeoutandaction-method"></a><span data-ttu-id="92ed6-103">ICLRPolicyManager::SetTimeoutAndAction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="92ed6-103">ICLRPolicyManager::SetTimeoutAndAction Method</span></span>

<span data-ttu-id="92ed6-104">Belirtilen işlem için bir zaman aşımı değeri ayarlar ve işlem gerçekleştiğinde ortak dil çalışma zamanının (CLR) yapması gereken ilke eylemini belirtir.</span><span class="sxs-lookup"><span data-stu-id="92ed6-104">Sets a timeout value for the specified operation, and specifies the policy action the common language runtime (CLR) should take when the operation occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92ed6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="92ed6-105">Syntax</span></span>  
  
```cpp  
HRESULT SetTimeoutAndAction (  
    [in] EClrOperation operation,  
    [in] DWORD dwMilliseconds,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92ed6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="92ed6-106">Parameters</span></span>  

 `operation`  
 <span data-ttu-id="92ed6-107">'ndaki Zaman aşımı ve ilke ayarlanacak işlemi belirten [EClrOperation](eclroperation-enumeration.md) değerlerinden biri `action` .</span><span class="sxs-lookup"><span data-stu-id="92ed6-107">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the operation for which to set the timeout and policy `action`.</span></span> <span data-ttu-id="92ed6-108">Aşağıdaki değerler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="92ed6-108">The following values are supported:</span></span>  
  
- <span data-ttu-id="92ed6-109">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="92ed6-109">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="92ed6-110">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="92ed6-110">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="92ed6-111">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="92ed6-111">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="92ed6-112">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="92ed6-112">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="92ed6-113">'ndaki Milisaniye cinsinden yeni zaman aşımı değeri.</span><span class="sxs-lookup"><span data-stu-id="92ed6-113">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="92ed6-114">Sonsuz değeri `operation` hiçbir zaman zaman aşımına uğramamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="92ed6-114">A value of INFINITE causes `operation` never to time out.</span></span>  
  
 `action`  
 <span data-ttu-id="92ed6-115">'ndaki CLR 'nin gerçekleştiğinde yapması gereken ilke eylemini gösteren [EPolicyAction](epolicyaction-enumeration.md) değerlerinden biri `operation` .</span><span class="sxs-lookup"><span data-stu-id="92ed6-115">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the policy action that the CLR should take when `operation` occurs.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="92ed6-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="92ed6-116">Return Value</span></span>  
  
|<span data-ttu-id="92ed6-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="92ed6-117">HRESULT</span></span>|<span data-ttu-id="92ed6-118">Description</span><span class="sxs-lookup"><span data-stu-id="92ed6-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="92ed6-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="92ed6-119">S_OK</span></span>|<span data-ttu-id="92ed6-120">`SetTimeoutAndAction` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="92ed6-120">`SetTimeoutAndAction` returned successfully.</span></span>|  
|<span data-ttu-id="92ed6-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="92ed6-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="92ed6-122">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="92ed6-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="92ed6-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="92ed6-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="92ed6-124">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="92ed6-124">The call timed out.</span></span>|  
|<span data-ttu-id="92ed6-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="92ed6-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="92ed6-126">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="92ed6-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="92ed6-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="92ed6-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="92ed6-128">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="92ed6-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="92ed6-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="92ed6-129">E_FAIL</span></span>|<span data-ttu-id="92ed6-130">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="92ed6-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="92ed6-131">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="92ed6-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="92ed6-132">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="92ed6-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="92ed6-133">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="92ed6-133">E_INVALIDARG</span></span>|<span data-ttu-id="92ed6-134">Belirtilen için bir zaman aşımı ayarlanamaz `operation` veya geçersiz bir değer sağlandı `action` .</span><span class="sxs-lookup"><span data-stu-id="92ed6-134">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `action`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92ed6-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="92ed6-135">Remarks</span></span>  

 <span data-ttu-id="92ed6-136">`SetTimeoutAndAction`[ICLRPolicyManager:: setTimeout](iclrpolicymanager-settimeout-method.md) ve [ICLRPolicyManager:: SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) yöntemlerinin yeteneklerini kapsüller ve bu iki yönteme sıralı çağrılar yerine çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="92ed6-136">`SetTimeoutAndAction` encapsulates the capabilities of the [ICLRPolicyManager::SetTimeout](iclrpolicymanager-settimeout-method.md) and [ICLRPolicyManager::SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) methods, and can be called in place of sequential calls to these two methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="92ed6-137">Tüm ilke eylemi değerleri CLR işlemleri için zaman aşımı davranışı olarak belirtilemez.</span><span class="sxs-lookup"><span data-stu-id="92ed6-137">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="92ed6-138">Geçerli değerler için bu iki yöntem için konuların açıklamalar bölümlerine bakın.</span><span class="sxs-lookup"><span data-stu-id="92ed6-138">See the Remarks sections of the topics for these two methods for valid values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92ed6-139">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="92ed6-139">Requirements</span></span>  

 <span data-ttu-id="92ed6-140">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92ed6-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92ed6-141">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="92ed6-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="92ed6-142">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="92ed6-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="92ed6-143">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92ed6-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92ed6-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92ed6-144">See also</span></span>

- [<span data-ttu-id="92ed6-145">EClrOperation Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="92ed6-145">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="92ed6-146">EPolicyAction Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="92ed6-146">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="92ed6-147">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="92ed6-147">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="92ed6-148">SetActionOnTimeout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="92ed6-148">SetActionOnTimeout Method</span></span>](iclrpolicymanager-setactionontimeout-method.md)
- [<span data-ttu-id="92ed6-149">ICLRPolicyManager:: Settimeoutandadction</span><span class="sxs-lookup"><span data-stu-id="92ed6-149">ICLRPolicyManager::SetTimeoutAndAction</span></span>](iclrpolicymanager-settimeoutandaction-method.md)
