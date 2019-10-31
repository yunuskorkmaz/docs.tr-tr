---
title: IHostSyncManager::CreateManualEvent Yöntemi
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateManualEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateManualEvent
helpviewer_keywords:
- CreateManualEvent method [.NET Framework hosting]
- IHostSyncManager::CreateManualEvent method [.NET Framework hosting]
ms.assetid: 68661fbd-09cf-46dc-890b-e694f8a3880a
topic_type:
- apiref
ms.openlocfilehash: 13679b4d40e660dfdd18e6fbafe19226b2ffda37
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195865"
---
# <a name="ihostsyncmanagercreatemanualevent-method"></a><span data-ttu-id="0f64d-102">IHostSyncManager::CreateManualEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f64d-102">IHostSyncManager::CreateManualEvent Method</span></span>
<span data-ttu-id="0f64d-103">El ile sıfırlama olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0f64d-103">Creates a manual-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f64d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0f64d-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateManualEvent (  
    [in]  BOOL bInitialState,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f64d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0f64d-105">Parameters</span></span>  
 `bInitialState`  
 <span data-ttu-id="0f64d-106">[in] `true`, nesne sinyalde varsa; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="0f64d-106">[in] `true`, if the object is signaled; otherwise, `false`.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="0f64d-107">dışı Bir [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) örneğinin adresine yönelik bir işaretçi ya da olay oluşturuoluşturulamadığı takdirde null.</span><span class="sxs-lookup"><span data-stu-id="0f64d-107">[out] A pointer to the address of an [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance, or null if the event could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f64d-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0f64d-108">Return Value</span></span>  
  
|<span data-ttu-id="0f64d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0f64d-109">HRESULT</span></span>|<span data-ttu-id="0f64d-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0f64d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0f64d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="0f64d-111">S_OK</span></span>|<span data-ttu-id="0f64d-112">`CreateManualEvent` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="0f64d-112">`CreateManualEvent` returned successfully.</span></span>|  
|<span data-ttu-id="0f64d-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0f64d-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0f64d-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="0f64d-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0f64d-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0f64d-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0f64d-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="0f64d-116">The call timed out.</span></span>|  
|<span data-ttu-id="0f64d-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0f64d-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0f64d-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="0f64d-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0f64d-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0f64d-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0f64d-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="0f64d-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0f64d-121">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="0f64d-121">E_FAIL</span></span>|<span data-ttu-id="0f64d-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="0f64d-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0f64d-123">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0f64d-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0f64d-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="0f64d-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0f64d-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="0f64d-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="0f64d-126">İstenen olay nesnesini oluşturmak için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="0f64d-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f64d-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0f64d-127">Remarks</span></span>  
 <span data-ttu-id="0f64d-128">`CreateManualEvent`, [IHostManualEvent:: Reset](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md) yöntemine çağrı gerektiren ve sinyal olmayan bir duruma ayarlamak için el ile sıfırlama olay nesnesi olan bir `IHostManualEvent`oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0f64d-128">`CreateManualEvent` creates an `IHostManualEvent`, a manual-reset event object that requires a call to the [IHostManualEvent::Reset](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md) method to set it to a non-signaled state.</span></span> <span data-ttu-id="0f64d-129">`CreateManualEvent`, Win32 `CreateEvent` işlevini `bManualReset` parametresi için belirtilen `true` değeriyle yansıtır.</span><span class="sxs-lookup"><span data-stu-id="0f64d-129">`CreateManualEvent` mirrors the Win32 `CreateEvent` function with a value of `true` specified for the `bManualReset` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f64d-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0f64d-130">Requirements</span></span>  
 <span data-ttu-id="0f64d-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f64d-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f64d-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0f64d-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0f64d-133">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="0f64d-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0f64d-134">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f64d-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f64d-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f64d-135">See also</span></span>

- [<span data-ttu-id="0f64d-136">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0f64d-136">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="0f64d-137">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0f64d-137">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="0f64d-138">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0f64d-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
