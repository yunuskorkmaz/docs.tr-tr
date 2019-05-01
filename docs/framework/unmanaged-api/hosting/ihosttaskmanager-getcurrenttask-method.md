---
title: IHostTaskManager::GetCurrentTask Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTaskManager.GetCurrentTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::GetCurrentTask
helpviewer_keywords:
- GetCurrentTask method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::GetCurrentTask method [.NET Framework hosting]
ms.assetid: f17bca49-90bd-4dee-a5e1-b9a57ea46f85
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2436288e2f2f241cab15b16abf4df99c73caec25
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789426"
---
# <a name="ihosttaskmanagergetcurrenttask-method"></a><span data-ttu-id="84233-102">IHostTaskManager::GetCurrentTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="84233-102">IHostTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="84233-103">Bu Çağrının yapıldığı işletim sistemi iş parçacığı üzerinde şu anda yürütülmekte olan görev için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="84233-103">Gets an interface pointer to the task that is currently executing on the operating system thread from which this call is made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84233-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="84233-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentTask (  
    [out] IHostTask **pTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84233-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="84233-105">Parameters</span></span>  
 `pTask`  
 <span data-ttu-id="84233-106">[out] Adresine bir işaretçi bir [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) hiçbir görev şu anda yürütülüyorsa o anda yürütülen görev veya null temsil eden örnek.</span><span class="sxs-lookup"><span data-stu-id="84233-106">[out] A pointer to the address of an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that represents the currently executing task, or null, if no task is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="84233-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="84233-107">Return Value</span></span>  
  
|<span data-ttu-id="84233-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="84233-108">HRESULT</span></span>|<span data-ttu-id="84233-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="84233-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="84233-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="84233-110">S_OK</span></span>|<span data-ttu-id="84233-111">`GetCurrentTask` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="84233-111">`GetCurrentTask` returned successfully.</span></span>|  
|<span data-ttu-id="84233-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="84233-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="84233-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="84233-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="84233-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="84233-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="84233-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="84233-115">The call timed out.</span></span>|  
|<span data-ttu-id="84233-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="84233-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="84233-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="84233-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="84233-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="84233-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="84233-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="84233-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="84233-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="84233-120">E_FAIL</span></span>|<span data-ttu-id="84233-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="84233-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="84233-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="84233-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="84233-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="84233-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="84233-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="84233-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="84233-125">`GetCurrentTask` konağın denetimin dışında kalan bir işletim sistemi iş parçacığı üzerinde çağrılmış.</span><span class="sxs-lookup"><span data-stu-id="84233-125">`GetCurrentTask` was called on an operating system thread outside the control of the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84233-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="84233-126">Remarks</span></span>  
 <span data-ttu-id="84233-127">Konak de ayarlayabilirsiniz `pTask` parametresi null değil başlatmak bir görev CLR girmesini önlemek için.</span><span class="sxs-lookup"><span data-stu-id="84233-127">The host can also set the `pTask` parameter to null to prevent a task that it did not initiate from entering the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84233-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="84233-128">Requirements</span></span>  
 <span data-ttu-id="84233-129">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84233-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84233-130">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="84233-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="84233-131">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="84233-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="84233-132">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84233-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84233-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84233-133">See also</span></span>

- [<span data-ttu-id="84233-134">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="84233-134">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="84233-135">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="84233-135">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="84233-136">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="84233-136">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="84233-137">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="84233-137">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
