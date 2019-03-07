---
title: IHostGCManager::SuspensionEnding Yöntemi
ms.date: 03/30/2017
api_name:
- IHostGCManager.SuspensionEnding
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager::SuspensionEnding
helpviewer_keywords:
- SuspensionEnding method, IHostGCManager interface [.NET Framework hosting]
- IHostGCManager::SuspensionEnding method [.NET Framework hosting]
ms.assetid: 8849a1db-17f0-44b7-880a-bd36d431eb91
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1995321e8598d010188fee2437640b4489eaa294
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57472037"
---
# <a name="ihostgcmanagersuspensionending-method"></a><span data-ttu-id="49b95-102">IHostGCManager::SuspensionEnding Yöntemi</span><span class="sxs-lookup"><span data-stu-id="49b95-102">IHostGCManager::SuspensionEnding Method</span></span>
<span data-ttu-id="49b95-103">Konak, ortak dil çalışma zamanı (CLR) askıya alındığı için çöp toplama iş parçacığı üzerinde görevlerin yürütülmesi sürdürülmekte bildirir.</span><span class="sxs-lookup"><span data-stu-id="49b95-103">Notifies the host that the common language runtime (CLR) is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49b95-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="49b95-104">Syntax</span></span>  
  
```  
HRESULT SuspensionEnding (  
    [in] DWORD generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49b95-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="49b95-105">Parameters</span></span>  
 `generation`  
 <span data-ttu-id="49b95-106">[in] Yalnızca tamamlama, çöp toplama oluşturma iş parçacığı içinden sürdürüyor.</span><span class="sxs-lookup"><span data-stu-id="49b95-106">[in] The garbage collection generation that is just finishing, from which the thread is resuming.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="49b95-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="49b95-107">Return Value</span></span>  
  
|<span data-ttu-id="49b95-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="49b95-108">HRESULT</span></span>|<span data-ttu-id="49b95-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="49b95-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="49b95-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="49b95-110">S_OK</span></span>|<span data-ttu-id="49b95-111">`SuspensionEnding` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="49b95-111">`SuspensionEnding` returned successfully.</span></span>|  
|<span data-ttu-id="49b95-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="49b95-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="49b95-113">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="49b95-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="49b95-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="49b95-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="49b95-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="49b95-115">The call timed out.</span></span>|  
|<span data-ttu-id="49b95-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="49b95-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="49b95-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="49b95-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="49b95-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="49b95-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="49b95-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="49b95-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="49b95-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="49b95-120">E_FAIL</span></span>|<span data-ttu-id="49b95-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="49b95-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="49b95-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="49b95-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="49b95-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="49b95-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="49b95-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="49b95-124">Remarks</span></span>  
 <span data-ttu-id="49b95-125">CLR çağrıları `SuspensionEnding` sonra ana iş parçacığı yürütme sürdürülmekte bildirmek için bir atık toplama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="49b95-125">The CLR calls `SuspensionEnding` after it performs a garbage collection, to inform the host that the thread is resuming execution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="49b95-126">Yöntem çağrısı yapılan iş parçacığı yeniden değil.</span><span class="sxs-lookup"><span data-stu-id="49b95-126">Do not reschedule the thread the method call was made from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49b95-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="49b95-127">Requirements</span></span>  
 <span data-ttu-id="49b95-128">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49b95-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49b95-129">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="49b95-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="49b95-130">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="49b95-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="49b95-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49b95-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49b95-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49b95-132">See also</span></span>
- [<span data-ttu-id="49b95-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="49b95-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="49b95-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="49b95-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="49b95-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="49b95-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="49b95-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="49b95-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="49b95-137">IHostGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="49b95-137">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
