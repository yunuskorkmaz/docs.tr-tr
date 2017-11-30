---
title: "IHostSyncManager::CreateRWLockReaderEvent Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager.CreateRWLockReaderEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager::CreateRWLockReaderEvent
helpviewer_keywords:
- CreateRWLockReaderEvent method [.NET Framework hosting]
- IHostSyncManager::CreateRWLockReaderEvent method [.NET Framework hosting]
ms.assetid: 68c4ea19-c47c-45c6-b420-d3a2ba1c2d50
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a783f4511e27b5d230a90444e5a91b34327543cf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsyncmanagercreaterwlockreaderevent-method"></a><span data-ttu-id="0b423-102">IHostSyncManager::CreateRWLockReaderEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0b423-102">IHostSyncManager::CreateRWLockReaderEvent Method</span></span>
<span data-ttu-id="0b423-103">Bir okuyucu kilidini uygulanması için el ile sıfırlama olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0b423-103">Creates a manual-reset event object for the implementation of a reader lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b423-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0b423-104">Syntax</span></span>  
  
```  
HRESULT CreateRWLockReaderEvent (  
    [in]  BOOL bInitialState,  
    [in]  SIZE_T cookie,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0b423-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0b423-105">Parameters</span></span>  
 `bInitialState`  
 <span data-ttu-id="0b423-106">[in] `true`, `ppEvent` olması gereken sinyal verilmiş; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="0b423-106">[in] `true`, if `ppEvent` should be signaled; otherwise, `false`.</span></span>  
  
 `cookie`  
 <span data-ttu-id="0b423-107">[in] Okuyucu kilidi ile ilişkilendirilecek bir tanımlama bilgisi.</span><span class="sxs-lookup"><span data-stu-id="0b423-107">[in] A cookie to associate with the reader lock.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="0b423-108">[out] Adresine bir işaretçi bir [Ihostmanualevent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) örneği veya olay nesnesi oluşturulamadı, boş.</span><span class="sxs-lookup"><span data-stu-id="0b423-108">[out] A pointer to the address of an [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0b423-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0b423-109">Return Value</span></span>  
  
|<span data-ttu-id="0b423-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0b423-110">HRESULT</span></span>|<span data-ttu-id="0b423-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b423-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0b423-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="0b423-112">S_OK</span></span>|<span data-ttu-id="0b423-113">`CreateRWLockReaderEvent`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="0b423-113">`CreateRWLockReaderEvent` returned successfully.</span></span>|  
|<span data-ttu-id="0b423-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0b423-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0b423-115">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="0b423-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0b423-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0b423-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0b423-117">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="0b423-117">The call timed out.</span></span>|  
|<span data-ttu-id="0b423-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0b423-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0b423-119">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="0b423-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0b423-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0b423-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0b423-121">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="0b423-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0b423-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0b423-122">E_FAIL</span></span>|<span data-ttu-id="0b423-123">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="0b423-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0b423-124">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0b423-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0b423-125">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="0b423-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0b423-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="0b423-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="0b423-127">İstenen olay nesnesi oluşturmak yeterli bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="0b423-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b423-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0b423-128">Remarks</span></span>  
 <span data-ttu-id="0b423-129">CLR çağrıları `CreateRWLockReaderEvent` bir başvuru almak için bir `IHostManualEvent` bir okuyucu kilidini kendi uygulamasında kullanılacak örneği.</span><span class="sxs-lookup"><span data-stu-id="0b423-129">The CLR calls `CreateRWLockReaderEvent` to get a reference to an `IHostManualEvent` instance to use in its implementation of a reader lock.</span></span> <span data-ttu-id="0b423-130">Konak sorgulanarak okuyucu kilidini bekleyen hangi görevleri belirlemek için tanımlama bilgisi kullanabilirsiniz [Iclrsyncmanager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="0b423-130">The host can use the cookie to determine which tasks are waiting on the reader lock by querying the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b423-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0b423-131">Requirements</span></span>  
 <span data-ttu-id="0b423-132">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b423-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b423-133">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0b423-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0b423-134">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="0b423-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0b423-135">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b423-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b423-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0b423-136">See Also</span></span>  
 [<span data-ttu-id="0b423-137">Iclrsyncmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b423-137">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="0b423-138">Ihostautoevent arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b423-138">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="0b423-139">Ihostmanualevent arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b423-139">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="0b423-140">Ihostsyncmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b423-140">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
