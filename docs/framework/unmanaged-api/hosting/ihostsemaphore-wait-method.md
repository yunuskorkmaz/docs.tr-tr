---
title: IHostSemaphore::Wait Yöntemi
ms.date: 03/30/2017
api_name:
- IHostSemaphore.Wait
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSemaphore::Wait
helpviewer_keywords:
- IHostSemaphore::Wait method [.NET Framework hosting]
- Wait method, IHostSemaphore interface [.NET Framework hosting]
ms.assetid: 0da962a3-ce55-44dd-ab7a-14ad7105af4a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9933948a5e67b91106cdadc6f747c1b1c4121813
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57490001"
---
# <a name="ihostsemaphorewait-method"></a><span data-ttu-id="6a39a-102">IHostSemaphore::Wait Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6a39a-102">IHostSemaphore::Wait Method</span></span>
<span data-ttu-id="6a39a-103">Geçerli neden [Ihostsemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) örneğin ait kadar bekleyin veya zaman geçtikçe belirtilen miktarı.</span><span class="sxs-lookup"><span data-stu-id="6a39a-103">Causes the current [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) instance to wait until it is owned or the specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a39a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6a39a-104">Syntax</span></span>  
  
```  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a39a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6a39a-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="6a39a-106">[in] Göndermeden önce varsa milisaniye sayısını geçerli `IHostSemaphore` örneği ait değil.</span><span class="sxs-lookup"><span data-stu-id="6a39a-106">[in] The number of milliseconds to wait before returning, if the current `IHostSemaphore` instance is not owned.</span></span>  
  
 `option`  
 <span data-ttu-id="6a39a-107">[in] Aşağıdakilerden birini [waıt_optıon](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) değerleri, bu konak sürecektir hangi eylemin belirtme işlemi engeller.</span><span class="sxs-lookup"><span data-stu-id="6a39a-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, specifying what action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6a39a-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6a39a-108">Return Value</span></span>  
  
|<span data-ttu-id="6a39a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6a39a-109">HRESULT</span></span>|<span data-ttu-id="6a39a-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a39a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6a39a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="6a39a-111">S_OK</span></span>|<span data-ttu-id="6a39a-112">`Wait` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="6a39a-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="6a39a-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6a39a-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6a39a-114">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="6a39a-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6a39a-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6a39a-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6a39a-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="6a39a-116">The call timed out.</span></span>|  
|<span data-ttu-id="6a39a-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6a39a-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6a39a-118">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="6a39a-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6a39a-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6a39a-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6a39a-120">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="6a39a-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6a39a-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6a39a-121">E_FAIL</span></span>|<span data-ttu-id="6a39a-122">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="6a39a-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6a39a-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6a39a-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6a39a-124">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="6a39a-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6a39a-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="6a39a-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="6a39a-126">Konak bekleme zaman aralığı boyunca kilitlenme algıladı ve geçerli seçtiğiniz `IHostSemaphore` kilitlenme kurbanı olarak örneği.</span><span class="sxs-lookup"><span data-stu-id="6a39a-126">The host detected a deadlock during the wait interval, and chose the current `IHostSemaphore` instance as a deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6a39a-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6a39a-127">Requirements</span></span>  
 <span data-ttu-id="6a39a-128">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a39a-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a39a-129">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6a39a-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6a39a-130">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="6a39a-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6a39a-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a39a-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a39a-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a39a-132">See also</span></span>
- [<span data-ttu-id="6a39a-133">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6a39a-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="6a39a-134">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6a39a-134">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="6a39a-135">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6a39a-135">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="6a39a-136">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6a39a-136">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="6a39a-137">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6a39a-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
