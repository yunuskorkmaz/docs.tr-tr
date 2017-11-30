---
title: "IHostSyncManager::CreateAutoEvent Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager.CreateAutoEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager::CreateAutoEvent
helpviewer_keywords:
- IHostSyncManager::CreateAutoEvent method [.NET Framework hosting]
- CreateAutoEvent method [.NET Framework hosting]
ms.assetid: 3153643e-cf5c-4b44-8e0e-c2b22cb08208
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e6a792ca9075e48a8092d92e1adf870174dd1af6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsyncmanagercreateautoevent-method"></a><span data-ttu-id="fc0c6-102">IHostSyncManager::CreateAutoEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fc0c6-102">IHostSyncManager::CreateAutoEvent Method</span></span>
<span data-ttu-id="fc0c6-103">Otomatik sıfırlama olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fc0c6-103">Creates an auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc0c6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fc0c6-104">Syntax</span></span>  
  
```  
HRESULT CreateAutoEvent (  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fc0c6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fc0c6-105">Parameters</span></span>  
 `ppEvent`  
 <span data-ttu-id="fc0c6-106">[out] Adresine bir işaretçi bir [Ihostautoevent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) örnek ana bilgisayar tarafından uygulanan ya da null olay nesnesi oluşturulamadı.</span><span class="sxs-lookup"><span data-stu-id="fc0c6-106">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance implemented by the host, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fc0c6-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fc0c6-107">Return Value</span></span>  
  
|<span data-ttu-id="fc0c6-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fc0c6-108">HRESULT</span></span>|<span data-ttu-id="fc0c6-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fc0c6-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fc0c6-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="fc0c6-110">S_OK</span></span>|<span data-ttu-id="fc0c6-111">`CreateAutoEvent`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="fc0c6-111">`CreateAutoEvent` returned successfully.</span></span>|  
|<span data-ttu-id="fc0c6-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fc0c6-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fc0c6-113">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="fc0c6-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fc0c6-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fc0c6-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fc0c6-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="fc0c6-115">The call timed out.</span></span>|  
|<span data-ttu-id="fc0c6-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fc0c6-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fc0c6-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="fc0c6-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fc0c6-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fc0c6-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fc0c6-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="fc0c6-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fc0c6-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fc0c6-120">E_FAIL</span></span>|<span data-ttu-id="fc0c6-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="fc0c6-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fc0c6-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="fc0c6-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fc0c6-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="fc0c6-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="fc0c6-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="fc0c6-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="fc0c6-125">İstenen olay nesnesi oluşturmak yeterli bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="fc0c6-125">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc0c6-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fc0c6-126">Remarks</span></span>  
 <span data-ttu-id="fc0c6-127">`CreateAutoEvent`durumu otomatik olarak olmayan-bekleyen iş parçacığı serbest bırakıldıktan sonra işaret değiştirildi bir otomatik olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fc0c6-127">`CreateAutoEvent` creates an auto-event object whose state is automatically changed to non-signaled after the waiting thread has been released.</span></span> <span data-ttu-id="fc0c6-128">Bu yöntem Win32 yansıtan `CreateEvent` değerini işlevi `false` için belirtilen `bManualReset` parametresi</span><span class="sxs-lookup"><span data-stu-id="fc0c6-128">This method mirrors the Win32 `CreateEvent` function with a value of `false` specified for the `bManualReset` parameter</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc0c6-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fc0c6-129">Requirements</span></span>  
 <span data-ttu-id="fc0c6-130">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc0c6-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc0c6-131">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fc0c6-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fc0c6-132">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="fc0c6-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fc0c6-133">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc0c6-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc0c6-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fc0c6-134">See Also</span></span>  
 [<span data-ttu-id="fc0c6-135">Iclrsyncmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="fc0c6-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="fc0c6-136">Ihostautoevent arabirimi</span><span class="sxs-lookup"><span data-stu-id="fc0c6-136">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="fc0c6-137">Ihostcontrol arabirimi</span><span class="sxs-lookup"><span data-stu-id="fc0c6-137">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 [<span data-ttu-id="fc0c6-138">Ihostsyncmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="fc0c6-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
