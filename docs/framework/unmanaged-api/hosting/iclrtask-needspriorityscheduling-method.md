---
title: ICLRTask::NeedsPriorityScheduling Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRTask.NeedsPriorityScheduling
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::NeedsPriorityScheduling
helpviewer_keywords:
- ICLRTask::NeedsPriorityScheduling method [.NET Framework hosting]
- NeedsPriorityScheduling method [.NET Framework hosting]
ms.assetid: 9c9db3f3-26bf-4317-88de-5eb926a22a1d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 91c7235fb8790783b05b217cad755d8eedc88971
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59092701"
---
# <a name="iclrtaskneedspriorityscheduling-method"></a><span data-ttu-id="2eb4c-102">ICLRTask::NeedsPriorityScheduling Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2eb4c-102">ICLRTask::NeedsPriorityScheduling Method</span></span>
<span data-ttu-id="2eb4c-103">Dışarı anahtarlanır, geçerli görevi yeniden zamanlama için bir yüksek öncelikli olarak işaretlenmiş olması gerekip gerekmediğini belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="2eb4c-103">Gets a value that indicates whether the current task, which is being switched out, needs to be marked as a high priority for rescheduling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2eb4c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2eb4c-104">Syntax</span></span>  
  
```  
HRESULT NeedsPriorityScheduling (  
    [out] BOOL *pbNeedsPriorityScheduling  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2eb4c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2eb4c-105">Parameters</span></span>  
 `pbNeedsPriorityRescheduling`  
 <span data-ttu-id="2eb4c-106">[out] `true`, olabildiğince çabuk; Aksi takdirde, geçerli görev örneği yeniden zamanlamak konak denemelidir `false`.</span><span class="sxs-lookup"><span data-stu-id="2eb4c-106">[out] `true`, if the host should attempt to reschedule the current task instance as soon as possible; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2eb4c-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2eb4c-107">Return Value</span></span>  
  
|<span data-ttu-id="2eb4c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2eb4c-108">HRESULT</span></span>|<span data-ttu-id="2eb4c-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2eb4c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2eb4c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2eb4c-110">S_OK</span></span>|<span data-ttu-id="2eb4c-111">`NeedsPriorityRescheduling` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="2eb4c-111">`NeedsPriorityRescheduling` returned successfully.</span></span>|  
|<span data-ttu-id="2eb4c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2eb4c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2eb4c-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="2eb4c-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2eb4c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2eb4c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2eb4c-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="2eb4c-115">The call timed out.</span></span>|  
|<span data-ttu-id="2eb4c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2eb4c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2eb4c-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="2eb4c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2eb4c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2eb4c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2eb4c-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="2eb4c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2eb4c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2eb4c-120">E_FAIL</span></span>|<span data-ttu-id="2eb4c-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="2eb4c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2eb4c-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2eb4c-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2eb4c-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="2eb4c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2eb4c-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2eb4c-124">Remarks</span></span>  
 <span data-ttu-id="2eb4c-125">Görev çöp toplayıcısı tarafından toplanmış yakın olduğu durumlarda, CLR değerini ayarlar `pbNeedsPriorityScheduling` için `true`, yüksek öncelikli kullanılabilirliğiyle belirten.</span><span class="sxs-lookup"><span data-stu-id="2eb4c-125">In situations where the task is close to being collected by the garbage collector, the CLR sets the value of `pbNeedsPriorityScheduling` to `true`, indicating high-priority rescheduling.</span></span> <span data-ttu-id="2eb4c-126">Bu görev hızlı bir şekilde yeniden zamanlamak için ana böylece atık toplamada gecikmeler olasılığını en aza indirmek ve konak ve çalışma zamanı bellek kaynakları koruma işbirliği yapmayı etkinleştirme sağlar.</span><span class="sxs-lookup"><span data-stu-id="2eb4c-126">This allows the host to reschedule the task quickly, thereby minimizing the potential for delays in garbage collection, and enabling the host and the runtime to cooperate in conserving memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2eb4c-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2eb4c-127">Requirements</span></span>  
 <span data-ttu-id="2eb4c-128">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2eb4c-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2eb4c-129">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2eb4c-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2eb4c-130">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="2eb4c-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2eb4c-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2eb4c-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2eb4c-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2eb4c-132">See also</span></span>

- [<span data-ttu-id="2eb4c-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2eb4c-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="2eb4c-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2eb4c-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="2eb4c-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2eb4c-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="2eb4c-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2eb4c-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
