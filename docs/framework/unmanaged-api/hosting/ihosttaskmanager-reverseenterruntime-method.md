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
ms.openlocfilehash: 6eefdaf5dee423b0a9ae054446224a3ea97e3c9b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59213785"
---
# <a name="ihosttaskmanagerreverseenterruntime-method"></a><span data-ttu-id="7a1a6-102">IHostTaskManager::ReverseEnterRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7a1a6-102">IHostTaskManager::ReverseEnterRuntime Method</span></span>
<span data-ttu-id="7a1a6-103">Konak, bir çağrı, yönetilmeyen koddan ortak dil çalışma zamanı (CLR) içine yapıldığı bildirir.</span><span class="sxs-lookup"><span data-stu-id="7a1a6-103">Notifies the host that a call is being made into the common language runtime (CLR) from unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a1a6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7a1a6-104">Syntax</span></span>  
  
```  
HRESULT ReverseEnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="7a1a6-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7a1a6-105">Return Value</span></span>  
  
|<span data-ttu-id="7a1a6-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7a1a6-106">HRESULT</span></span>|<span data-ttu-id="7a1a6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7a1a6-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7a1a6-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="7a1a6-108">S_OK</span></span>|`ReverseEnterRuntime` <span data-ttu-id="7a1a6-109">başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="7a1a6-109">returned successfully.</span></span>|  
|<span data-ttu-id="7a1a6-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7a1a6-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7a1a6-111">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="7a1a6-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7a1a6-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7a1a6-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7a1a6-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="7a1a6-113">The call timed out.</span></span>|  
|<span data-ttu-id="7a1a6-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7a1a6-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7a1a6-115">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="7a1a6-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7a1a6-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7a1a6-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7a1a6-117">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="7a1a6-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7a1a6-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7a1a6-118">E_FAIL</span></span>|<span data-ttu-id="7a1a6-119">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="7a1a6-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7a1a6-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="7a1a6-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7a1a6-121">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="7a1a6-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7a1a6-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="7a1a6-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="7a1a6-123">İstenen kaynak ayırma tamamlamak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="7a1a6-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a1a6-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7a1a6-124">Remarks</span></span>  
 <span data-ttu-id="7a1a6-125">Yönetilen kodda kaynaklanan bir dizisinden CLR çağrı yapılırsa, her çağrısı `ReverseEnterRuntime` çağrısı karşılık gelen [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="7a1a6-125">If the call into the CLR is made from a sequence that originated in managed code, each call to `ReverseEnterRuntime` corresponds to a call to [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a1a6-126">Çağrıları, iç içe olmadan, yönetilmeyen koddan gönderilebilir.</span><span class="sxs-lookup"><span data-stu-id="7a1a6-126">Calls can originate from unmanaged code without being nested.</span></span> <span data-ttu-id="7a1a6-127">Bu durumda, hiçbir yok [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), veya `ReverseLeaveRuntime`ve çağrı sayısı `ReverseEnterRuntime` çağrıları sayısına eşit değil `ReverseLeaveRuntime`.</span><span class="sxs-lookup"><span data-stu-id="7a1a6-127">In this case, there is no call to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), or `ReverseLeaveRuntime`, and the number of calls to `ReverseEnterRuntime` does not equal the number of calls to `ReverseLeaveRuntime`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a1a6-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7a1a6-128">Requirements</span></span>  
 <span data-ttu-id="7a1a6-129">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a1a6-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a1a6-130">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7a1a6-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7a1a6-131">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="7a1a6-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="7a1a6-132">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="7a1a6-132">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7a1a6-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a1a6-133">See also</span></span>

- [<span data-ttu-id="7a1a6-134">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7a1a6-134">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="7a1a6-135">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7a1a6-135">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="7a1a6-136">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7a1a6-136">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="7a1a6-137">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7a1a6-137">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
