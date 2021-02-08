---
description: ': IHostSyncManager:: CreateManualEvent yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 300d6cbf9555eb331a470767cdfb2745da300bb6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784801"
---
# <a name="ihostsyncmanagercreatemanualevent-method"></a><span data-ttu-id="20185-103">IHostSyncManager::CreateManualEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="20185-103">IHostSyncManager::CreateManualEvent Method</span></span>

<span data-ttu-id="20185-104">El ile sıfırlama olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="20185-104">Creates a manual-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20185-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="20185-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateManualEvent (  
    [in]  BOOL bInitialState,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20185-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="20185-106">Parameters</span></span>  

 `bInitialState`  
 <span data-ttu-id="20185-107">[in] `true` , nesne sinyalse, aksi durumda `false` .</span><span class="sxs-lookup"><span data-stu-id="20185-107">[in] `true`, if the object is signaled; otherwise, `false`.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="20185-108">dışı Bir [IHostManualEvent](ihostmanualevent-interface.md) örneğinin adresine yönelik bir işaretçi ya da olay oluşturuoluşturulamadığı takdirde null.</span><span class="sxs-lookup"><span data-stu-id="20185-108">[out] A pointer to the address of an [IHostManualEvent](ihostmanualevent-interface.md) instance, or null if the event could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="20185-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="20185-109">Return Value</span></span>  
  
|<span data-ttu-id="20185-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="20185-110">HRESULT</span></span>|<span data-ttu-id="20185-111">Description</span><span class="sxs-lookup"><span data-stu-id="20185-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="20185-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="20185-112">S_OK</span></span>|<span data-ttu-id="20185-113">`CreateManualEvent` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="20185-113">`CreateManualEvent` returned successfully.</span></span>|  
|<span data-ttu-id="20185-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="20185-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="20185-115">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="20185-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="20185-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="20185-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="20185-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="20185-117">The call timed out.</span></span>|  
|<span data-ttu-id="20185-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="20185-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="20185-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="20185-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="20185-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="20185-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="20185-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="20185-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="20185-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="20185-122">E_FAIL</span></span>|<span data-ttu-id="20185-123">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="20185-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="20185-124">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="20185-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="20185-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="20185-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="20185-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="20185-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="20185-127">İstenen olay nesnesini oluşturmak için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="20185-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20185-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="20185-128">Remarks</span></span>  

 <span data-ttu-id="20185-129">`CreateManualEvent``IHostManualEvent` [IHostManualEvent:: Reset](ihostmanualevent-reset-method.md) yöntemine çağrı gerektiren, sinyal olmayan bir duruma ayarlamak için bir el ile sıfırlama olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="20185-129">`CreateManualEvent` creates an `IHostManualEvent`, a manual-reset event object that requires a call to the [IHostManualEvent::Reset](ihostmanualevent-reset-method.md) method to set it to a non-signaled state.</span></span> <span data-ttu-id="20185-130">`CreateManualEvent``CreateEvent`parametresi için belirtilen bir değere sahip Win32 işlevini yansıtır `true` `bManualReset` .</span><span class="sxs-lookup"><span data-stu-id="20185-130">`CreateManualEvent` mirrors the Win32 `CreateEvent` function with a value of `true` specified for the `bManualReset` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20185-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="20185-131">Requirements</span></span>  

 <span data-ttu-id="20185-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20185-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20185-133">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="20185-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="20185-134">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="20185-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="20185-135">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20185-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20185-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="20185-136">See also</span></span>

- [<span data-ttu-id="20185-137">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="20185-137">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="20185-138">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="20185-138">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="20185-139">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="20185-139">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
