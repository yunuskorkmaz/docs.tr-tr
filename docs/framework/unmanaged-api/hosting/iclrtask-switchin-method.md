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
ms.openlocfilehash: d8f57af459d1bb3f338cfbfcbb29f69f533ea927
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762935"
---
# <a name="iclrtaskswitchin-method"></a><span data-ttu-id="872e0-102">ICLRTask::SwitchIn Yöntemi</span><span class="sxs-lookup"><span data-stu-id="872e0-102">ICLRTask::SwitchIn Method</span></span>
<span data-ttu-id="872e0-103">Geçerli [ICLRTask](iclrtask-interface.md) örneğinin gösterdiği görevin Şu anda bir çalıştırılabilir durumunda olduğunu ortak dil çalışma zamanına (CLR) bildirir.</span><span class="sxs-lookup"><span data-stu-id="872e0-103">Notifies the common language runtime (CLR) that the task that the current [ICLRTask](iclrtask-interface.md) instance represents is now in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="872e0-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="872e0-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchIn (  
    [in] HANDLE threadHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="872e0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="872e0-105">Parameters</span></span>  
 `threadHandle`  
 <span data-ttu-id="872e0-106">'ndaki Geçerli örnek tarafından temsil edilen görevin yürütüldüğü fiziksel iş parçacığına yönelik bir tanıtıcı `ICLRTask` .</span><span class="sxs-lookup"><span data-stu-id="872e0-106">[in] A handle to the physical thread on which the task represented by the current `ICLRTask` instance is executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="872e0-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="872e0-107">Return Value</span></span>  
  
|<span data-ttu-id="872e0-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="872e0-108">HRESULT</span></span>|<span data-ttu-id="872e0-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="872e0-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="872e0-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="872e0-110">S_OK</span></span>|<span data-ttu-id="872e0-111">`SwitchIn`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="872e0-111">`SwitchIn` returned successfully.</span></span>|  
|<span data-ttu-id="872e0-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="872e0-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="872e0-113">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="872e0-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="872e0-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="872e0-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="872e0-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="872e0-115">The call timed out.</span></span>|  
|<span data-ttu-id="872e0-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="872e0-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="872e0-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="872e0-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="872e0-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="872e0-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="872e0-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="872e0-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="872e0-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="872e0-120">E_FAIL</span></span>|<span data-ttu-id="872e0-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="872e0-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="872e0-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="872e0-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="872e0-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="872e0-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="872e0-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="872e0-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="872e0-125">`SwitchIn`, önceki bir [geçiş yöntemine](iclrtask-switchout-method.md)çağrı olmadan çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="872e0-125">`SwitchIn` was called without an earlier call to [SwitchOut Method](iclrtask-switchout-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="872e0-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="872e0-126">Remarks</span></span>  
 <span data-ttu-id="872e0-127">`threadHandle`Parametresi, geçerli örnek tarafından temsil edilen görevin zamanlandığı işletim sistemi iş parçacığı tanıtıcısını temsil eder `ICLRTask` .</span><span class="sxs-lookup"><span data-stu-id="872e0-127">The `threadHandle` parameter represents a handle to the operating system thread on which the task represented by the current `ICLRTask` instance has been scheduled.</span></span> <span data-ttu-id="872e0-128">Bu iş parçacığında kimliğe bürünme gerçekleştiyse, göreve geçmeden önce [IHostSecurityManager:: RevertToSelf](ihostsecuritymanager-reverttoself-method.md) öğesini çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="872e0-128">If impersonation has occurred on this thread, you must call [IHostSecurityManager::RevertToSelf](ihostsecuritymanager-reverttoself-method.md) before switching in the task.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="872e0-129">`SwitchIn`Daha önceki bir çağrısı olmayan bir çağrısı `SwitchOut` , HOST_E_INVALIDOPERATION HRESULT değeriyle başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="872e0-129">A call to `SwitchIn` without an earlier call to `SwitchOut` fails with an HRESULT value of HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="872e0-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="872e0-130">Requirements</span></span>  
 <span data-ttu-id="872e0-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="872e0-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="872e0-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="872e0-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="872e0-133">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="872e0-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="872e0-134">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="872e0-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="872e0-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="872e0-135">See also</span></span>

- [<span data-ttu-id="872e0-136">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="872e0-136">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="872e0-137">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="872e0-137">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="872e0-138">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="872e0-138">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="872e0-139">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="872e0-139">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
