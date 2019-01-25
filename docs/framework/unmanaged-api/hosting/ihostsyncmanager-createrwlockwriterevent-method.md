---
title: IHostSyncManager::CreateRWLockWriterEvent Yöntemi
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateRWLockWriterEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateRWLockWriterEvent
helpviewer_keywords:
- CreateRWLockWriterEvent method [.NET Framework hosting]
- IHostSyncManager::CreateRWLockWriterEvent method [.NET Framework hosting]
ms.assetid: 70e488c2-cf53-4dc0-ba52-74372d215c41
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fc62c5084d91e99193e9ddc5bfbb400fd8d87772
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54531073"
---
# <a name="ihostsyncmanagercreaterwlockwriterevent-method"></a><span data-ttu-id="528c9-102">IHostSyncManager::CreateRWLockWriterEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="528c9-102">IHostSyncManager::CreateRWLockWriterEvent Method</span></span>
<span data-ttu-id="528c9-103">Bir yazıcı kilidi uygulanması için bir otomatik sıfırlama olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="528c9-103">Creates an auto-reset event object for the implementation of a writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="528c9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="528c9-104">Syntax</span></span>  
  
```  
HRESULT CreateRWLockWriterEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="528c9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="528c9-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="528c9-106">[in] Otomatik sıfırlama olay ile ilişkilendirilecek bir tanımlama bilgisi.</span><span class="sxs-lookup"><span data-stu-id="528c9-106">[in] A cookie to associate with the auto-reset event.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="528c9-107">[out] Adresine bir işaretçi bir [Ihostautoevent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) örneği veya olay nesnesi oluşturulamadı yoksa null.</span><span class="sxs-lookup"><span data-stu-id="528c9-107">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="528c9-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="528c9-108">Return Value</span></span>  
  
|<span data-ttu-id="528c9-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="528c9-109">HRESULT</span></span>|<span data-ttu-id="528c9-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="528c9-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="528c9-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="528c9-111">S_OK</span></span>|<span data-ttu-id="528c9-112">`CreateRWLockWriterEvent` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="528c9-112">`CreateRWLockWriterEvent` returned successfully.</span></span>|  
|<span data-ttu-id="528c9-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="528c9-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="528c9-114">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="528c9-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="528c9-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="528c9-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="528c9-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="528c9-116">The call timed out.</span></span>|  
|<span data-ttu-id="528c9-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="528c9-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="528c9-118">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="528c9-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="528c9-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="528c9-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="528c9-120">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="528c9-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="528c9-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="528c9-121">E_FAIL</span></span>|<span data-ttu-id="528c9-122">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="528c9-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="528c9-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="528c9-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="528c9-124">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="528c9-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="528c9-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="528c9-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="528c9-126">İstenen olay nesnesi oluşturmak yeterli bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="528c9-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="528c9-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="528c9-127">Remarks</span></span>  
 <span data-ttu-id="528c9-128">CLR çağrıları `CreateRWLockWriterEvent` bir başvuru almak için yöntemi bir `IHostAutoEvent` bir yazıcı kilidi uygulaması içinde kullanılacak örneği.</span><span class="sxs-lookup"><span data-stu-id="528c9-128">The CLR calls the `CreateRWLockWriterEvent` method to get a reference to an `IHostAutoEvent` instance to use in its implementation of a writer lock.</span></span> <span data-ttu-id="528c9-129">Ana bilgisayarın hangi görevlerin yineleme yöntemleri çağırarak üzerindeki kilit bekleyen belirlemek için belirtilen tanımlama bilgisinin kullanabilirsiniz [Iclrsyncmanager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="528c9-129">The host can use the specified cookie to determine which tasks are waiting on the lock by calling the iteration methods of the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="528c9-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="528c9-130">Requirements</span></span>  
 <span data-ttu-id="528c9-131">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="528c9-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="528c9-132">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="528c9-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="528c9-133">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="528c9-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="528c9-134">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="528c9-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="528c9-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="528c9-135">See also</span></span>
- [<span data-ttu-id="528c9-136">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="528c9-136">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="528c9-137">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="528c9-137">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="528c9-138">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="528c9-138">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="528c9-139">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="528c9-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
