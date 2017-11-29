---
title: "ICLRPolicyManager::SetTimeout Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRPolicyManager.SetTimeout
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRPolicyManager::SetTimeout
helpviewer_keywords:
- SetTimeout method [.NET Framework hosting]
- ICLRPolicyManager::SetTimeout method [.NET Framework hosting]
ms.assetid: 954404fd-d52d-4e68-b582-8692f3a5f608
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 31dfd4654f849d01958be2690afed0f31c736dfd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrpolicymanagersettimeout-method"></a><span data-ttu-id="2e80e-102">ICLRPolicyManager::SetTimeout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2e80e-102">ICLRPolicyManager::SetTimeout Method</span></span>
<span data-ttu-id="2e80e-103">Belirtilen işlem için bir zaman aşımı değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2e80e-103">Sets a timeout value for the specified operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e80e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2e80e-104">Syntax</span></span>  
  
```  
HRESULT SetTimeout (  
    [in] EClrOperation operation,  
    [in] DWORD dsMilliseconds  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2e80e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2e80e-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="2e80e-106">[in] Aşağıdakilerden birini [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) ortak dil çalışma zamanı (CLR) işlemi zaman aşımı ayarlanacak belirten değer.</span><span class="sxs-lookup"><span data-stu-id="2e80e-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the common language runtime (CLR) operation for which to set a timeout.</span></span> <span data-ttu-id="2e80e-107">Aşağıdaki değerleri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="2e80e-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="2e80e-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="2e80e-108">OPR_AppDomainUnload</span></span>  
  
-   <span data-ttu-id="2e80e-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="2e80e-109">OPR_ProcessExit</span></span>  
  
-   <span data-ttu-id="2e80e-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="2e80e-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
-   <span data-ttu-id="2e80e-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="2e80e-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="2e80e-112">[in] Yeni zaman aşımı değeri, milisaniye cinsinden.</span><span class="sxs-lookup"><span data-stu-id="2e80e-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="2e80e-113">SONSUZ değeri işlemi hiçbir zaman zaman aşımına neden olur.</span><span class="sxs-lookup"><span data-stu-id="2e80e-113">A value of INFINITE causes the operation never to time out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2e80e-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2e80e-114">Return Value</span></span>  
  
|<span data-ttu-id="2e80e-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2e80e-115">HRESULT</span></span>|<span data-ttu-id="2e80e-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2e80e-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2e80e-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="2e80e-117">S_OK</span></span>|<span data-ttu-id="2e80e-118">`SetTimeout`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="2e80e-118">`SetTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="2e80e-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2e80e-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2e80e-120">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="2e80e-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2e80e-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2e80e-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2e80e-122">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="2e80e-122">The call timed out.</span></span>|  
|<span data-ttu-id="2e80e-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2e80e-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2e80e-124">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="2e80e-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2e80e-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2e80e-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2e80e-126">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="2e80e-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2e80e-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2e80e-127">E_FAIL</span></span>|<span data-ttu-id="2e80e-128">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="2e80e-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2e80e-129">CLR, artık bir yöntem E_FAIL döndükten sonra işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2e80e-129">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2e80e-130">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="2e80e-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2e80e-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="2e80e-131">E_INVALIDARG</span></span>|<span data-ttu-id="2e80e-132">Zaman aşımı ayarlanamaz için belirtilen `operation`, ya da geçersiz bir değer için sağlanan `operation`.</span><span class="sxs-lookup"><span data-stu-id="2e80e-132">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2e80e-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2e80e-133">Requirements</span></span>  
 <span data-ttu-id="2e80e-134">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e80e-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e80e-135">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2e80e-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2e80e-136">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="2e80e-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2e80e-137">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e80e-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e80e-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2e80e-138">See Also</span></span>  
 [<span data-ttu-id="2e80e-139">EClrOperation numaralandırması</span><span class="sxs-lookup"><span data-stu-id="2e80e-139">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="2e80e-140">Iclrcontrol arabirimi</span><span class="sxs-lookup"><span data-stu-id="2e80e-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="2e80e-141">Iclrpolicymanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="2e80e-141">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
