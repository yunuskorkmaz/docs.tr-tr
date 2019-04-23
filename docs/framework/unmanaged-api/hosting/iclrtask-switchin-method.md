---
title: ICLRTask::SwitchIn Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRTask.SwitchIn
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SwitchIn
helpviewer_keywords:
- ICLRTask::SwitchIn method [.NET Framework hosting]
- SwitchIn method [.NET Framework hosting]
ms.assetid: 3d37ce20-aa65-4043-8f13-7c728b5d8a52
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5f36a963417aba082667bb9fb609e0d1dcad7b09
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59187687"
---
# <a name="iclrtaskswitchin-method"></a><span data-ttu-id="a942e-102">ICLRTask::SwitchIn Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a942e-102">ICLRTask::SwitchIn Method</span></span>
<span data-ttu-id="a942e-103">Ortak dil çalışma zamanı (CLR) bildirir, bir görev, geçerli [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) örneği temsil eder, artık çalıştırılabilir bir durumda.</span><span class="sxs-lookup"><span data-stu-id="a942e-103">Notifies the common language runtime (CLR) that the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents is now in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a942e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a942e-104">Syntax</span></span>  
  
```  
HRESULT SwitchIn (  
    [in] HANDLE threadHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a942e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a942e-105">Parameters</span></span>  
 `threadHandle`  
 <span data-ttu-id="a942e-106">[in] Görev tarafından geçerli temsil fiziksel iş parçacığına bir tanıtıcı `ICLRTask` örneği yürütüyordur.</span><span class="sxs-lookup"><span data-stu-id="a942e-106">[in] A handle to the physical thread on which the task represented by the current `ICLRTask` instance is executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a942e-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a942e-107">Return Value</span></span>  
  
|<span data-ttu-id="a942e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a942e-108">HRESULT</span></span>|<span data-ttu-id="a942e-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a942e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a942e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a942e-110">S_OK</span></span>|<span data-ttu-id="a942e-111">`SwitchIn` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="a942e-111">`SwitchIn` returned successfully.</span></span>|  
|<span data-ttu-id="a942e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a942e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a942e-113">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="a942e-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a942e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a942e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a942e-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="a942e-115">The call timed out.</span></span>|  
|<span data-ttu-id="a942e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a942e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a942e-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="a942e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a942e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a942e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a942e-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="a942e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a942e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a942e-120">E_FAIL</span></span>|<span data-ttu-id="a942e-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a942e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a942e-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a942e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a942e-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="a942e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a942e-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="a942e-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="a942e-125">`SwitchIn` çağrısında olmadan çağrıldı [SwitchOut yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md).</span><span class="sxs-lookup"><span data-stu-id="a942e-125">`SwitchIn` was called without an earlier call to [SwitchOut Method](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a942e-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a942e-126">Remarks</span></span>  
 <span data-ttu-id="a942e-127">`threadHandle` Parametresini görev üzerinde geçerli tarafından gösterilen işletim sistemi iş parçacığına bir tanıtıcı temsil `ICLRTask` örneği zamanlandı.</span><span class="sxs-lookup"><span data-stu-id="a942e-127">The `threadHandle` parameter represents a handle to the operating system thread on which the task represented by the current `ICLRTask` instance has been scheduled.</span></span> <span data-ttu-id="a942e-128">Bu iş parçacığı üzerinde kimliğe bürünme oluştuysa çağırmalısınız [Ihostsecuritymanager::RevertToSelf](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md) görevde geçmeden önce.</span><span class="sxs-lookup"><span data-stu-id="a942e-128">If impersonation has occurred on this thread, you must call [IHostSecurityManager::RevertToSelf](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md) before switching in the task.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a942e-129">Bir çağrı `SwitchIn` çağrısında olmadan `SwitchOut` HOST_E_INVALIDOPERATION bir HRESULT değerini ile başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="a942e-129">A call to `SwitchIn` without an earlier call to `SwitchOut` fails with an HRESULT value of HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a942e-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a942e-130">Requirements</span></span>  
 <span data-ttu-id="a942e-131">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a942e-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a942e-132">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a942e-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a942e-133">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="a942e-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a942e-134">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a942e-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a942e-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a942e-135">See also</span></span>

- [<span data-ttu-id="a942e-136">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a942e-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="a942e-137">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a942e-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="a942e-138">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a942e-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="a942e-139">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a942e-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
