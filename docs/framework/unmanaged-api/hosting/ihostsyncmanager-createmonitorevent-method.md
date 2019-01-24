---
title: IHostSyncManager::CreateMonitorEvent Yöntemi
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateMonitorEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateMonitorEvent
helpviewer_keywords:
- CreateMonitorEvent method [.NET Framework hosting]
- IHostSyncManager::CreateMonitorEvent method [.NET Framework hosting]
ms.assetid: 524c7fd3-9b5c-46e7-99ba-555fd2fe33f0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f8901d7b5076cc0ac9ddb6d4745b63839fecd025
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611234"
---
# <a name="ihostsyncmanagercreatemonitorevent-method"></a><span data-ttu-id="de857-102">IHostSyncManager::CreateMonitorEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="de857-102">IHostSyncManager::CreateMonitorEvent Method</span></span>
<span data-ttu-id="de857-103">İzlenen otomatik sıfırlama olayı nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="de857-103">Creates a monitored auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de857-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="de857-104">Syntax</span></span>  
  
```  
HRESULT CreateMonitorEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="de857-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="de857-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="de857-106">[in] Olay nesnesiyle ilişkilendirmek için bir tanımlama bilgisi.</span><span class="sxs-lookup"><span data-stu-id="de857-106">[in] A cookie to associate with the event object.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="de857-107">[out] Adresine bir işaretçi bir [Ihostautoevent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) örneği veya olay nesnesi oluşturulamadı yoksa null.</span><span class="sxs-lookup"><span data-stu-id="de857-107">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="de857-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="de857-108">Return Value</span></span>  
  
|<span data-ttu-id="de857-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="de857-109">HRESULT</span></span>|<span data-ttu-id="de857-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de857-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="de857-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="de857-111">S_OK</span></span>|<span data-ttu-id="de857-112">`CreateMonitorEvent` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="de857-112">`CreateMonitorEvent` returned successfully.</span></span>|  
|<span data-ttu-id="de857-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="de857-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="de857-114">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="de857-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="de857-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="de857-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="de857-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="de857-116">The call timed out.</span></span>|  
|<span data-ttu-id="de857-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="de857-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="de857-118">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="de857-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="de857-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="de857-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="de857-120">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="de857-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="de857-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="de857-121">E_FAIL</span></span>|<span data-ttu-id="de857-122">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="de857-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="de857-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="de857-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="de857-124">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="de857-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="de857-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="de857-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="de857-126">İstenen olay nesnesi oluşturmak yeterli bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="de857-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de857-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="de857-127">Remarks</span></span>  
 <span data-ttu-id="de857-128">`CreateMonitorEvent` döndürür bir `IHostAutoEvent` CLR, yönetilen uygulamada kullanan <xref:System.Threading.Monitor?displayProperty=nameWithType> türü.</span><span class="sxs-lookup"><span data-stu-id="de857-128">`CreateMonitorEvent` returns an `IHostAutoEvent` that the CLR uses in its implementation of the managed <xref:System.Threading.Monitor?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="de857-129">Bu yöntem Win32 yansıtır `CreateEvent` değerine sahip bir işlev `false` için belirtilen `bManualReset` parametresi.</span><span class="sxs-lookup"><span data-stu-id="de857-129">This method mirrors the Win32 `CreateEvent` function, with a value of `false` specified for the `bManualReset` parameter.</span></span>  
  
 <span data-ttu-id="de857-130">Ana bilgisayarın hangi görevin izleyicide çağırarak bekleyen belirlemek için tanımlama bilgisi kullanabilirsiniz [Iclrsyncmanager::getmonitorowner](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="de857-130">The host can use the cookie to determine which task is waiting on the monitor by calling the [ICLRSyncManager::GetMonitorOwner](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de857-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="de857-131">Requirements</span></span>  
 <span data-ttu-id="de857-132">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de857-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de857-133">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="de857-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="de857-134">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="de857-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="de857-135">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de857-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de857-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="de857-136">See also</span></span>
- [<span data-ttu-id="de857-137">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="de857-137">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="de857-138">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="de857-138">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="de857-139">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="de857-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- <xref:System.Threading.Monitor>
