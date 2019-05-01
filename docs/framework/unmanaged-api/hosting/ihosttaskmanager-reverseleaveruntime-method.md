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
ms.openlocfilehash: 4cd3012d966c777749eb800b8986974a4e8d401f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796649"
---
# <a name="ihosttaskmanagerreverseleaveruntime-method"></a><span data-ttu-id="1f037-102">IHostTaskManager::ReverseLeaveRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1f037-102">IHostTaskManager::ReverseLeaveRuntime Method</span></span>
<span data-ttu-id="1f037-103">Konak denetimi ortak dil çalışma zamanı (CLR) bırakarak ve buna karşılık, yönetilen koddan çağrılan yönetilmeyen bir işlev girerek bildirir.</span><span class="sxs-lookup"><span data-stu-id="1f037-103">Notifies the host that control is leaving the common language runtime (CLR) and entering an unmanaged function that was, in turn, called from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f037-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1f037-104">Syntax</span></span>  
  
```  
HRESULT ReverseLeaveRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="1f037-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1f037-105">Return Value</span></span>  
  
|<span data-ttu-id="1f037-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1f037-106">HRESULT</span></span>|<span data-ttu-id="1f037-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f037-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1f037-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="1f037-108">S_OK</span></span>|<span data-ttu-id="1f037-109">`ReverseLeaveRuntime` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="1f037-109">`ReverseLeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="1f037-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1f037-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1f037-111">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="1f037-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1f037-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1f037-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1f037-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="1f037-113">The call timed out.</span></span>|  
|<span data-ttu-id="1f037-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1f037-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1f037-115">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="1f037-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1f037-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1f037-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1f037-117">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="1f037-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1f037-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1f037-118">E_FAIL</span></span>|<span data-ttu-id="1f037-119">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="1f037-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1f037-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1f037-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1f037-121">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="1f037-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1f037-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="1f037-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="1f037-123">İstenen kaynak ayırma tamamlamak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="1f037-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f037-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1f037-124">Remarks</span></span>  
 <span data-ttu-id="1f037-125">CLR çağrıları `ReverseLeaveRuntime` şu anda yürütülen görev döndüren konak bildirmek için sırasıyla platformu aracılığıyla yönetilen koddan çağrılan yönetilmeyen bir işleve denetim çağırma.</span><span class="sxs-lookup"><span data-stu-id="1f037-125">The CLR calls `ReverseLeaveRuntime` to inform the host that the currently executing task is returning control to an unmanaged function that was, in turn, called from managed code through platform invoke.</span></span> <span data-ttu-id="1f037-126">Her çağrı `ReverseLeaveRuntime` yapılan çağrı ile eşleşen [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="1f037-126">Each call to `ReverseLeaveRuntime` matches a corresponding call to [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f037-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1f037-127">Requirements</span></span>  
 <span data-ttu-id="1f037-128">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f037-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f037-129">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1f037-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1f037-130">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="1f037-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1f037-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f037-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f037-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f037-132">See also</span></span>

- [<span data-ttu-id="1f037-133">CallNeedsHostHook Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1f037-133">CallNeedsHostHook Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-callneedshosthook-method.md)
- [<span data-ttu-id="1f037-134">EnterRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1f037-134">EnterRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)
- [<span data-ttu-id="1f037-135">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1f037-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="1f037-136">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1f037-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="1f037-137">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1f037-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="1f037-138">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1f037-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="1f037-139">LeaveRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1f037-139">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)
- <span data-ttu-id="1f037-140">[Yakından Platform çağırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0h9e9t7d(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1f037-140">[A Closer Look at Platform Invoke](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0h9e9t7d(v=vs.100))</span></span>
