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
ms.openlocfilehash: c0c59d9f5abb200b17d3c46915e73fd3b9e9c8fd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780572"
---
# <a name="ihostgcmanagerthreadisblockingforsuspension-method"></a><span data-ttu-id="58a90-102">IHostGCManager::ThreadIsBlockingForSuspension Yöntemi</span><span class="sxs-lookup"><span data-stu-id="58a90-102">IHostGCManager::ThreadIsBlockingForSuspension Method</span></span>
<span data-ttu-id="58a90-103">İş parçacığı içinden yöntem çağrısı yapıldı, konağa bildirir yönelik bir çöp toplamanın engellemek üzere.</span><span class="sxs-lookup"><span data-stu-id="58a90-103">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58a90-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="58a90-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForSuspension ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="58a90-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="58a90-105">Return Value</span></span>  
  
|<span data-ttu-id="58a90-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="58a90-106">HRESULT</span></span>|<span data-ttu-id="58a90-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="58a90-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="58a90-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="58a90-108">S_OK</span></span>|<span data-ttu-id="58a90-109">`ThreadIsBlockingForSuspension` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="58a90-109">`ThreadIsBlockingForSuspension` returned successfully.</span></span>|  
|<span data-ttu-id="58a90-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="58a90-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="58a90-111">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="58a90-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="58a90-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="58a90-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="58a90-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="58a90-113">The call timed out.</span></span>|  
|<span data-ttu-id="58a90-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="58a90-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="58a90-115">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="58a90-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="58a90-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="58a90-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="58a90-117">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="58a90-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="58a90-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="58a90-118">E_FAIL</span></span>|<span data-ttu-id="58a90-119">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="58a90-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="58a90-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="58a90-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="58a90-121">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="58a90-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58a90-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="58a90-122">Remarks</span></span>  
 <span data-ttu-id="58a90-123">CLR genellikle çağrıları `ThreadIsBlockForSuspension` hazırlık ana iş parçacığı yönetilmeyen görevleri yeniden zamanlamak için bir fırsat vermek için bir çöp toplama için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="58a90-123">The CLR typically calls the `ThreadIsBlockForSuspension` method in preparation for a garbage collection, to give the host an opportunity to reschedule the thread for unmanaged tasks.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="58a90-124">Konak yalnızca çağrısı yapıldıktan sonra görevleri zamanlayabilirsiniz `ThreadIsBlockingForSuspension`.</span><span class="sxs-lookup"><span data-stu-id="58a90-124">The host can reschedule tasks only after a call to `ThreadIsBlockingForSuspension`.</span></span> <span data-ttu-id="58a90-125">Çalışma zamanı çağırdıktan sonra [SuspensionStarting](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md), ana görevin zamanlanmalı değil.</span><span class="sxs-lookup"><span data-stu-id="58a90-125">After the runtime calls [SuspensionStarting](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md), the host must not reschedule a task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58a90-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="58a90-126">Requirements</span></span>  
 <span data-ttu-id="58a90-127">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58a90-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58a90-128">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="58a90-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="58a90-129">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="58a90-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="58a90-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58a90-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58a90-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58a90-131">See also</span></span>

- [<span data-ttu-id="58a90-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="58a90-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="58a90-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="58a90-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="58a90-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="58a90-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="58a90-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="58a90-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="58a90-136">IHostGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="58a90-136">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
