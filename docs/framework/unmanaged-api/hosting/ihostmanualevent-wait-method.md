---
title: IHostManualEvent::Wait Yöntemi
ms.date: 03/30/2017
api_name:
- IHostManualEvent.Wait
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent::Wait
helpviewer_keywords:
- IHostManualEvent::Wait method [.NET Framework hosting]
- Wait method, IHostManualEvent interface [.NET Framework hosting]
ms.assetid: 1fbb7d8b-8a23-4c2b-8376-1a70cd2d6030
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2242395a02254268c9492e534309c690a343ffbe
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767269"
---
# <a name="ihostmanualeventwait-method"></a><span data-ttu-id="ca76d-102">IHostManualEvent::Wait Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ca76d-102">IHostManualEvent::Wait Method</span></span>
<span data-ttu-id="ca76d-103">Geçerli neden [Ihostmanualevent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) ait kadar beklenecek örneği veya belirli bir zaman geçtikçe miktarını.</span><span class="sxs-lookup"><span data-stu-id="ca76d-103">Causes the current [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance to wait until it is owned, or a specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca76d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ca76d-104">Syntax</span></span>  
  
```cpp  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca76d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ca76d-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="ca76d-106">[in] Göndermeden önce varsa milisaniye sayısını geçerli `IHostManualEvent` örneği ait değil.</span><span class="sxs-lookup"><span data-stu-id="ca76d-106">[in] The number of milliseconds to wait before returning, if the current `IHostManualEvent` instance is not owned.</span></span>  
  
 `option`  
 <span data-ttu-id="ca76d-107">[in] Birini [waıt_optıon](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) bu konak sürecektir eylemini belirten değerleri, işlem engeller.</span><span class="sxs-lookup"><span data-stu-id="ca76d-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating the action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ca76d-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ca76d-108">Return Value</span></span>  
  
|<span data-ttu-id="ca76d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ca76d-109">HRESULT</span></span>|<span data-ttu-id="ca76d-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ca76d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ca76d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ca76d-111">S_OK</span></span>|<span data-ttu-id="ca76d-112">`Wait` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="ca76d-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="ca76d-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ca76d-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ca76d-114">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="ca76d-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ca76d-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ca76d-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ca76d-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="ca76d-116">The call timed out.</span></span>|  
|<span data-ttu-id="ca76d-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ca76d-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ca76d-118">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="ca76d-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ca76d-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ca76d-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ca76d-120">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="ca76d-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ca76d-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ca76d-121">E_FAIL</span></span>|<span data-ttu-id="ca76d-122">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="ca76d-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ca76d-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ca76d-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ca76d-124">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="ca76d-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ca76d-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="ca76d-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="ca76d-126">Konak bekleme zaman aralığı boyunca kilitlenme algıladı ve geçerli seçtiğiniz `IHostManualEvent` kilitlenme kurbanı olarak örneği.</span><span class="sxs-lookup"><span data-stu-id="ca76d-126">The host detected a deadlock during the wait interval, and chose the current `IHostManualEvent` instance as the deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ca76d-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ca76d-127">Requirements</span></span>  
 <span data-ttu-id="ca76d-128">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca76d-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca76d-129">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ca76d-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ca76d-130">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="ca76d-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ca76d-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca76d-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca76d-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca76d-132">See also</span></span>

- [<span data-ttu-id="ca76d-133">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ca76d-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="ca76d-134">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ca76d-134">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="ca76d-135">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ca76d-135">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="ca76d-136">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ca76d-136">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="ca76d-137">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ca76d-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
