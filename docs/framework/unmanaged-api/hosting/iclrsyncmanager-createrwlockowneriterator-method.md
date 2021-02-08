---
description: ': ICLRSyncManager:: CreateRWLockOwnerIterator yöntemi hakkında daha fazla bilgi edinin'
title: ICLRSyncManager::CreateRWLockOwnerIterator Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.CreateRWLockOwnerIterator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::CreateRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::CreateRWLockOwnerIterator method [.NET Framework hosting]
- CreateRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: b5535b87-9439-424e-b9b3-7d6fafb9819e
topic_type:
- apiref
ms.openlocfilehash: c6997b7720586f422cba3c96ca06a93f747d05bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781785"
---
# <a name="iclrsyncmanagercreaterwlockowneriterator-method"></a><span data-ttu-id="6a6ee-103">ICLRSyncManager::CreateRWLockOwnerIterator Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6a6ee-103">ICLRSyncManager::CreateRWLockOwnerIterator Method</span></span>

<span data-ttu-id="6a6ee-104">Ortak dil çalışma zamanının (CLR), bir okuyucu-yazıcı kilidinde bekleyen görev kümesini belirlemede kullanacağı konak için bir yineleyici oluşturmasını ister.</span><span class="sxs-lookup"><span data-stu-id="6a6ee-104">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a6ee-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6a6ee-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateRWLockOwnerIterator (  
    [in]  SIZE_T    cookie,  
    [out] SIZE_T   *pIterator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a6ee-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6a6ee-106">Parameters</span></span>  

 `cookie`  
 <span data-ttu-id="6a6ee-107">'ndaki İstenen okuyucu-yazıcı kilidi ile ilişkili tanımlama bilgisi.</span><span class="sxs-lookup"><span data-stu-id="6a6ee-107">[in] The cookie associated with the desired reader-writer lock.</span></span>  
  
 `pIterator`  
 <span data-ttu-id="6a6ee-108">dışı [GetRWLockOwnerNext](iclrsyncmanager-getrwlockownernext-method.md) ve [DeleteRWLockOwnerIterator](iclrsyncmanager-deleterwlockowneriterator-method.md) yöntemlerine geçirilebileceğini bir yineleyici işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="6a6ee-108">[out] A pointer to an iterator that can be passed to the [GetRWLockOwnerNext](iclrsyncmanager-getrwlockownernext-method.md) and [DeleteRWLockOwnerIterator](iclrsyncmanager-deleterwlockowneriterator-method.md) methods.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6a6ee-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6a6ee-109">Return Value</span></span>  
  
|<span data-ttu-id="6a6ee-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6a6ee-110">HRESULT</span></span>|<span data-ttu-id="6a6ee-111">Description</span><span class="sxs-lookup"><span data-stu-id="6a6ee-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6a6ee-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="6a6ee-112">S_OK</span></span>|<span data-ttu-id="6a6ee-113">`CreateRWLockOwnerIterator` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="6a6ee-113">`CreateRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="6a6ee-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6a6ee-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6a6ee-115">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="6a6ee-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6a6ee-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6a6ee-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6a6ee-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="6a6ee-117">The call timed out.</span></span>|  
|<span data-ttu-id="6a6ee-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6a6ee-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6a6ee-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="6a6ee-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6a6ee-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6a6ee-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6a6ee-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="6a6ee-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6a6ee-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6a6ee-122">E_FAIL</span></span>|<span data-ttu-id="6a6ee-123">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="6a6ee-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6a6ee-124">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6a6ee-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6a6ee-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="6a6ee-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6a6ee-126">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="6a6ee-126">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="6a6ee-127">`CreateRWLockOwnerIterator` Şu anda yönetilen kodu çalıştıran bir iş parçacığında çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="6a6ee-127">`CreateRWLockOwnerIterator` was called on a thread that is currently running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6a6ee-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6a6ee-128">Remarks</span></span>  

 <span data-ttu-id="6a6ee-129">Konaklar genellikle `CreateRWLockOwnerIterator` `DeleteRWLockOwnerIterator` `GetRWLockOwnerNext` kilitlenme algılama sırasında,, ve yöntemlerini çağırır.</span><span class="sxs-lookup"><span data-stu-id="6a6ee-129">Hosts typically call the `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`, and `GetRWLockOwnerNext` methods during deadlock detection.</span></span> <span data-ttu-id="6a6ee-130">CLR, okuyucu-yazıcı kilidini canlı tutmaya hiçbir girişim olmadığından, okuyucu-yazıcı kilidinin hala geçerli olduğundan emin olmak için ana bilgisayar sorumludur.</span><span class="sxs-lookup"><span data-stu-id="6a6ee-130">The host is responsible for ensuring that the reader-writer lock is still valid, because the CLR makes no attempt to keep the reader-writer lock alive.</span></span> <span data-ttu-id="6a6ee-131">Kilit geçerliliğini sağlamak için ana bilgisayar için birkaç strateji mevcuttur:</span><span class="sxs-lookup"><span data-stu-id="6a6ee-131">Several strategies are available for the host to ensure the validity of the lock:</span></span>  
  
- <span data-ttu-id="6a6ee-132">Ana bilgisayar okuyucu-yazıcı kilidinde (örneğin, [ıhostsemafor:: releasesemafor](ihostsemaphore-releasesemaphore-method.md)) yayın çağrılarını engelleyebilir, bu da bloğun kilitlenmeye neden olmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="6a6ee-132">The host can block release calls on the reader-writer lock (for example, [IHostSemaphore::ReleaseSemaphore](ihostsemaphore-releasesemaphore-method.md)) while ensuring that this block does not cause deadlock.</span></span>  
  
- <span data-ttu-id="6a6ee-133">Ana bilgisayar, okuyucu-yazıcı kilidi ile ilişkili olay nesnesi üzerinde beklemeyi, bu bloğun kilitlenmeye neden olmamasını sağlamak üzere engelleyebilir.</span><span class="sxs-lookup"><span data-stu-id="6a6ee-133">The host can block the exit from waiting on the event object associated with the reader-writer lock, again ensuring that this block does not cause deadlock.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6a6ee-134">`CreateRWLockOwnerIterator` yalnızca şu anda yönetilmeyen kodu yürüten iş parçacıklarında çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6a6ee-134">`CreateRWLockOwnerIterator` must be called only on threads that are currently executing unmanaged code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a6ee-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6a6ee-135">Requirements</span></span>  

 <span data-ttu-id="6a6ee-136">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a6ee-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a6ee-137">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6a6ee-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6a6ee-138">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="6a6ee-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6a6ee-139">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a6ee-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a6ee-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a6ee-140">See also</span></span>

- [<span data-ttu-id="6a6ee-141">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6a6ee-141">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="6a6ee-142">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6a6ee-142">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
