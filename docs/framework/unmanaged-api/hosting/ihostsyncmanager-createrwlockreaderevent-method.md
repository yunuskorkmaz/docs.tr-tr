---
title: IHostSyncManager::CreateRWLockReaderEvent Yöntemi
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateRWLockReaderEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateRWLockReaderEvent
helpviewer_keywords:
- CreateRWLockReaderEvent method [.NET Framework hosting]
- IHostSyncManager::CreateRWLockReaderEvent method [.NET Framework hosting]
ms.assetid: 68c4ea19-c47c-45c6-b420-d3a2ba1c2d50
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b5aef90fa14dac58a0b38316cd5f64b4ac8c9aa1
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57495656"
---
# <a name="ihostsyncmanagercreaterwlockreaderevent-method"></a><span data-ttu-id="e9f16-102">IHostSyncManager::CreateRWLockReaderEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e9f16-102">IHostSyncManager::CreateRWLockReaderEvent Method</span></span>
<span data-ttu-id="e9f16-103">Bir okuyucu kilidi uygulanması için bir elle sıfırlama olayı nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e9f16-103">Creates a manual-reset event object for the implementation of a reader lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9f16-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e9f16-104">Syntax</span></span>  
  
```  
HRESULT CreateRWLockReaderEvent (  
    [in]  BOOL bInitialState,  
    [in]  SIZE_T cookie,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9f16-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e9f16-105">Parameters</span></span>  
 `bInitialState`  
 <span data-ttu-id="e9f16-106">[in] `true`, `ppEvent` olması gereken sinyal; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="e9f16-106">[in] `true`, if `ppEvent` should be signaled; otherwise, `false`.</span></span>  
  
 `cookie`  
 <span data-ttu-id="e9f16-107">[in] Okuyucu kilit ile ilişkilendirmek için bir tanımlama bilgisi.</span><span class="sxs-lookup"><span data-stu-id="e9f16-107">[in] A cookie to associate with the reader lock.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="e9f16-108">[out] Adresine bir işaretçi bir [Ihostmanualevent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) örneği veya olay nesnesi oluşturulamadı yoksa null.</span><span class="sxs-lookup"><span data-stu-id="e9f16-108">[out] A pointer to the address of an [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e9f16-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e9f16-109">Return Value</span></span>  
  
|<span data-ttu-id="e9f16-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e9f16-110">HRESULT</span></span>|<span data-ttu-id="e9f16-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e9f16-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e9f16-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="e9f16-112">S_OK</span></span>|<span data-ttu-id="e9f16-113">`CreateRWLockReaderEvent` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e9f16-113">`CreateRWLockReaderEvent` returned successfully.</span></span>|  
|<span data-ttu-id="e9f16-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e9f16-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e9f16-115">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="e9f16-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e9f16-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e9f16-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e9f16-117">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="e9f16-117">The call timed out.</span></span>|  
|<span data-ttu-id="e9f16-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e9f16-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e9f16-119">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="e9f16-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e9f16-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e9f16-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e9f16-121">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="e9f16-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e9f16-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e9f16-122">E_FAIL</span></span>|<span data-ttu-id="e9f16-123">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e9f16-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e9f16-124">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e9f16-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e9f16-125">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="e9f16-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e9f16-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="e9f16-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="e9f16-127">İstenen olay nesnesi oluşturmak yeterli bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="e9f16-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9f16-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e9f16-128">Remarks</span></span>  
 <span data-ttu-id="e9f16-129">CLR çağrıları `CreateRWLockReaderEvent` bir başvuru almak için bir `IHostManualEvent` okuyucu kilit uygulaması içinde kullanılacak örneği.</span><span class="sxs-lookup"><span data-stu-id="e9f16-129">The CLR calls `CreateRWLockReaderEvent` to get a reference to an `IHostManualEvent` instance to use in its implementation of a reader lock.</span></span> <span data-ttu-id="e9f16-130">Ana bilgisayarın hangi görevlerin sorgulayarak okuyucu kilit bekleyen belirlemek için tanımlama bilgisi kullanabilirsiniz [Iclrsyncmanager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="e9f16-130">The host can use the cookie to determine which tasks are waiting on the reader lock by querying the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9f16-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e9f16-131">Requirements</span></span>  
 <span data-ttu-id="e9f16-132">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9f16-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9f16-133">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e9f16-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e9f16-134">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e9f16-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e9f16-135">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9f16-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9f16-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9f16-136">See also</span></span>
- [<span data-ttu-id="e9f16-137">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9f16-137">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="e9f16-138">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9f16-138">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="e9f16-139">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9f16-139">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="e9f16-140">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9f16-140">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
