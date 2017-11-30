---
title: "IHostTask::SetCLRTask Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTask.SetCLRTask
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTask::SetCLRTask
helpviewer_keywords:
- SetCLRTask method [.NET Framework hosting]
- IHostTask::SetCLRTask method [.NET Framework hosting]
ms.assetid: e9d39c80-41a1-49e7-bb5e-ea3433bfb5d7
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 54706b1c3a6ea1864137e2eca135fa6bd883b345
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttasksetclrtask-method"></a><span data-ttu-id="7af9b-102">IHostTask::SetCLRTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7af9b-102">IHostTask::SetCLRTask Method</span></span>
<span data-ttu-id="7af9b-103">İlişkilendiren bir `ICLRTask` geçerli örnekle [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="7af9b-103">Associates an `ICLRTask` instance with the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7af9b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7af9b-104">Syntax</span></span>  
  
```  
HRESULT SetCLRTask (  
    [in] ICLRTask *pCLRTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7af9b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7af9b-105">Parameters</span></span>  
 `pCLRTask`  
 <span data-ttu-id="7af9b-106">[in] Bir arabirim işaretçisi `ICLRTask` geçerli ilişkilendirilmesi örneği `IHostTask` örneği.</span><span class="sxs-lookup"><span data-stu-id="7af9b-106">[in] An interface pointer to the `ICLRTask` instance to be associated with the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7af9b-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7af9b-107">Return Value</span></span>  
  
|<span data-ttu-id="7af9b-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7af9b-108">HRESULT</span></span>|<span data-ttu-id="7af9b-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7af9b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7af9b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7af9b-110">S_OK</span></span>|<span data-ttu-id="7af9b-111">`SetCLRTask`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="7af9b-111">`SetCLRTask` returned successfully.</span></span>|  
|<span data-ttu-id="7af9b-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7af9b-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7af9b-113">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="7af9b-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7af9b-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7af9b-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7af9b-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="7af9b-115">The call timed out.</span></span>|  
|<span data-ttu-id="7af9b-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7af9b-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7af9b-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="7af9b-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7af9b-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7af9b-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7af9b-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="7af9b-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7af9b-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7af9b-120">E_FAIL</span></span>|<span data-ttu-id="7af9b-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="7af9b-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7af9b-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="7af9b-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7af9b-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="7af9b-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7af9b-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7af9b-124">Remarks</span></span>  
 <span data-ttu-id="7af9b-125">CLR çağrıları `SetCLRTask` ilişkilendirilecek bir `ICLRTask` geçerli örnekle `IHostTask` yapılan bir çağrı tarafından oluşturulan örnek [Ihosttaskmanager::createtask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md).</span><span class="sxs-lookup"><span data-stu-id="7af9b-125">The CLR calls `SetCLRTask` to associate an `ICLRTask` instance with the current `IHostTask` instance, which was created by a call to [IHostTaskManager::CreateTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7af9b-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7af9b-126">Requirements</span></span>  
 <span data-ttu-id="7af9b-127">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7af9b-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7af9b-128">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7af9b-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7af9b-129">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="7af9b-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7af9b-130">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7af9b-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7af9b-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7af9b-131">See Also</span></span>  
 [<span data-ttu-id="7af9b-132">Iclrtask arabirimi</span><span class="sxs-lookup"><span data-stu-id="7af9b-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="7af9b-133">Iclrtaskmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="7af9b-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="7af9b-134">Ihosttask arabirimi</span><span class="sxs-lookup"><span data-stu-id="7af9b-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="7af9b-135">Ihosttaskmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="7af9b-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
