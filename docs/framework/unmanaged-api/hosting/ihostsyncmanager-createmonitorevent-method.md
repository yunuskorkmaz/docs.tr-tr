---
title: "IHostSyncManager::CreateMonitorEvent Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager.CreateMonitorEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager::CreateMonitorEvent
helpviewer_keywords:
- CreateMonitorEvent method [.NET Framework hosting]
- IHostSyncManager::CreateMonitorEvent method [.NET Framework hosting]
ms.assetid: 524c7fd3-9b5c-46e7-99ba-555fd2fe33f0
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c16c1376237916d09fb4156b023f4f1cc51a7d54
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsyncmanagercreatemonitorevent-method"></a><span data-ttu-id="faa52-102">IHostSyncManager::CreateMonitorEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="faa52-102">IHostSyncManager::CreateMonitorEvent Method</span></span>
<span data-ttu-id="faa52-103">İzlenen otomatik sıfırlama olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="faa52-103">Creates a monitored auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="faa52-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="faa52-104">Syntax</span></span>  
  
```  
HRESULT CreateMonitorEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="faa52-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="faa52-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="faa52-106">[in] Olay nesne ile ilişkilendirilecek bir tanımlama bilgisi.</span><span class="sxs-lookup"><span data-stu-id="faa52-106">[in] A cookie to associate with the event object.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="faa52-107">[out] Adresine bir işaretçi bir [Ihostautoevent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) örneği veya olay nesnesi oluşturulamadı, boş.</span><span class="sxs-lookup"><span data-stu-id="faa52-107">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="faa52-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="faa52-108">Return Value</span></span>  
  
|<span data-ttu-id="faa52-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="faa52-109">HRESULT</span></span>|<span data-ttu-id="faa52-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="faa52-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="faa52-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="faa52-111">S_OK</span></span>|<span data-ttu-id="faa52-112">`CreateMonitorEvent`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="faa52-112">`CreateMonitorEvent` returned successfully.</span></span>|  
|<span data-ttu-id="faa52-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="faa52-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="faa52-114">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="faa52-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="faa52-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="faa52-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="faa52-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="faa52-116">The call timed out.</span></span>|  
|<span data-ttu-id="faa52-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="faa52-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="faa52-118">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="faa52-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="faa52-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="faa52-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="faa52-120">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="faa52-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="faa52-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="faa52-121">E_FAIL</span></span>|<span data-ttu-id="faa52-122">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="faa52-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="faa52-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="faa52-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="faa52-124">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="faa52-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="faa52-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="faa52-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="faa52-126">İstenen olay nesnesi oluşturmak yeterli bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="faa52-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="faa52-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="faa52-127">Remarks</span></span>  
 <span data-ttu-id="faa52-128">`CreateMonitorEvent`döndüren bir `IHostAutoEvent` yönetilen uygulamasında CLR kullanan <xref:System.Threading.Monitor?displayProperty=nameWithType> türü.</span><span class="sxs-lookup"><span data-stu-id="faa52-128">`CreateMonitorEvent` returns an `IHostAutoEvent` that the CLR uses in its implementation of the managed <xref:System.Threading.Monitor?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="faa52-129">Bu yöntem Win32 yansıtan `CreateEvent` değerini işlevi `false` için belirtilen `bManualReset` parametresi.</span><span class="sxs-lookup"><span data-stu-id="faa52-129">This method mirrors the Win32 `CreateEvent` function, with a value of `false` specified for the `bManualReset` parameter.</span></span>  
  
 <span data-ttu-id="faa52-130">Ana bilgisayarın hangi görev monitörde çağırarak bekliyor. belirlemek için tanımlama bilgisi kullanabilirsiniz [Iclrsyncmanager::getmonitorowner](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="faa52-130">The host can use the cookie to determine which task is waiting on the monitor by calling the [ICLRSyncManager::GetMonitorOwner](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="faa52-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="faa52-131">Requirements</span></span>  
 <span data-ttu-id="faa52-132">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="faa52-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="faa52-133">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="faa52-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="faa52-134">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="faa52-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="faa52-135">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="faa52-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faa52-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="faa52-136">See Also</span></span>  
 [<span data-ttu-id="faa52-137">Iclrsyncmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="faa52-137">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="faa52-138">Ihostautoevent arabirimi</span><span class="sxs-lookup"><span data-stu-id="faa52-138">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="faa52-139">Ihostsyncmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="faa52-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="faa52-140">İzleyicileri</span><span class="sxs-lookup"><span data-stu-id="faa52-140">Monitors</span></span>](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)
