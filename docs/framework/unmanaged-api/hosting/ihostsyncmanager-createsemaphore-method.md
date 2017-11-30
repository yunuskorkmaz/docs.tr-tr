---
title: "IHostSyncManager::CreateSemaphore Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager.CreateSemaphore
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager::CreateSemaphore
helpviewer_keywords:
- CreateSemaphore method [.NET Framework hosting]
- IHostSyncManager::CreateSemaphore method [.NET Framework hosting]
ms.assetid: 37679e94-5ff9-4173-8fa5-457febeb89bf
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7c7e33e4f178a4fd51ae27912959d0e4edf30ecb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsyncmanagercreatesemaphore-method"></a><span data-ttu-id="0e29d-102">IHostSyncManager::CreateSemaphore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0e29d-102">IHostSyncManager::CreateSemaphore Method</span></span>
<span data-ttu-id="0e29d-103">Oluşturur bir [Ihostsemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) nesnesi semafor bekleme olayları için kullanılacak ortak dil çalışma zamanı (CLR).</span><span class="sxs-lookup"><span data-stu-id="0e29d-103">Creates an [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) object for the common language runtime (CLR) to use as a semaphore for wait events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e29d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0e29d-104">Syntax</span></span>  
  
```  
HRESULT CreateSemaphore (  
    [in]  DWORD dwInitial,  
    [in]  DWORD dwMax,  
    [out] IHostSemaphore **ppSemaphore  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0e29d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0e29d-105">Parameters</span></span>  
 `dwInitial`  
 <span data-ttu-id="0e29d-106">[in] İçin ilk sayısı `ppSemaphore`.</span><span class="sxs-lookup"><span data-stu-id="0e29d-106">[in] The initial count for `ppSemaphore`.</span></span>  
  
 `dwMax`  
 <span data-ttu-id="0e29d-107">[in] İçin en fazla sayısı `ppSemaphore`.</span><span class="sxs-lookup"><span data-stu-id="0e29d-107">[in] The maximum count for `ppSemaphore`.</span></span>  
  
 `ppSemaphore`  
 <span data-ttu-id="0e29d-108">[out] Adresine bir işaretçi bir `IHostSemaphore` örneği veya semafor oluşturulamadı yoksa null.</span><span class="sxs-lookup"><span data-stu-id="0e29d-108">[out] A pointer to the address of an `IHostSemaphore` instance, or null if the semaphore could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0e29d-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0e29d-109">Return Value</span></span>  
  
|<span data-ttu-id="0e29d-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0e29d-110">HRESULT</span></span>|<span data-ttu-id="0e29d-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e29d-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0e29d-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="0e29d-112">S_OK</span></span>|<span data-ttu-id="0e29d-113">`CreateSemaphore`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="0e29d-113">`CreateSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="0e29d-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0e29d-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0e29d-115">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="0e29d-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0e29d-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0e29d-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0e29d-117">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="0e29d-117">The call timed out.</span></span>|  
|<span data-ttu-id="0e29d-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0e29d-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0e29d-119">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="0e29d-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0e29d-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0e29d-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0e29d-121">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="0e29d-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0e29d-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0e29d-122">E_FAIL</span></span>|<span data-ttu-id="0e29d-123">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="0e29d-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0e29d-124">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0e29d-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0e29d-125">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="0e29d-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0e29d-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="0e29d-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="0e29d-127">İstenen olay nesnesi oluşturmak yeterli bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="0e29d-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e29d-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0e29d-128">Remarks</span></span>  
 <span data-ttu-id="0e29d-129">`CreateSemaphore`aynı ada sahip Win32 işlevi yansıtır.</span><span class="sxs-lookup"><span data-stu-id="0e29d-129">`CreateSemaphore` mirrors the Win32 function that has the same name.</span></span> <span data-ttu-id="0e29d-130">`dwInitial` Ve `dwMax` parametreleri Win32 için semafor sayısı aynı semantiğini kullanın `lInitialCount` ve `lMaximumCount` parametreleri, sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="0e29d-130">The `dwInitial` and `dwMax` parameters use the same semantics for the semaphore count as the Win32 `lInitialCount` and `lMaximumCount` parameters, respectively.</span></span> <span data-ttu-id="0e29d-131">`dwInitial`sıfır arasında olmalıdır ve `dwMax`(dahil).</span><span class="sxs-lookup"><span data-stu-id="0e29d-131">`dwInitial` must be between zero and `dwMax`, inclusive.</span></span> <span data-ttu-id="0e29d-132">`dwMax`sıfırdan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0e29d-132">`dwMax` must be greater than zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e29d-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0e29d-133">Requirements</span></span>  
 <span data-ttu-id="0e29d-134">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e29d-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e29d-135">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0e29d-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0e29d-136">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="0e29d-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0e29d-137">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e29d-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e29d-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0e29d-138">See Also</span></span>  
 [<span data-ttu-id="0e29d-139">Iclrsyncmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="0e29d-139">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="0e29d-140">Ihostsemaphore arabirimi</span><span class="sxs-lookup"><span data-stu-id="0e29d-140">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="0e29d-141">Ihostsyncmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="0e29d-141">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
