---
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
ms.openlocfilehash: f07958a1a21bb3e93e4ca8202a65407b39188af4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680787"
---
# <a name="ihostautoeventwait-method"></a><span data-ttu-id="d9cdb-102">IHostAutoEvent::Wait Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d9cdb-102">IHostAutoEvent::Wait Method</span></span>

<span data-ttu-id="d9cdb-103">Geçerli [IHostAutoEvent](ihostautoevent-interface.md) örneğinin, ait olana veya belirtilen süre geçtikten sonra beklemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d9cdb-103">Causes the current [IHostAutoEvent](ihostautoevent-interface.md) instance to wait until it is owned or a specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9cdb-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="d9cdb-104">Syntax</span></span>  
  
```cpp  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9cdb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d9cdb-105">Parameters</span></span>  

 `dwMilliseconds`  
 <span data-ttu-id="d9cdb-106">'ndaki `IHostAutoEvent` Hiçbir iş parçacığı veya fiber sahiplik alırsa, geçerli örneğin döndürülmeden önce beklemesi gereken milisaniye sayısı.</span><span class="sxs-lookup"><span data-stu-id="d9cdb-106">[in] The number of milliseconds the current `IHostAutoEvent` instance should wait before returning, if no thread or fiber takes ownership.</span></span>  
  
 `option`  
 <span data-ttu-id="d9cdb-107">'ndaki Bu işlem engelliyorsa konağın yapması gereken eylemi belirten [WAIT_OPTION](wait-option-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="d9cdb-107">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values, specifying the action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9cdb-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d9cdb-108">Return Value</span></span>  
  
|<span data-ttu-id="d9cdb-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d9cdb-109">HRESULT</span></span>|<span data-ttu-id="d9cdb-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d9cdb-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d9cdb-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d9cdb-111">S_OK</span></span>|<span data-ttu-id="d9cdb-112">`Wait` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="d9cdb-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="d9cdb-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d9cdb-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d9cdb-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="d9cdb-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d9cdb-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d9cdb-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d9cdb-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="d9cdb-116">The call timed out.</span></span>|  
|<span data-ttu-id="d9cdb-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d9cdb-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d9cdb-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="d9cdb-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d9cdb-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d9cdb-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d9cdb-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="d9cdb-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d9cdb-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d9cdb-121">E_FAIL</span></span>|<span data-ttu-id="d9cdb-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="d9cdb-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d9cdb-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d9cdb-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d9cdb-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="d9cdb-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d9cdb-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="d9cdb-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="d9cdb-126">Ana bilgisayar bekleme aralığı sırasında bir kilitlenme algıladı ve kilitlenme kurbanı olarak geçerli örnek tarafından temsil edilen olayı seçti `IHostAutoEvent` .</span><span class="sxs-lookup"><span data-stu-id="d9cdb-126">The host detected a deadlock during the wait interval, and chose the event represented by the current `IHostAutoEvent` instance as the deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d9cdb-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d9cdb-127">Requirements</span></span>  

 <span data-ttu-id="d9cdb-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9cdb-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9cdb-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d9cdb-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d9cdb-130">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="d9cdb-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d9cdb-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9cdb-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9cdb-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9cdb-132">See also</span></span>

- [<span data-ttu-id="d9cdb-133">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d9cdb-133">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="d9cdb-134">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d9cdb-134">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="d9cdb-135">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d9cdb-135">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="d9cdb-136">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d9cdb-136">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
