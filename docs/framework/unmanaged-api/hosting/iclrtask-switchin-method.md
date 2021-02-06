---
description: ': ICLRTask:: SwitchIn Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 0bbcd2b9594a8ce465a1dcd7b5ae3f8a0799826d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636838"
---
# <a name="iclrtaskswitchin-method"></a><span data-ttu-id="fcd39-103">ICLRTask::SwitchIn Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fcd39-103">ICLRTask::SwitchIn Method</span></span>

<span data-ttu-id="fcd39-104">Geçerli [ICLRTask](iclrtask-interface.md) örneğinin gösterdiği görevin Şu anda bir çalıştırılabilir durumunda olduğunu ortak dil çalışma zamanına (CLR) bildirir.</span><span class="sxs-lookup"><span data-stu-id="fcd39-104">Notifies the common language runtime (CLR) that the task that the current [ICLRTask](iclrtask-interface.md) instance represents is now in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcd39-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fcd39-105">Syntax</span></span>  
  
```cpp  
HRESULT SwitchIn (  
    [in] HANDLE threadHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fcd39-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fcd39-106">Parameters</span></span>  

 `threadHandle`  
 <span data-ttu-id="fcd39-107">'ndaki Geçerli örnek tarafından temsil edilen görevin yürütüldüğü fiziksel iş parçacığına yönelik bir tanıtıcı `ICLRTask` .</span><span class="sxs-lookup"><span data-stu-id="fcd39-107">[in] A handle to the physical thread on which the task represented by the current `ICLRTask` instance is executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fcd39-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fcd39-108">Return Value</span></span>  
  
|<span data-ttu-id="fcd39-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fcd39-109">HRESULT</span></span>|<span data-ttu-id="fcd39-110">Description</span><span class="sxs-lookup"><span data-stu-id="fcd39-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fcd39-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="fcd39-111">S_OK</span></span>|<span data-ttu-id="fcd39-112">`SwitchIn` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="fcd39-112">`SwitchIn` returned successfully.</span></span>|  
|<span data-ttu-id="fcd39-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fcd39-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fcd39-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="fcd39-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fcd39-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fcd39-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fcd39-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="fcd39-116">The call timed out.</span></span>|  
|<span data-ttu-id="fcd39-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fcd39-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fcd39-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="fcd39-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fcd39-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fcd39-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fcd39-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="fcd39-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fcd39-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fcd39-121">E_FAIL</span></span>|<span data-ttu-id="fcd39-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="fcd39-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fcd39-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="fcd39-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fcd39-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="fcd39-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="fcd39-125">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="fcd39-125">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="fcd39-126">`SwitchIn` , önceki bir [geçiş yöntemine](iclrtask-switchout-method.md)çağrı olmadan çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="fcd39-126">`SwitchIn` was called without an earlier call to [SwitchOut Method](iclrtask-switchout-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fcd39-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fcd39-127">Remarks</span></span>  

 <span data-ttu-id="fcd39-128">`threadHandle`Parametresi, geçerli örnek tarafından temsil edilen görevin zamanlandığı işletim sistemi iş parçacığı tanıtıcısını temsil eder `ICLRTask` .</span><span class="sxs-lookup"><span data-stu-id="fcd39-128">The `threadHandle` parameter represents a handle to the operating system thread on which the task represented by the current `ICLRTask` instance has been scheduled.</span></span> <span data-ttu-id="fcd39-129">Bu iş parçacığında kimliğe bürünme gerçekleştiyse, göreve geçmeden önce [IHostSecurityManager:: RevertToSelf](ihostsecuritymanager-reverttoself-method.md) öğesini çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fcd39-129">If impersonation has occurred on this thread, you must call [IHostSecurityManager::RevertToSelf](ihostsecuritymanager-reverttoself-method.md) before switching in the task.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fcd39-130">`SwitchIn`Daha önceki bir çağrısı olmayan bir çağrısı `SwitchOut` , HOST_E_INVALIDOPERATION HRESULT değeriyle başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="fcd39-130">A call to `SwitchIn` without an earlier call to `SwitchOut` fails with an HRESULT value of HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcd39-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fcd39-131">Requirements</span></span>  

 <span data-ttu-id="fcd39-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fcd39-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcd39-133">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fcd39-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fcd39-134">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="fcd39-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fcd39-135">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcd39-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcd39-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fcd39-136">See also</span></span>

- [<span data-ttu-id="fcd39-137">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fcd39-137">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="fcd39-138">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fcd39-138">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="fcd39-139">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fcd39-139">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="fcd39-140">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fcd39-140">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
