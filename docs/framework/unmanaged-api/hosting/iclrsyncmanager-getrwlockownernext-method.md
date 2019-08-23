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
ms.openlocfilehash: dbc38d9cf88f2449bbf689e4cf1b4101f47a0577
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943255"
---
# <a name="iclrsyncmanagergetrwlockownernext-method"></a><span data-ttu-id="383ea-102">ICLRSyncManager::GetRWLockOwnerNext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="383ea-102">ICLRSyncManager::GetRWLockOwnerNext Method</span></span>
<span data-ttu-id="383ea-103">Geçerli okuyucu-yazıcı kilidinde engellenen bir sonraki [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="383ea-103">Gets the next [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that is blocked on the current reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="383ea-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="383ea-104">Syntax</span></span>  
  
```  
HRESULT GetRWLockOwnerNext (  
    [in] SIZE_T       Iterator,  
    [out] IHostTask  *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="383ea-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="383ea-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="383ea-106">'ndaki [CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md)çağrısı kullanılarak oluşturulan Yineleyici.</span><span class="sxs-lookup"><span data-stu-id="383ea-106">[in] The iterator that was created by using a call to [CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="383ea-107">dışı Bir sonraki `IHostTask` , kilidi bekleyen bir işaretçi veya bekleyen bir görev yoksa null.</span><span class="sxs-lookup"><span data-stu-id="383ea-107">[out] A pointer to the next `IHostTask` that is waiting on the lock, or null if no task is waiting.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="383ea-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="383ea-108">Return Value</span></span>  
  
|<span data-ttu-id="383ea-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="383ea-109">HRESULT</span></span>|<span data-ttu-id="383ea-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="383ea-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="383ea-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="383ea-111">S_OK</span></span>|<span data-ttu-id="383ea-112">`GetRWLockOwnerNext`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="383ea-112">`GetRWLockOwnerNext` returned successfully.</span></span>|  
|<span data-ttu-id="383ea-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="383ea-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="383ea-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="383ea-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="383ea-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="383ea-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="383ea-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="383ea-116">The call timed out.</span></span>|  
|<span data-ttu-id="383ea-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="383ea-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="383ea-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="383ea-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="383ea-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="383ea-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="383ea-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="383ea-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="383ea-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="383ea-121">E_FAIL</span></span>|<span data-ttu-id="383ea-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="383ea-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="383ea-123">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="383ea-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="383ea-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="383ea-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="383ea-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="383ea-125">Remarks</span></span>  
 <span data-ttu-id="383ea-126">Null olarak ayarlanırsa, yineleme sonlandırılır ve konak [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) yöntemini çağırmalıdır. `ppOwnerHostTask`</span><span class="sxs-lookup"><span data-stu-id="383ea-126">If `ppOwnerHostTask` is set to null, the iteration has terminated, and the host should call the [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="383ea-127">Konakta, `AddRef` `IHostTask` konak işaretçiyitutarkenbugörevinçıkışyapmasınıengellemekiçingerekenclrçağrıları.`ppOwnerHostTask`</span><span class="sxs-lookup"><span data-stu-id="383ea-127">The CLR calls `AddRef` on the `IHostTask` to which `ppOwnerHostTask` points to prevent this task from exiting while the host holds the pointer.</span></span> <span data-ttu-id="383ea-128">Ana bilgisayar, tamamlandığında `Release` başvuru sayısını azaltmak için çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="383ea-128">The host must call `Release` to decrement the reference count when it is finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="383ea-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="383ea-129">Requirements</span></span>  
 <span data-ttu-id="383ea-130">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="383ea-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="383ea-131">**Üst bilgi** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="383ea-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="383ea-132">**Kitaplığı** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="383ea-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="383ea-133">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="383ea-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="383ea-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="383ea-134">See also</span></span>

- [<span data-ttu-id="383ea-135">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="383ea-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="383ea-136">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="383ea-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
