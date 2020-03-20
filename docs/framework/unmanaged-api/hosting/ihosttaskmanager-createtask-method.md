---
title: IHostTaskManager::CreateTask Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTaskManager.CreateTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::CreateTask
helpviewer_keywords:
- CreateTask method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::CreateTask method [.NET Framework hosting]
ms.assetid: a6f8ad36-61e1-42b0-9db2-add575646d18
topic_type:
- apiref
ms.openlocfilehash: fef2f56fd000a8610a40661a30aa306ae5a7884e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177993"
---
# <a name="ihosttaskmanagercreatetask-method"></a><span data-ttu-id="0327c-102">IHostTaskManager::CreateTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0327c-102">IHostTaskManager::CreateTask Method</span></span>
<span data-ttu-id="0327c-103">Ana bilgisayaryeni bir görev oluşturmasını ister.</span><span class="sxs-lookup"><span data-stu-id="0327c-103">Requests that the host create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0327c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0327c-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateTask (  
    [in]  DWORD stacksize,
    [in]  LPTHREAD_START_ROUTINE pStartAddress,  
    [in]  PVOID pParameter,  
    [out] IHostTask **ppTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0327c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0327c-105">Parameters</span></span>  
 `stacksize`  
 <span data-ttu-id="0327c-106">[içinde] İstenen yığındaki istenen boyut, baytlar veya varsayılan boyut için 0 (sıfır).</span><span class="sxs-lookup"><span data-stu-id="0327c-106">[in] The requested size, in bytes, of the requested stack, or 0 (zero) for the default size.</span></span>  
  
 `pStartAddress`  
 <span data-ttu-id="0327c-107">[içinde] Görev in işlevi için bir işaretçi yürütmektir.</span><span class="sxs-lookup"><span data-stu-id="0327c-107">[in] A pointer to the function the task is to execute.</span></span>  
  
 `pParameter`  
 <span data-ttu-id="0327c-108">[içinde] İşleviçin geçirilecek kullanıcı verilerine işaretçi veya işlev parametre yoksa null.</span><span class="sxs-lookup"><span data-stu-id="0327c-108">[in] A pointer to the user data to be passed to the function, or null if the function takes no parameters.</span></span>  
  
 `ppTask`  
 <span data-ttu-id="0327c-109">[çıkış] Ana bilgisayar tarafından oluşturulan bir [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) örneğinin adresine işaretçi veya görev oluşturulamıyorsa geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="0327c-109">[out] A pointer to the address of an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance created by the host, or null if the task cannot be created.</span></span> <span data-ttu-id="0327c-110">Görev, Açıkça IHostTask için bir çağrı tarafından başlatılana kadar askıya alınmış durumda [kalır::Başlat.](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)</span><span class="sxs-lookup"><span data-stu-id="0327c-110">The task remains in a suspended state until it is explicitly started by a call to [IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0327c-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0327c-111">Return Value</span></span>  
  
|<span data-ttu-id="0327c-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0327c-112">HRESULT</span></span>|<span data-ttu-id="0327c-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0327c-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0327c-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="0327c-114">S_OK</span></span>|<span data-ttu-id="0327c-115">`CreateTask`başarıyla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="0327c-115">`CreateTask` returned successfully.</span></span>|  
|<span data-ttu-id="0327c-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0327c-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0327c-117">Ortak dil çalışma süresi (CLR) bir işleme yüklenmedi veya CLR yönetilen kodu çalıştıramadığı veya aramayı başarıyla işleyemediği bir durumdadır.</span><span class="sxs-lookup"><span data-stu-id="0327c-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0327c-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0327c-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0327c-119">Arama zaman doldu.</span><span class="sxs-lookup"><span data-stu-id="0327c-119">The call timed out.</span></span>|  
|<span data-ttu-id="0327c-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0327c-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0327c-121">Arayan kilidin sahibi değildir.</span><span class="sxs-lookup"><span data-stu-id="0327c-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0327c-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0327c-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0327c-123">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="0327c-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0327c-124">E_faıl</span><span class="sxs-lookup"><span data-stu-id="0327c-124">E_FAIL</span></span>|<span data-ttu-id="0327c-125">Bilinmeyen bir felaket hatası meydana geldi.</span><span class="sxs-lookup"><span data-stu-id="0327c-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0327c-126">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0327c-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0327c-127">Barındırma yöntemleri sonraki aramalar HOST_E_CLRNOTAVAILABLE döndürün.</span><span class="sxs-lookup"><span data-stu-id="0327c-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0327c-128">E_outofmemory</span><span class="sxs-lookup"><span data-stu-id="0327c-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="0327c-129">İstenen görevi oluşturmak için yeterli bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="0327c-129">Not enough memory was available to create the requested task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0327c-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0327c-130">Remarks</span></span>  
 <span data-ttu-id="0327c-131">CLR, `CreateTask` ana bilgisayaryeni bir görev oluşturmasını istemek için çağırır.</span><span class="sxs-lookup"><span data-stu-id="0327c-131">The CLR calls `CreateTask` to request that the host create a new task.</span></span> <span data-ttu-id="0327c-132">Ana bilgisayar, bir `IHostTask` örnek için bir arabirim işaretçisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="0327c-132">The host returns an interface pointer to an `IHostTask` instance.</span></span> <span data-ttu-id="0327c-133">Döndürülen görev, `IHostTask::Start`'' için yapılan bir çağrı tarafından açıkça başlatılana kadar askıya alınmalı</span><span class="sxs-lookup"><span data-stu-id="0327c-133">The returned task must remain suspended until it is explicitly started by a call to `IHostTask::Start`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0327c-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0327c-134">Requirements</span></span>  
 <span data-ttu-id="0327c-135">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0327c-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0327c-136">**Üstbilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0327c-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0327c-137">**Kütüphane:** MSCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="0327c-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0327c-138">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0327c-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0327c-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0327c-139">See also</span></span>

- [<span data-ttu-id="0327c-140">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0327c-140">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="0327c-141">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0327c-141">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="0327c-142">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0327c-142">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="0327c-143">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0327c-143">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
