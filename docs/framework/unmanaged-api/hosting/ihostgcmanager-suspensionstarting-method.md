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
ms.openlocfilehash: 6a84da2a337554873e94b47eb51916088edbb5a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439039"
---
# <a name="ihostgcmanagersuspensionstarting-method"></a><span data-ttu-id="56b81-102">IHostGCManager::SuspensionStarting Yöntemi</span><span class="sxs-lookup"><span data-stu-id="56b81-102">IHostGCManager::SuspensionStarting Method</span></span>
<span data-ttu-id="56b81-103">Ortak dil çalışma zamanı (CLR) yürütme görevlerin çöp toplama gerçekleştirmek için askıya alma konak bildirir.</span><span class="sxs-lookup"><span data-stu-id="56b81-103">Notifies the host that the common language runtime (CLR) is suspending execution of tasks, to perform a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56b81-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="56b81-104">Syntax</span></span>  
  
```  
HRESULT SuspensionStarting ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="56b81-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="56b81-105">Return Value</span></span>  
  
|<span data-ttu-id="56b81-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="56b81-106">HRESULT</span></span>|<span data-ttu-id="56b81-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="56b81-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="56b81-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="56b81-108">S_OK</span></span>|<span data-ttu-id="56b81-109">`SuspensionStarting` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="56b81-109">`SuspensionStarting` returned successfully.</span></span>|  
|<span data-ttu-id="56b81-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="56b81-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="56b81-111">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="56b81-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="56b81-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="56b81-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="56b81-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="56b81-113">The call timed out.</span></span>|  
|<span data-ttu-id="56b81-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="56b81-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="56b81-115">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="56b81-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="56b81-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="56b81-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="56b81-117">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="56b81-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="56b81-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="56b81-118">E_FAIL</span></span>|<span data-ttu-id="56b81-119">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="56b81-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="56b81-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="56b81-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="56b81-121">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="56b81-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56b81-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="56b81-122">Remarks</span></span>  
 <span data-ttu-id="56b81-123">CLR çağrıları `SuspensionStarting` çöp toplama oluştuğunu konak bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56b81-123">The CLR calls `SuspensionStarting` to inform the host that garbage collection is occurring.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="56b81-124">Bu görevi yeniden zamanlayın değil.</span><span class="sxs-lookup"><span data-stu-id="56b81-124">Do not reschedule this task.</span></span> <span data-ttu-id="56b81-125">Konak bir görev zamanlanmalı zaman [Threadısblockingforsuspension](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md) olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="56b81-125">The host must reschedule a task when [ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md) is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56b81-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="56b81-126">Requirements</span></span>  
 <span data-ttu-id="56b81-127">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56b81-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56b81-128">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="56b81-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="56b81-129">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="56b81-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="56b81-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56b81-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56b81-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="56b81-131">See Also</span></span>  
 [<span data-ttu-id="56b81-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="56b81-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="56b81-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="56b81-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="56b81-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="56b81-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="56b81-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="56b81-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="56b81-136">IHostGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="56b81-136">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
