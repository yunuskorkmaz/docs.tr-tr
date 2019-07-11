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
ms.openlocfilehash: 9a815d1a5e8b40aee84ca2b9971ae4be7fb2c725
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763733"
---
# <a name="ihostgcmanagersuspensionending-method"></a><span data-ttu-id="571b1-102">IHostGCManager::SuspensionEnding Yöntemi</span><span class="sxs-lookup"><span data-stu-id="571b1-102">IHostGCManager::SuspensionEnding Method</span></span>
<span data-ttu-id="571b1-103">Konak, ortak dil çalışma zamanı (CLR) askıya alındığı için çöp toplama iş parçacığı üzerinde görevlerin yürütülmesi sürdürülmekte bildirir.</span><span class="sxs-lookup"><span data-stu-id="571b1-103">Notifies the host that the common language runtime (CLR) is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="571b1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="571b1-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionEnding (  
    [in] DWORD generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="571b1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="571b1-105">Parameters</span></span>  
 `generation`  
 <span data-ttu-id="571b1-106">[in] Yalnızca tamamlama, çöp toplama oluşturma iş parçacığı içinden sürdürüyor.</span><span class="sxs-lookup"><span data-stu-id="571b1-106">[in] The garbage collection generation that is just finishing, from which the thread is resuming.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="571b1-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="571b1-107">Return Value</span></span>  
  
|<span data-ttu-id="571b1-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="571b1-108">HRESULT</span></span>|<span data-ttu-id="571b1-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="571b1-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="571b1-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="571b1-110">S_OK</span></span>|<span data-ttu-id="571b1-111">`SuspensionEnding` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="571b1-111">`SuspensionEnding` returned successfully.</span></span>|  
|<span data-ttu-id="571b1-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="571b1-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="571b1-113">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="571b1-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="571b1-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="571b1-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="571b1-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="571b1-115">The call timed out.</span></span>|  
|<span data-ttu-id="571b1-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="571b1-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="571b1-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="571b1-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="571b1-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="571b1-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="571b1-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="571b1-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="571b1-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="571b1-120">E_FAIL</span></span>|<span data-ttu-id="571b1-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="571b1-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="571b1-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="571b1-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="571b1-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="571b1-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="571b1-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="571b1-124">Remarks</span></span>  
 <span data-ttu-id="571b1-125">CLR çağrıları `SuspensionEnding` sonra ana iş parçacığı yürütme sürdürülmekte bildirmek için bir atık toplama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="571b1-125">The CLR calls `SuspensionEnding` after it performs a garbage collection, to inform the host that the thread is resuming execution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="571b1-126">Yöntem çağrısı yapılan iş parçacığı yeniden değil.</span><span class="sxs-lookup"><span data-stu-id="571b1-126">Do not reschedule the thread the method call was made from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="571b1-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="571b1-127">Requirements</span></span>  
 <span data-ttu-id="571b1-128">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="571b1-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="571b1-129">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="571b1-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="571b1-130">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="571b1-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="571b1-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="571b1-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="571b1-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="571b1-132">See also</span></span>

- [<span data-ttu-id="571b1-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="571b1-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="571b1-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="571b1-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="571b1-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="571b1-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="571b1-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="571b1-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="571b1-137">IHostGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="571b1-137">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
