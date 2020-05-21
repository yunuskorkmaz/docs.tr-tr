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
ms.openlocfilehash: e5a8f69e66bb4b6373aea2c753bff9351bff8128
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762493"
---
# <a name="iclrsyncmanagergetrwlockownernext-method"></a><span data-ttu-id="babaf-102">ICLRSyncManager::GetRWLockOwnerNext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="babaf-102">ICLRSyncManager::GetRWLockOwnerNext Method</span></span>
<span data-ttu-id="babaf-103">Geçerli okuyucu-yazıcı kilidinde engellenen bir sonraki [IHostTask](ihosttask-interface.md) örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="babaf-103">Gets the next [IHostTask](ihosttask-interface.md) instance that is blocked on the current reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="babaf-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="babaf-104">Syntax</span></span>  
  
```cpp
HRESULT GetRWLockOwnerNext (  
    [in] SIZE_T       Iterator,  
    [out] IHostTask  *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="babaf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="babaf-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="babaf-106">'ndaki [CreateRWLockOwnerIterator](iclrsyncmanager-createrwlockowneriterator-method.md)çağrısı kullanılarak oluşturulan Yineleyici.</span><span class="sxs-lookup"><span data-stu-id="babaf-106">[in] The iterator that was created by using a call to [CreateRWLockOwnerIterator](iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="babaf-107">dışı Bir sonraki, `IHostTask` kilidi bekleyen bir işaretçi veya bekleyen bir görev yoksa null.</span><span class="sxs-lookup"><span data-stu-id="babaf-107">[out] A pointer to the next `IHostTask` that is waiting on the lock, or null if no task is waiting.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="babaf-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="babaf-108">Return Value</span></span>  
  
|<span data-ttu-id="babaf-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="babaf-109">HRESULT</span></span>|<span data-ttu-id="babaf-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="babaf-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="babaf-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="babaf-111">S_OK</span></span>|<span data-ttu-id="babaf-112">`GetRWLockOwnerNext`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="babaf-112">`GetRWLockOwnerNext` returned successfully.</span></span>|  
|<span data-ttu-id="babaf-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="babaf-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="babaf-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="babaf-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="babaf-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="babaf-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="babaf-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="babaf-116">The call timed out.</span></span>|  
|<span data-ttu-id="babaf-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="babaf-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="babaf-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="babaf-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="babaf-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="babaf-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="babaf-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="babaf-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="babaf-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="babaf-121">E_FAIL</span></span>|<span data-ttu-id="babaf-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="babaf-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="babaf-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="babaf-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="babaf-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="babaf-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="babaf-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="babaf-125">Remarks</span></span>  
 <span data-ttu-id="babaf-126">`ppOwnerHostTask`Null olarak ayarlanırsa, yineleme sonlandırılır ve konak [DeleteRWLockOwnerIterator](iclrsyncmanager-deleterwlockowneriterator-method.md) yöntemini çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="babaf-126">If `ppOwnerHostTask` is set to null, the iteration has terminated, and the host should call the [DeleteRWLockOwnerIterator](iclrsyncmanager-deleterwlockowneriterator-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="babaf-127">`AddRef` `IHostTask` `ppOwnerHostTask` Konakta, konak işaretçiyi tutarken bu görevin çıkış yapmasını engellemek için gereken clr çağrıları.</span><span class="sxs-lookup"><span data-stu-id="babaf-127">The CLR calls `AddRef` on the `IHostTask` to which `ppOwnerHostTask` points to prevent this task from exiting while the host holds the pointer.</span></span> <span data-ttu-id="babaf-128">Ana bilgisayar, `Release` tamamlandığında başvuru sayısını azaltmak için çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="babaf-128">The host must call `Release` to decrement the reference count when it is finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="babaf-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="babaf-129">Requirements</span></span>  
 <span data-ttu-id="babaf-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="babaf-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="babaf-131">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="babaf-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="babaf-132">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="babaf-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="babaf-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="babaf-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="babaf-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="babaf-134">See also</span></span>

- [<span data-ttu-id="babaf-135">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="babaf-135">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="babaf-136">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="babaf-136">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
