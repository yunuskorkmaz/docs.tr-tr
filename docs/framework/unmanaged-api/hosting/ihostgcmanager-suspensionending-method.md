---
title: "IHostGCManager::SuspensionEnding Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostGCManager.SuspensionEnding
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostGCManager::SuspensionEnding
helpviewer_keywords:
- SuspensionEnding method, IHostGCManager interface [.NET Framework hosting]
- IHostGCManager::SuspensionEnding method [.NET Framework hosting]
ms.assetid: 8849a1db-17f0-44b7-880a-bd36d431eb91
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9952e62d4979efa0d07b19f183ca71adcc643365
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostgcmanagersuspensionending-method"></a><span data-ttu-id="bbe06-102">IHostGCManager::SuspensionEnding Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bbe06-102">IHostGCManager::SuspensionEnding Method</span></span>
<span data-ttu-id="bbe06-103">Ortak dil çalışma zamanı (CLR) görevler için bir atık toplama askıya iş parçacığı üzerinde yürütülmesi sürdürüyor konak bildirir.</span><span class="sxs-lookup"><span data-stu-id="bbe06-103">Notifies the host that the common language runtime (CLR) is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbe06-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bbe06-104">Syntax</span></span>  
  
```  
HRESULT SuspensionEnding (  
    [in] DWORD generation  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bbe06-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bbe06-105">Parameters</span></span>  
 `generation`  
 <span data-ttu-id="bbe06-106">[in] Yalnızca bitiyor çöp koleksiyonu oluşturma, iş parçacığı sürdürüyor.</span><span class="sxs-lookup"><span data-stu-id="bbe06-106">[in] The garbage collection generation that is just finishing, from which the thread is resuming.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bbe06-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bbe06-107">Return Value</span></span>  
  
|<span data-ttu-id="bbe06-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bbe06-108">HRESULT</span></span>|<span data-ttu-id="bbe06-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bbe06-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bbe06-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="bbe06-110">S_OK</span></span>|<span data-ttu-id="bbe06-111">`SuspensionEnding`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="bbe06-111">`SuspensionEnding` returned successfully.</span></span>|  
|<span data-ttu-id="bbe06-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bbe06-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bbe06-113">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="bbe06-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bbe06-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bbe06-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bbe06-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="bbe06-115">The call timed out.</span></span>|  
|<span data-ttu-id="bbe06-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bbe06-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bbe06-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="bbe06-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bbe06-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bbe06-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bbe06-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="bbe06-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bbe06-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bbe06-120">E_FAIL</span></span>|<span data-ttu-id="bbe06-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="bbe06-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bbe06-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="bbe06-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bbe06-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="bbe06-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bbe06-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bbe06-124">Remarks</span></span>  
 <span data-ttu-id="bbe06-125">CLR çağrıları `SuspensionEnding` ana iş parçacığı yürütme sürdürüyor bildirmek için bir atık toplama gerçekleştirdikten sonra.</span><span class="sxs-lookup"><span data-stu-id="bbe06-125">The CLR calls `SuspensionEnding` after it performs a garbage collection, to inform the host that the thread is resuming execution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bbe06-126">Yöntem çağrısının yapılan iş parçacığı yeniden zamanla değil.</span><span class="sxs-lookup"><span data-stu-id="bbe06-126">Do not reschedule the thread the method call was made from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbe06-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bbe06-127">Requirements</span></span>  
 <span data-ttu-id="bbe06-128">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bbe06-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbe06-129">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bbe06-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bbe06-130">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="bbe06-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bbe06-131">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbe06-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbe06-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bbe06-132">See Also</span></span>  
 [<span data-ttu-id="bbe06-133">Iclrtask arabirimi</span><span class="sxs-lookup"><span data-stu-id="bbe06-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="bbe06-134">Iclrtaskmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="bbe06-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="bbe06-135">Ihosttask arabirimi</span><span class="sxs-lookup"><span data-stu-id="bbe06-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="bbe06-136">Ihosttaskmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="bbe06-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="bbe06-137">Ihostgcmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="bbe06-137">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
