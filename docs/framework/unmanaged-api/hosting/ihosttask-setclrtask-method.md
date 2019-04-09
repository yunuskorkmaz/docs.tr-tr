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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59131969"
---
# <a name="ihosttasksetclrtask-method"></a><span data-ttu-id="1f0d3-102">IHostTask::SetCLRTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1f0d3-102">IHostTask::SetCLRTask Method</span></span>
<span data-ttu-id="1f0d3-103">İlişkilendirir bir `ICLRTask` geçerli örnekle [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="1f0d3-103">Associates an `ICLRTask` instance with the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f0d3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1f0d3-104">Syntax</span></span>  
  
```  
HRESULT SetCLRTask (  
    [in] ICLRTask *pCLRTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f0d3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1f0d3-105">Parameters</span></span>  
 `pCLRTask`  
 <span data-ttu-id="1f0d3-106">[in] Bir arabirim işaretçisine `ICLRTask` geçerli ile ilişkilendirilecek örneği `IHostTask` örneği.</span><span class="sxs-lookup"><span data-stu-id="1f0d3-106">[in] An interface pointer to the `ICLRTask` instance to be associated with the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1f0d3-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1f0d3-107">Return Value</span></span>  
  
|<span data-ttu-id="1f0d3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1f0d3-108">HRESULT</span></span>|<span data-ttu-id="1f0d3-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f0d3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1f0d3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1f0d3-110">S_OK</span></span>|`SetCLRTask` <span data-ttu-id="1f0d3-111">başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="1f0d3-111">returned successfully.</span></span>|  
|<span data-ttu-id="1f0d3-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1f0d3-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1f0d3-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="1f0d3-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1f0d3-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1f0d3-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1f0d3-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="1f0d3-115">The call timed out.</span></span>|  
|<span data-ttu-id="1f0d3-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1f0d3-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1f0d3-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="1f0d3-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1f0d3-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1f0d3-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1f0d3-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="1f0d3-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1f0d3-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1f0d3-120">E_FAIL</span></span>|<span data-ttu-id="1f0d3-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="1f0d3-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1f0d3-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1f0d3-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1f0d3-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="1f0d3-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f0d3-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1f0d3-124">Remarks</span></span>  
 <span data-ttu-id="1f0d3-125">CLR çağrıları `SetCLRTask` ilişkilendirilecek bir `ICLRTask` geçerli örnekle `IHostTask` bir çağrı tarafından oluşturulan örnek [Ihosttaskmanager::createtask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md).</span><span class="sxs-lookup"><span data-stu-id="1f0d3-125">The CLR calls `SetCLRTask` to associate an `ICLRTask` instance with the current `IHostTask` instance, which was created by a call to [IHostTaskManager::CreateTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f0d3-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1f0d3-126">Requirements</span></span>  
 <span data-ttu-id="1f0d3-127">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f0d3-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f0d3-128">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1f0d3-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1f0d3-129">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="1f0d3-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="1f0d3-130">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="1f0d3-130">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1f0d3-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f0d3-131">See also</span></span>

- [<span data-ttu-id="1f0d3-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1f0d3-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="1f0d3-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1f0d3-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="1f0d3-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1f0d3-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="1f0d3-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1f0d3-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
