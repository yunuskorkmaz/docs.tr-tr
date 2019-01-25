---
title: IHostSyncManager::CreateAutoEvent Yöntemi
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateAutoEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateAutoEvent
helpviewer_keywords:
- IHostSyncManager::CreateAutoEvent method [.NET Framework hosting]
- CreateAutoEvent method [.NET Framework hosting]
ms.assetid: 3153643e-cf5c-4b44-8e0e-c2b22cb08208
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9166d7934c56a897ef766bc3a4962041e6d19f5c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54658643"
---
# <a name="ihostsyncmanagercreateautoevent-method"></a><span data-ttu-id="465a3-102">IHostSyncManager::CreateAutoEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="465a3-102">IHostSyncManager::CreateAutoEvent Method</span></span>
<span data-ttu-id="465a3-103">Otomatik sıfırlama olayından nesne oluşturur.</span><span class="sxs-lookup"><span data-stu-id="465a3-103">Creates an auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="465a3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="465a3-104">Syntax</span></span>  
  
```  
HRESULT CreateAutoEvent (  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="465a3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="465a3-105">Parameters</span></span>  
 `ppEvent`  
 <span data-ttu-id="465a3-106">[out] Adresine bir işaretçi bir [Ihostautoevent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) örneği ana bilgisayar tarafından uygulanan ya da null olay nesnesi oluşturulamadı.</span><span class="sxs-lookup"><span data-stu-id="465a3-106">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance implemented by the host, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="465a3-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="465a3-107">Return Value</span></span>  
  
|<span data-ttu-id="465a3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="465a3-108">HRESULT</span></span>|<span data-ttu-id="465a3-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="465a3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="465a3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="465a3-110">S_OK</span></span>|<span data-ttu-id="465a3-111">`CreateAutoEvent` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="465a3-111">`CreateAutoEvent` returned successfully.</span></span>|  
|<span data-ttu-id="465a3-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="465a3-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="465a3-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="465a3-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="465a3-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="465a3-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="465a3-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="465a3-115">The call timed out.</span></span>|  
|<span data-ttu-id="465a3-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="465a3-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="465a3-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="465a3-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="465a3-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="465a3-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="465a3-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="465a3-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="465a3-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="465a3-120">E_FAIL</span></span>|<span data-ttu-id="465a3-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="465a3-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="465a3-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="465a3-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="465a3-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="465a3-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="465a3-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="465a3-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="465a3-125">İstenen olay nesnesi oluşturmak yeterli bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="465a3-125">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="465a3-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="465a3-126">Remarks</span></span>  
 <span data-ttu-id="465a3-127">`CreateAutoEvent` durumu otomatik olarak bekleyen iş parçacığı piyasaya sürüldükten sonra verilmemiş değiştirildi otomatik olay nesne oluşturur.</span><span class="sxs-lookup"><span data-stu-id="465a3-127">`CreateAutoEvent` creates an auto-event object whose state is automatically changed to non-signaled after the waiting thread has been released.</span></span> <span data-ttu-id="465a3-128">Bu yöntem Win32 yansıtır `CreateEvent` işlevi değeriyle `false` için belirtilen `bManualReset` parametresi</span><span class="sxs-lookup"><span data-stu-id="465a3-128">This method mirrors the Win32 `CreateEvent` function with a value of `false` specified for the `bManualReset` parameter</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="465a3-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="465a3-129">Requirements</span></span>  
 <span data-ttu-id="465a3-130">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="465a3-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="465a3-131">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="465a3-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="465a3-132">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="465a3-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="465a3-133">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="465a3-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="465a3-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="465a3-134">See also</span></span>
- [<span data-ttu-id="465a3-135">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="465a3-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="465a3-136">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="465a3-136">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="465a3-137">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="465a3-137">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
- [<span data-ttu-id="465a3-138">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="465a3-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
