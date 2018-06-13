---
title: IHostTaskManager::BeginThreadAffinity Yöntemi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a94797e6279a1f1d419b977c22d73ca41bbafc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443382"
---
# <a name="ihosttaskmanagerbeginthreadaffinity-method"></a><span data-ttu-id="fd9ff-102">IHostTaskManager::BeginThreadAffinity Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fd9ff-102">IHostTaskManager::BeginThreadAffinity Method</span></span>
<span data-ttu-id="fd9ff-103">Yönetilen kod konak bir süre içinde geçerli görev başka bir işletim sistemi iş parçacığına taşınmalıdır değil girme bildirir.</span><span class="sxs-lookup"><span data-stu-id="fd9ff-103">Notifies the host that managed code is entering a period in which the current task must not be moved to another operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd9ff-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fd9ff-104">Syntax</span></span>  
  
```  
HRESULT BeginThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="fd9ff-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fd9ff-105">Return Value</span></span>  
  
|<span data-ttu-id="fd9ff-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fd9ff-106">HRESULT</span></span>|<span data-ttu-id="fd9ff-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd9ff-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fd9ff-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="fd9ff-108">S_OK</span></span>|<span data-ttu-id="fd9ff-109">`BeginThreadAffinity` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="fd9ff-109">`BeginThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="fd9ff-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fd9ff-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fd9ff-111">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="fd9ff-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fd9ff-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fd9ff-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fd9ff-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="fd9ff-113">The call timed out.</span></span>|  
|<span data-ttu-id="fd9ff-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fd9ff-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fd9ff-115">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="fd9ff-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fd9ff-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fd9ff-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fd9ff-117">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="fd9ff-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fd9ff-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fd9ff-118">E_FAIL</span></span>|<span data-ttu-id="fd9ff-119">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="fd9ff-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fd9ff-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="fd9ff-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fd9ff-121">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="fd9ff-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd9ff-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fd9ff-122">Remarks</span></span>  
 <span data-ttu-id="fd9ff-123">CLR genellikle çağırır `IHostTaskManager::BeginThreadAffinity` yapılan bir çağrı bağlamında <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fd9ff-123">The CLR typically calls `IHostTaskManager::BeginThreadAffinity` in the context of a call to <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fd9ff-124">Karşılık gelen bir çağrı yapılır kadar geçerli görev zamanlanması gerekir değil [Ihosttaskmanager::endthreadaffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md).</span><span class="sxs-lookup"><span data-stu-id="fd9ff-124">The current task must not be rescheduled until a corresponding call is made to [IHostTaskManager::EndThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md).</span></span> <span data-ttu-id="fd9ff-125">Görevler çıkışı değiştirilebilir, ancak geri anahtarlı olduğunda, bunlar çıkışı anahtarlı aynı işletim sistemi iş parçacığına atanmaları gerekir. İç içe çağrıları `BeginThreadAffinity` çağrısı geçerli görevle başvurduğundan herhangi bir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="fd9ff-125">Tasks can be switched out, but when they are switched back in, they must be assigned to the same operating system thread from which they were switched out. Nested calls to `BeginThreadAffinity` have no effect, because the call refers to the current task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd9ff-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fd9ff-126">Requirements</span></span>  
 <span data-ttu-id="fd9ff-127">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd9ff-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd9ff-128">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fd9ff-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fd9ff-129">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="fd9ff-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fd9ff-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd9ff-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd9ff-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fd9ff-131">See Also</span></span>  
 [<span data-ttu-id="fd9ff-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fd9ff-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="fd9ff-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fd9ff-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="fd9ff-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fd9ff-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="fd9ff-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fd9ff-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
