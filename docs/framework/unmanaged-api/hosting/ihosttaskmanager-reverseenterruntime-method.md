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
ms.workload: dotnet
ms.openlocfilehash: 69743f6b7229f89d19d4134a11bb5f37fe5ca928
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskmanagerreverseenterruntime-method"></a><span data-ttu-id="aa707-102">IHostTaskManager::ReverseEnterRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aa707-102">IHostTaskManager::ReverseEnterRuntime Method</span></span>
<span data-ttu-id="aa707-103">Konak bir çağrı yönetilmeyen koddan ortak dil çalışma zamanı (CLR) içine yapılıyor bildirir.</span><span class="sxs-lookup"><span data-stu-id="aa707-103">Notifies the host that a call is being made into the common language runtime (CLR) from unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa707-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aa707-104">Syntax</span></span>  
  
```  
HRESULT ReverseEnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="aa707-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="aa707-105">Return Value</span></span>  
  
|<span data-ttu-id="aa707-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aa707-106">HRESULT</span></span>|<span data-ttu-id="aa707-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aa707-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aa707-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="aa707-108">S_OK</span></span>|<span data-ttu-id="aa707-109">`ReverseEnterRuntime`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="aa707-109">`ReverseEnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="aa707-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="aa707-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="aa707-111">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="aa707-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="aa707-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="aa707-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="aa707-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="aa707-113">The call timed out.</span></span>|  
|<span data-ttu-id="aa707-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="aa707-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="aa707-115">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="aa707-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="aa707-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="aa707-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="aa707-117">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="aa707-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="aa707-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="aa707-118">E_FAIL</span></span>|<span data-ttu-id="aa707-119">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="aa707-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="aa707-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="aa707-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="aa707-121">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="aa707-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="aa707-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="aa707-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="aa707-123">İstenen kaynak ayırma tamamlamak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="aa707-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa707-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aa707-124">Remarks</span></span>  
 <span data-ttu-id="aa707-125">CLR çağrısından kaynaklanan bir dizisinden yönetilen kodda yaptıysanız, her çağrısı `ReverseEnterRuntime` yapılan bir çağrı karşılık gelen [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="aa707-125">If the call into the CLR is made from a sequence that originated in managed code, each call to `ReverseEnterRuntime` corresponds to a call to [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aa707-126">Çağrılar, iç içe olmadan yönetilmeyen koddan kaynaklanan.</span><span class="sxs-lookup"><span data-stu-id="aa707-126">Calls can originate from unmanaged code without being nested.</span></span> <span data-ttu-id="aa707-127">Bu durumda, hiçbir çağrısı yok [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), veya `ReverseLeaveRuntime`ve çağrı sayısı `ReverseEnterRuntime` çağrı sayısı eşit değil `ReverseLeaveRuntime`.</span><span class="sxs-lookup"><span data-stu-id="aa707-127">In this case, there is no call to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), or `ReverseLeaveRuntime`, and the number of calls to `ReverseEnterRuntime` does not equal the number of calls to `ReverseLeaveRuntime`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa707-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aa707-128">Requirements</span></span>  
 <span data-ttu-id="aa707-129">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa707-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa707-130">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="aa707-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aa707-131">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="aa707-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aa707-132">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa707-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa707-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aa707-133">See Also</span></span>  
 [<span data-ttu-id="aa707-134">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aa707-134">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="aa707-135">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aa707-135">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="aa707-136">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aa707-136">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="aa707-137">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aa707-137">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
