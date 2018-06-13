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
ms.openlocfilehash: ecf53606dd12b517d9ec31ab25f98452d35bdf98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443455"
---
# <a name="ihostsyncmanagercreatemanualevent-method"></a><span data-ttu-id="34394-102">IHostSyncManager::CreateManualEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="34394-102">IHostSyncManager::CreateManualEvent Method</span></span>
<span data-ttu-id="34394-103">El ile sıfırlama olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="34394-103">Creates a manual-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34394-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="34394-104">Syntax</span></span>  
  
```  
HRESULT CreateManualEvent (  
    [in]  BOOL bInitialState,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="34394-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="34394-105">Parameters</span></span>  
 `bInitialState`  
 <span data-ttu-id="34394-106">[in] `true`nesnesi, iş, aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="34394-106">[in] `true`, if the object is signaled; otherwise, `false`.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="34394-107">[out] Adresine bir işaretçi bir [Ihostmanualevent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) örneği veya olayı oluşturulamadı yoksa null.</span><span class="sxs-lookup"><span data-stu-id="34394-107">[out] A pointer to the address of an [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance, or null if the event could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="34394-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="34394-108">Return Value</span></span>  
  
|<span data-ttu-id="34394-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="34394-109">HRESULT</span></span>|<span data-ttu-id="34394-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34394-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="34394-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="34394-111">S_OK</span></span>|<span data-ttu-id="34394-112">`CreateManualEvent` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="34394-112">`CreateManualEvent` returned successfully.</span></span>|  
|<span data-ttu-id="34394-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="34394-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="34394-114">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="34394-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="34394-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="34394-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="34394-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="34394-116">The call timed out.</span></span>|  
|<span data-ttu-id="34394-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="34394-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="34394-118">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="34394-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="34394-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="34394-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="34394-120">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="34394-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="34394-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="34394-121">E_FAIL</span></span>|<span data-ttu-id="34394-122">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="34394-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="34394-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="34394-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="34394-124">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="34394-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="34394-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="34394-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="34394-126">İstenen olay nesnesi oluşturmak yeterli bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="34394-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34394-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="34394-127">Remarks</span></span>  
 <span data-ttu-id="34394-128">`CreateManualEvent` oluşturur bir `IHostManualEvent`, çağrı gerektiren bir elle sıfırlama olayı nesnesi [Ihostmanualevent::reset](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md) bir işaret dışı durumuna ayarlanacak yöntemi.</span><span class="sxs-lookup"><span data-stu-id="34394-128">`CreateManualEvent` creates an `IHostManualEvent`, a manual-reset event object that requires a call to the [IHostManualEvent::Reset](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md) method to set it to a non-signaled state.</span></span> <span data-ttu-id="34394-129">`CreateManualEvent` Win32 yansıtan `CreateEvent` değerini işlevi `true` için belirtilen `bManualReset` parametresi.</span><span class="sxs-lookup"><span data-stu-id="34394-129">`CreateManualEvent` mirrors the Win32 `CreateEvent` function with a value of `true` specified for the `bManualReset` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34394-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="34394-130">Requirements</span></span>  
 <span data-ttu-id="34394-131">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34394-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34394-132">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="34394-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="34394-133">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="34394-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="34394-134">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34394-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34394-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="34394-135">See Also</span></span>  
 [<span data-ttu-id="34394-136">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="34394-136">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="34394-137">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="34394-137">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="34394-138">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="34394-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
