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
ms.openlocfilehash: fb78026f875c18a557951108518c9280f5eb567d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937674"
---
# <a name="ihostgcmanagerthreadisblockingforsuspension-method"></a><span data-ttu-id="00cf6-102">IHostGCManager::ThreadIsBlockingForSuspension Yöntemi</span><span class="sxs-lookup"><span data-stu-id="00cf6-102">IHostGCManager::ThreadIsBlockingForSuspension Method</span></span>
<span data-ttu-id="00cf6-103">Ana bilgisayara, yöntem çağrısının yaptığı iş parçacığının çöp toplama için engellemek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="00cf6-103">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00cf6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="00cf6-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForSuspension ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="00cf6-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="00cf6-105">Return Value</span></span>  
  
|<span data-ttu-id="00cf6-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="00cf6-106">HRESULT</span></span>|<span data-ttu-id="00cf6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="00cf6-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="00cf6-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="00cf6-108">S_OK</span></span>|<span data-ttu-id="00cf6-109">`ThreadIsBlockingForSuspension`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="00cf6-109">`ThreadIsBlockingForSuspension` returned successfully.</span></span>|  
|<span data-ttu-id="00cf6-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="00cf6-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="00cf6-111">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="00cf6-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="00cf6-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="00cf6-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="00cf6-113">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="00cf6-113">The call timed out.</span></span>|  
|<span data-ttu-id="00cf6-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="00cf6-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="00cf6-115">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="00cf6-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="00cf6-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="00cf6-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="00cf6-117">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="00cf6-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="00cf6-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="00cf6-118">E_FAIL</span></span>|<span data-ttu-id="00cf6-119">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="00cf6-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="00cf6-120">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="00cf6-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="00cf6-121">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="00cf6-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00cf6-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="00cf6-122">Remarks</span></span>  
 <span data-ttu-id="00cf6-123">CLR, ana bilgisayara yönetilmeyen `ThreadIsBlockForSuspension` görevler için iş parçacığını yeniden zamanlama fırsatı vermek üzere bir çöp toplama hazırlığı için genellikle yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="00cf6-123">The CLR typically calls the `ThreadIsBlockForSuspension` method in preparation for a garbage collection, to give the host an opportunity to reschedule the thread for unmanaged tasks.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="00cf6-124">Konak, yalnızca öğesine `ThreadIsBlockingForSuspension`yapılan çağrıdan sonra görevleri yeniden zamanlayabilir.</span><span class="sxs-lookup"><span data-stu-id="00cf6-124">The host can reschedule tasks only after a call to `ThreadIsBlockingForSuspension`.</span></span> <span data-ttu-id="00cf6-125">Çalışma zamanı [SuspensionStarting](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md)öğesini çağırdıktan sonra konağın bir görevi yeniden zamanlamalı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="00cf6-125">After the runtime calls [SuspensionStarting](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md), the host must not reschedule a task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00cf6-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="00cf6-126">Requirements</span></span>  
 <span data-ttu-id="00cf6-127">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00cf6-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00cf6-128">**Üst bilgi** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="00cf6-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="00cf6-129">**Kitaplığı** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="00cf6-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="00cf6-130">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00cf6-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00cf6-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00cf6-131">See also</span></span>

- [<span data-ttu-id="00cf6-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00cf6-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="00cf6-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00cf6-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="00cf6-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00cf6-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="00cf6-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00cf6-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="00cf6-136">IHostGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00cf6-136">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
