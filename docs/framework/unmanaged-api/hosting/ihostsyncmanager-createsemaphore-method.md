---
title: IHostSyncManager::CreateSemaphore Yöntemi
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateSemaphore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateSemaphore
helpviewer_keywords:
- CreateSemaphore method [.NET Framework hosting]
- IHostSyncManager::CreateSemaphore method [.NET Framework hosting]
ms.assetid: 37679e94-5ff9-4173-8fa5-457febeb89bf
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3ef9a5896c2ecc54b7fd48670f751d193ac74554
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59138625"
---
# <a name="ihostsyncmanagercreatesemaphore-method"></a><span data-ttu-id="6d6cf-102">IHostSyncManager::CreateSemaphore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6d6cf-102">IHostSyncManager::CreateSemaphore Method</span></span>
<span data-ttu-id="6d6cf-103">Oluşturur bir [Ihostsemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) semafor bekleme olaylar için kullanılacak ortak dil çalışma zamanı (CLR) nesnesi.</span><span class="sxs-lookup"><span data-stu-id="6d6cf-103">Creates an [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) object for the common language runtime (CLR) to use as a semaphore for wait events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d6cf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6d6cf-104">Syntax</span></span>  
  
```  
HRESULT CreateSemaphore (  
    [in]  DWORD dwInitial,  
    [in]  DWORD dwMax,  
    [out] IHostSemaphore **ppSemaphore  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d6cf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6d6cf-105">Parameters</span></span>  
 `dwInitial`  
 <span data-ttu-id="6d6cf-106">[in] Başlangıç sayısı için `ppSemaphore`.</span><span class="sxs-lookup"><span data-stu-id="6d6cf-106">[in] The initial count for `ppSemaphore`.</span></span>  
  
 `dwMax`  
 <span data-ttu-id="6d6cf-107">[in] İçin en fazla sayıyı `ppSemaphore`.</span><span class="sxs-lookup"><span data-stu-id="6d6cf-107">[in] The maximum count for `ppSemaphore`.</span></span>  
  
 `ppSemaphore`  
 <span data-ttu-id="6d6cf-108">[out] Adresine bir işaretçi bir `IHostSemaphore` örneği veya semafor oluşturulamadı yoksa null.</span><span class="sxs-lookup"><span data-stu-id="6d6cf-108">[out] A pointer to the address of an `IHostSemaphore` instance, or null if the semaphore could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6d6cf-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6d6cf-109">Return Value</span></span>  
  
|<span data-ttu-id="6d6cf-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6d6cf-110">HRESULT</span></span>|<span data-ttu-id="6d6cf-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6d6cf-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6d6cf-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="6d6cf-112">S_OK</span></span>|<span data-ttu-id="6d6cf-113">`CreateSemaphore` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="6d6cf-113">`CreateSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="6d6cf-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6d6cf-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6d6cf-115">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="6d6cf-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6d6cf-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6d6cf-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6d6cf-117">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="6d6cf-117">The call timed out.</span></span>|  
|<span data-ttu-id="6d6cf-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6d6cf-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6d6cf-119">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="6d6cf-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6d6cf-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6d6cf-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6d6cf-121">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="6d6cf-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6d6cf-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6d6cf-122">E_FAIL</span></span>|<span data-ttu-id="6d6cf-123">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="6d6cf-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6d6cf-124">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6d6cf-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6d6cf-125">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="6d6cf-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6d6cf-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="6d6cf-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="6d6cf-127">İstenen olay nesnesi oluşturmak yeterli bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="6d6cf-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d6cf-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6d6cf-128">Remarks</span></span>  
 <span data-ttu-id="6d6cf-129">`CreateSemaphore` aynı ada sahip bir Win32 işlevini yansıtır.</span><span class="sxs-lookup"><span data-stu-id="6d6cf-129">`CreateSemaphore` mirrors the Win32 function that has the same name.</span></span> <span data-ttu-id="6d6cf-130">`dwInitial` Ve `dwMax` parametreleri Win32 için semafor sayısı ile aynı semantiğe kullanma `lInitialCount` ve `lMaximumCount` parametreleri, sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="6d6cf-130">The `dwInitial` and `dwMax` parameters use the same semantics for the semaphore count as the Win32 `lInitialCount` and `lMaximumCount` parameters, respectively.</span></span> <span data-ttu-id="6d6cf-131">`dwInitial` arasında sıfır olmalıdır ve `dwMax`(dahil).</span><span class="sxs-lookup"><span data-stu-id="6d6cf-131">`dwInitial` must be between zero and `dwMax`, inclusive.</span></span> <span data-ttu-id="6d6cf-132">`dwMax` Sıfırdan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6d6cf-132">`dwMax` must be greater than zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d6cf-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6d6cf-133">Requirements</span></span>  
 <span data-ttu-id="6d6cf-134">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d6cf-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d6cf-135">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6d6cf-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6d6cf-136">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="6d6cf-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6d6cf-137">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d6cf-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d6cf-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d6cf-138">See also</span></span>

- [<span data-ttu-id="6d6cf-139">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6d6cf-139">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="6d6cf-140">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6d6cf-140">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="6d6cf-141">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6d6cf-141">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
