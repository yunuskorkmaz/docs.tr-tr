---
description: ': ICLRTask:: gereksiz Spriorityscheduling yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: e6e1b93b38d86259dc2f405f8512ec1063fe7b3b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781772"
---
# <a name="iclrtaskneedspriorityscheduling-method"></a><span data-ttu-id="41e7c-103">ICLRTask::NeedsPriorityScheduling Yöntemi</span><span class="sxs-lookup"><span data-stu-id="41e7c-103">ICLRTask::NeedsPriorityScheduling Method</span></span>

<span data-ttu-id="41e7c-104">Dışarı aktarılan geçerli görevin, yeniden zamanlama için yüksek öncelikli olarak işaretlenmesi gerekip gerekmediğini belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="41e7c-104">Gets a value that indicates whether the current task, which is being switched out, needs to be marked as a high priority for rescheduling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41e7c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="41e7c-105">Syntax</span></span>  
  
```cpp  
HRESULT NeedsPriorityScheduling (  
    [out] BOOL *pbNeedsPriorityScheduling  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41e7c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="41e7c-106">Parameters</span></span>  

 `pbNeedsPriorityRescheduling`  
 <span data-ttu-id="41e7c-107">[out] `true` konağın geçerli görev örneğini mümkün olan en kısa sürede yeniden zamanlamayı denemesi gerekiyorsa; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="41e7c-107">[out] `true`, if the host should attempt to reschedule the current task instance as soon as possible; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="41e7c-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="41e7c-108">Return Value</span></span>  
  
|<span data-ttu-id="41e7c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="41e7c-109">HRESULT</span></span>|<span data-ttu-id="41e7c-110">Description</span><span class="sxs-lookup"><span data-stu-id="41e7c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="41e7c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="41e7c-111">S_OK</span></span>|<span data-ttu-id="41e7c-112">`NeedsPriorityRescheduling` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="41e7c-112">`NeedsPriorityRescheduling` returned successfully.</span></span>|  
|<span data-ttu-id="41e7c-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="41e7c-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="41e7c-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="41e7c-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="41e7c-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="41e7c-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="41e7c-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="41e7c-116">The call timed out.</span></span>|  
|<span data-ttu-id="41e7c-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="41e7c-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="41e7c-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="41e7c-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="41e7c-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="41e7c-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="41e7c-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="41e7c-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="41e7c-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="41e7c-121">E_FAIL</span></span>|<span data-ttu-id="41e7c-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="41e7c-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="41e7c-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="41e7c-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="41e7c-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="41e7c-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41e7c-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="41e7c-125">Remarks</span></span>  

 <span data-ttu-id="41e7c-126">Görevin çöp toplayıcı tarafından toplanmaya yakın olduğu durumlarda CLR 'nin değerini, `pbNeedsPriorityScheduling` `true` yüksek öncelikli yeniden çizelgeleme belirten olarak olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="41e7c-126">In situations where the task is close to being collected by the garbage collector, the CLR sets the value of `pbNeedsPriorityScheduling` to `true`, indicating high-priority rescheduling.</span></span> <span data-ttu-id="41e7c-127">Bu, konağın görevi hızla yeniden zamanlayabilmesini, böylelikle çöp toplamadaki gecikmelerin olasılığını en aza indirmesini ve ana bilgisayarı ve çalışma zamanının bellek kaynaklarını koruma bölümünde birlikte çalışmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="41e7c-127">This allows the host to reschedule the task quickly, thereby minimizing the potential for delays in garbage collection, and enabling the host and the runtime to cooperate in conserving memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41e7c-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="41e7c-128">Requirements</span></span>  

 <span data-ttu-id="41e7c-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41e7c-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41e7c-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="41e7c-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="41e7c-131">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="41e7c-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="41e7c-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41e7c-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41e7c-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41e7c-133">See also</span></span>

- [<span data-ttu-id="41e7c-134">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="41e7c-134">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="41e7c-135">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="41e7c-135">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="41e7c-136">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="41e7c-136">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="41e7c-137">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="41e7c-137">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
