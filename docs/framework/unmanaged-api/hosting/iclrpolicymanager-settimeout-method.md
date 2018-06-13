---
title: ICLRPolicyManager::SetTimeout Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetTimeout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetTimeout
helpviewer_keywords:
- SetTimeout method [.NET Framework hosting]
- ICLRPolicyManager::SetTimeout method [.NET Framework hosting]
ms.assetid: 954404fd-d52d-4e68-b582-8692f3a5f608
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b5a389af718322d1e0fffebae046bf28731877b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435783"
---
# <a name="iclrpolicymanagersettimeout-method"></a><span data-ttu-id="49836-102">ICLRPolicyManager::SetTimeout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="49836-102">ICLRPolicyManager::SetTimeout Method</span></span>
<span data-ttu-id="49836-103">Belirtilen işlem için bir zaman aşımı değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="49836-103">Sets a timeout value for the specified operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49836-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="49836-104">Syntax</span></span>  
  
```  
HRESULT SetTimeout (  
    [in] EClrOperation operation,  
    [in] DWORD dsMilliseconds  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="49836-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="49836-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="49836-106">[in] Aşağıdakilerden birini [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) ortak dil çalışma zamanı (CLR) işlemi zaman aşımı ayarlanacak belirten değer.</span><span class="sxs-lookup"><span data-stu-id="49836-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the common language runtime (CLR) operation for which to set a timeout.</span></span> <span data-ttu-id="49836-107">Aşağıdaki değerleri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="49836-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="49836-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="49836-108">OPR_AppDomainUnload</span></span>  
  
-   <span data-ttu-id="49836-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="49836-109">OPR_ProcessExit</span></span>  
  
-   <span data-ttu-id="49836-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="49836-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
-   <span data-ttu-id="49836-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="49836-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="49836-112">[in] Yeni zaman aşımı değeri, milisaniye cinsinden.</span><span class="sxs-lookup"><span data-stu-id="49836-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="49836-113">SONSUZ değeri işlemi hiçbir zaman zaman aşımına neden olur.</span><span class="sxs-lookup"><span data-stu-id="49836-113">A value of INFINITE causes the operation never to time out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="49836-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="49836-114">Return Value</span></span>  
  
|<span data-ttu-id="49836-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="49836-115">HRESULT</span></span>|<span data-ttu-id="49836-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="49836-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="49836-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="49836-117">S_OK</span></span>|<span data-ttu-id="49836-118">`SetTimeout` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="49836-118">`SetTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="49836-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="49836-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="49836-120">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="49836-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="49836-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="49836-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="49836-122">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="49836-122">The call timed out.</span></span>|  
|<span data-ttu-id="49836-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="49836-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="49836-124">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="49836-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="49836-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="49836-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="49836-126">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="49836-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="49836-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="49836-127">E_FAIL</span></span>|<span data-ttu-id="49836-128">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="49836-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="49836-129">CLR, artık bir yöntem E_FAIL döndükten sonra işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="49836-129">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="49836-130">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="49836-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="49836-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="49836-131">E_INVALIDARG</span></span>|<span data-ttu-id="49836-132">Zaman aşımı ayarlanamaz için belirtilen `operation`, ya da geçersiz bir değer için sağlanan `operation`.</span><span class="sxs-lookup"><span data-stu-id="49836-132">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="49836-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="49836-133">Requirements</span></span>  
 <span data-ttu-id="49836-134">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49836-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49836-135">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="49836-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="49836-136">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="49836-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="49836-137">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49836-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49836-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="49836-138">See Also</span></span>  
 [<span data-ttu-id="49836-139">EClrOperation Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="49836-139">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="49836-140">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="49836-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="49836-141">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="49836-141">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
