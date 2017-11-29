---
title: ICLRSyncManager::GetRWLockOwnerNext Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRSyncManager.GetRWLockOwnerNext
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRSyncManager::GetRWLockOwnerNext
helpviewer_keywords:
- ICLRSyncManager::GetRWLockOwnerNext method [.NET Framework hosting]
- GetRWLockOwnerNext method [.NET Framework hosting]
ms.assetid: 0e025b6a-280e-40a2-a2d0-b15f58777b81
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8551a6981efd1005f5433c8c862623766bf838f8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrsyncmanagergetrwlockownernext-method"></a><span data-ttu-id="c17f6-102">ICLRSyncManager::GetRWLockOwnerNext Metodu</span><span class="sxs-lookup"><span data-stu-id="c17f6-102">ICLRSyncManager::GetRWLockOwnerNext Method</span></span>
<span data-ttu-id="c17f6-103">Sonraki alır [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) geçerli Okuyucu-Yazıcı kilidi engellenen örneği.</span><span class="sxs-lookup"><span data-stu-id="c17f6-103">Gets the next [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that is blocked on the current reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c17f6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c17f6-104">Syntax</span></span>  
  
```  
HRESULT GetRWLockOwnerNext (  
    [in] SIZE_T       Iterator,  
    [out] IHostTask  *ppOwnerHostTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c17f6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c17f6-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="c17f6-106">[in] Bir çağrı kullanılarak oluşturulmuş yineleyici [Createrwlockownerıterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span><span class="sxs-lookup"><span data-stu-id="c17f6-106">[in] The iterator that was created by using a call to [CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="c17f6-107">[out] Sonraki gösteren bir işaretçi `IHostTask` , bekliyor kilitleme veya null hiçbir görev bekliyorsa.</span><span class="sxs-lookup"><span data-stu-id="c17f6-107">[out] A pointer to the next `IHostTask` that is waiting on the lock, or null if no task is waiting.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c17f6-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c17f6-108">Return Value</span></span>  
  
|<span data-ttu-id="c17f6-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c17f6-109">HRESULT</span></span>|<span data-ttu-id="c17f6-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c17f6-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c17f6-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c17f6-111">S_OK</span></span>|<span data-ttu-id="c17f6-112">`GetRWLockOwnerNext`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="c17f6-112">`GetRWLockOwnerNext` returned successfully.</span></span>|  
|<span data-ttu-id="c17f6-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c17f6-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c17f6-114">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="c17f6-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c17f6-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c17f6-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c17f6-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="c17f6-116">The call timed out.</span></span>|  
|<span data-ttu-id="c17f6-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c17f6-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c17f6-118">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="c17f6-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c17f6-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c17f6-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c17f6-120">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="c17f6-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c17f6-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c17f6-121">E_FAIL</span></span>|<span data-ttu-id="c17f6-122">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="c17f6-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c17f6-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c17f6-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c17f6-124">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="c17f6-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c17f6-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c17f6-125">Remarks</span></span>  
 <span data-ttu-id="c17f6-126">Varsa `ppOwnerHostTask` ayarlamak null, yineleme sona erdi ve ana bilgisayar çağırmalıdır [Deleterwlockownerıterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c17f6-126">If `ppOwnerHostTask` is set to null, the iteration has terminated, and the host should call the [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c17f6-127">CLR çağrıları `AddRef` üzerinde `IHostTask` hangi `ppOwnerHostTask` bu görevi konak işaretçinin tutan çıkmasını önlemek için noktaları.</span><span class="sxs-lookup"><span data-stu-id="c17f6-127">The CLR calls `AddRef` on the `IHostTask` to which `ppOwnerHostTask` points to prevent this task from exiting while the host holds the pointer.</span></span> <span data-ttu-id="c17f6-128">Ana bilgisayar çağırmalısınız `Release` bittiğinde başvuru sayısı düşürmek için.</span><span class="sxs-lookup"><span data-stu-id="c17f6-128">The host must call `Release` to decrement the reference count when it is finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c17f6-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c17f6-129">Requirements</span></span>  
 <span data-ttu-id="c17f6-130">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c17f6-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c17f6-131">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c17f6-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c17f6-132">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="c17f6-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c17f6-133">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c17f6-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c17f6-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c17f6-134">See Also</span></span>  
 [<span data-ttu-id="c17f6-135">Iclrsyncmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="c17f6-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="c17f6-136">Ihostsyncmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="c17f6-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
