---
description: ': ICLRPolicyManager:: SetTimeout Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 5fb65e93cc6eea7826498ff6b03147773f06e0b8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781902"
---
# <a name="iclrpolicymanagersettimeout-method"></a><span data-ttu-id="68113-103">ICLRPolicyManager::SetTimeout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="68113-103">ICLRPolicyManager::SetTimeout Method</span></span>

<span data-ttu-id="68113-104">Belirtilen işlem için bir zaman aşımı değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="68113-104">Sets a timeout value for the specified operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68113-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="68113-105">Syntax</span></span>  
  
```cpp  
HRESULT SetTimeout (  
    [in] EClrOperation operation,  
    [in] DWORD dsMilliseconds  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68113-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="68113-106">Parameters</span></span>  

 `operation`  
 <span data-ttu-id="68113-107">'ndaki Bir zaman aşımı ayarlanacak ortak dil çalışma zamanı (CLR) işlemini belirten [EClrOperation](eclroperation-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="68113-107">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the common language runtime (CLR) operation for which to set a timeout.</span></span> <span data-ttu-id="68113-108">Aşağıdaki değerler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="68113-108">The following values are supported:</span></span>  
  
- <span data-ttu-id="68113-109">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="68113-109">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="68113-110">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="68113-110">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="68113-111">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="68113-111">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="68113-112">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="68113-112">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="68113-113">'ndaki Milisaniye cinsinden yeni zaman aşımı değeri.</span><span class="sxs-lookup"><span data-stu-id="68113-113">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="68113-114">Sonsuz değeri işlemin zaman aşımına uğramamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="68113-114">A value of INFINITE causes the operation never to time out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="68113-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="68113-115">Return Value</span></span>  
  
|<span data-ttu-id="68113-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="68113-116">HRESULT</span></span>|<span data-ttu-id="68113-117">Description</span><span class="sxs-lookup"><span data-stu-id="68113-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="68113-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="68113-118">S_OK</span></span>|<span data-ttu-id="68113-119">`SetTimeout` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="68113-119">`SetTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="68113-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="68113-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="68113-121">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="68113-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="68113-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="68113-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="68113-123">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="68113-123">The call timed out.</span></span>|  
|<span data-ttu-id="68113-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="68113-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="68113-125">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="68113-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="68113-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="68113-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="68113-127">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="68113-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="68113-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="68113-128">E_FAIL</span></span>|<span data-ttu-id="68113-129">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="68113-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="68113-130">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="68113-130">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="68113-131">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="68113-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="68113-132">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="68113-132">E_INVALIDARG</span></span>|<span data-ttu-id="68113-133">Belirtilen için bir zaman aşımı ayarlanamaz `operation` veya geçersiz bir değer sağlandı `operation` .</span><span class="sxs-lookup"><span data-stu-id="68113-133">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="68113-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="68113-134">Requirements</span></span>  

 <span data-ttu-id="68113-135">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68113-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68113-136">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="68113-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="68113-137">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="68113-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="68113-138">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68113-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68113-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68113-139">See also</span></span>

- [<span data-ttu-id="68113-140">EClrOperation Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="68113-140">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="68113-141">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="68113-141">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="68113-142">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="68113-142">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
