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
ms.openlocfilehash: 16916d62a528222db952a1d29dc7c69de2352191
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133119"
---
# <a name="ihosttaskmanagercreatetask-method"></a><span data-ttu-id="be08b-102">IHostTaskManager::CreateTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="be08b-102">IHostTaskManager::CreateTask Method</span></span>
<span data-ttu-id="be08b-103">Konağın yeni bir görev oluşturmasını ister.</span><span class="sxs-lookup"><span data-stu-id="be08b-103">Requests that the host create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be08b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="be08b-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateTask (  
    [in]  DWORD stacksize,   
    [in]  LPTHREAD_START_ROUTINE pStartAddress,  
    [in]  PVOID pParameter,  
    [out] IHostTask **ppTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be08b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="be08b-105">Parameters</span></span>  
 `stacksize`  
 <span data-ttu-id="be08b-106">'ndaki İstenen yığının bayt cinsinden istenen boyutu veya varsayılan boyut için 0 (sıfır).</span><span class="sxs-lookup"><span data-stu-id="be08b-106">[in] The requested size, in bytes, of the requested stack, or 0 (zero) for the default size.</span></span>  
  
 `pStartAddress`  
 <span data-ttu-id="be08b-107">'ndaki Görevin yürütüleceği işleve yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="be08b-107">[in] A pointer to the function the task is to execute.</span></span>  
  
 `pParameter`  
 <span data-ttu-id="be08b-108">'ndaki İşleve geçirilecek Kullanıcı verilerine yönelik bir işaretçi veya işlev hiçbir parametre alırsa null.</span><span class="sxs-lookup"><span data-stu-id="be08b-108">[in] A pointer to the user data to be passed to the function, or null if the function takes no parameters.</span></span>  
  
 `ppTask`  
 <span data-ttu-id="be08b-109">dışı Konak tarafından oluşturulan bir [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) örneğinin adresine yönelik bir işaretçi veya görev oluşturulanmadıysa null.</span><span class="sxs-lookup"><span data-stu-id="be08b-109">[out] A pointer to the address of an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance created by the host, or null if the task cannot be created.</span></span> <span data-ttu-id="be08b-110">Görev, [IHostTask:: Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)çağrısıyla açıkça başlatılana kadar askıya alınmış durumda kalır.</span><span class="sxs-lookup"><span data-stu-id="be08b-110">The task remains in a suspended state until it is explicitly started by a call to [IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="be08b-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="be08b-111">Return Value</span></span>  
  
|<span data-ttu-id="be08b-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="be08b-112">HRESULT</span></span>|<span data-ttu-id="be08b-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="be08b-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="be08b-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="be08b-114">S_OK</span></span>|<span data-ttu-id="be08b-115">`CreateTask` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="be08b-115">`CreateTask` returned successfully.</span></span>|  
|<span data-ttu-id="be08b-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="be08b-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="be08b-117">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="be08b-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="be08b-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="be08b-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="be08b-119">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="be08b-119">The call timed out.</span></span>|  
|<span data-ttu-id="be08b-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="be08b-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="be08b-121">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="be08b-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="be08b-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="be08b-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="be08b-123">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="be08b-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="be08b-124">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="be08b-124">E_FAIL</span></span>|<span data-ttu-id="be08b-125">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="be08b-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="be08b-126">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="be08b-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="be08b-127">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="be08b-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="be08b-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="be08b-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="be08b-129">İstenen görevi oluşturmak için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="be08b-129">Not enough memory was available to create the requested task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be08b-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="be08b-130">Remarks</span></span>  
 <span data-ttu-id="be08b-131">CLR, konağın yeni bir görev oluşturmasını istemek için `CreateTask` çağırır.</span><span class="sxs-lookup"><span data-stu-id="be08b-131">The CLR calls `CreateTask` to request that the host create a new task.</span></span> <span data-ttu-id="be08b-132">Konak bir `IHostTask` örneğine bir arabirim işaretçisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="be08b-132">The host returns an interface pointer to an `IHostTask` instance.</span></span> <span data-ttu-id="be08b-133">Döndürülen görev, bir `IHostTask::Start`çağrısıyla açıkça başlatılana kadar askıya alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="be08b-133">The returned task must remain suspended until it is explicitly started by a call to `IHostTask::Start`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be08b-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="be08b-134">Requirements</span></span>  
 <span data-ttu-id="be08b-135">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be08b-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be08b-136">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="be08b-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="be08b-137">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="be08b-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="be08b-138">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be08b-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be08b-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be08b-139">See also</span></span>

- [<span data-ttu-id="be08b-140">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="be08b-140">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="be08b-141">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="be08b-141">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="be08b-142">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="be08b-142">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="be08b-143">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="be08b-143">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
