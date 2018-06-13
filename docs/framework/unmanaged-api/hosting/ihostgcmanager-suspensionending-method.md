---
title: IHostGCManager::SuspensionEnding Yöntemi
ms.date: 03/30/2017
api_name:
- IHostGCManager.SuspensionEnding
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager::SuspensionEnding
helpviewer_keywords:
- SuspensionEnding method, IHostGCManager interface [.NET Framework hosting]
- IHostGCManager::SuspensionEnding method [.NET Framework hosting]
ms.assetid: 8849a1db-17f0-44b7-880a-bd36d431eb91
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f2835c9846657edffc745c435211f93b20f7173
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438840"
---
# <a name="ihostgcmanagersuspensionending-method"></a><span data-ttu-id="31f84-102">IHostGCManager::SuspensionEnding Yöntemi</span><span class="sxs-lookup"><span data-stu-id="31f84-102">IHostGCManager::SuspensionEnding Method</span></span>
<span data-ttu-id="31f84-103">Ortak dil çalışma zamanı (CLR) görevler için bir atık toplama askıya iş parçacığı üzerinde yürütülmesi sürdürüyor konak bildirir.</span><span class="sxs-lookup"><span data-stu-id="31f84-103">Notifies the host that the common language runtime (CLR) is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31f84-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="31f84-104">Syntax</span></span>  
  
```  
HRESULT SuspensionEnding (  
    [in] DWORD generation  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="31f84-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="31f84-105">Parameters</span></span>  
 `generation`  
 <span data-ttu-id="31f84-106">[in] Yalnızca bitiyor çöp koleksiyonu oluşturma, iş parçacığı sürdürüyor.</span><span class="sxs-lookup"><span data-stu-id="31f84-106">[in] The garbage collection generation that is just finishing, from which the thread is resuming.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="31f84-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="31f84-107">Return Value</span></span>  
  
|<span data-ttu-id="31f84-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="31f84-108">HRESULT</span></span>|<span data-ttu-id="31f84-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="31f84-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="31f84-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="31f84-110">S_OK</span></span>|<span data-ttu-id="31f84-111">`SuspensionEnding` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="31f84-111">`SuspensionEnding` returned successfully.</span></span>|  
|<span data-ttu-id="31f84-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="31f84-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="31f84-113">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="31f84-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="31f84-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="31f84-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="31f84-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="31f84-115">The call timed out.</span></span>|  
|<span data-ttu-id="31f84-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="31f84-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="31f84-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="31f84-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="31f84-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="31f84-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="31f84-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="31f84-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="31f84-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="31f84-120">E_FAIL</span></span>|<span data-ttu-id="31f84-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="31f84-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="31f84-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="31f84-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="31f84-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="31f84-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31f84-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="31f84-124">Remarks</span></span>  
 <span data-ttu-id="31f84-125">CLR çağrıları `SuspensionEnding` ana iş parçacığı yürütme sürdürüyor bildirmek için bir atık toplama gerçekleştirdikten sonra.</span><span class="sxs-lookup"><span data-stu-id="31f84-125">The CLR calls `SuspensionEnding` after it performs a garbage collection, to inform the host that the thread is resuming execution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="31f84-126">Yöntem çağrısının yapılan iş parçacığı yeniden zamanla değil.</span><span class="sxs-lookup"><span data-stu-id="31f84-126">Do not reschedule the thread the method call was made from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31f84-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="31f84-127">Requirements</span></span>  
 <span data-ttu-id="31f84-128">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31f84-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31f84-129">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="31f84-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="31f84-130">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="31f84-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="31f84-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31f84-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31f84-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="31f84-132">See Also</span></span>  
 [<span data-ttu-id="31f84-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31f84-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="31f84-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31f84-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="31f84-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31f84-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="31f84-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31f84-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="31f84-137">IHostGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31f84-137">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
