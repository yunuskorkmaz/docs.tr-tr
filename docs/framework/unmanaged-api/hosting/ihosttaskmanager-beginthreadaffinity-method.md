---
title: "IHostTaskManager::BeginThreadAffinity Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostTaskManager.BeginThreadAffinity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::BeginThreadAffinity
helpviewer_keywords:
- IHostTaskManager::BeginThreadAffinity method [.NET Framework hosting]
- BeginThreadAffinity method [.NET Framework hosting]
ms.assetid: fea3ab88-ce41-4c5a-847b-bb78cd748da6
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9c86473fba6447bc97619aeb6a6d7b10472120fc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskmanagerbeginthreadaffinity-method"></a><span data-ttu-id="9f62d-102">IHostTaskManager::BeginThreadAffinity Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f62d-102">IHostTaskManager::BeginThreadAffinity Method</span></span>
<span data-ttu-id="9f62d-103">Yönetilen kod konak bir süre içinde geçerli görev başka bir işletim sistemi iş parçacığına taşınmalıdır değil girme bildirir.</span><span class="sxs-lookup"><span data-stu-id="9f62d-103">Notifies the host that managed code is entering a period in which the current task must not be moved to another operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f62d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9f62d-104">Syntax</span></span>  
  
```  
HRESULT BeginThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="9f62d-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9f62d-105">Return Value</span></span>  
  
|<span data-ttu-id="9f62d-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9f62d-106">HRESULT</span></span>|<span data-ttu-id="9f62d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9f62d-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9f62d-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="9f62d-108">S_OK</span></span>|<span data-ttu-id="9f62d-109">`BeginThreadAffinity`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="9f62d-109">`BeginThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="9f62d-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9f62d-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9f62d-111">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="9f62d-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9f62d-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9f62d-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9f62d-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="9f62d-113">The call timed out.</span></span>|  
|<span data-ttu-id="9f62d-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9f62d-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9f62d-115">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="9f62d-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9f62d-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9f62d-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9f62d-117">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="9f62d-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9f62d-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9f62d-118">E_FAIL</span></span>|<span data-ttu-id="9f62d-119">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="9f62d-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9f62d-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9f62d-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9f62d-121">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="9f62d-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f62d-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9f62d-122">Remarks</span></span>  
 <span data-ttu-id="9f62d-123">CLR genellikle çağırır `IHostTaskManager::BeginThreadAffinity` yapılan bir çağrı bağlamında <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9f62d-123">The CLR typically calls `IHostTaskManager::BeginThreadAffinity` in the context of a call to <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9f62d-124">Karşılık gelen bir çağrı yapılır kadar geçerli görev zamanlanması gerekir değil [Ihosttaskmanager::endthreadaffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md).</span><span class="sxs-lookup"><span data-stu-id="9f62d-124">The current task must not be rescheduled until a corresponding call is made to [IHostTaskManager::EndThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md).</span></span> <span data-ttu-id="9f62d-125">Görevler çıkışı değiştirilebilir, ancak geri anahtarlı olduğunda, bunlar çıkışı anahtarlı aynı işletim sistemi iş parçacığına atanmaları gerekir. İç içe çağrıları `BeginThreadAffinity` çağrısı geçerli görevle başvurduğundan herhangi bir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="9f62d-125">Tasks can be switched out, but when they are switched back in, they must be assigned to the same operating system thread from which they were switched out. Nested calls to `BeginThreadAffinity` have no effect, because the call refers to the current task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f62d-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9f62d-126">Requirements</span></span>  
 <span data-ttu-id="9f62d-127">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f62d-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f62d-128">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9f62d-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9f62d-129">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="9f62d-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9f62d-130">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f62d-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f62d-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9f62d-131">See Also</span></span>  
 [<span data-ttu-id="9f62d-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9f62d-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="9f62d-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9f62d-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="9f62d-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9f62d-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="9f62d-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9f62d-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
