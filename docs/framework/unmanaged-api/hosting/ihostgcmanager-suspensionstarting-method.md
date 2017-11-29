---
title: "IHostGCManager::SuspensionStarting Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostGCManager.SuspensionStarting
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostGCManager::SuspensionStarting
helpviewer_keywords:
- SuspensionStarting method, IHostGCManager interface [.NET Framework hosting]
- IHostGCManager::SuspensionStarting method [.NET Framework hosting]
ms.assetid: c381f524-94cf-4fa2-9298-50f847a03431
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9c807a124570f38922509d27e52936b980e36fba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostgcmanagersuspensionstarting-method"></a><span data-ttu-id="14676-102">IHostGCManager::SuspensionStarting Yöntemi</span><span class="sxs-lookup"><span data-stu-id="14676-102">IHostGCManager::SuspensionStarting Method</span></span>
<span data-ttu-id="14676-103">Ortak dil çalışma zamanı (CLR) yürütme görevlerin çöp toplama gerçekleştirmek için askıya alma konak bildirir.</span><span class="sxs-lookup"><span data-stu-id="14676-103">Notifies the host that the common language runtime (CLR) is suspending execution of tasks, to perform a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14676-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="14676-104">Syntax</span></span>  
  
```  
HRESULT SuspensionStarting ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="14676-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="14676-105">Return Value</span></span>  
  
|<span data-ttu-id="14676-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="14676-106">HRESULT</span></span>|<span data-ttu-id="14676-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="14676-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="14676-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="14676-108">S_OK</span></span>|<span data-ttu-id="14676-109">`SuspensionStarting`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="14676-109">`SuspensionStarting` returned successfully.</span></span>|  
|<span data-ttu-id="14676-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="14676-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="14676-111">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="14676-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="14676-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="14676-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="14676-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="14676-113">The call timed out.</span></span>|  
|<span data-ttu-id="14676-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="14676-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="14676-115">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="14676-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="14676-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="14676-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="14676-117">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="14676-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="14676-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="14676-118">E_FAIL</span></span>|<span data-ttu-id="14676-119">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="14676-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="14676-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="14676-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="14676-121">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="14676-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14676-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="14676-122">Remarks</span></span>  
 <span data-ttu-id="14676-123">CLR çağrıları `SuspensionStarting` çöp toplama oluştuğunu konak bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="14676-123">The CLR calls `SuspensionStarting` to inform the host that garbage collection is occurring.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="14676-124">Bu görevi yeniden zamanlayın değil.</span><span class="sxs-lookup"><span data-stu-id="14676-124">Do not reschedule this task.</span></span> <span data-ttu-id="14676-125">Konak bir görev zamanlanmalı zaman [Threadısblockingforsuspension](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md) olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="14676-125">The host must reschedule a task when [ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md) is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14676-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="14676-126">Requirements</span></span>  
 <span data-ttu-id="14676-127">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14676-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14676-128">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="14676-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="14676-129">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="14676-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="14676-130">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14676-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14676-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="14676-131">See Also</span></span>  
 [<span data-ttu-id="14676-132">Iclrtask arabirimi</span><span class="sxs-lookup"><span data-stu-id="14676-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="14676-133">Iclrtaskmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="14676-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="14676-134">Ihosttask arabirimi</span><span class="sxs-lookup"><span data-stu-id="14676-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="14676-135">Ihosttaskmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="14676-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="14676-136">Ihostgcmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="14676-136">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
