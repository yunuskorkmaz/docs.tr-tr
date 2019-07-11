---
title: ICLRTaskManager::GetCurrentTask Metodu
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.GetCurrentTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::GetCurrentTask
helpviewer_keywords:
- GetCurrentTask method, ICLRTaskManager interface [.NET Framework hosting]
- ICLRTaskManager::GetCurrentTask method [.NET Framework hosting]
ms.assetid: c0b82a9f-edc6-4878-9c81-48de53c02142
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9996b1a84a5f095cf12d74d0c6f594911e7a7788
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770203"
---
# <a name="iclrtaskmanagergetcurrenttask-method"></a><span data-ttu-id="9d55a-102">ICLRTaskManager::GetCurrentTask Metodu</span><span class="sxs-lookup"><span data-stu-id="9d55a-102">ICLRTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="9d55a-103">Alır [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) yöntem çağrısında kaynaklandığı işletim sistemi iş parçacığı üzerinde çalışmakta olan bir örneği.</span><span class="sxs-lookup"><span data-stu-id="9d55a-103">Gets the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance that is currently running on the operating system thread from which the method call originated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d55a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9d55a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentTask (  
    [out] ICLRTask **ppTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d55a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9d55a-105">Parameters</span></span>  
 `ppTask`  
 <span data-ttu-id="9d55a-106">[out] Adresine bir işaretçi bir `ICLRTask` çağrı kaynaklandığı işletim sistemi iş parçacığı üzerinde Yürütülüyor örneği veya hiçbir görev şu anda bu iş parçacığı üzerinde Yürütülüyor yoksa null.</span><span class="sxs-lookup"><span data-stu-id="9d55a-106">[out] A pointer to the address of an `ICLRTask` instance that is currently executing on the operating system thread from which the call originated, or null if no task is currently executing on this thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d55a-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9d55a-107">Return Value</span></span>  
  
|<span data-ttu-id="9d55a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9d55a-108">HRESULT</span></span>|<span data-ttu-id="9d55a-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9d55a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9d55a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9d55a-110">S_OK</span></span>|<span data-ttu-id="9d55a-111">Yöntemi başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="9d55a-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="9d55a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9d55a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9d55a-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="9d55a-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9d55a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9d55a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9d55a-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="9d55a-115">The call timed out.</span></span>|  
|<span data-ttu-id="9d55a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9d55a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9d55a-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="9d55a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9d55a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9d55a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9d55a-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="9d55a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9d55a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9d55a-120">E_FAIL</span></span>|<span data-ttu-id="9d55a-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="9d55a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9d55a-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9d55a-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9d55a-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="9d55a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d55a-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9d55a-124">Remarks</span></span>  
 <span data-ttu-id="9d55a-125">`ICLRTask` Örneğin `ppTask` parametresi için CLR şu anda yürütülmekte olan görevi temsil için gösterir.</span><span class="sxs-lookup"><span data-stu-id="9d55a-125">The `ICLRTask` instance that the `ppTask` parameter points to represents the currently executing task for the CLR.</span></span> <span data-ttu-id="9d55a-126">`ICLRTask` Örneğidir karşılık gelen ile ilişkili [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) görev ana bilgisayarı temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="9d55a-126">The `ICLRTask` instance is associated with a corresponding [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that represents the task for the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d55a-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9d55a-127">Requirements</span></span>  
 <span data-ttu-id="9d55a-128">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d55a-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d55a-129">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9d55a-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9d55a-130">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="9d55a-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9d55a-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d55a-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d55a-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d55a-132">See also</span></span>

- [<span data-ttu-id="9d55a-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d55a-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="9d55a-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d55a-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="9d55a-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d55a-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="9d55a-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d55a-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
