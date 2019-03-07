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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 93deb2d0457fef6f190d90cc4084b9bb5997680d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57488493"
---
# <a name="ihosttaskmanagercreatetask-method"></a><span data-ttu-id="887d7-102">IHostTaskManager::CreateTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="887d7-102">IHostTaskManager::CreateTask Method</span></span>
<span data-ttu-id="887d7-103">İstek ana bilgisayar yeni bir görev oluşturun.</span><span class="sxs-lookup"><span data-stu-id="887d7-103">Requests that the host create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="887d7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="887d7-104">Syntax</span></span>  
  
```  
HRESULT CreateTask (  
    [in]  DWORD stacksize,   
    [in]  LPTHREAD_START_ROUTINE pStartAddress,  
    [in]  PVOID pParameter,  
    [out] IHostTask **ppTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="887d7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="887d7-105">Parameters</span></span>  
 `stacksize`  
 <span data-ttu-id="887d7-106">[in] İstenen bayt boyutu, istenen yığın ya da varsayılan boyutu 0 (sıfır).</span><span class="sxs-lookup"><span data-stu-id="887d7-106">[in] The requested size, in bytes, of the requested stack, or 0 (zero) for the default size.</span></span>  
  
 `pStartAddress`  
 <span data-ttu-id="887d7-107">[in] İşlev işaretçisi yürütülecek görevdir.</span><span class="sxs-lookup"><span data-stu-id="887d7-107">[in] A pointer to the function the task is to execute.</span></span>  
  
 `pParameter`  
 <span data-ttu-id="887d7-108">[in] İşlev veya null ise, işlev geçirilecek kullanıcı verileri için bir işaretçi herhangi bir parametre alır.</span><span class="sxs-lookup"><span data-stu-id="887d7-108">[in] A pointer to the user data to be passed to the function, or null if the function takes no parameters.</span></span>  
  
 `ppTask`  
 <span data-ttu-id="887d7-109">[out] Adresine bir işaretçi bir [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) görev oluşturduysanız konak veya null tarafından oluşturulan örneği.</span><span class="sxs-lookup"><span data-stu-id="887d7-109">[out] A pointer to the address of an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance created by the host, or null if the task cannot be created.</span></span> <span data-ttu-id="887d7-110">Açıkça bir çağrı tarafından başlatılana kadar görev askıya alınmış durumda kalır [Ihosttask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="887d7-110">The task remains in a suspended state until it is explicitly started by a call to [IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="887d7-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="887d7-111">Return Value</span></span>  
  
|<span data-ttu-id="887d7-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="887d7-112">HRESULT</span></span>|<span data-ttu-id="887d7-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="887d7-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="887d7-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="887d7-114">S_OK</span></span>|<span data-ttu-id="887d7-115">`CreateTask` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="887d7-115">`CreateTask` returned successfully.</span></span>|  
|<span data-ttu-id="887d7-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="887d7-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="887d7-117">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="887d7-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="887d7-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="887d7-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="887d7-119">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="887d7-119">The call timed out.</span></span>|  
|<span data-ttu-id="887d7-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="887d7-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="887d7-121">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="887d7-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="887d7-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="887d7-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="887d7-123">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="887d7-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="887d7-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="887d7-124">E_FAIL</span></span>|<span data-ttu-id="887d7-125">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="887d7-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="887d7-126">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="887d7-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="887d7-127">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="887d7-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="887d7-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="887d7-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="887d7-129">İstenen görevi oluşturmak yeterli bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="887d7-129">Not enough memory was available to create the requested task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="887d7-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="887d7-130">Remarks</span></span>  
 <span data-ttu-id="887d7-131">CLR çağrıları `CreateTask` ana bilgisayar yeni bir görev oluşturma istemek için.</span><span class="sxs-lookup"><span data-stu-id="887d7-131">The CLR calls `CreateTask` to request that the host create a new task.</span></span> <span data-ttu-id="887d7-132">Konak için bir arabirim işaretçisini döndürür bir `IHostTask` örneği.</span><span class="sxs-lookup"><span data-stu-id="887d7-132">The host returns an interface pointer to an `IHostTask` instance.</span></span> <span data-ttu-id="887d7-133">Açıkça bir çağrı tarafından başlatılana kadar döndürülen görevin askıda kalması gereken `IHostTask::Start`.</span><span class="sxs-lookup"><span data-stu-id="887d7-133">The returned task must remain suspended until it is explicitly started by a call to `IHostTask::Start`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="887d7-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="887d7-134">Requirements</span></span>  
 <span data-ttu-id="887d7-135">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="887d7-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="887d7-136">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="887d7-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="887d7-137">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="887d7-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="887d7-138">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="887d7-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="887d7-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="887d7-139">See also</span></span>
- [<span data-ttu-id="887d7-140">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="887d7-140">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="887d7-141">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="887d7-141">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="887d7-142">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="887d7-142">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="887d7-143">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="887d7-143">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
