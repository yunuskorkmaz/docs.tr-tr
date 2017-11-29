---
title: "IHostSyncManager::CreateCrst Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager.CreateCrst
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager::CreateCrst
helpviewer_keywords:
- CreateCrst method [.NET Framework hosting]
- IHostSyncManager::CreateCrst method [.NET Framework hosting]
ms.assetid: ac278cc8-2540-4a6c-b5c6-b90c3970b4f4
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b54abb60b00d071900d3bfdd01c2e5f1807998a5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsyncmanagercreatecrst-method"></a><span data-ttu-id="79b04-102">IHostSyncManager::CreateCrst Yöntemi</span><span class="sxs-lookup"><span data-stu-id="79b04-102">IHostSyncManager::CreateCrst Method</span></span>
<span data-ttu-id="79b04-103">Eşitleme için bir kritik bölüm nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="79b04-103">Creates a critical section object for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79b04-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="79b04-104">Syntax</span></span>  
  
```  
HRESULT CreateCrst (  
    [out] IHostCrst** ppCrst  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="79b04-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="79b04-105">Parameters</span></span>  
 `ppCrst`  
 <span data-ttu-id="79b04-106">[out] Adresine bir işaretçi bir [Ihostcrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) örnek ana bilgisayar tarafından uygulanan ya da null kritik bölüm oluşturulamadı.</span><span class="sxs-lookup"><span data-stu-id="79b04-106">[out] A pointer to the address of an [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance implemented by the host, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="79b04-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="79b04-107">Return Value</span></span>  
  
|<span data-ttu-id="79b04-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="79b04-108">HRESULT</span></span>|<span data-ttu-id="79b04-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="79b04-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="79b04-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="79b04-110">S_OK</span></span>|<span data-ttu-id="79b04-111">`CreateCrst`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="79b04-111">`CreateCrst` returned successfully.</span></span>|  
|<span data-ttu-id="79b04-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="79b04-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="79b04-113">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="79b04-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="79b04-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="79b04-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="79b04-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="79b04-115">The call timed out.</span></span>|  
|<span data-ttu-id="79b04-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="79b04-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="79b04-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="79b04-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="79b04-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="79b04-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="79b04-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="79b04-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="79b04-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="79b04-120">E_FAIL</span></span>|<span data-ttu-id="79b04-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="79b04-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="79b04-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="79b04-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="79b04-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="79b04-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="79b04-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="79b04-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="79b04-125">İstenen kritik bölüm oluşturmak yeterli bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="79b04-125">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79b04-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="79b04-126">Remarks</span></span>  
 <span data-ttu-id="79b04-127">Kritik bölümler yalnızca tek bir işlem iş parçacığı tarafından kullanılabilir dışında kritik bölüm nesneleri eşitleme mutex nesnesi tarafından sağlanan benzer sağlar.</span><span class="sxs-lookup"><span data-stu-id="79b04-127">Critical section objects provide synchronization similar to that provided by a mutex object, except that critical sections can be used only by the threads of a single process.</span></span> <span data-ttu-id="79b04-128">`CreateCrst`Win32 yansıtan `InitializeCriticalSection` işlevi.</span><span class="sxs-lookup"><span data-stu-id="79b04-128">`CreateCrst` mirrors the Win32 `InitializeCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79b04-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="79b04-129">Requirements</span></span>  
 <span data-ttu-id="79b04-130">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79b04-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79b04-131">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="79b04-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="79b04-132">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="79b04-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="79b04-133">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79b04-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79b04-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="79b04-134">See Also</span></span>  
 [<span data-ttu-id="79b04-135">Iclrsyncmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="79b04-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="79b04-136">Ihostcrst arabirimi</span><span class="sxs-lookup"><span data-stu-id="79b04-136">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 [<span data-ttu-id="79b04-137">Ihostsyncmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="79b04-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="79b04-138">Ihostsemaphore arabirimi</span><span class="sxs-lookup"><span data-stu-id="79b04-138">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="79b04-139">Zaman uyumu sağlayıcılar</span><span class="sxs-lookup"><span data-stu-id="79b04-139">Mutexes</span></span>](../../../../docs/standard/threading/mutexes.md)  
 [<span data-ttu-id="79b04-140">Semafor ve SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="79b04-140">Semaphore and SemaphoreSlim</span></span>](../../../../docs/standard/threading/semaphore-and-semaphoreslim.md)
