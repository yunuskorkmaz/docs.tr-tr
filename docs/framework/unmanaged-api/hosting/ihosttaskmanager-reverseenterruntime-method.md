---
title: "IHostTaskManager::ReverseEnterRuntime Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.ReverseEnterRuntime
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::ReverseEnterRuntime
helpviewer_keywords:
- IHostTaskManager::ReverseEnterRuntime method [.NET Framework hosting]
- ReverseEnterRuntime method [.NET Framework hosting]
ms.assetid: b1e26bff-d3ea-436e-9867-29720df999f4
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1c8d84cbd02527a026206d6fa172a9d3f40683fb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskmanagerreverseenterruntime-method"></a><span data-ttu-id="05c9a-102">IHostTaskManager::ReverseEnterRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="05c9a-102">IHostTaskManager::ReverseEnterRuntime Method</span></span>
<span data-ttu-id="05c9a-103">Konak bir çağrı yönetilmeyen koddan ortak dil çalışma zamanı (CLR) içine yapılıyor bildirir.</span><span class="sxs-lookup"><span data-stu-id="05c9a-103">Notifies the host that a call is being made into the common language runtime (CLR) from unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05c9a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="05c9a-104">Syntax</span></span>  
  
```  
HRESULT ReverseEnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="05c9a-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="05c9a-105">Return Value</span></span>  
  
|<span data-ttu-id="05c9a-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="05c9a-106">HRESULT</span></span>|<span data-ttu-id="05c9a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="05c9a-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="05c9a-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="05c9a-108">S_OK</span></span>|<span data-ttu-id="05c9a-109">`ReverseEnterRuntime`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="05c9a-109">`ReverseEnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="05c9a-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="05c9a-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="05c9a-111">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="05c9a-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="05c9a-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="05c9a-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="05c9a-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="05c9a-113">The call timed out.</span></span>|  
|<span data-ttu-id="05c9a-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="05c9a-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="05c9a-115">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="05c9a-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="05c9a-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="05c9a-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="05c9a-117">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="05c9a-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="05c9a-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="05c9a-118">E_FAIL</span></span>|<span data-ttu-id="05c9a-119">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="05c9a-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="05c9a-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="05c9a-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="05c9a-121">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="05c9a-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="05c9a-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="05c9a-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="05c9a-123">İstenen kaynak ayırma tamamlamak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="05c9a-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05c9a-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="05c9a-124">Remarks</span></span>  
 <span data-ttu-id="05c9a-125">CLR çağrısından kaynaklanan bir dizisinden yönetilen kodda yaptıysanız, her çağrısı `ReverseEnterRuntime` yapılan bir çağrı karşılık gelen [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="05c9a-125">If the call into the CLR is made from a sequence that originated in managed code, each call to `ReverseEnterRuntime` corresponds to a call to [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05c9a-126">Çağrılar, iç içe olmadan yönetilmeyen koddan kaynaklanan.</span><span class="sxs-lookup"><span data-stu-id="05c9a-126">Calls can originate from unmanaged code without being nested.</span></span> <span data-ttu-id="05c9a-127">Bu durumda, hiçbir çağrısı yok [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), veya `ReverseLeaveRuntime`ve çağrı sayısı `ReverseEnterRuntime` çağrı sayısı eşit değil `ReverseLeaveRuntime`.</span><span class="sxs-lookup"><span data-stu-id="05c9a-127">In this case, there is no call to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), or `ReverseLeaveRuntime`, and the number of calls to `ReverseEnterRuntime` does not equal the number of calls to `ReverseLeaveRuntime`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05c9a-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="05c9a-128">Requirements</span></span>  
 <span data-ttu-id="05c9a-129">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05c9a-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05c9a-130">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="05c9a-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="05c9a-131">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="05c9a-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="05c9a-132">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05c9a-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05c9a-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="05c9a-133">See Also</span></span>  
 [<span data-ttu-id="05c9a-134">Iclrtask arabirimi</span><span class="sxs-lookup"><span data-stu-id="05c9a-134">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="05c9a-135">Iclrtaskmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="05c9a-135">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="05c9a-136">Ihosttask arabirimi</span><span class="sxs-lookup"><span data-stu-id="05c9a-136">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="05c9a-137">Ihosttaskmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="05c9a-137">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
