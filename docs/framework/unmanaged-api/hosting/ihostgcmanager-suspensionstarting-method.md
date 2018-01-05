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
ms.workload: dotnet
ms.openlocfilehash: 30f6c611dc719fa6f1162498082cc9a60fb5059b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostgcmanagersuspensionstarting-method"></a><span data-ttu-id="e9a82-102">IHostGCManager::SuspensionStarting Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e9a82-102">IHostGCManager::SuspensionStarting Method</span></span>
<span data-ttu-id="e9a82-103">Ortak dil çalışma zamanı (CLR) yürütme görevlerin çöp toplama gerçekleştirmek için askıya alma konak bildirir.</span><span class="sxs-lookup"><span data-stu-id="e9a82-103">Notifies the host that the common language runtime (CLR) is suspending execution of tasks, to perform a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9a82-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e9a82-104">Syntax</span></span>  
  
```  
HRESULT SuspensionStarting ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e9a82-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e9a82-105">Return Value</span></span>  
  
|<span data-ttu-id="e9a82-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e9a82-106">HRESULT</span></span>|<span data-ttu-id="e9a82-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e9a82-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e9a82-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="e9a82-108">S_OK</span></span>|<span data-ttu-id="e9a82-109">`SuspensionStarting`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e9a82-109">`SuspensionStarting` returned successfully.</span></span>|  
|<span data-ttu-id="e9a82-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e9a82-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e9a82-111">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="e9a82-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e9a82-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e9a82-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e9a82-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="e9a82-113">The call timed out.</span></span>|  
|<span data-ttu-id="e9a82-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e9a82-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e9a82-115">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="e9a82-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e9a82-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e9a82-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e9a82-117">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="e9a82-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e9a82-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e9a82-118">E_FAIL</span></span>|<span data-ttu-id="e9a82-119">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e9a82-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e9a82-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e9a82-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e9a82-121">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="e9a82-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9a82-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e9a82-122">Remarks</span></span>  
 <span data-ttu-id="e9a82-123">CLR çağrıları `SuspensionStarting` çöp toplama oluştuğunu konak bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9a82-123">The CLR calls `SuspensionStarting` to inform the host that garbage collection is occurring.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e9a82-124">Bu görevi yeniden zamanlayın değil.</span><span class="sxs-lookup"><span data-stu-id="e9a82-124">Do not reschedule this task.</span></span> <span data-ttu-id="e9a82-125">Konak bir görev zamanlanmalı zaman [Threadısblockingforsuspension](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md) olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="e9a82-125">The host must reschedule a task when [ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md) is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9a82-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e9a82-126">Requirements</span></span>  
 <span data-ttu-id="e9a82-127">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9a82-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9a82-128">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e9a82-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e9a82-129">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e9a82-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e9a82-130">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9a82-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9a82-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e9a82-131">See Also</span></span>  
 [<span data-ttu-id="e9a82-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9a82-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="e9a82-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9a82-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="e9a82-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9a82-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="e9a82-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9a82-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="e9a82-136">IHostGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9a82-136">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
