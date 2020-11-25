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
ms.openlocfilehash: 459c5bc0699487b62d5dcf76f1044faf53ebab8b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732469"
---
# <a name="iclrpolicymanagersettimeout-method"></a><span data-ttu-id="a42d2-102">ICLRPolicyManager::SetTimeout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a42d2-102">ICLRPolicyManager::SetTimeout Method</span></span>

<span data-ttu-id="a42d2-103">Belirtilen işlem için bir zaman aşımı değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a42d2-103">Sets a timeout value for the specified operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a42d2-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a42d2-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTimeout (  
    [in] EClrOperation operation,  
    [in] DWORD dsMilliseconds  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a42d2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a42d2-105">Parameters</span></span>  

 `operation`  
 <span data-ttu-id="a42d2-106">'ndaki Bir zaman aşımı ayarlanacak ortak dil çalışma zamanı (CLR) işlemini belirten [EClrOperation](eclroperation-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="a42d2-106">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the common language runtime (CLR) operation for which to set a timeout.</span></span> <span data-ttu-id="a42d2-107">Aşağıdaki değerler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="a42d2-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="a42d2-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="a42d2-108">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="a42d2-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="a42d2-109">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="a42d2-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="a42d2-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="a42d2-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="a42d2-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="a42d2-112">'ndaki Milisaniye cinsinden yeni zaman aşımı değeri.</span><span class="sxs-lookup"><span data-stu-id="a42d2-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="a42d2-113">Sonsuz değeri işlemin zaman aşımına uğramamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a42d2-113">A value of INFINITE causes the operation never to time out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a42d2-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a42d2-114">Return Value</span></span>  
  
|<span data-ttu-id="a42d2-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a42d2-115">HRESULT</span></span>|<span data-ttu-id="a42d2-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a42d2-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a42d2-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="a42d2-117">S_OK</span></span>|<span data-ttu-id="a42d2-118">`SetTimeout` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="a42d2-118">`SetTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="a42d2-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a42d2-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a42d2-120">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="a42d2-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a42d2-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a42d2-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a42d2-122">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="a42d2-122">The call timed out.</span></span>|  
|<span data-ttu-id="a42d2-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a42d2-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a42d2-124">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a42d2-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a42d2-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a42d2-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a42d2-126">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="a42d2-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a42d2-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a42d2-127">E_FAIL</span></span>|<span data-ttu-id="a42d2-128">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a42d2-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a42d2-129">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a42d2-129">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a42d2-130">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="a42d2-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a42d2-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a42d2-131">E_INVALIDARG</span></span>|<span data-ttu-id="a42d2-132">Belirtilen için bir zaman aşımı ayarlanamaz `operation` veya geçersiz bir değer sağlandı `operation` .</span><span class="sxs-lookup"><span data-stu-id="a42d2-132">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a42d2-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a42d2-133">Requirements</span></span>  

 <span data-ttu-id="a42d2-134">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a42d2-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a42d2-135">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a42d2-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a42d2-136">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="a42d2-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a42d2-137">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a42d2-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a42d2-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a42d2-138">See also</span></span>

- [<span data-ttu-id="a42d2-139">EClrOperation Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="a42d2-139">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="a42d2-140">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a42d2-140">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="a42d2-141">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a42d2-141">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
