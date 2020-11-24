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
ms.openlocfilehash: 86e0899b883f09f2e7b27c0f957e943deb73bb66
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690804"
---
# <a name="iclrtaskneedspriorityscheduling-method"></a><span data-ttu-id="062d8-102">ICLRTask::NeedsPriorityScheduling Yöntemi</span><span class="sxs-lookup"><span data-stu-id="062d8-102">ICLRTask::NeedsPriorityScheduling Method</span></span>

<span data-ttu-id="062d8-103">Dışarı aktarılan geçerli görevin, yeniden zamanlama için yüksek öncelikli olarak işaretlenmesi gerekip gerekmediğini belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="062d8-103">Gets a value that indicates whether the current task, which is being switched out, needs to be marked as a high priority for rescheduling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="062d8-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="062d8-104">Syntax</span></span>  
  
```cpp  
HRESULT NeedsPriorityScheduling (  
    [out] BOOL *pbNeedsPriorityScheduling  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="062d8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="062d8-105">Parameters</span></span>  

 `pbNeedsPriorityRescheduling`  
 <span data-ttu-id="062d8-106">[out] `true` konağın geçerli görev örneğini mümkün olan en kısa sürede yeniden zamanlamayı denemesi gerekiyorsa; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="062d8-106">[out] `true`, if the host should attempt to reschedule the current task instance as soon as possible; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="062d8-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="062d8-107">Return Value</span></span>  
  
|<span data-ttu-id="062d8-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="062d8-108">HRESULT</span></span>|<span data-ttu-id="062d8-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="062d8-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="062d8-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="062d8-110">S_OK</span></span>|<span data-ttu-id="062d8-111">`NeedsPriorityRescheduling` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="062d8-111">`NeedsPriorityRescheduling` returned successfully.</span></span>|  
|<span data-ttu-id="062d8-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="062d8-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="062d8-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="062d8-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="062d8-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="062d8-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="062d8-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="062d8-115">The call timed out.</span></span>|  
|<span data-ttu-id="062d8-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="062d8-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="062d8-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="062d8-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="062d8-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="062d8-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="062d8-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="062d8-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="062d8-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="062d8-120">E_FAIL</span></span>|<span data-ttu-id="062d8-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="062d8-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="062d8-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="062d8-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="062d8-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="062d8-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="062d8-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="062d8-124">Remarks</span></span>  

 <span data-ttu-id="062d8-125">Görevin çöp toplayıcı tarafından toplanmaya yakın olduğu durumlarda CLR 'nin değerini, `pbNeedsPriorityScheduling` `true` yüksek öncelikli yeniden çizelgeleme belirten olarak olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="062d8-125">In situations where the task is close to being collected by the garbage collector, the CLR sets the value of `pbNeedsPriorityScheduling` to `true`, indicating high-priority rescheduling.</span></span> <span data-ttu-id="062d8-126">Bu, konağın görevi hızla yeniden zamanlayabilmesini, böylelikle çöp toplamadaki gecikmelerin olasılığını en aza indirmesini ve ana bilgisayarı ve çalışma zamanının bellek kaynaklarını koruma bölümünde birlikte çalışmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="062d8-126">This allows the host to reschedule the task quickly, thereby minimizing the potential for delays in garbage collection, and enabling the host and the runtime to cooperate in conserving memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="062d8-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="062d8-127">Requirements</span></span>  

 <span data-ttu-id="062d8-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="062d8-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="062d8-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="062d8-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="062d8-130">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="062d8-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="062d8-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="062d8-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="062d8-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="062d8-132">See also</span></span>

- [<span data-ttu-id="062d8-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="062d8-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="062d8-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="062d8-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="062d8-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="062d8-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="062d8-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="062d8-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
