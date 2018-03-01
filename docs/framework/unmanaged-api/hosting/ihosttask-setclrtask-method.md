---
title: "IHostTask::SetCLRTask Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostTask.SetCLRTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::SetCLRTask
helpviewer_keywords:
- SetCLRTask method [.NET Framework hosting]
- IHostTask::SetCLRTask method [.NET Framework hosting]
ms.assetid: e9d39c80-41a1-49e7-bb5e-ea3433bfb5d7
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 680ad2c13d8d6fc24134c9399cffb236bd637057
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttasksetclrtask-method"></a><span data-ttu-id="e02c1-102">IHostTask::SetCLRTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e02c1-102">IHostTask::SetCLRTask Method</span></span>
<span data-ttu-id="e02c1-103">İlişkilendiren bir `ICLRTask` geçerli örnekle [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="e02c1-103">Associates an `ICLRTask` instance with the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e02c1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e02c1-104">Syntax</span></span>  
  
```  
HRESULT SetCLRTask (  
    [in] ICLRTask *pCLRTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e02c1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e02c1-105">Parameters</span></span>  
 `pCLRTask`  
 <span data-ttu-id="e02c1-106">[in] Bir arabirim işaretçisi `ICLRTask` geçerli ilişkilendirilmesi örneği `IHostTask` örneği.</span><span class="sxs-lookup"><span data-stu-id="e02c1-106">[in] An interface pointer to the `ICLRTask` instance to be associated with the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e02c1-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e02c1-107">Return Value</span></span>  
  
|<span data-ttu-id="e02c1-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e02c1-108">HRESULT</span></span>|<span data-ttu-id="e02c1-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e02c1-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e02c1-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e02c1-110">S_OK</span></span>|<span data-ttu-id="e02c1-111">`SetCLRTask`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e02c1-111">`SetCLRTask` returned successfully.</span></span>|  
|<span data-ttu-id="e02c1-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e02c1-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e02c1-113">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="e02c1-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e02c1-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e02c1-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e02c1-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="e02c1-115">The call timed out.</span></span>|  
|<span data-ttu-id="e02c1-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e02c1-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e02c1-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="e02c1-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e02c1-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e02c1-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e02c1-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="e02c1-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e02c1-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e02c1-120">E_FAIL</span></span>|<span data-ttu-id="e02c1-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e02c1-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e02c1-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e02c1-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e02c1-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="e02c1-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e02c1-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e02c1-124">Remarks</span></span>  
 <span data-ttu-id="e02c1-125">CLR çağrıları `SetCLRTask` ilişkilendirilecek bir `ICLRTask` geçerli örnekle `IHostTask` yapılan bir çağrı tarafından oluşturulan örnek [Ihosttaskmanager::createtask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md).</span><span class="sxs-lookup"><span data-stu-id="e02c1-125">The CLR calls `SetCLRTask` to associate an `ICLRTask` instance with the current `IHostTask` instance, which was created by a call to [IHostTaskManager::CreateTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e02c1-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e02c1-126">Requirements</span></span>  
 <span data-ttu-id="e02c1-127">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e02c1-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e02c1-128">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e02c1-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e02c1-129">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e02c1-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e02c1-130">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e02c1-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e02c1-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e02c1-131">See Also</span></span>  
 [<span data-ttu-id="e02c1-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e02c1-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="e02c1-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e02c1-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="e02c1-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e02c1-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="e02c1-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e02c1-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
