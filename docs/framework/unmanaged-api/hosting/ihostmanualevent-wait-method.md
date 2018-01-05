---
title: "IHostManualEvent::Wait Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostManualEvent.Wait
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostManualEvent::Wait
helpviewer_keywords:
- IHostManualEvent::Wait method [.NET Framework hosting]
- Wait method, IHostManualEvent interface [.NET Framework hosting]
ms.assetid: 1fbb7d8b-8a23-4c2b-8376-1a70cd2d6030
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2dd456a3901f91fc8598a707a5699637ec450dbd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmanualeventwait-method"></a><span data-ttu-id="4a688-102">IHostManualEvent::Wait Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4a688-102">IHostManualEvent::Wait Method</span></span>
<span data-ttu-id="4a688-103">Geçerli neden [Ihostmanualevent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) örneği ait kadar bekleyin veya belirli bir süre geçtikten miktarını.</span><span class="sxs-lookup"><span data-stu-id="4a688-103">Causes the current [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance to wait until it is owned, or a specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a688-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4a688-104">Syntax</span></span>  
  
```  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4a688-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4a688-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="4a688-106">[in] Varsa döndürmeden önce beklenmesi gereken milisaniye sayısını geçerli `IHostManualEvent` örneği ait değil.</span><span class="sxs-lookup"><span data-stu-id="4a688-106">[in] The number of milliseconds to wait before returning, if the current `IHostManualEvent` instance is not owned.</span></span>  
  
 `option`  
 <span data-ttu-id="4a688-107">[in] Aşağıdakilerden birini [waıt_optıon](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) değerleri, bu konak gerçekleştirmesi eylemi belirten işlemi engeller.</span><span class="sxs-lookup"><span data-stu-id="4a688-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating the action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4a688-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4a688-108">Return Value</span></span>  
  
|<span data-ttu-id="4a688-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4a688-109">HRESULT</span></span>|<span data-ttu-id="4a688-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4a688-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4a688-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="4a688-111">S_OK</span></span>|<span data-ttu-id="4a688-112">`Wait`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="4a688-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="4a688-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4a688-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4a688-114">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="4a688-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4a688-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4a688-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4a688-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="4a688-116">The call timed out.</span></span>|  
|<span data-ttu-id="4a688-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4a688-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4a688-118">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="4a688-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4a688-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4a688-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4a688-120">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="4a688-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4a688-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4a688-121">E_FAIL</span></span>|<span data-ttu-id="4a688-122">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="4a688-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4a688-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4a688-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4a688-124">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="4a688-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4a688-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="4a688-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="4a688-126">Ana bilgisayar bekleme zaman aralığı boyunca Kilitlenme algılandı ve geçerli seçtiğiniz `IHostManualEvent` örneği kilitleme kurbanı olarak.</span><span class="sxs-lookup"><span data-stu-id="4a688-126">The host detected a deadlock during the wait interval, and chose the current `IHostManualEvent` instance as the deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4a688-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4a688-127">Requirements</span></span>  
 <span data-ttu-id="4a688-128">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a688-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a688-129">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4a688-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4a688-130">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="4a688-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4a688-131">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a688-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a688-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4a688-132">See Also</span></span>  
 [<span data-ttu-id="4a688-133">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4a688-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="4a688-134">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4a688-134">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="4a688-135">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4a688-135">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="4a688-136">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4a688-136">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="4a688-137">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4a688-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
