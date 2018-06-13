---
title: IHostTask::SetCLRTask Yöntemi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2149293989136e0b006f044c925353efbfd94031
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442806"
---
# <a name="ihosttasksetclrtask-method"></a><span data-ttu-id="57cb7-102">IHostTask::SetCLRTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="57cb7-102">IHostTask::SetCLRTask Method</span></span>
<span data-ttu-id="57cb7-103">İlişkilendiren bir `ICLRTask` geçerli örnekle [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="57cb7-103">Associates an `ICLRTask` instance with the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57cb7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="57cb7-104">Syntax</span></span>  
  
```  
HRESULT SetCLRTask (  
    [in] ICLRTask *pCLRTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="57cb7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="57cb7-105">Parameters</span></span>  
 `pCLRTask`  
 <span data-ttu-id="57cb7-106">[in] Bir arabirim işaretçisi `ICLRTask` geçerli ilişkilendirilmesi örneği `IHostTask` örneği.</span><span class="sxs-lookup"><span data-stu-id="57cb7-106">[in] An interface pointer to the `ICLRTask` instance to be associated with the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57cb7-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="57cb7-107">Return Value</span></span>  
  
|<span data-ttu-id="57cb7-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="57cb7-108">HRESULT</span></span>|<span data-ttu-id="57cb7-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57cb7-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="57cb7-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="57cb7-110">S_OK</span></span>|<span data-ttu-id="57cb7-111">`SetCLRTask` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="57cb7-111">`SetCLRTask` returned successfully.</span></span>|  
|<span data-ttu-id="57cb7-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="57cb7-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="57cb7-113">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="57cb7-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="57cb7-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="57cb7-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="57cb7-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="57cb7-115">The call timed out.</span></span>|  
|<span data-ttu-id="57cb7-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="57cb7-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="57cb7-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="57cb7-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="57cb7-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="57cb7-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="57cb7-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="57cb7-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="57cb7-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="57cb7-120">E_FAIL</span></span>|<span data-ttu-id="57cb7-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="57cb7-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="57cb7-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="57cb7-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="57cb7-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="57cb7-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57cb7-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="57cb7-124">Remarks</span></span>  
 <span data-ttu-id="57cb7-125">CLR çağrıları `SetCLRTask` ilişkilendirilecek bir `ICLRTask` geçerli örnekle `IHostTask` yapılan bir çağrı tarafından oluşturulan örnek [Ihosttaskmanager::createtask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md).</span><span class="sxs-lookup"><span data-stu-id="57cb7-125">The CLR calls `SetCLRTask` to associate an `ICLRTask` instance with the current `IHostTask` instance, which was created by a call to [IHostTaskManager::CreateTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57cb7-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="57cb7-126">Requirements</span></span>  
 <span data-ttu-id="57cb7-127">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57cb7-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57cb7-128">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="57cb7-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="57cb7-129">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="57cb7-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="57cb7-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57cb7-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57cb7-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="57cb7-131">See Also</span></span>  
 [<span data-ttu-id="57cb7-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="57cb7-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="57cb7-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="57cb7-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="57cb7-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="57cb7-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="57cb7-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="57cb7-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
