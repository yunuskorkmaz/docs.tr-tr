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
ms.openlocfilehash: 0258999bae8b04ddaccf264276d1439b027b4a43
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195897"
---
# <a name="ihostautoeventwait-method"></a><span data-ttu-id="229ff-102">IHostAutoEvent::Wait Yöntemi</span><span class="sxs-lookup"><span data-stu-id="229ff-102">IHostAutoEvent::Wait Method</span></span>
<span data-ttu-id="229ff-103">Geçerli [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) örneğinin, ait olana veya belirtilen süre geçtikten sonra beklemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="229ff-103">Causes the current [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance to wait until it is owned or a specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="229ff-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="229ff-104">Syntax</span></span>  
  
```cpp  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="229ff-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="229ff-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="229ff-106">'ndaki Hiçbir iş parçacığı veya fiber sahiplik alırsa geçerli `IHostAutoEvent` örneğinin döndürmeden önce beklemesi gereken milisaniye sayısı.</span><span class="sxs-lookup"><span data-stu-id="229ff-106">[in] The number of milliseconds the current `IHostAutoEvent` instance should wait before returning, if no thread or fiber takes ownership.</span></span>  
  
 `option`  
 <span data-ttu-id="229ff-107">'ndaki Bu işlem engelliyorsa konağın yapması gereken eylemi belirten [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="229ff-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, specifying the action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="229ff-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="229ff-108">Return Value</span></span>  
  
|<span data-ttu-id="229ff-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="229ff-109">HRESULT</span></span>|<span data-ttu-id="229ff-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="229ff-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="229ff-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="229ff-111">S_OK</span></span>|<span data-ttu-id="229ff-112">`Wait` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="229ff-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="229ff-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="229ff-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="229ff-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="229ff-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="229ff-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="229ff-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="229ff-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="229ff-116">The call timed out.</span></span>|  
|<span data-ttu-id="229ff-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="229ff-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="229ff-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="229ff-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="229ff-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="229ff-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="229ff-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="229ff-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="229ff-121">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="229ff-121">E_FAIL</span></span>|<span data-ttu-id="229ff-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="229ff-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="229ff-123">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="229ff-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="229ff-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="229ff-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="229ff-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="229ff-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="229ff-126">Ana bilgisayar bekleme aralığı sırasında bir kilitlenme algıladı ve geçerli `IHostAutoEvent` örneği tarafından temsil edilen olayı kilitlenme kurbanı olarak seçti.</span><span class="sxs-lookup"><span data-stu-id="229ff-126">The host detected a deadlock during the wait interval, and chose the event represented by the current `IHostAutoEvent` instance as the deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="229ff-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="229ff-127">Requirements</span></span>  
 <span data-ttu-id="229ff-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="229ff-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="229ff-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="229ff-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="229ff-130">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="229ff-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="229ff-131">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="229ff-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="229ff-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="229ff-132">See also</span></span>

- [<span data-ttu-id="229ff-133">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="229ff-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="229ff-134">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="229ff-134">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="229ff-135">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="229ff-135">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="229ff-136">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="229ff-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
