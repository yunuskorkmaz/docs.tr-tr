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
ms.openlocfilehash: 3fe8434ba4a7fc49b99bdf3084ce4f3981f25a9b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719833"
---
# <a name="ihostmanualeventwait-method"></a><span data-ttu-id="8cecc-102">IHostManualEvent::Wait Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8cecc-102">IHostManualEvent::Wait Method</span></span>

<span data-ttu-id="8cecc-103">Geçerli [IHostManualEvent](ihostmanualevent-interface.md) örneğinin, ait olana veya belirli bir süre geçtikten sonra beklemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="8cecc-103">Causes the current [IHostManualEvent](ihostmanualevent-interface.md) instance to wait until it is owned, or a specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cecc-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="8cecc-104">Syntax</span></span>  
  
```cpp  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8cecc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8cecc-105">Parameters</span></span>  

 `dwMilliseconds`  
 <span data-ttu-id="8cecc-106">'ndaki Geçerli örneğe ait değilse, döndürülmeden önce beklenecek milisaniye sayısı `IHostManualEvent` .</span><span class="sxs-lookup"><span data-stu-id="8cecc-106">[in] The number of milliseconds to wait before returning, if the current `IHostManualEvent` instance is not owned.</span></span>  
  
 `option`  
 <span data-ttu-id="8cecc-107">'ndaki Bu işlem engelliyorsa konağın yapması gereken eylemi belirten [WAIT_OPTION](wait-option-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="8cecc-107">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values, indicating the action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8cecc-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8cecc-108">Return Value</span></span>  
  
|<span data-ttu-id="8cecc-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8cecc-109">HRESULT</span></span>|<span data-ttu-id="8cecc-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8cecc-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8cecc-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="8cecc-111">S_OK</span></span>|<span data-ttu-id="8cecc-112">`Wait` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="8cecc-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="8cecc-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8cecc-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8cecc-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="8cecc-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8cecc-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8cecc-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8cecc-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="8cecc-116">The call timed out.</span></span>|  
|<span data-ttu-id="8cecc-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8cecc-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8cecc-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="8cecc-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8cecc-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8cecc-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8cecc-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="8cecc-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8cecc-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8cecc-121">E_FAIL</span></span>|<span data-ttu-id="8cecc-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="8cecc-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8cecc-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="8cecc-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8cecc-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="8cecc-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8cecc-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="8cecc-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="8cecc-126">Ana bilgisayar bekleme aralığı sırasında bir kilitlenme algıladı ve `IHostManualEvent` kilitlenme kurbanı olarak geçerli örneği seçti.</span><span class="sxs-lookup"><span data-stu-id="8cecc-126">The host detected a deadlock during the wait interval, and chose the current `IHostManualEvent` instance as the deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8cecc-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8cecc-127">Requirements</span></span>  

 <span data-ttu-id="8cecc-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8cecc-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8cecc-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8cecc-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8cecc-130">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="8cecc-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8cecc-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cecc-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cecc-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8cecc-132">See also</span></span>

- [<span data-ttu-id="8cecc-133">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8cecc-133">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="8cecc-134">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8cecc-134">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="8cecc-135">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8cecc-135">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="8cecc-136">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8cecc-136">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="8cecc-137">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8cecc-137">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
