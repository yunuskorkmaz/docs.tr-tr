---
description: ': IHostTaskManager:: CreateTask Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: c14c80ea9067b0a28e7b9186ea66eb695687bf27
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784580"
---
# <a name="ihosttaskmanagercreatetask-method"></a><span data-ttu-id="31aaa-103">IHostTaskManager::CreateTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="31aaa-103">IHostTaskManager::CreateTask Method</span></span>

<span data-ttu-id="31aaa-104">Konağın yeni bir görev oluşturmasını ister.</span><span class="sxs-lookup"><span data-stu-id="31aaa-104">Requests that the host create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31aaa-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="31aaa-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateTask (  
    [in]  DWORD stacksize,
    [in]  LPTHREAD_START_ROUTINE pStartAddress,  
    [in]  PVOID pParameter,  
    [out] IHostTask **ppTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31aaa-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="31aaa-106">Parameters</span></span>  

 `stacksize`  
 <span data-ttu-id="31aaa-107">'ndaki İstenen yığının bayt cinsinden istenen boyutu veya varsayılan boyut için 0 (sıfır).</span><span class="sxs-lookup"><span data-stu-id="31aaa-107">[in] The requested size, in bytes, of the requested stack, or 0 (zero) for the default size.</span></span>  
  
 `pStartAddress`  
 <span data-ttu-id="31aaa-108">'ndaki Görevin yürütüleceği işleve yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="31aaa-108">[in] A pointer to the function the task is to execute.</span></span>  
  
 `pParameter`  
 <span data-ttu-id="31aaa-109">'ndaki İşleve geçirilecek Kullanıcı verilerine yönelik bir işaretçi veya işlev hiçbir parametre alırsa null.</span><span class="sxs-lookup"><span data-stu-id="31aaa-109">[in] A pointer to the user data to be passed to the function, or null if the function takes no parameters.</span></span>  
  
 `ppTask`  
 <span data-ttu-id="31aaa-110">dışı Konak tarafından oluşturulan bir [IHostTask](ihosttask-interface.md) örneğinin adresine yönelik bir işaretçi veya görev oluşturulanmadıysa null.</span><span class="sxs-lookup"><span data-stu-id="31aaa-110">[out] A pointer to the address of an [IHostTask](ihosttask-interface.md) instance created by the host, or null if the task cannot be created.</span></span> <span data-ttu-id="31aaa-111">Görev, [IHostTask:: Start](ihosttask-start-method.md)çağrısıyla açıkça başlatılana kadar askıya alınmış durumda kalır.</span><span class="sxs-lookup"><span data-stu-id="31aaa-111">The task remains in a suspended state until it is explicitly started by a call to [IHostTask::Start](ihosttask-start-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="31aaa-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="31aaa-112">Return Value</span></span>  
  
|<span data-ttu-id="31aaa-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="31aaa-113">HRESULT</span></span>|<span data-ttu-id="31aaa-114">Description</span><span class="sxs-lookup"><span data-stu-id="31aaa-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="31aaa-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="31aaa-115">S_OK</span></span>|<span data-ttu-id="31aaa-116">`CreateTask` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="31aaa-116">`CreateTask` returned successfully.</span></span>|  
|<span data-ttu-id="31aaa-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="31aaa-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="31aaa-118">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="31aaa-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="31aaa-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="31aaa-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="31aaa-120">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="31aaa-120">The call timed out.</span></span>|  
|<span data-ttu-id="31aaa-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="31aaa-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="31aaa-122">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="31aaa-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="31aaa-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="31aaa-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="31aaa-124">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="31aaa-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="31aaa-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="31aaa-125">E_FAIL</span></span>|<span data-ttu-id="31aaa-126">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="31aaa-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="31aaa-127">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="31aaa-127">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="31aaa-128">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="31aaa-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="31aaa-129">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="31aaa-129">E_OUTOFMEMORY</span></span>|<span data-ttu-id="31aaa-130">İstenen görevi oluşturmak için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="31aaa-130">Not enough memory was available to create the requested task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31aaa-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="31aaa-131">Remarks</span></span>  

 <span data-ttu-id="31aaa-132">CLR, `CreateTask` konağın yeni bir görev oluşturmasını istemek için çağırır.</span><span class="sxs-lookup"><span data-stu-id="31aaa-132">The CLR calls `CreateTask` to request that the host create a new task.</span></span> <span data-ttu-id="31aaa-133">Konak, bir örneğe bir arabirim işaretçisi döndürür `IHostTask` .</span><span class="sxs-lookup"><span data-stu-id="31aaa-133">The host returns an interface pointer to an `IHostTask` instance.</span></span> <span data-ttu-id="31aaa-134">Döndürülen görev, öğesine yapılan bir çağrı tarafından açıkça başlatılana kadar askıya alınmalıdır `IHostTask::Start` .</span><span class="sxs-lookup"><span data-stu-id="31aaa-134">The returned task must remain suspended until it is explicitly started by a call to `IHostTask::Start`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31aaa-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="31aaa-135">Requirements</span></span>  

 <span data-ttu-id="31aaa-136">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31aaa-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31aaa-137">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="31aaa-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="31aaa-138">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="31aaa-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="31aaa-139">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31aaa-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31aaa-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31aaa-140">See also</span></span>

- [<span data-ttu-id="31aaa-141">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31aaa-141">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="31aaa-142">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31aaa-142">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="31aaa-143">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31aaa-143">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="31aaa-144">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31aaa-144">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
