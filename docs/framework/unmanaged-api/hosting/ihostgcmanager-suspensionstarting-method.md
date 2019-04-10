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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59213096"
---
# <a name="ihostgcmanagersuspensionstarting-method"></a><span data-ttu-id="b328b-102">IHostGCManager::SuspensionStarting Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b328b-102">IHostGCManager::SuspensionStarting Method</span></span>
<span data-ttu-id="b328b-103">Konak, ortak dil çalışma zamanı (CLR) yürütme görevlerin bir çöp toplama için askıya alma bildirir.</span><span class="sxs-lookup"><span data-stu-id="b328b-103">Notifies the host that the common language runtime (CLR) is suspending execution of tasks, to perform a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b328b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b328b-104">Syntax</span></span>  
  
```  
HRESULT SuspensionStarting ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="b328b-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b328b-105">Return Value</span></span>  
  
|<span data-ttu-id="b328b-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b328b-106">HRESULT</span></span>|<span data-ttu-id="b328b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b328b-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b328b-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="b328b-108">S_OK</span></span>|`SuspensionStarting` <span data-ttu-id="b328b-109">başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="b328b-109">returned successfully.</span></span>|  
|<span data-ttu-id="b328b-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b328b-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b328b-111">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="b328b-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b328b-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b328b-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b328b-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="b328b-113">The call timed out.</span></span>|  
|<span data-ttu-id="b328b-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b328b-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b328b-115">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="b328b-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b328b-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b328b-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b328b-117">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="b328b-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b328b-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b328b-118">E_FAIL</span></span>|<span data-ttu-id="b328b-119">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="b328b-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b328b-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b328b-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b328b-121">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="b328b-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b328b-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b328b-122">Remarks</span></span>  
 <span data-ttu-id="b328b-123">CLR çağrıları `SuspensionStarting` çöp toplama oluştuğu ana bilgisayara bildirmek için.</span><span class="sxs-lookup"><span data-stu-id="b328b-123">The CLR calls `SuspensionStarting` to inform the host that garbage collection is occurring.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b328b-124">Bu görevi yeniden değil.</span><span class="sxs-lookup"><span data-stu-id="b328b-124">Do not reschedule this task.</span></span> <span data-ttu-id="b328b-125">Konak, bir görev zamanlanmalı olduğunda [Threadısblockingforsuspension](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md) çağrılır.</span><span class="sxs-lookup"><span data-stu-id="b328b-125">The host must reschedule a task when [ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md) is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b328b-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b328b-126">Requirements</span></span>  
 <span data-ttu-id="b328b-127">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b328b-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b328b-128">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b328b-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b328b-129">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="b328b-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="b328b-130">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="b328b-130">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b328b-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b328b-131">See also</span></span>

- [<span data-ttu-id="b328b-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b328b-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="b328b-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b328b-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="b328b-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b328b-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="b328b-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b328b-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="b328b-136">IHostGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b328b-136">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
