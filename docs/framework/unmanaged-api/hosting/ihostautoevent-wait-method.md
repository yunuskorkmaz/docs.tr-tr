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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b282ca35135fd16dceb92e6a0eeab15837d9b10d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57491457"
---
# <a name="ihostautoeventwait-method"></a><span data-ttu-id="d4bef-102">IHostAutoEvent::Wait Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d4bef-102">IHostAutoEvent::Wait Method</span></span>
<span data-ttu-id="d4bef-103">Geçerli neden [Ihostautoevent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) örneğin ait kadar bekleyin veya belirli bir zaman geçtikçe miktarını.</span><span class="sxs-lookup"><span data-stu-id="d4bef-103">Causes the current [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance to wait until it is owned or a specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4bef-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d4bef-104">Syntax</span></span>  
  
```  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4bef-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d4bef-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="d4bef-106">[in] Milisaniye olarak geçerli `IHostAutoEvent` örneği beklemesi göndermeden önce iş parçacığı, gereken veya fiber sahipliğini alır.</span><span class="sxs-lookup"><span data-stu-id="d4bef-106">[in] The number of milliseconds the current `IHostAutoEvent` instance should wait before returning, if no thread or fiber takes ownership.</span></span>  
  
 `option`  
 <span data-ttu-id="d4bef-107">[in] Aşağıdakilerden birini [waıt_optıon](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) değerleri, bu konak sürecektir eylem belirtme işlemi engeller.</span><span class="sxs-lookup"><span data-stu-id="d4bef-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, specifying the action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d4bef-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d4bef-108">Return Value</span></span>  
  
|<span data-ttu-id="d4bef-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d4bef-109">HRESULT</span></span>|<span data-ttu-id="d4bef-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d4bef-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d4bef-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d4bef-111">S_OK</span></span>|<span data-ttu-id="d4bef-112">`Wait` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="d4bef-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="d4bef-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d4bef-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d4bef-114">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="d4bef-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d4bef-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d4bef-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d4bef-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="d4bef-116">The call timed out.</span></span>|  
|<span data-ttu-id="d4bef-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d4bef-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d4bef-118">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="d4bef-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d4bef-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d4bef-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d4bef-120">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="d4bef-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d4bef-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d4bef-121">E_FAIL</span></span>|<span data-ttu-id="d4bef-122">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="d4bef-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d4bef-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d4bef-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d4bef-124">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="d4bef-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d4bef-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="d4bef-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="d4bef-126">Konak bekleme zaman aralığı boyunca kilitlenme algıladı ve geçerli tarafından temsil edilen olay seçtiğiniz `IHostAutoEvent` kilitlenme kurbanı olarak örneği.</span><span class="sxs-lookup"><span data-stu-id="d4bef-126">The host detected a deadlock during the wait interval, and chose the event represented by the current `IHostAutoEvent` instance as the deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d4bef-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d4bef-127">Requirements</span></span>  
 <span data-ttu-id="d4bef-128">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4bef-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4bef-129">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d4bef-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d4bef-130">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d4bef-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d4bef-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4bef-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4bef-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4bef-132">See also</span></span>
- [<span data-ttu-id="d4bef-133">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4bef-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="d4bef-134">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4bef-134">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="d4bef-135">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4bef-135">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="d4bef-136">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4bef-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
