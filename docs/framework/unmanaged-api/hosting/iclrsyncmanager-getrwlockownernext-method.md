---
title: ICLRSyncManager::GetRWLockOwnerNext Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.GetRWLockOwnerNext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::GetRWLockOwnerNext
helpviewer_keywords:
- ICLRSyncManager::GetRWLockOwnerNext method [.NET Framework hosting]
- GetRWLockOwnerNext method [.NET Framework hosting]
ms.assetid: 0e025b6a-280e-40a2-a2d0-b15f58777b81
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3efe80c0442e765274b309e39a79cc867676043
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59169656"
---
# <a name="iclrsyncmanagergetrwlockownernext-method"></a><span data-ttu-id="5e6ba-102">ICLRSyncManager::GetRWLockOwnerNext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5e6ba-102">ICLRSyncManager::GetRWLockOwnerNext Method</span></span>
<span data-ttu-id="5e6ba-103">Sonraki alır [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) geçerli Okuyucu-Yazıcı kilidi engellenir örneği.</span><span class="sxs-lookup"><span data-stu-id="5e6ba-103">Gets the next [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that is blocked on the current reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e6ba-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5e6ba-104">Syntax</span></span>  
  
```  
HRESULT GetRWLockOwnerNext (  
    [in] SIZE_T       Iterator,  
    [out] IHostTask  *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e6ba-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5e6ba-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="5e6ba-106">[in] Bir çağrı kullanılarak oluşturulmuş yineleyici [Createrwlockownerıterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span><span class="sxs-lookup"><span data-stu-id="5e6ba-106">[in] The iterator that was created by using a call to [CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="5e6ba-107">[out] Sonraki işaretçisi `IHostTask` , bekliyor kilitleme veya null görev bekliyorsa.</span><span class="sxs-lookup"><span data-stu-id="5e6ba-107">[out] A pointer to the next `IHostTask` that is waiting on the lock, or null if no task is waiting.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5e6ba-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5e6ba-108">Return Value</span></span>  
  
|<span data-ttu-id="5e6ba-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5e6ba-109">HRESULT</span></span>|<span data-ttu-id="5e6ba-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5e6ba-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5e6ba-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="5e6ba-111">S_OK</span></span>|`GetRWLockOwnerNext` <span data-ttu-id="5e6ba-112">başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="5e6ba-112">returned successfully.</span></span>|  
|<span data-ttu-id="5e6ba-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5e6ba-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5e6ba-114">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="5e6ba-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5e6ba-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5e6ba-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5e6ba-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="5e6ba-116">The call timed out.</span></span>|  
|<span data-ttu-id="5e6ba-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5e6ba-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5e6ba-118">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="5e6ba-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5e6ba-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5e6ba-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5e6ba-120">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="5e6ba-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5e6ba-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5e6ba-121">E_FAIL</span></span>|<span data-ttu-id="5e6ba-122">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="5e6ba-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5e6ba-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="5e6ba-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5e6ba-124">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="5e6ba-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e6ba-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5e6ba-125">Remarks</span></span>  
 <span data-ttu-id="5e6ba-126">Varsa `ppOwnerHostTask` ayarlamak yineleme null sonlandırıldı ve konak çağırmalıdır [Deleterwlockownerıterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5e6ba-126">If `ppOwnerHostTask` is set to null, the iteration has terminated, and the host should call the [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e6ba-127">CLR çağrıları `AddRef` üzerinde `IHostTask` hangi `ppOwnerHostTask` noktaları konak işaretçinin üzerindeyken bu görevi çıkmasını önlemek için.</span><span class="sxs-lookup"><span data-stu-id="5e6ba-127">The CLR calls `AddRef` on the `IHostTask` to which `ppOwnerHostTask` points to prevent this task from exiting while the host holds the pointer.</span></span> <span data-ttu-id="5e6ba-128">Konak çağırmalıdır `Release` sona erdiğinde başvuru sayısını azaltmak için.</span><span class="sxs-lookup"><span data-stu-id="5e6ba-128">The host must call `Release` to decrement the reference count when it is finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e6ba-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5e6ba-129">Requirements</span></span>  
 <span data-ttu-id="5e6ba-130">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e6ba-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e6ba-131">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5e6ba-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5e6ba-132">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="5e6ba-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="5e6ba-133">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="5e6ba-133">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5e6ba-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e6ba-134">See also</span></span>

- [<span data-ttu-id="5e6ba-135">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5e6ba-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="5e6ba-136">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5e6ba-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
