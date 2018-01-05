---
title: "IHostSyncManager::CreateRWLockWriterEvent Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager.CreateRWLockWriterEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager::CreateRWLockWriterEvent
helpviewer_keywords:
- CreateRWLockWriterEvent method [.NET Framework hosting]
- IHostSyncManager::CreateRWLockWriterEvent method [.NET Framework hosting]
ms.assetid: 70e488c2-cf53-4dc0-ba52-74372d215c41
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eb38cd76a051b1a4459dff4f8164a6405f5fb32d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsyncmanagercreaterwlockwriterevent-method"></a><span data-ttu-id="5c4b5-102">IHostSyncManager::CreateRWLockWriterEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c4b5-102">IHostSyncManager::CreateRWLockWriterEvent Method</span></span>
<span data-ttu-id="5c4b5-103">Bir yazıcı kilidi uygulama için bir otomatik sıfırlama olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5c4b5-103">Creates an auto-reset event object for the implementation of a writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c4b5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5c4b5-104">Syntax</span></span>  
  
```  
HRESULT CreateRWLockWriterEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5c4b5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5c4b5-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="5c4b5-106">[in] Otomatik sıfırlama ilişkilendirmek için bir tanımlama bilgisi.</span><span class="sxs-lookup"><span data-stu-id="5c4b5-106">[in] A cookie to associate with the auto-reset event.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="5c4b5-107">[out] Adresine bir işaretçi bir [Ihostautoevent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) örneği veya olay nesnesi oluşturulamadı, boş.</span><span class="sxs-lookup"><span data-stu-id="5c4b5-107">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5c4b5-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5c4b5-108">Return Value</span></span>  
  
|<span data-ttu-id="5c4b5-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5c4b5-109">HRESULT</span></span>|<span data-ttu-id="5c4b5-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5c4b5-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5c4b5-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="5c4b5-111">S_OK</span></span>|<span data-ttu-id="5c4b5-112">`CreateRWLockWriterEvent`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="5c4b5-112">`CreateRWLockWriterEvent` returned successfully.</span></span>|  
|<span data-ttu-id="5c4b5-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5c4b5-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5c4b5-114">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="5c4b5-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5c4b5-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5c4b5-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5c4b5-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="5c4b5-116">The call timed out.</span></span>|  
|<span data-ttu-id="5c4b5-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5c4b5-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5c4b5-118">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="5c4b5-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5c4b5-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5c4b5-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5c4b5-120">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="5c4b5-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5c4b5-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5c4b5-121">E_FAIL</span></span>|<span data-ttu-id="5c4b5-122">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="5c4b5-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5c4b5-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="5c4b5-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5c4b5-124">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="5c4b5-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5c4b5-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="5c4b5-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="5c4b5-126">İstenen olay nesnesi oluşturmak yeterli bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="5c4b5-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c4b5-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5c4b5-127">Remarks</span></span>  
 <span data-ttu-id="5c4b5-128">CLR çağrıları `CreateRWLockWriterEvent` bir başvuru almak için yöntemi bir `IHostAutoEvent` yazan kilit kendi uygulamasında kullanılacak örneği.</span><span class="sxs-lookup"><span data-stu-id="5c4b5-128">The CLR calls the `CreateRWLockWriterEvent` method to get a reference to an `IHostAutoEvent` instance to use in its implementation of a writer lock.</span></span> <span data-ttu-id="5c4b5-129">Konak belirtilen tanımlama bilgisi yineleme yöntemlerini çağırarak kilidi beklerken hangi görevleri belirlemek için kullanabilirsiniz [Iclrsyncmanager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="5c4b5-129">The host can use the specified cookie to determine which tasks are waiting on the lock by calling the iteration methods of the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c4b5-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5c4b5-130">Requirements</span></span>  
 <span data-ttu-id="5c4b5-131">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c4b5-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c4b5-132">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5c4b5-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5c4b5-133">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="5c4b5-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5c4b5-134">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c4b5-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c4b5-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5c4b5-135">See Also</span></span>  
 [<span data-ttu-id="5c4b5-136">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5c4b5-136">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="5c4b5-137">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5c4b5-137">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="5c4b5-138">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5c4b5-138">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="5c4b5-139">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5c4b5-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
