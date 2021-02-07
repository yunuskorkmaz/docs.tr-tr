---
description: 'Şu konuda daha fazla bilgi edinin: ıhostsemafor:: wait yöntemi'
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
ms.openlocfilehash: 386f9806d6457f30d13e18e7d0d1ab16aafb84ee
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728450"
---
# <a name="ihostsemaphorewait-method"></a><span data-ttu-id="0dd6a-103">IHostSemaphore::Wait Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0dd6a-103">IHostSemaphore::Wait Method</span></span>

<span data-ttu-id="0dd6a-104">Geçerli [ıhostsemafor](ihostsemaphore-interface.md) örneğinin, kendisine ait olana veya belirtilen süre geçtikten sonra beklemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0dd6a-104">Causes the current [IHostSemaphore](ihostsemaphore-interface.md) instance to wait until it is owned or the specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0dd6a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0dd6a-105">Syntax</span></span>  
  
```cpp  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0dd6a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0dd6a-106">Parameters</span></span>  

 `dwMilliseconds`  
 <span data-ttu-id="0dd6a-107">'ndaki Geçerli örneğe ait değilse, döndürülmeden önce beklenecek milisaniye sayısı `IHostSemaphore` .</span><span class="sxs-lookup"><span data-stu-id="0dd6a-107">[in] The number of milliseconds to wait before returning, if the current `IHostSemaphore` instance is not owned.</span></span>  
  
 `option`  
 <span data-ttu-id="0dd6a-108">'ndaki Bu işlem engelliyorsa konağın yapması gereken eylemi belirten [WAIT_OPTION](wait-option-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="0dd6a-108">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values, specifying what action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0dd6a-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0dd6a-109">Return Value</span></span>  
  
|<span data-ttu-id="0dd6a-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0dd6a-110">HRESULT</span></span>|<span data-ttu-id="0dd6a-111">Description</span><span class="sxs-lookup"><span data-stu-id="0dd6a-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0dd6a-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="0dd6a-112">S_OK</span></span>|<span data-ttu-id="0dd6a-113">`Wait` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="0dd6a-113">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="0dd6a-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0dd6a-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0dd6a-115">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="0dd6a-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0dd6a-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0dd6a-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0dd6a-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="0dd6a-117">The call timed out.</span></span>|  
|<span data-ttu-id="0dd6a-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0dd6a-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0dd6a-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="0dd6a-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0dd6a-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0dd6a-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0dd6a-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="0dd6a-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0dd6a-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0dd6a-122">E_FAIL</span></span>|<span data-ttu-id="0dd6a-123">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="0dd6a-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0dd6a-124">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0dd6a-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0dd6a-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="0dd6a-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0dd6a-126">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="0dd6a-126">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="0dd6a-127">Ana bilgisayar bekleme aralığı sırasında bir kilitlenme algıladı ve geçerli `IHostSemaphore` örneği bir kilitlenme kurbanı olarak seçti.</span><span class="sxs-lookup"><span data-stu-id="0dd6a-127">The host detected a deadlock during the wait interval, and chose the current `IHostSemaphore` instance as a deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0dd6a-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0dd6a-128">Requirements</span></span>  

 <span data-ttu-id="0dd6a-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0dd6a-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0dd6a-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0dd6a-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0dd6a-131">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="0dd6a-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0dd6a-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0dd6a-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dd6a-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0dd6a-133">See also</span></span>

- [<span data-ttu-id="0dd6a-134">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0dd6a-134">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="0dd6a-135">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0dd6a-135">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="0dd6a-136">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0dd6a-136">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="0dd6a-137">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0dd6a-137">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="0dd6a-138">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0dd6a-138">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
