---
title: IHostGCManager::ThreadIsBlockingForSuspension Yöntemi
ms.date: 03/30/2017
api_name:
- IHostGCManager.ThreadIsBlockingForSuspension
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager::ThreadIsBlockingForSuspension
helpviewer_keywords:
- IHostGCManager::ThreadIsBlockingForSuspension method [.NET Framework hosting]
- ThreadIsBlockingForSuspension method [.NET Framework hosting]
ms.assetid: 2657d45d-26d2-4d0a-8473-32b652e3321d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 740f408b84dad67ee20c2508ae42a9569ed095f1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59179874"
---
# <a name="ihostgcmanagerthreadisblockingforsuspension-method"></a><span data-ttu-id="317b8-102">IHostGCManager::ThreadIsBlockingForSuspension Yöntemi</span><span class="sxs-lookup"><span data-stu-id="317b8-102">IHostGCManager::ThreadIsBlockingForSuspension Method</span></span>
<span data-ttu-id="317b8-103">İş parçacığı içinden yöntem çağrısı yapıldı, konağa bildirir yönelik bir çöp toplamanın engellemek üzere.</span><span class="sxs-lookup"><span data-stu-id="317b8-103">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="317b8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="317b8-104">Syntax</span></span>  
  
```  
HRESULT ThreadIsBlockingForSuspension ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="317b8-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="317b8-105">Return Value</span></span>  
  
|<span data-ttu-id="317b8-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="317b8-106">HRESULT</span></span>|<span data-ttu-id="317b8-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="317b8-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="317b8-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="317b8-108">S_OK</span></span>|<span data-ttu-id="317b8-109">`ThreadIsBlockingForSuspension` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="317b8-109">`ThreadIsBlockingForSuspension` returned successfully.</span></span>|  
|<span data-ttu-id="317b8-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="317b8-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="317b8-111">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="317b8-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="317b8-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="317b8-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="317b8-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="317b8-113">The call timed out.</span></span>|  
|<span data-ttu-id="317b8-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="317b8-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="317b8-115">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="317b8-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="317b8-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="317b8-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="317b8-117">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="317b8-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="317b8-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="317b8-118">E_FAIL</span></span>|<span data-ttu-id="317b8-119">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="317b8-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="317b8-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="317b8-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="317b8-121">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="317b8-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="317b8-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="317b8-122">Remarks</span></span>  
 <span data-ttu-id="317b8-123">CLR genellikle çağrıları `ThreadIsBlockForSuspension` hazırlık ana iş parçacığı yönetilmeyen görevleri yeniden zamanlamak için bir fırsat vermek için bir çöp toplama için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="317b8-123">The CLR typically calls the `ThreadIsBlockForSuspension` method in preparation for a garbage collection, to give the host an opportunity to reschedule the thread for unmanaged tasks.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="317b8-124">Konak yalnızca çağrısı yapıldıktan sonra görevleri zamanlayabilirsiniz `ThreadIsBlockingForSuspension`.</span><span class="sxs-lookup"><span data-stu-id="317b8-124">The host can reschedule tasks only after a call to `ThreadIsBlockingForSuspension`.</span></span> <span data-ttu-id="317b8-125">Çalışma zamanı çağırdıktan sonra [SuspensionStarting](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md), ana görevin zamanlanmalı değil.</span><span class="sxs-lookup"><span data-stu-id="317b8-125">After the runtime calls [SuspensionStarting](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md), the host must not reschedule a task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="317b8-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="317b8-126">Requirements</span></span>  
 <span data-ttu-id="317b8-127">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="317b8-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="317b8-128">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="317b8-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="317b8-129">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="317b8-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="317b8-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="317b8-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="317b8-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="317b8-131">See also</span></span>

- [<span data-ttu-id="317b8-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="317b8-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="317b8-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="317b8-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="317b8-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="317b8-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="317b8-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="317b8-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="317b8-136">IHostGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="317b8-136">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
