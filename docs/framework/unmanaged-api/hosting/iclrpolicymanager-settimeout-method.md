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
ms.workload: dotnet
ms.openlocfilehash: b5042d2f06d25b2cccc81239367362313210d3c9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrpolicymanagersettimeout-method"></a><span data-ttu-id="3001b-102">ICLRPolicyManager::SetTimeout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3001b-102">ICLRPolicyManager::SetTimeout Method</span></span>
<span data-ttu-id="3001b-103">Belirtilen işlem için bir zaman aşımı değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3001b-103">Sets a timeout value for the specified operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3001b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3001b-104">Syntax</span></span>  
  
```  
HRESULT SetTimeout (  
    [in] EClrOperation operation,  
    [in] DWORD dsMilliseconds  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3001b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3001b-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="3001b-106">[in] Aşağıdakilerden birini [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) ortak dil çalışma zamanı (CLR) işlemi zaman aşımı ayarlanacak belirten değer.</span><span class="sxs-lookup"><span data-stu-id="3001b-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the common language runtime (CLR) operation for which to set a timeout.</span></span> <span data-ttu-id="3001b-107">Aşağıdaki değerleri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="3001b-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="3001b-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="3001b-108">OPR_AppDomainUnload</span></span>  
  
-   <span data-ttu-id="3001b-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="3001b-109">OPR_ProcessExit</span></span>  
  
-   <span data-ttu-id="3001b-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="3001b-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
-   <span data-ttu-id="3001b-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="3001b-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="3001b-112">[in] Yeni zaman aşımı değeri, milisaniye cinsinden.</span><span class="sxs-lookup"><span data-stu-id="3001b-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="3001b-113">SONSUZ değeri işlemi hiçbir zaman zaman aşımına neden olur.</span><span class="sxs-lookup"><span data-stu-id="3001b-113">A value of INFINITE causes the operation never to time out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3001b-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3001b-114">Return Value</span></span>  
  
|<span data-ttu-id="3001b-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3001b-115">HRESULT</span></span>|<span data-ttu-id="3001b-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3001b-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3001b-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="3001b-117">S_OK</span></span>|<span data-ttu-id="3001b-118">`SetTimeout`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="3001b-118">`SetTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="3001b-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3001b-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3001b-120">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="3001b-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3001b-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3001b-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3001b-122">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="3001b-122">The call timed out.</span></span>|  
|<span data-ttu-id="3001b-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3001b-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3001b-124">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="3001b-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3001b-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3001b-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3001b-126">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="3001b-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3001b-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3001b-127">E_FAIL</span></span>|<span data-ttu-id="3001b-128">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="3001b-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3001b-129">CLR, artık bir yöntem E_FAIL döndükten sonra işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="3001b-129">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3001b-130">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="3001b-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3001b-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="3001b-131">E_INVALIDARG</span></span>|<span data-ttu-id="3001b-132">Zaman aşımı ayarlanamaz için belirtilen `operation`, ya da geçersiz bir değer için sağlanan `operation`.</span><span class="sxs-lookup"><span data-stu-id="3001b-132">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3001b-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3001b-133">Requirements</span></span>  
 <span data-ttu-id="3001b-134">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3001b-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3001b-135">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3001b-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3001b-136">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="3001b-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3001b-137">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3001b-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3001b-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3001b-138">See Also</span></span>  
 [<span data-ttu-id="3001b-139">EClrOperation Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="3001b-139">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="3001b-140">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3001b-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="3001b-141">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3001b-141">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
