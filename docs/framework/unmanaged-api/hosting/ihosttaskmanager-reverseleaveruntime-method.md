---
title: IHostTaskManager::ReverseLeaveRuntime Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTaskManager.ReverseLeaveRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::ReverseLeaveRuntime
helpviewer_keywords:
- IHostTaskManager::ReverseLeaveRuntime method [.NET Framework hosting]
- ReverseLeaveRuntime method [.NET Framework hosting]
ms.assetid: 4837d398-16a1-4e32-902c-022cd1aad3ca
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a9f5b6ad4765edfdea9f56debad085d69e9fc769
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54680445"
---
# <a name="ihosttaskmanagerreverseleaveruntime-method"></a><span data-ttu-id="08c74-102">IHostTaskManager::ReverseLeaveRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08c74-102">IHostTaskManager::ReverseLeaveRuntime Method</span></span>
<span data-ttu-id="08c74-103">Konak denetimi ortak dil çalışma zamanı (CLR) bırakarak ve buna karşılık, yönetilen koddan çağrılan yönetilmeyen bir işlev girerek bildirir.</span><span class="sxs-lookup"><span data-stu-id="08c74-103">Notifies the host that control is leaving the common language runtime (CLR) and entering an unmanaged function that was, in turn, called from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08c74-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="08c74-104">Syntax</span></span>  
  
```  
HRESULT ReverseLeaveRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="08c74-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="08c74-105">Return Value</span></span>  
  
|<span data-ttu-id="08c74-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="08c74-106">HRESULT</span></span>|<span data-ttu-id="08c74-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="08c74-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="08c74-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="08c74-108">S_OK</span></span>|<span data-ttu-id="08c74-109">`ReverseLeaveRuntime` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="08c74-109">`ReverseLeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="08c74-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="08c74-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="08c74-111">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="08c74-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="08c74-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="08c74-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="08c74-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="08c74-113">The call timed out.</span></span>|  
|<span data-ttu-id="08c74-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="08c74-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="08c74-115">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="08c74-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="08c74-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="08c74-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="08c74-117">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="08c74-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="08c74-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="08c74-118">E_FAIL</span></span>|<span data-ttu-id="08c74-119">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="08c74-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="08c74-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="08c74-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="08c74-121">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="08c74-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="08c74-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="08c74-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="08c74-123">İstenen kaynak ayırma tamamlamak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="08c74-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08c74-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="08c74-124">Remarks</span></span>  
 <span data-ttu-id="08c74-125">CLR çağrıları `ReverseLeaveRuntime` şu anda yürütülen görev döndüren konak bildirmek için sırasıyla platformu aracılığıyla yönetilen koddan çağrılan yönetilmeyen bir işleve denetim çağırma.</span><span class="sxs-lookup"><span data-stu-id="08c74-125">The CLR calls `ReverseLeaveRuntime` to inform the host that the currently executing task is returning control to an unmanaged function that was, in turn, called from managed code through platform invoke.</span></span> <span data-ttu-id="08c74-126">Her çağrı `ReverseLeaveRuntime` yapılan çağrı ile eşleşen [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="08c74-126">Each call to `ReverseLeaveRuntime` matches a corresponding call to [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08c74-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="08c74-127">Requirements</span></span>  
 <span data-ttu-id="08c74-128">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08c74-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08c74-129">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="08c74-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="08c74-130">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="08c74-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="08c74-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08c74-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08c74-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08c74-132">See also</span></span>
- [<span data-ttu-id="08c74-133">CallNeedsHostHook Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08c74-133">CallNeedsHostHook Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-callneedshosthook-method.md)
- [<span data-ttu-id="08c74-134">EnterRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08c74-134">EnterRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)
- [<span data-ttu-id="08c74-135">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="08c74-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="08c74-136">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="08c74-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="08c74-137">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="08c74-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="08c74-138">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="08c74-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="08c74-139">LeaveRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08c74-139">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)
- [<span data-ttu-id="08c74-140">Yakından Platform çağırma</span><span class="sxs-lookup"><span data-stu-id="08c74-140">A Closer Look at Platform Invoke</span></span>](https://msdn.microsoft.com/library/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)
