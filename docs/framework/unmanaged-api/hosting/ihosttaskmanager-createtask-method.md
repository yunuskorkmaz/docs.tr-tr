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
ms.openlocfilehash: 0cb539d5b10c8a027a8c73c68ccc04aa490cb4df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443173"
---
# <a name="ihosttaskmanagercreatetask-method"></a><span data-ttu-id="dc1ae-102">IHostTaskManager::CreateTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dc1ae-102">IHostTaskManager::CreateTask Method</span></span>
<span data-ttu-id="dc1ae-103">İstekleri ana bilgisayar yeni bir görev oluşturun.</span><span class="sxs-lookup"><span data-stu-id="dc1ae-103">Requests that the host create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc1ae-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dc1ae-104">Syntax</span></span>  
  
```  
HRESULT CreateTask (  
    [in]  DWORD stacksize,   
    [in]  LPTHREAD_START_ROUTINE pStartAddress,  
    [in]  PVOID pParameter,  
    [out] IHostTask **ppTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dc1ae-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dc1ae-105">Parameters</span></span>  
 `stacksize`  
 <span data-ttu-id="dc1ae-106">[in] İstenen yığını ya da 0 (sıfır) için varsayılan boyutunu bayt istenen boyutu.</span><span class="sxs-lookup"><span data-stu-id="dc1ae-106">[in] The requested size, in bytes, of the requested stack, or 0 (zero) for the default size.</span></span>  
  
 `pStartAddress`  
 <span data-ttu-id="dc1ae-107">[in] İşlev işaretçisi çalıştırılacak bir görevdir.</span><span class="sxs-lookup"><span data-stu-id="dc1ae-107">[in] A pointer to the function the task is to execute.</span></span>  
  
 `pParameter`  
 <span data-ttu-id="dc1ae-108">[in] İşlev veya null ise işlevi geçirilecek kullanıcı verileri için bir işaretçi parametre almaz.</span><span class="sxs-lookup"><span data-stu-id="dc1ae-108">[in] A pointer to the user data to be passed to the function, or null if the function takes no parameters.</span></span>  
  
 `ppTask`  
 <span data-ttu-id="dc1ae-109">[out] Adresine bir işaretçi bir [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) görev oluşturduysanız ana bilgisayar veya null tarafından oluşturulan örneği.</span><span class="sxs-lookup"><span data-stu-id="dc1ae-109">[out] A pointer to the address of an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance created by the host, or null if the task cannot be created.</span></span> <span data-ttu-id="dc1ae-110">Açıkça bir çağrı tarafından başlatılana kadar görev askıya alınmış durumda kalır [Ihosttask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="dc1ae-110">The task remains in a suspended state until it is explicitly started by a call to [IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dc1ae-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="dc1ae-111">Return Value</span></span>  
  
|<span data-ttu-id="dc1ae-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dc1ae-112">HRESULT</span></span>|<span data-ttu-id="dc1ae-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dc1ae-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dc1ae-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="dc1ae-114">S_OK</span></span>|<span data-ttu-id="dc1ae-115">`CreateTask` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="dc1ae-115">`CreateTask` returned successfully.</span></span>|  
|<span data-ttu-id="dc1ae-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dc1ae-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dc1ae-117">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="dc1ae-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dc1ae-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dc1ae-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dc1ae-119">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="dc1ae-119">The call timed out.</span></span>|  
|<span data-ttu-id="dc1ae-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dc1ae-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dc1ae-121">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="dc1ae-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dc1ae-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dc1ae-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dc1ae-123">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="dc1ae-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dc1ae-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dc1ae-124">E_FAIL</span></span>|<span data-ttu-id="dc1ae-125">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="dc1ae-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dc1ae-126">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="dc1ae-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dc1ae-127">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="dc1ae-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="dc1ae-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="dc1ae-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="dc1ae-129">İstenen görevi oluşturmak yeterli bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="dc1ae-129">Not enough memory was available to create the requested task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc1ae-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dc1ae-130">Remarks</span></span>  
 <span data-ttu-id="dc1ae-131">CLR çağrıları `CreateTask` ana bilgisayar yeni bir görev oluşturma istemek için.</span><span class="sxs-lookup"><span data-stu-id="dc1ae-131">The CLR calls `CreateTask` to request that the host create a new task.</span></span> <span data-ttu-id="dc1ae-132">Ana bilgisayar için bir arabirim işaretçisi döndürür bir `IHostTask` örneği.</span><span class="sxs-lookup"><span data-stu-id="dc1ae-132">The host returns an interface pointer to an `IHostTask` instance.</span></span> <span data-ttu-id="dc1ae-133">Açıkça bir çağrı tarafından başlatılana kadar döndürülen görev askıya alınmış kalması gereken `IHostTask::Start`.</span><span class="sxs-lookup"><span data-stu-id="dc1ae-133">The returned task must remain suspended until it is explicitly started by a call to `IHostTask::Start`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc1ae-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dc1ae-134">Requirements</span></span>  
 <span data-ttu-id="dc1ae-135">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc1ae-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc1ae-136">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dc1ae-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dc1ae-137">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="dc1ae-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dc1ae-138">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc1ae-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc1ae-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dc1ae-139">See Also</span></span>  
 [<span data-ttu-id="dc1ae-140">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dc1ae-140">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="dc1ae-141">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dc1ae-141">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="dc1ae-142">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dc1ae-142">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="dc1ae-143">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dc1ae-143">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
