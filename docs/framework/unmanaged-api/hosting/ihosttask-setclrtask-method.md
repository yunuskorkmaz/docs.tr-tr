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
ms.openlocfilehash: b0220a0699e7325c6d81ba3ad4627176640937dd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789551"
---
# <a name="ihosttasksetclrtask-method"></a><span data-ttu-id="07a38-102">IHostTask::SetCLRTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="07a38-102">IHostTask::SetCLRTask Method</span></span>
<span data-ttu-id="07a38-103">İlişkilendirir bir `ICLRTask` geçerli örnekle [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="07a38-103">Associates an `ICLRTask` instance with the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07a38-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="07a38-104">Syntax</span></span>  
  
```  
HRESULT SetCLRTask (  
    [in] ICLRTask *pCLRTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07a38-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="07a38-105">Parameters</span></span>  
 `pCLRTask`  
 <span data-ttu-id="07a38-106">[in] Bir arabirim işaretçisine `ICLRTask` geçerli ile ilişkilendirilecek örneği `IHostTask` örneği.</span><span class="sxs-lookup"><span data-stu-id="07a38-106">[in] An interface pointer to the `ICLRTask` instance to be associated with the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="07a38-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="07a38-107">Return Value</span></span>  
  
|<span data-ttu-id="07a38-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="07a38-108">HRESULT</span></span>|<span data-ttu-id="07a38-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07a38-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="07a38-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="07a38-110">S_OK</span></span>|<span data-ttu-id="07a38-111">`SetCLRTask` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="07a38-111">`SetCLRTask` returned successfully.</span></span>|  
|<span data-ttu-id="07a38-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="07a38-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="07a38-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="07a38-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="07a38-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="07a38-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="07a38-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="07a38-115">The call timed out.</span></span>|  
|<span data-ttu-id="07a38-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="07a38-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="07a38-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="07a38-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="07a38-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="07a38-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="07a38-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="07a38-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="07a38-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="07a38-120">E_FAIL</span></span>|<span data-ttu-id="07a38-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="07a38-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="07a38-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="07a38-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="07a38-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="07a38-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="07a38-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="07a38-124">Remarks</span></span>  
 <span data-ttu-id="07a38-125">CLR çağrıları `SetCLRTask` ilişkilendirilecek bir `ICLRTask` geçerli örnekle `IHostTask` bir çağrı tarafından oluşturulan örnek [Ihosttaskmanager::createtask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md).</span><span class="sxs-lookup"><span data-stu-id="07a38-125">The CLR calls `SetCLRTask` to associate an `ICLRTask` instance with the current `IHostTask` instance, which was created by a call to [IHostTaskManager::CreateTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07a38-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="07a38-126">Requirements</span></span>  
 <span data-ttu-id="07a38-127">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07a38-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07a38-128">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="07a38-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="07a38-129">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="07a38-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="07a38-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07a38-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07a38-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07a38-131">See also</span></span>

- [<span data-ttu-id="07a38-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="07a38-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="07a38-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="07a38-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="07a38-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="07a38-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="07a38-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="07a38-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
