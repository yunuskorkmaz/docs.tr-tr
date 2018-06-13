---
title: IHostSyncManager::CreateCrst Yöntemi
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateCrst
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateCrst
helpviewer_keywords:
- CreateCrst method [.NET Framework hosting]
- IHostSyncManager::CreateCrst method [.NET Framework hosting]
ms.assetid: ac278cc8-2540-4a6c-b5c6-b90c3970b4f4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 101a652aa77e587003fb7e773e00ba9b77461a06
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441899"
---
# <a name="ihostsyncmanagercreatecrst-method"></a><span data-ttu-id="c6114-102">IHostSyncManager::CreateCrst Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c6114-102">IHostSyncManager::CreateCrst Method</span></span>
<span data-ttu-id="c6114-103">Eşitleme için bir kritik bölüm nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c6114-103">Creates a critical section object for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6114-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c6114-104">Syntax</span></span>  
  
```  
HRESULT CreateCrst (  
    [out] IHostCrst** ppCrst  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c6114-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c6114-105">Parameters</span></span>  
 `ppCrst`  
 <span data-ttu-id="c6114-106">[out] Adresine bir işaretçi bir [Ihostcrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) örnek ana bilgisayar tarafından uygulanan ya da null kritik bölüm oluşturulamadı.</span><span class="sxs-lookup"><span data-stu-id="c6114-106">[out] A pointer to the address of an [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance implemented by the host, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c6114-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c6114-107">Return Value</span></span>  
  
|<span data-ttu-id="c6114-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c6114-108">HRESULT</span></span>|<span data-ttu-id="c6114-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6114-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c6114-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c6114-110">S_OK</span></span>|<span data-ttu-id="c6114-111">`CreateCrst` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="c6114-111">`CreateCrst` returned successfully.</span></span>|  
|<span data-ttu-id="c6114-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c6114-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c6114-113">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="c6114-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c6114-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c6114-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c6114-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="c6114-115">The call timed out.</span></span>|  
|<span data-ttu-id="c6114-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c6114-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c6114-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="c6114-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c6114-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c6114-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c6114-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="c6114-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c6114-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c6114-120">E_FAIL</span></span>|<span data-ttu-id="c6114-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="c6114-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c6114-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c6114-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c6114-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="c6114-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c6114-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="c6114-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="c6114-125">İstenen kritik bölüm oluşturmak yeterli bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="c6114-125">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6114-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c6114-126">Remarks</span></span>  
 <span data-ttu-id="c6114-127">Kritik bölümler yalnızca tek bir işlem iş parçacığı tarafından kullanılabilir dışında kritik bölüm nesneleri eşitleme mutex nesnesi tarafından sağlanan benzer sağlar.</span><span class="sxs-lookup"><span data-stu-id="c6114-127">Critical section objects provide synchronization similar to that provided by a mutex object, except that critical sections can be used only by the threads of a single process.</span></span> <span data-ttu-id="c6114-128">`CreateCrst` Win32 yansıtan `InitializeCriticalSection` işlevi.</span><span class="sxs-lookup"><span data-stu-id="c6114-128">`CreateCrst` mirrors the Win32 `InitializeCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6114-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c6114-129">Requirements</span></span>  
 <span data-ttu-id="c6114-130">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6114-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6114-131">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c6114-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c6114-132">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="c6114-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c6114-133">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6114-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6114-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c6114-134">See Also</span></span>  
 [<span data-ttu-id="c6114-135">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c6114-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="c6114-136">IHostCrst Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c6114-136">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 [<span data-ttu-id="c6114-137">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c6114-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="c6114-138">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c6114-138">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="c6114-139">Karşılıklı dışlamalar</span><span class="sxs-lookup"><span data-stu-id="c6114-139">Mutexes</span></span>](../../../../docs/standard/threading/mutexes.md)  
 [<span data-ttu-id="c6114-140">Semaphore ve SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="c6114-140">Semaphore and SemaphoreSlim</span></span>](../../../../docs/standard/threading/semaphore-and-semaphoreslim.md)
