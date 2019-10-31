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
ms.openlocfilehash: 516ba1325404e757af8e38de239864b21b1640f1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140753"
---
# <a name="iclrpolicymanagersettimeout-method"></a><span data-ttu-id="5756b-102">ICLRPolicyManager::SetTimeout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5756b-102">ICLRPolicyManager::SetTimeout Method</span></span>
<span data-ttu-id="5756b-103">Belirtilen işlem için bir zaman aşımı değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5756b-103">Sets a timeout value for the specified operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5756b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5756b-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTimeout (  
    [in] EClrOperation operation,  
    [in] DWORD dsMilliseconds  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5756b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5756b-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="5756b-106">'ndaki Bir zaman aşımı ayarlanacak ortak dil çalışma zamanı (CLR) işlemini belirten [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="5756b-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the common language runtime (CLR) operation for which to set a timeout.</span></span> <span data-ttu-id="5756b-107">Aşağıdaki değerler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="5756b-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="5756b-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="5756b-108">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="5756b-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="5756b-109">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="5756b-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="5756b-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="5756b-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="5756b-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="5756b-112">'ndaki Milisaniye cinsinden yeni zaman aşımı değeri.</span><span class="sxs-lookup"><span data-stu-id="5756b-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="5756b-113">Sonsuz değeri işlemin zaman aşımına uğramamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="5756b-113">A value of INFINITE causes the operation never to time out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5756b-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5756b-114">Return Value</span></span>  
  
|<span data-ttu-id="5756b-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5756b-115">HRESULT</span></span>|<span data-ttu-id="5756b-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5756b-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5756b-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="5756b-117">S_OK</span></span>|<span data-ttu-id="5756b-118">`SetTimeout` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="5756b-118">`SetTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="5756b-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5756b-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5756b-120">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="5756b-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5756b-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5756b-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5756b-122">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="5756b-122">The call timed out.</span></span>|  
|<span data-ttu-id="5756b-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5756b-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5756b-124">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="5756b-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5756b-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5756b-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5756b-126">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="5756b-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5756b-127">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="5756b-127">E_FAIL</span></span>|<span data-ttu-id="5756b-128">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="5756b-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5756b-129">Bir yöntem E_FAıL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="5756b-129">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5756b-130">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="5756b-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5756b-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="5756b-131">E_INVALIDARG</span></span>|<span data-ttu-id="5756b-132">Belirtilen `operation`için zaman aşımı ayarlanamaz veya `operation`için geçersiz bir değer sağlandı.</span><span class="sxs-lookup"><span data-stu-id="5756b-132">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5756b-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5756b-133">Requirements</span></span>  
 <span data-ttu-id="5756b-134">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5756b-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5756b-135">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5756b-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5756b-136">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="5756b-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5756b-137">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5756b-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5756b-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5756b-138">See also</span></span>

- [<span data-ttu-id="5756b-139">EClrOperation Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="5756b-139">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="5756b-140">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5756b-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="5756b-141">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5756b-141">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
