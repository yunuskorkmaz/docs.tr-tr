---
title: IHostSyncManager::CreateManualEvent Yöntemi
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateManualEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateManualEvent
helpviewer_keywords:
- CreateManualEvent method [.NET Framework hosting]
- IHostSyncManager::CreateManualEvent method [.NET Framework hosting]
ms.assetid: 68661fbd-09cf-46dc-890b-e694f8a3880a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1cfb57ba6f07437abfc8576ca4d5ff9cd0131d8b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753441"
---
# <a name="ihostsyncmanagercreatemanualevent-method"></a><span data-ttu-id="4e7a2-102">IHostSyncManager::CreateManualEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4e7a2-102">IHostSyncManager::CreateManualEvent Method</span></span>
<span data-ttu-id="4e7a2-103">Elle sıfırlama olayı nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4e7a2-103">Creates a manual-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e7a2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4e7a2-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateManualEvent (  
    [in]  BOOL bInitialState,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e7a2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4e7a2-105">Parameters</span></span>  
 `bInitialState`  
 <span data-ttu-id="4e7a2-106">[in] `true`nesnedir, sinyal; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="4e7a2-106">[in] `true`, if the object is signaled; otherwise, `false`.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="4e7a2-107">[out] Adresine bir işaretçi bir [Ihostmanualevent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) örneği veya olayı oluşturulamadı yoksa null.</span><span class="sxs-lookup"><span data-stu-id="4e7a2-107">[out] A pointer to the address of an [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance, or null if the event could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4e7a2-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4e7a2-108">Return Value</span></span>  
  
|<span data-ttu-id="4e7a2-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4e7a2-109">HRESULT</span></span>|<span data-ttu-id="4e7a2-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4e7a2-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4e7a2-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="4e7a2-111">S_OK</span></span>|<span data-ttu-id="4e7a2-112">`CreateManualEvent` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="4e7a2-112">`CreateManualEvent` returned successfully.</span></span>|  
|<span data-ttu-id="4e7a2-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4e7a2-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4e7a2-114">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="4e7a2-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4e7a2-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4e7a2-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4e7a2-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="4e7a2-116">The call timed out.</span></span>|  
|<span data-ttu-id="4e7a2-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4e7a2-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4e7a2-118">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="4e7a2-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4e7a2-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4e7a2-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4e7a2-120">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="4e7a2-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4e7a2-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4e7a2-121">E_FAIL</span></span>|<span data-ttu-id="4e7a2-122">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="4e7a2-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4e7a2-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4e7a2-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4e7a2-124">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="4e7a2-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4e7a2-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="4e7a2-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="4e7a2-126">İstenen olay nesnesi oluşturmak yeterli bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="4e7a2-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e7a2-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4e7a2-127">Remarks</span></span>  
 <span data-ttu-id="4e7a2-128">`CreateManualEvent` oluşturur bir `IHostManualEvent`, yapılan bir çağrı gerektirir. bir elle sıfırlama olayı nesnesi [Ihostmanualevent::reset](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md) verilmemiş bir duruma ayarlamak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4e7a2-128">`CreateManualEvent` creates an `IHostManualEvent`, a manual-reset event object that requires a call to the [IHostManualEvent::Reset](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md) method to set it to a non-signaled state.</span></span> <span data-ttu-id="4e7a2-129">`CreateManualEvent` Win32 yansıtır `CreateEvent` işlevi değeriyle `true` için belirtilen `bManualReset` parametresi.</span><span class="sxs-lookup"><span data-stu-id="4e7a2-129">`CreateManualEvent` mirrors the Win32 `CreateEvent` function with a value of `true` specified for the `bManualReset` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e7a2-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4e7a2-130">Requirements</span></span>  
 <span data-ttu-id="4e7a2-131">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e7a2-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e7a2-132">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4e7a2-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4e7a2-133">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="4e7a2-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4e7a2-134">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e7a2-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e7a2-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e7a2-135">See also</span></span>

- [<span data-ttu-id="4e7a2-136">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4e7a2-136">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="4e7a2-137">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4e7a2-137">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="4e7a2-138">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4e7a2-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
