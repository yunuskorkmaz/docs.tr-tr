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
ms.openlocfilehash: b3e66a1e04ca3f3031adf1f0f7f71d689ee76b04
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703408"
---
# <a name="iclrpolicymanagersettimeout-method"></a><span data-ttu-id="ecffc-102">ICLRPolicyManager::SetTimeout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ecffc-102">ICLRPolicyManager::SetTimeout Method</span></span>
<span data-ttu-id="ecffc-103">Belirtilen işlem için bir zaman aşımı değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ecffc-103">Sets a timeout value for the specified operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecffc-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ecffc-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTimeout (  
    [in] EClrOperation operation,  
    [in] DWORD dsMilliseconds  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ecffc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ecffc-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="ecffc-106">'ndaki Bir zaman aşımı ayarlanacak ortak dil çalışma zamanı (CLR) işlemini belirten [EClrOperation](eclroperation-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="ecffc-106">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the common language runtime (CLR) operation for which to set a timeout.</span></span> <span data-ttu-id="ecffc-107">Aşağıdaki değerler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="ecffc-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="ecffc-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="ecffc-108">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="ecffc-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="ecffc-109">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="ecffc-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="ecffc-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="ecffc-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="ecffc-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="ecffc-112">'ndaki Milisaniye cinsinden yeni zaman aşımı değeri.</span><span class="sxs-lookup"><span data-stu-id="ecffc-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="ecffc-113">Sonsuz değeri işlemin zaman aşımına uğramamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="ecffc-113">A value of INFINITE causes the operation never to time out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ecffc-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ecffc-114">Return Value</span></span>  
  
|<span data-ttu-id="ecffc-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ecffc-115">HRESULT</span></span>|<span data-ttu-id="ecffc-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ecffc-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ecffc-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="ecffc-117">S_OK</span></span>|<span data-ttu-id="ecffc-118">`SetTimeout`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="ecffc-118">`SetTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="ecffc-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ecffc-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ecffc-120">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="ecffc-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ecffc-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ecffc-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ecffc-122">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="ecffc-122">The call timed out.</span></span>|  
|<span data-ttu-id="ecffc-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ecffc-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ecffc-124">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="ecffc-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ecffc-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ecffc-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ecffc-126">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="ecffc-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ecffc-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ecffc-127">E_FAIL</span></span>|<span data-ttu-id="ecffc-128">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="ecffc-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ecffc-129">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ecffc-129">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ecffc-130">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="ecffc-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ecffc-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="ecffc-131">E_INVALIDARG</span></span>|<span data-ttu-id="ecffc-132">Belirtilen için bir zaman aşımı ayarlanamaz `operation` veya geçersiz bir değer sağlandı `operation` .</span><span class="sxs-lookup"><span data-stu-id="ecffc-132">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ecffc-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ecffc-133">Requirements</span></span>  
 <span data-ttu-id="ecffc-134">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecffc-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecffc-135">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ecffc-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ecffc-136">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="ecffc-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ecffc-137">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecffc-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecffc-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ecffc-138">See also</span></span>

- [<span data-ttu-id="ecffc-139">EClrOperation Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="ecffc-139">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="ecffc-140">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ecffc-140">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="ecffc-141">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ecffc-141">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
