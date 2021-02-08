---
description: 'Şu konuda daha fazla bilgi edinin: IHostAutoEvent:: wait yöntemi'
title: IHostAutoEvent::Wait Yöntemi
ms.date: 03/30/2017
api_name:
- IHostAutoEvent.Wait
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAutoEvent::Wait
helpviewer_keywords:
- Wait method, IHostAutoEvent interface [.NET Framework hosting]
- IHostAutoEvent::Wait method [.NET Framework hosting]
ms.assetid: 535d51c5-9112-401b-8c36-85f35d7ee609
topic_type:
- apiref
ms.openlocfilehash: 0b75b44075dda46a3d84850cebd6b8f3851b055c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789483"
---
# <a name="ihostautoeventwait-method"></a><span data-ttu-id="6664a-103">IHostAutoEvent::Wait Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6664a-103">IHostAutoEvent::Wait Method</span></span>

<span data-ttu-id="6664a-104">Geçerli [IHostAutoEvent](ihostautoevent-interface.md) örneğinin, ait olana veya belirtilen süre geçtikten sonra beklemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="6664a-104">Causes the current [IHostAutoEvent](ihostautoevent-interface.md) instance to wait until it is owned or a specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6664a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6664a-105">Syntax</span></span>  
  
```cpp  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6664a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6664a-106">Parameters</span></span>  

 `dwMilliseconds`  
 <span data-ttu-id="6664a-107">'ndaki `IHostAutoEvent` Hiçbir iş parçacığı veya fiber sahiplik alırsa, geçerli örneğin döndürülmeden önce beklemesi gereken milisaniye sayısı.</span><span class="sxs-lookup"><span data-stu-id="6664a-107">[in] The number of milliseconds the current `IHostAutoEvent` instance should wait before returning, if no thread or fiber takes ownership.</span></span>  
  
 `option`  
 <span data-ttu-id="6664a-108">'ndaki Bu işlem engelliyorsa konağın yapması gereken eylemi belirten [WAIT_OPTION](wait-option-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="6664a-108">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values, specifying the action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6664a-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6664a-109">Return Value</span></span>  
  
|<span data-ttu-id="6664a-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6664a-110">HRESULT</span></span>|<span data-ttu-id="6664a-111">Description</span><span class="sxs-lookup"><span data-stu-id="6664a-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6664a-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="6664a-112">S_OK</span></span>|<span data-ttu-id="6664a-113">`Wait` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="6664a-113">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="6664a-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6664a-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6664a-115">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="6664a-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6664a-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6664a-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6664a-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="6664a-117">The call timed out.</span></span>|  
|<span data-ttu-id="6664a-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6664a-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6664a-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="6664a-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6664a-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6664a-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6664a-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="6664a-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6664a-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6664a-122">E_FAIL</span></span>|<span data-ttu-id="6664a-123">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="6664a-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6664a-124">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6664a-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6664a-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="6664a-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6664a-126">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="6664a-126">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="6664a-127">Ana bilgisayar bekleme aralığı sırasında bir kilitlenme algıladı ve kilitlenme kurbanı olarak geçerli örnek tarafından temsil edilen olayı seçti `IHostAutoEvent` .</span><span class="sxs-lookup"><span data-stu-id="6664a-127">The host detected a deadlock during the wait interval, and chose the event represented by the current `IHostAutoEvent` instance as the deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6664a-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6664a-128">Requirements</span></span>  

 <span data-ttu-id="6664a-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6664a-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6664a-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6664a-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6664a-131">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="6664a-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6664a-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6664a-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6664a-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6664a-133">See also</span></span>

- [<span data-ttu-id="6664a-134">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6664a-134">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="6664a-135">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6664a-135">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="6664a-136">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6664a-136">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="6664a-137">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6664a-137">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
