---
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
ms.openlocfilehash: 9eace3e7330d3f8c0c9762e0b1b456ad1bf8a3ac
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763195"
---
# <a name="iclrsyncmanagercreaterwlockowneriterator-method"></a><span data-ttu-id="faf27-102">ICLRSyncManager::CreateRWLockOwnerIterator Yöntemi</span><span class="sxs-lookup"><span data-stu-id="faf27-102">ICLRSyncManager::CreateRWLockOwnerIterator Method</span></span>
<span data-ttu-id="faf27-103">Ortak dil çalışma zamanının (CLR), bir okuyucu-yazıcı kilidinde bekleyen görev kümesini belirlemede kullanacağı konak için bir yineleyici oluşturmasını ister.</span><span class="sxs-lookup"><span data-stu-id="faf27-103">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="faf27-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="faf27-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateRWLockOwnerIterator (  
    [in]  SIZE_T    cookie,  
    [out] SIZE_T   *pIterator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="faf27-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="faf27-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="faf27-106">'ndaki İstenen okuyucu-yazıcı kilidi ile ilişkili tanımlama bilgisi.</span><span class="sxs-lookup"><span data-stu-id="faf27-106">[in] The cookie associated with the desired reader-writer lock.</span></span>  
  
 `pIterator`  
 <span data-ttu-id="faf27-107">dışı [GetRWLockOwnerNext](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) ve [DeleteRWLockOwnerIterator](iclrsyncmanager-deleterwlockowneriterator-method.md) yöntemlerine geçirilebileceğini bir yineleyici işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="faf27-107">[out] A pointer to an iterator that can be passed to the [GetRWLockOwnerNext](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) and [DeleteRWLockOwnerIterator](iclrsyncmanager-deleterwlockowneriterator-method.md) methods.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="faf27-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="faf27-108">Return Value</span></span>  
  
|<span data-ttu-id="faf27-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="faf27-109">HRESULT</span></span>|<span data-ttu-id="faf27-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="faf27-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="faf27-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="faf27-111">S_OK</span></span>|<span data-ttu-id="faf27-112">`CreateRWLockOwnerIterator`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="faf27-112">`CreateRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="faf27-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="faf27-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="faf27-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="faf27-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="faf27-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="faf27-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="faf27-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="faf27-116">The call timed out.</span></span>|  
|<span data-ttu-id="faf27-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="faf27-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="faf27-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="faf27-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="faf27-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="faf27-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="faf27-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="faf27-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="faf27-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="faf27-121">E_FAIL</span></span>|<span data-ttu-id="faf27-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="faf27-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="faf27-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="faf27-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="faf27-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="faf27-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="faf27-125">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="faf27-125">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="faf27-126">`CreateRWLockOwnerIterator`Şu anda yönetilen kodu çalıştıran bir iş parçacığında çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="faf27-126">`CreateRWLockOwnerIterator` was called on a thread that is currently running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="faf27-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="faf27-127">Remarks</span></span>  
 <span data-ttu-id="faf27-128">Konaklar genellikle `CreateRWLockOwnerIterator` `DeleteRWLockOwnerIterator` `GetRWLockOwnerNext` kilitlenme algılama sırasında,, ve yöntemlerini çağırır.</span><span class="sxs-lookup"><span data-stu-id="faf27-128">Hosts typically call the `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`, and `GetRWLockOwnerNext` methods during deadlock detection.</span></span> <span data-ttu-id="faf27-129">CLR, okuyucu-yazıcı kilidini canlı tutmaya hiçbir girişim olmadığından, okuyucu-yazıcı kilidinin hala geçerli olduğundan emin olmak için ana bilgisayar sorumludur.</span><span class="sxs-lookup"><span data-stu-id="faf27-129">The host is responsible for ensuring that the reader-writer lock is still valid, because the CLR makes no attempt to keep the reader-writer lock alive.</span></span> <span data-ttu-id="faf27-130">Kilit geçerliliğini sağlamak için ana bilgisayar için birkaç strateji mevcuttur:</span><span class="sxs-lookup"><span data-stu-id="faf27-130">Several strategies are available for the host to ensure the validity of the lock:</span></span>  
  
- <span data-ttu-id="faf27-131">Ana bilgisayar okuyucu-yazıcı kilidinde (örneğin, [ıhostsemafor:: releasesemafor](ihostsemaphore-releasesemaphore-method.md)) yayın çağrılarını engelleyebilir, bu da bloğun kilitlenmeye neden olmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="faf27-131">The host can block release calls on the reader-writer lock (for example, [IHostSemaphore::ReleaseSemaphore](ihostsemaphore-releasesemaphore-method.md)) while ensuring that this block does not cause deadlock.</span></span>  
  
- <span data-ttu-id="faf27-132">Ana bilgisayar, okuyucu-yazıcı kilidi ile ilişkili olay nesnesi üzerinde beklemeyi, bu bloğun kilitlenmeye neden olmamasını sağlamak üzere engelleyebilir.</span><span class="sxs-lookup"><span data-stu-id="faf27-132">The host can block the exit from waiting on the event object associated with the reader-writer lock, again ensuring that this block does not cause deadlock.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="faf27-133">`CreateRWLockOwnerIterator`yalnızca şu anda yönetilmeyen kodu yürüten iş parçacıklarında çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="faf27-133">`CreateRWLockOwnerIterator` must be called only on threads that are currently executing unmanaged code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="faf27-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="faf27-134">Requirements</span></span>  
 <span data-ttu-id="faf27-135">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="faf27-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="faf27-136">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="faf27-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="faf27-137">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="faf27-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="faf27-138">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="faf27-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faf27-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="faf27-139">See also</span></span>

- [<span data-ttu-id="faf27-140">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="faf27-140">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="faf27-141">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="faf27-141">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
