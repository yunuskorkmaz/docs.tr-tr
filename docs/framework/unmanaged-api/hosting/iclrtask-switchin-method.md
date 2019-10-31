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
ms.openlocfilehash: fbfd44c8e20bc75638d6356fe405f02790da8ac7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124614"
---
# <a name="iclrtaskswitchin-method"></a><span data-ttu-id="6e57f-102">ICLRTask::SwitchIn Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e57f-102">ICLRTask::SwitchIn Method</span></span>
<span data-ttu-id="6e57f-103">Geçerli [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) örneğinin gösterdiği görevin Şu anda bir çalıştırılabilir durumunda olduğunu ortak dil çalışma zamanına (CLR) bildirir.</span><span class="sxs-lookup"><span data-stu-id="6e57f-103">Notifies the common language runtime (CLR) that the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents is now in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e57f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e57f-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchIn (  
    [in] HANDLE threadHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e57f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6e57f-105">Parameters</span></span>  
 `threadHandle`  
 <span data-ttu-id="6e57f-106">'ndaki Geçerli `ICLRTask` örneği tarafından temsil edilen görevin yürütüldüğü fiziksel iş parçacığına yönelik bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="6e57f-106">[in] A handle to the physical thread on which the task represented by the current `ICLRTask` instance is executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6e57f-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6e57f-107">Return Value</span></span>  
  
|<span data-ttu-id="6e57f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6e57f-108">HRESULT</span></span>|<span data-ttu-id="6e57f-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e57f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6e57f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="6e57f-110">S_OK</span></span>|<span data-ttu-id="6e57f-111">`SwitchIn` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="6e57f-111">`SwitchIn` returned successfully.</span></span>|  
|<span data-ttu-id="6e57f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6e57f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6e57f-113">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="6e57f-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6e57f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6e57f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6e57f-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="6e57f-115">The call timed out.</span></span>|  
|<span data-ttu-id="6e57f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6e57f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6e57f-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="6e57f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6e57f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6e57f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6e57f-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="6e57f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6e57f-120">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="6e57f-120">E_FAIL</span></span>|<span data-ttu-id="6e57f-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="6e57f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6e57f-122">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6e57f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6e57f-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="6e57f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6e57f-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="6e57f-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="6e57f-125">`SwitchIn`, [geçiş yöntemine](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md)daha önceki bir çağrı olmadan çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="6e57f-125">`SwitchIn` was called without an earlier call to [SwitchOut Method](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e57f-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e57f-126">Remarks</span></span>  
 <span data-ttu-id="6e57f-127">`threadHandle` parametresi, geçerli `ICLRTask` örneği tarafından temsil edilen görevin zamanlandığı işletim sistemi iş parçacığı tanıtıcısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6e57f-127">The `threadHandle` parameter represents a handle to the operating system thread on which the task represented by the current `ICLRTask` instance has been scheduled.</span></span> <span data-ttu-id="6e57f-128">Bu iş parçacığında kimliğe bürünme gerçekleştiyse, göreve geçmeden önce [IHostSecurityManager:: RevertToSelf](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md) öğesini çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6e57f-128">If impersonation has occurred on this thread, you must call [IHostSecurityManager::RevertToSelf](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md) before switching in the task.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6e57f-129">Daha önceki `SwitchOut` çağrısı olmayan bir `SwitchIn` çağrısı, HRESULT değeri HOST_E_INVALIDOPERATION ile başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="6e57f-129">A call to `SwitchIn` without an earlier call to `SwitchOut` fails with an HRESULT value of HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e57f-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6e57f-130">Requirements</span></span>  
 <span data-ttu-id="6e57f-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e57f-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e57f-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6e57f-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6e57f-133">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="6e57f-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6e57f-134">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e57f-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e57f-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e57f-135">See also</span></span>

- [<span data-ttu-id="6e57f-136">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e57f-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="6e57f-137">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e57f-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="6e57f-138">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e57f-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="6e57f-139">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e57f-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
