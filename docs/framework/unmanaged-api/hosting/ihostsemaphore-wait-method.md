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
ms.openlocfilehash: c1d578fa0f8e80ae2c8fbada9e383bcd849ff2f8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753616"
---
# <a name="ihostsemaphorewait-method"></a><span data-ttu-id="d9cf1-102">IHostSemaphore::Wait Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d9cf1-102">IHostSemaphore::Wait Method</span></span>
<span data-ttu-id="d9cf1-103">Geçerli neden [Ihostsemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) örneğin ait kadar bekleyin veya zaman geçtikçe belirtilen miktarı.</span><span class="sxs-lookup"><span data-stu-id="d9cf1-103">Causes the current [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) instance to wait until it is owned or the specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9cf1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d9cf1-104">Syntax</span></span>  
  
```cpp  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9cf1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d9cf1-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="d9cf1-106">[in] Göndermeden önce varsa milisaniye sayısını geçerli `IHostSemaphore` örneği ait değil.</span><span class="sxs-lookup"><span data-stu-id="d9cf1-106">[in] The number of milliseconds to wait before returning, if the current `IHostSemaphore` instance is not owned.</span></span>  
  
 `option`  
 <span data-ttu-id="d9cf1-107">[in] Aşağıdakilerden birini [waıt_optıon](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) değerleri, bu konak sürecektir hangi eylemin belirtme işlemi engeller.</span><span class="sxs-lookup"><span data-stu-id="d9cf1-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, specifying what action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9cf1-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d9cf1-108">Return Value</span></span>  
  
|<span data-ttu-id="d9cf1-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d9cf1-109">HRESULT</span></span>|<span data-ttu-id="d9cf1-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d9cf1-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d9cf1-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d9cf1-111">S_OK</span></span>|<span data-ttu-id="d9cf1-112">`Wait` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="d9cf1-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="d9cf1-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d9cf1-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d9cf1-114">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="d9cf1-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d9cf1-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d9cf1-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d9cf1-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="d9cf1-116">The call timed out.</span></span>|  
|<span data-ttu-id="d9cf1-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d9cf1-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d9cf1-118">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="d9cf1-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d9cf1-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d9cf1-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d9cf1-120">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="d9cf1-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d9cf1-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d9cf1-121">E_FAIL</span></span>|<span data-ttu-id="d9cf1-122">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="d9cf1-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d9cf1-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d9cf1-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d9cf1-124">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="d9cf1-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d9cf1-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="d9cf1-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="d9cf1-126">Konak bekleme zaman aralığı boyunca kilitlenme algıladı ve geçerli seçtiğiniz `IHostSemaphore` kilitlenme kurbanı olarak örneği.</span><span class="sxs-lookup"><span data-stu-id="d9cf1-126">The host detected a deadlock during the wait interval, and chose the current `IHostSemaphore` instance as a deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d9cf1-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d9cf1-127">Requirements</span></span>  
 <span data-ttu-id="d9cf1-128">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9cf1-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9cf1-129">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d9cf1-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d9cf1-130">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d9cf1-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d9cf1-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9cf1-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9cf1-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9cf1-132">See also</span></span>

- [<span data-ttu-id="d9cf1-133">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d9cf1-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="d9cf1-134">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d9cf1-134">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="d9cf1-135">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d9cf1-135">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="d9cf1-136">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d9cf1-136">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="d9cf1-137">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d9cf1-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
