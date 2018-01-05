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
ms.workload: dotnet
ms.openlocfilehash: d8df29b3eeb565aaa4a977762fcc453fb985e40d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsyncmanagercreatesemaphore-method"></a><span data-ttu-id="4c5c1-102">IHostSyncManager::CreateSemaphore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4c5c1-102">IHostSyncManager::CreateSemaphore Method</span></span>
<span data-ttu-id="4c5c1-103">Oluşturur bir [Ihostsemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) nesnesi semafor bekleme olayları için kullanılacak ortak dil çalışma zamanı (CLR).</span><span class="sxs-lookup"><span data-stu-id="4c5c1-103">Creates an [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) object for the common language runtime (CLR) to use as a semaphore for wait events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c5c1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4c5c1-104">Syntax</span></span>  
  
```  
HRESULT CreateSemaphore (  
    [in]  DWORD dwInitial,  
    [in]  DWORD dwMax,  
    [out] IHostSemaphore **ppSemaphore  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4c5c1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4c5c1-105">Parameters</span></span>  
 `dwInitial`  
 <span data-ttu-id="4c5c1-106">[in] İçin ilk sayısı `ppSemaphore`.</span><span class="sxs-lookup"><span data-stu-id="4c5c1-106">[in] The initial count for `ppSemaphore`.</span></span>  
  
 `dwMax`  
 <span data-ttu-id="4c5c1-107">[in] İçin en fazla sayısı `ppSemaphore`.</span><span class="sxs-lookup"><span data-stu-id="4c5c1-107">[in] The maximum count for `ppSemaphore`.</span></span>  
  
 `ppSemaphore`  
 <span data-ttu-id="4c5c1-108">[out] Adresine bir işaretçi bir `IHostSemaphore` örneği veya semafor oluşturulamadı yoksa null.</span><span class="sxs-lookup"><span data-stu-id="4c5c1-108">[out] A pointer to the address of an `IHostSemaphore` instance, or null if the semaphore could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4c5c1-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4c5c1-109">Return Value</span></span>  
  
|<span data-ttu-id="4c5c1-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4c5c1-110">HRESULT</span></span>|<span data-ttu-id="4c5c1-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4c5c1-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4c5c1-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="4c5c1-112">S_OK</span></span>|<span data-ttu-id="4c5c1-113">`CreateSemaphore`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="4c5c1-113">`CreateSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="4c5c1-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4c5c1-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4c5c1-115">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="4c5c1-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4c5c1-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4c5c1-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4c5c1-117">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="4c5c1-117">The call timed out.</span></span>|  
|<span data-ttu-id="4c5c1-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4c5c1-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4c5c1-119">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="4c5c1-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4c5c1-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4c5c1-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4c5c1-121">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="4c5c1-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4c5c1-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4c5c1-122">E_FAIL</span></span>|<span data-ttu-id="4c5c1-123">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="4c5c1-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4c5c1-124">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4c5c1-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4c5c1-125">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="4c5c1-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4c5c1-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="4c5c1-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="4c5c1-127">İstenen olay nesnesi oluşturmak yeterli bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="4c5c1-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c5c1-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4c5c1-128">Remarks</span></span>  
 <span data-ttu-id="4c5c1-129">`CreateSemaphore`aynı ada sahip Win32 işlevi yansıtır.</span><span class="sxs-lookup"><span data-stu-id="4c5c1-129">`CreateSemaphore` mirrors the Win32 function that has the same name.</span></span> <span data-ttu-id="4c5c1-130">`dwInitial` Ve `dwMax` parametreleri Win32 için semafor sayısı aynı semantiğini kullanın `lInitialCount` ve `lMaximumCount` parametreleri, sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="4c5c1-130">The `dwInitial` and `dwMax` parameters use the same semantics for the semaphore count as the Win32 `lInitialCount` and `lMaximumCount` parameters, respectively.</span></span> <span data-ttu-id="4c5c1-131">`dwInitial`sıfır arasında olmalıdır ve `dwMax`(dahil).</span><span class="sxs-lookup"><span data-stu-id="4c5c1-131">`dwInitial` must be between zero and `dwMax`, inclusive.</span></span> <span data-ttu-id="4c5c1-132">`dwMax`sıfırdan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4c5c1-132">`dwMax` must be greater than zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c5c1-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4c5c1-133">Requirements</span></span>  
 <span data-ttu-id="4c5c1-134">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c5c1-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c5c1-135">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4c5c1-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4c5c1-136">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="4c5c1-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4c5c1-137">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c5c1-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c5c1-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4c5c1-138">See Also</span></span>  
 [<span data-ttu-id="4c5c1-139">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4c5c1-139">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="4c5c1-140">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4c5c1-140">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="4c5c1-141">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4c5c1-141">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
