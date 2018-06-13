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
ms.openlocfilehash: 8d87243da4d68eb1ec12fda7aa62a5c4006b9729
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440431"
---
# <a name="ihostsemaphorewait-method"></a><span data-ttu-id="6ff36-102">IHostSemaphore::Wait Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6ff36-102">IHostSemaphore::Wait Method</span></span>
<span data-ttu-id="6ff36-103">Geçerli neden [Ihostsemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) örneği ait kadar bekleyin veya geçtiğinde belirtilen miktarı.</span><span class="sxs-lookup"><span data-stu-id="6ff36-103">Causes the current [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) instance to wait until it is owned or the specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ff36-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6ff36-104">Syntax</span></span>  
  
```  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6ff36-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6ff36-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="6ff36-106">[in] Varsa döndürmeden önce beklenmesi gereken milisaniye sayısını geçerli `IHostSemaphore` örneği ait değil.</span><span class="sxs-lookup"><span data-stu-id="6ff36-106">[in] The number of milliseconds to wait before returning, if the current `IHostSemaphore` instance is not owned.</span></span>  
  
 `option`  
 <span data-ttu-id="6ff36-107">[in] Aşağıdakilerden birini [waıt_optıon](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) değerleri, bu konak almalıdır hangi eylemini belirten işlemi engeller.</span><span class="sxs-lookup"><span data-stu-id="6ff36-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, specifying what action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6ff36-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6ff36-108">Return Value</span></span>  
  
|<span data-ttu-id="6ff36-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6ff36-109">HRESULT</span></span>|<span data-ttu-id="6ff36-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6ff36-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6ff36-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="6ff36-111">S_OK</span></span>|<span data-ttu-id="6ff36-112">`Wait` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="6ff36-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="6ff36-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6ff36-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6ff36-114">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="6ff36-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6ff36-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6ff36-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6ff36-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="6ff36-116">The call timed out.</span></span>|  
|<span data-ttu-id="6ff36-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6ff36-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6ff36-118">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="6ff36-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6ff36-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6ff36-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6ff36-120">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="6ff36-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6ff36-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6ff36-121">E_FAIL</span></span>|<span data-ttu-id="6ff36-122">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="6ff36-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6ff36-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6ff36-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6ff36-124">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="6ff36-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6ff36-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="6ff36-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="6ff36-126">Ana bilgisayar bekleme zaman aralığı boyunca Kilitlenme algılandı ve geçerli seçtiğiniz `IHostSemaphore` örneği kilitlenme kurbanı olarak.</span><span class="sxs-lookup"><span data-stu-id="6ff36-126">The host detected a deadlock during the wait interval, and chose the current `IHostSemaphore` instance as a deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6ff36-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6ff36-127">Requirements</span></span>  
 <span data-ttu-id="6ff36-128">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ff36-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ff36-129">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6ff36-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6ff36-130">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="6ff36-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6ff36-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ff36-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ff36-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6ff36-132">See Also</span></span>  
 [<span data-ttu-id="6ff36-133">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6ff36-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="6ff36-134">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6ff36-134">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="6ff36-135">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6ff36-135">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="6ff36-136">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6ff36-136">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="6ff36-137">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6ff36-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
