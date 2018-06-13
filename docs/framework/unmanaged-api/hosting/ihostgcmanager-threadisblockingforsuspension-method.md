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
ms.openlocfilehash: 85921156860f52eb2a898e6be356e191c2a4f02d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439276"
---
# <a name="ihostgcmanagerthreadisblockingforsuspension-method"></a><span data-ttu-id="ed9e5-102">IHostGCManager::ThreadIsBlockingForSuspension Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ed9e5-102">IHostGCManager::ThreadIsBlockingForSuspension Method</span></span>
<span data-ttu-id="ed9e5-103">İçinden yöntem çağrısı yapıldı iş parçacığı konak bildirir atık toplama için engellemek üzere.</span><span class="sxs-lookup"><span data-stu-id="ed9e5-103">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed9e5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ed9e5-104">Syntax</span></span>  
  
```  
HRESULT ThreadIsBlockingForSuspension ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ed9e5-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ed9e5-105">Return Value</span></span>  
  
|<span data-ttu-id="ed9e5-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ed9e5-106">HRESULT</span></span>|<span data-ttu-id="ed9e5-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ed9e5-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ed9e5-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="ed9e5-108">S_OK</span></span>|<span data-ttu-id="ed9e5-109">`ThreadIsBlockingForSuspension` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="ed9e5-109">`ThreadIsBlockingForSuspension` returned successfully.</span></span>|  
|<span data-ttu-id="ed9e5-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ed9e5-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ed9e5-111">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="ed9e5-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ed9e5-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ed9e5-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ed9e5-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="ed9e5-113">The call timed out.</span></span>|  
|<span data-ttu-id="ed9e5-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ed9e5-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ed9e5-115">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="ed9e5-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ed9e5-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ed9e5-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ed9e5-117">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="ed9e5-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ed9e5-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ed9e5-118">E_FAIL</span></span>|<span data-ttu-id="ed9e5-119">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="ed9e5-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ed9e5-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ed9e5-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ed9e5-121">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="ed9e5-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ed9e5-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ed9e5-122">Remarks</span></span>  
 <span data-ttu-id="ed9e5-123">CLR genellikle çağırır `ThreadIsBlockForSuspension` konak yönetilmeyen görevler için iş parçacığı yeniden zamanlamak için bir fırsat vermek için bir atık toplama hazırlığı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ed9e5-123">The CLR typically calls the `ThreadIsBlockForSuspension` method in preparation for a garbage collection, to give the host an opportunity to reschedule the thread for unmanaged tasks.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ed9e5-124">Ana bilgisayar için bir çağrı sonra yalnızca görevleri zamanlayabilirsiniz `ThreadIsBlockingForSuspension`.</span><span class="sxs-lookup"><span data-stu-id="ed9e5-124">The host can reschedule tasks only after a call to `ThreadIsBlockingForSuspension`.</span></span> <span data-ttu-id="ed9e5-125">Çalışma zamanı çağrıları sonra [SuspensionStarting](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md), ana bilgisayar, bir görev zamanlanmalı değil.</span><span class="sxs-lookup"><span data-stu-id="ed9e5-125">After the runtime calls [SuspensionStarting](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md), the host must not reschedule a task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed9e5-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ed9e5-126">Requirements</span></span>  
 <span data-ttu-id="ed9e5-127">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed9e5-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed9e5-128">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ed9e5-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ed9e5-129">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="ed9e5-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ed9e5-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed9e5-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed9e5-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ed9e5-131">See Also</span></span>  
 [<span data-ttu-id="ed9e5-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ed9e5-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="ed9e5-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ed9e5-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="ed9e5-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ed9e5-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="ed9e5-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ed9e5-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="ed9e5-136">IHostGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ed9e5-136">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
