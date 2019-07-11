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
ms.openlocfilehash: 920aecab03e386a48f59843b26610cf260419293
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749448"
---
# <a name="ihosttaskmanagerreverseleaveruntime-method"></a><span data-ttu-id="92d1f-102">IHostTaskManager::ReverseLeaveRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="92d1f-102">IHostTaskManager::ReverseLeaveRuntime Method</span></span>
<span data-ttu-id="92d1f-103">Konak denetimi ortak dil çalışma zamanı (CLR) bırakarak ve buna karşılık, yönetilen koddan çağrılan yönetilmeyen bir işlev girerek bildirir.</span><span class="sxs-lookup"><span data-stu-id="92d1f-103">Notifies the host that control is leaving the common language runtime (CLR) and entering an unmanaged function that was, in turn, called from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92d1f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="92d1f-104">Syntax</span></span>  
  
```cpp  
HRESULT ReverseLeaveRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="92d1f-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="92d1f-105">Return Value</span></span>  
  
|<span data-ttu-id="92d1f-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="92d1f-106">HRESULT</span></span>|<span data-ttu-id="92d1f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92d1f-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="92d1f-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="92d1f-108">S_OK</span></span>|<span data-ttu-id="92d1f-109">`ReverseLeaveRuntime` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="92d1f-109">`ReverseLeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="92d1f-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="92d1f-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="92d1f-111">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="92d1f-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="92d1f-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="92d1f-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="92d1f-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="92d1f-113">The call timed out.</span></span>|  
|<span data-ttu-id="92d1f-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="92d1f-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="92d1f-115">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="92d1f-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="92d1f-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="92d1f-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="92d1f-117">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="92d1f-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="92d1f-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="92d1f-118">E_FAIL</span></span>|<span data-ttu-id="92d1f-119">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="92d1f-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="92d1f-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="92d1f-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="92d1f-121">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="92d1f-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="92d1f-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="92d1f-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="92d1f-123">İstenen kaynak ayırma tamamlamak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="92d1f-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92d1f-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="92d1f-124">Remarks</span></span>  
 <span data-ttu-id="92d1f-125">CLR çağrıları `ReverseLeaveRuntime` şu anda yürütülen görev döndüren konak bildirmek için sırasıyla platformu aracılığıyla yönetilen koddan çağrılan yönetilmeyen bir işleve denetim çağırma.</span><span class="sxs-lookup"><span data-stu-id="92d1f-125">The CLR calls `ReverseLeaveRuntime` to inform the host that the currently executing task is returning control to an unmanaged function that was, in turn, called from managed code through platform invoke.</span></span> <span data-ttu-id="92d1f-126">Her çağrı `ReverseLeaveRuntime` yapılan çağrı ile eşleşen [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="92d1f-126">Each call to `ReverseLeaveRuntime` matches a corresponding call to [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92d1f-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="92d1f-127">Requirements</span></span>  
 <span data-ttu-id="92d1f-128">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92d1f-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92d1f-129">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="92d1f-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="92d1f-130">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="92d1f-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="92d1f-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92d1f-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92d1f-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92d1f-132">See also</span></span>

- [<span data-ttu-id="92d1f-133">CallNeedsHostHook Yöntemi</span><span class="sxs-lookup"><span data-stu-id="92d1f-133">CallNeedsHostHook Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-callneedshosthook-method.md)
- [<span data-ttu-id="92d1f-134">EnterRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="92d1f-134">EnterRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)
- [<span data-ttu-id="92d1f-135">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="92d1f-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="92d1f-136">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="92d1f-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="92d1f-137">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="92d1f-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="92d1f-138">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="92d1f-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="92d1f-139">LeaveRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="92d1f-139">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)
- <span data-ttu-id="92d1f-140">[Yakından Platform çağırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0h9e9t7d(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="92d1f-140">[A Closer Look at Platform Invoke](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0h9e9t7d(v=vs.100))</span></span>
