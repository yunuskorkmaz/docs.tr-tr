---
description: ': ICLRSyncManager:: GetRWLockOwnerNext yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: f49bdd5065ac896147967c0a013347ab39ce1eff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785010"
---
# <a name="iclrsyncmanagergetrwlockownernext-method"></a><span data-ttu-id="e41f5-103">ICLRSyncManager::GetRWLockOwnerNext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e41f5-103">ICLRSyncManager::GetRWLockOwnerNext Method</span></span>

<span data-ttu-id="e41f5-104">Geçerli okuyucu-yazıcı kilidinde engellenen bir sonraki [IHostTask](ihosttask-interface.md) örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="e41f5-104">Gets the next [IHostTask](ihosttask-interface.md) instance that is blocked on the current reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e41f5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e41f5-105">Syntax</span></span>  
  
```cpp
HRESULT GetRWLockOwnerNext (  
    [in] SIZE_T       Iterator,  
    [out] IHostTask  *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e41f5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e41f5-106">Parameters</span></span>  

 `Iterator`  
 <span data-ttu-id="e41f5-107">'ndaki [CreateRWLockOwnerIterator](iclrsyncmanager-createrwlockowneriterator-method.md)çağrısı kullanılarak oluşturulan Yineleyici.</span><span class="sxs-lookup"><span data-stu-id="e41f5-107">[in] The iterator that was created by using a call to [CreateRWLockOwnerIterator](iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="e41f5-108">dışı Bir sonraki, `IHostTask` kilidi bekleyen bir işaretçi veya bekleyen bir görev yoksa null.</span><span class="sxs-lookup"><span data-stu-id="e41f5-108">[out] A pointer to the next `IHostTask` that is waiting on the lock, or null if no task is waiting.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e41f5-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e41f5-109">Return Value</span></span>  
  
|<span data-ttu-id="e41f5-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e41f5-110">HRESULT</span></span>|<span data-ttu-id="e41f5-111">Description</span><span class="sxs-lookup"><span data-stu-id="e41f5-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e41f5-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="e41f5-112">S_OK</span></span>|<span data-ttu-id="e41f5-113">`GetRWLockOwnerNext` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e41f5-113">`GetRWLockOwnerNext` returned successfully.</span></span>|  
|<span data-ttu-id="e41f5-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e41f5-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e41f5-115">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="e41f5-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e41f5-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e41f5-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e41f5-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="e41f5-117">The call timed out.</span></span>|  
|<span data-ttu-id="e41f5-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e41f5-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e41f5-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="e41f5-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e41f5-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e41f5-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e41f5-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="e41f5-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e41f5-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e41f5-122">E_FAIL</span></span>|<span data-ttu-id="e41f5-123">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e41f5-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e41f5-124">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e41f5-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e41f5-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="e41f5-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e41f5-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e41f5-126">Remarks</span></span>  

 <span data-ttu-id="e41f5-127">`ppOwnerHostTask`Null olarak ayarlanırsa, yineleme sonlandırılır ve konak [DeleteRWLockOwnerIterator](iclrsyncmanager-deleterwlockowneriterator-method.md) yöntemini çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e41f5-127">If `ppOwnerHostTask` is set to null, the iteration has terminated, and the host should call the [DeleteRWLockOwnerIterator](iclrsyncmanager-deleterwlockowneriterator-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e41f5-128">`AddRef` `IHostTask` `ppOwnerHostTask` Konakta, konak işaretçiyi tutarken bu görevin çıkış yapmasını engellemek için gereken clr çağrıları.</span><span class="sxs-lookup"><span data-stu-id="e41f5-128">The CLR calls `AddRef` on the `IHostTask` to which `ppOwnerHostTask` points to prevent this task from exiting while the host holds the pointer.</span></span> <span data-ttu-id="e41f5-129">Ana bilgisayar, `Release` tamamlandığında başvuru sayısını azaltmak için çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e41f5-129">The host must call `Release` to decrement the reference count when it is finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e41f5-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e41f5-130">Requirements</span></span>  

 <span data-ttu-id="e41f5-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e41f5-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e41f5-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e41f5-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e41f5-133">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="e41f5-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e41f5-134">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e41f5-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e41f5-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e41f5-135">See also</span></span>

- [<span data-ttu-id="e41f5-136">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e41f5-136">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="e41f5-137">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e41f5-137">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
