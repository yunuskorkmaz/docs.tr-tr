---
title: IHostTaskManager::ReverseEnterRuntime Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTaskManager.ReverseEnterRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::ReverseEnterRuntime
helpviewer_keywords:
- IHostTaskManager::ReverseEnterRuntime method [.NET Framework hosting]
- ReverseEnterRuntime method [.NET Framework hosting]
ms.assetid: b1e26bff-d3ea-436e-9867-29720df999f4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b30919f6d89f151a93fc46407165279187ef6e4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749478"
---
# <a name="ihosttaskmanagerreverseenterruntime-method"></a><span data-ttu-id="d8a77-102">IHostTaskManager::ReverseEnterRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d8a77-102">IHostTaskManager::ReverseEnterRuntime Method</span></span>
<span data-ttu-id="d8a77-103">Konak, bir çağrı, yönetilmeyen koddan ortak dil çalışma zamanı (CLR) içine yapıldığı bildirir.</span><span class="sxs-lookup"><span data-stu-id="d8a77-103">Notifies the host that a call is being made into the common language runtime (CLR) from unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8a77-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8a77-104">Syntax</span></span>  
  
```cpp  
HRESULT ReverseEnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="d8a77-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d8a77-105">Return Value</span></span>  
  
|<span data-ttu-id="d8a77-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d8a77-106">HRESULT</span></span>|<span data-ttu-id="d8a77-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d8a77-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d8a77-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="d8a77-108">S_OK</span></span>|<span data-ttu-id="d8a77-109">`ReverseEnterRuntime` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="d8a77-109">`ReverseEnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="d8a77-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d8a77-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d8a77-111">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="d8a77-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d8a77-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d8a77-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d8a77-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="d8a77-113">The call timed out.</span></span>|  
|<span data-ttu-id="d8a77-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d8a77-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d8a77-115">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="d8a77-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d8a77-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d8a77-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d8a77-117">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="d8a77-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d8a77-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d8a77-118">E_FAIL</span></span>|<span data-ttu-id="d8a77-119">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="d8a77-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d8a77-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d8a77-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d8a77-121">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="d8a77-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d8a77-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="d8a77-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="d8a77-123">İstenen kaynak ayırma tamamlamak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="d8a77-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8a77-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8a77-124">Remarks</span></span>  
 <span data-ttu-id="d8a77-125">Yönetilen kodda kaynaklanan bir dizisinden CLR çağrı yapılırsa, her çağrısı `ReverseEnterRuntime` çağrısı karşılık gelen [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="d8a77-125">If the call into the CLR is made from a sequence that originated in managed code, each call to `ReverseEnterRuntime` corresponds to a call to [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d8a77-126">Çağrıları, iç içe olmadan, yönetilmeyen koddan gönderilebilir.</span><span class="sxs-lookup"><span data-stu-id="d8a77-126">Calls can originate from unmanaged code without being nested.</span></span> <span data-ttu-id="d8a77-127">Bu durumda, hiçbir yok [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), veya `ReverseLeaveRuntime`ve çağrı sayısı `ReverseEnterRuntime` çağrıları sayısına eşit değil `ReverseLeaveRuntime`.</span><span class="sxs-lookup"><span data-stu-id="d8a77-127">In this case, there is no call to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), or `ReverseLeaveRuntime`, and the number of calls to `ReverseEnterRuntime` does not equal the number of calls to `ReverseLeaveRuntime`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8a77-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d8a77-128">Requirements</span></span>  
 <span data-ttu-id="d8a77-129">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8a77-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8a77-130">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d8a77-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d8a77-131">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d8a77-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d8a77-132">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8a77-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8a77-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8a77-133">See also</span></span>

- [<span data-ttu-id="d8a77-134">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8a77-134">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="d8a77-135">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8a77-135">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="d8a77-136">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8a77-136">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="d8a77-137">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8a77-137">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
