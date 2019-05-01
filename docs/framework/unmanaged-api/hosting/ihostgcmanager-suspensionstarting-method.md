---
title: IHostGCManager::SuspensionStarting Yöntemi
ms.date: 03/30/2017
api_name:
- IHostGCManager.SuspensionStarting
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager::SuspensionStarting
helpviewer_keywords:
- SuspensionStarting method, IHostGCManager interface [.NET Framework hosting]
- IHostGCManager::SuspensionStarting method [.NET Framework hosting]
ms.assetid: c381f524-94cf-4fa2-9298-50f847a03431
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 47ef5bb2539820d5a7bcd4ca6b4de86564290709
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61984418"
---
# <a name="ihostgcmanagersuspensionstarting-method"></a><span data-ttu-id="4cb0d-102">IHostGCManager::SuspensionStarting Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4cb0d-102">IHostGCManager::SuspensionStarting Method</span></span>
<span data-ttu-id="4cb0d-103">Konak, ortak dil çalışma zamanı (CLR) yürütme görevlerin bir çöp toplama için askıya alma bildirir.</span><span class="sxs-lookup"><span data-stu-id="4cb0d-103">Notifies the host that the common language runtime (CLR) is suspending execution of tasks, to perform a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cb0d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4cb0d-104">Syntax</span></span>  
  
```  
HRESULT SuspensionStarting ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="4cb0d-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4cb0d-105">Return Value</span></span>  
  
|<span data-ttu-id="4cb0d-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4cb0d-106">HRESULT</span></span>|<span data-ttu-id="4cb0d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4cb0d-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4cb0d-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="4cb0d-108">S_OK</span></span>|<span data-ttu-id="4cb0d-109">`SuspensionStarting` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="4cb0d-109">`SuspensionStarting` returned successfully.</span></span>|  
|<span data-ttu-id="4cb0d-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4cb0d-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4cb0d-111">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="4cb0d-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4cb0d-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4cb0d-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4cb0d-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="4cb0d-113">The call timed out.</span></span>|  
|<span data-ttu-id="4cb0d-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4cb0d-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4cb0d-115">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="4cb0d-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4cb0d-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4cb0d-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4cb0d-117">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="4cb0d-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4cb0d-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4cb0d-118">E_FAIL</span></span>|<span data-ttu-id="4cb0d-119">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="4cb0d-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4cb0d-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4cb0d-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4cb0d-121">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="4cb0d-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4cb0d-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4cb0d-122">Remarks</span></span>  
 <span data-ttu-id="4cb0d-123">CLR çağrıları `SuspensionStarting` çöp toplama oluştuğu ana bilgisayara bildirmek için.</span><span class="sxs-lookup"><span data-stu-id="4cb0d-123">The CLR calls `SuspensionStarting` to inform the host that garbage collection is occurring.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4cb0d-124">Bu görevi yeniden değil.</span><span class="sxs-lookup"><span data-stu-id="4cb0d-124">Do not reschedule this task.</span></span> <span data-ttu-id="4cb0d-125">Konak, bir görev zamanlanmalı olduğunda [Threadısblockingforsuspension](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md) çağrılır.</span><span class="sxs-lookup"><span data-stu-id="4cb0d-125">The host must reschedule a task when [ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md) is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4cb0d-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4cb0d-126">Requirements</span></span>  
 <span data-ttu-id="4cb0d-127">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4cb0d-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4cb0d-128">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4cb0d-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4cb0d-129">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="4cb0d-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4cb0d-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4cb0d-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cb0d-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4cb0d-131">See also</span></span>

- [<span data-ttu-id="4cb0d-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4cb0d-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="4cb0d-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4cb0d-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="4cb0d-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4cb0d-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="4cb0d-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4cb0d-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="4cb0d-136">IHostGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4cb0d-136">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
