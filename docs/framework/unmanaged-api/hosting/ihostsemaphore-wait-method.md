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
ms.openlocfilehash: bf09f7bc6c3e3aabfc16f9cad277c46be024b01d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139457"
---
# <a name="ihostsemaphorewait-method"></a><span data-ttu-id="aedc7-102">IHostSemaphore::Wait Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aedc7-102">IHostSemaphore::Wait Method</span></span>
<span data-ttu-id="aedc7-103">Geçerli [ıhostsemafor](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) örneğinin, kendisine ait olana veya belirtilen süre geçtikten sonra beklemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="aedc7-103">Causes the current [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) instance to wait until it is owned or the specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aedc7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aedc7-104">Syntax</span></span>  
  
```cpp  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aedc7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="aedc7-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="aedc7-106">'ndaki Geçerli `IHostSemaphore` örneği ait değilse, döndürülmeden önce beklenecek milisaniye sayısı.</span><span class="sxs-lookup"><span data-stu-id="aedc7-106">[in] The number of milliseconds to wait before returning, if the current `IHostSemaphore` instance is not owned.</span></span>  
  
 `option`  
 <span data-ttu-id="aedc7-107">'ndaki Bu işlem engelliyorsa konağın yapması gereken eylemi belirten [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="aedc7-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, specifying what action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aedc7-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="aedc7-108">Return Value</span></span>  
  
|<span data-ttu-id="aedc7-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aedc7-109">HRESULT</span></span>|<span data-ttu-id="aedc7-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aedc7-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aedc7-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="aedc7-111">S_OK</span></span>|<span data-ttu-id="aedc7-112">`Wait` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="aedc7-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="aedc7-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="aedc7-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="aedc7-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="aedc7-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="aedc7-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="aedc7-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="aedc7-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="aedc7-116">The call timed out.</span></span>|  
|<span data-ttu-id="aedc7-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="aedc7-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="aedc7-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="aedc7-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="aedc7-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="aedc7-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="aedc7-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="aedc7-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="aedc7-121">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="aedc7-121">E_FAIL</span></span>|<span data-ttu-id="aedc7-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="aedc7-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="aedc7-123">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="aedc7-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="aedc7-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="aedc7-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="aedc7-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="aedc7-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="aedc7-126">Ana bilgisayar bekleme aralığı sırasında bir kilitlenme algıladı ve geçerli `IHostSemaphore` örneğini bir kilitlenme kurbanı olarak seçti.</span><span class="sxs-lookup"><span data-stu-id="aedc7-126">The host detected a deadlock during the wait interval, and chose the current `IHostSemaphore` instance as a deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="aedc7-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aedc7-127">Requirements</span></span>  
 <span data-ttu-id="aedc7-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aedc7-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aedc7-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="aedc7-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aedc7-130">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="aedc7-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aedc7-131">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aedc7-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aedc7-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aedc7-132">See also</span></span>

- [<span data-ttu-id="aedc7-133">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aedc7-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="aedc7-134">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aedc7-134">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="aedc7-135">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aedc7-135">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="aedc7-136">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aedc7-136">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="aedc7-137">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aedc7-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
