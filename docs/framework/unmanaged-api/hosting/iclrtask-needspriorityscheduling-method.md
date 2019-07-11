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
ms.openlocfilehash: 9503e5aeeb1b59c8e62cab20736ea6ab7d5f629f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758924"
---
# <a name="iclrtaskneedspriorityscheduling-method"></a><span data-ttu-id="75094-102">ICLRTask::NeedsPriorityScheduling Yöntemi</span><span class="sxs-lookup"><span data-stu-id="75094-102">ICLRTask::NeedsPriorityScheduling Method</span></span>
<span data-ttu-id="75094-103">Dışarı anahtarlanır, geçerli görevi yeniden zamanlama için bir yüksek öncelikli olarak işaretlenmiş olması gerekip gerekmediğini belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="75094-103">Gets a value that indicates whether the current task, which is being switched out, needs to be marked as a high priority for rescheduling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75094-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="75094-104">Syntax</span></span>  
  
```cpp  
HRESULT NeedsPriorityScheduling (  
    [out] BOOL *pbNeedsPriorityScheduling  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75094-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="75094-105">Parameters</span></span>  
 `pbNeedsPriorityRescheduling`  
 <span data-ttu-id="75094-106">[out] `true`, olabildiğince çabuk; Aksi takdirde, geçerli görev örneği yeniden zamanlamak konak denemelidir `false`.</span><span class="sxs-lookup"><span data-stu-id="75094-106">[out] `true`, if the host should attempt to reschedule the current task instance as soon as possible; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="75094-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="75094-107">Return Value</span></span>  
  
|<span data-ttu-id="75094-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="75094-108">HRESULT</span></span>|<span data-ttu-id="75094-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="75094-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="75094-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="75094-110">S_OK</span></span>|<span data-ttu-id="75094-111">`NeedsPriorityRescheduling` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="75094-111">`NeedsPriorityRescheduling` returned successfully.</span></span>|  
|<span data-ttu-id="75094-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="75094-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="75094-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="75094-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="75094-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="75094-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="75094-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="75094-115">The call timed out.</span></span>|  
|<span data-ttu-id="75094-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="75094-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="75094-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="75094-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="75094-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="75094-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="75094-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="75094-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="75094-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="75094-120">E_FAIL</span></span>|<span data-ttu-id="75094-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="75094-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="75094-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="75094-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="75094-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="75094-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75094-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="75094-124">Remarks</span></span>  
 <span data-ttu-id="75094-125">Görev çöp toplayıcısı tarafından toplanmış yakın olduğu durumlarda, CLR değerini ayarlar `pbNeedsPriorityScheduling` için `true`, yüksek öncelikli kullanılabilirliğiyle belirten.</span><span class="sxs-lookup"><span data-stu-id="75094-125">In situations where the task is close to being collected by the garbage collector, the CLR sets the value of `pbNeedsPriorityScheduling` to `true`, indicating high-priority rescheduling.</span></span> <span data-ttu-id="75094-126">Bu görev hızlı bir şekilde yeniden zamanlamak için ana böylece atık toplamada gecikmeler olasılığını en aza indirmek ve konak ve çalışma zamanı bellek kaynakları koruma işbirliği yapmayı etkinleştirme sağlar.</span><span class="sxs-lookup"><span data-stu-id="75094-126">This allows the host to reschedule the task quickly, thereby minimizing the potential for delays in garbage collection, and enabling the host and the runtime to cooperate in conserving memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75094-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="75094-127">Requirements</span></span>  
 <span data-ttu-id="75094-128">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75094-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75094-129">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="75094-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="75094-130">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="75094-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="75094-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75094-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75094-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75094-132">See also</span></span>

- [<span data-ttu-id="75094-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="75094-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="75094-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="75094-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="75094-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="75094-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="75094-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="75094-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
